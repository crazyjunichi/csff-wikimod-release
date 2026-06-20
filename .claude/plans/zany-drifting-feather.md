# 命名重构：WebWiki → LiveWiki

## Context

WikiMod 内嵌 HTTP 服务器 + SPA 模块当前命名为 "WebWiki"，与本仓库及上游用户文档已经使用的对外名称 "Live Wiki" 不一致：

- `doc/userdoc/en/features.md`、`changelog.md` 等已经用 **"Live Wiki"** 描述这个功能
- 而代码层全部是 `WebWiki*`（命名空间路径、类、配置 key、资源目录、日志前缀）

本次重构把代码层、构建脚本、设计文档、历史 plan 全部统一到 **LiveWiki**，让对外宣传名与对内标识符一致，避免后续维护时出现两套术语。

**重要边界**：`WebView` / `WebViewBrowser` / `WebView2Runtime` / `WebViewEnabled` / `WikiBrowser.exe` / `WebView2Loader.dll` 是嵌入式浏览器组件（用于在游戏窗口里弹出 SPA 页面），与 LiveWiki 是不同模块，**不在本次重命名范围内**——它们恰好住在 `src/WebWiki/` 目录下，目录改名后位置跟着变，但类名/文件名保持原样。

## 范围清单

### 1. 代码标识符与文件路径

| 当前 | 改为 |
|---|---|
| `src/WebWiki/` | `src/LiveWiki/` |
| `src/WebWiki/WebWikiMod.cs` | `src/LiveWiki/LiveWikiMod.cs` |
| `src/WebWiki/WebWikiUpdatePatch.cs` | `src/LiveWiki/LiveWikiUpdatePatch.cs` |
| 类 `WebWikiMod` | `LiveWikiMod` |
| 类 `WebWikiUpdatePatch` | `LiveWikiUpdatePatch` |
| 类 `WebWikiMainThreadRunner` | `LiveWikiMainThreadRunner` |
| GameObject 名 `"WebWikiMainThreadRunner"` | `"LiveWikiMainThreadRunner"` |

`src/WebWiki/` 下其他文件（`WebServer.cs`、`WikiRouter.cs`、`WikiDataService.cs`、`Endpoints/`、`EntitySerializers/` 等）随目录搬到 `src/LiveWiki/`，文件名保持。`WebView2Runtime.cs`、其中的 `WebViewBrowser` 类、嵌入资源 `WikiMod.Resources.native.WebView2Loader.dll` 等保持原样。

### 2. 配置 key（含字符串值）

[src/Core/ModConfigs.cs:203-204](src/Core/ModConfigs.cs#L203-L204)

```csharp
// 改前
public const string WebWikiEnabled = "WebWikiEnabled";
public const string WebWikiPort = "WebWikiPort";

// 改后
public const string LiveWikiEnabled = "LiveWikiEnabled";
public const string LiveWikiPort = "LiveWikiPort";
```

[src/Core/ModConfigs.cs:1211-1231](src/Core/ModConfigs.cs#L1211-L1231) 的 `#region WebWiki`、`I18n.t("WebWiki 服务器", "WebWiki Server")`、`I18n.t("WebWiki 端口", "WebWiki Port")`、`WebWikiMod.DefaultPort` 等同步改名。

**破坏性影响**：已有用户的 BepInEx 配置文件中的 `[Features] WebWikiEnabled` / `WebWikiPort` 条目失效，回到默认值。这是已与用户确认的取舍。

`WikiMode`、`WebViewEnabled` 这两个 key 不动。

### 3. 资源目录与嵌入资源前缀

| 当前 | 改为 |
|---|---|
| `Resources/webwiki/` | `Resources/livewiki/` |
| 嵌入资源前缀 `WikiMod.Resources.webwiki.` | `WikiMod.Resources.livewiki.` |

涉及文件：

- [src/WebWiki/Endpoints/StaticFileEndpoint.cs:12](src/WebWiki/Endpoints/StaticFileEndpoint.cs#L12) `ResourcePrefix`
- [src/WebWiki/Endpoints/StaticFileEndpoint.cs:46,82,87,89](src/WebWiki/Endpoints/StaticFileEndpoint.cs#L46) 三处提示文字中的 `webwiki manifest` / `Resources/webwiki/`
- [src/WebWiki/Endpoints/SpriteEndpoint.cs:85](src/WebWiki/Endpoints/SpriteEndpoint.cs#L85) `WikiMod.Resources.webwiki.None.png`

`Resources/webwiki/` 目录里的内容（200.html、index.html、_nuxt/、_fonts/、None.png 等 SPA 构建产物）整体迁到 `Resources/livewiki/`。`_manifest.txt` 由构建生成，不需要手工迁移内容（迁完目录后下次 build 会重写）。

### 4. csproj 构建脚本

[WikiMod.csproj:128-136](WikiMod.csproj#L128-L136)

```xml
<!-- 改前 -->
<Target Name="GenerateWebWikiManifest" BeforeTargets="PrepareForBuild"
        Condition="Exists('Resources\webwiki\index.html')">
  <ItemGroup>
    <WebWikiFiles Include="Resources\webwiki\**\*.*" Exclude="Resources\webwiki\_manifest.txt" />
  </ItemGroup>
  <WriteLinesToFile File="Resources\webwiki\_manifest.txt"
                   Lines="@(WebWikiFiles->'%(RecursiveDir)%(Filename)%(Extension)')"
                   Overwrite="true" />
</Target>

<!-- 改后 -->
<Target Name="GenerateLiveWikiManifest" BeforeTargets="PrepareForBuild"
        Condition="Exists('Resources\livewiki\index.html')">
  <ItemGroup>
    <LiveWikiFiles Include="Resources\livewiki\**\*.*" Exclude="Resources\livewiki\_manifest.txt" />
  </ItemGroup>
  <WriteLinesToFile File="Resources\livewiki\_manifest.txt"
                   Lines="@(LiveWikiFiles->'%(RecursiveDir)%(Filename)%(Extension)')"
                   Overwrite="true" />
</Target>
```

### 5. 日志类别字符串

| 当前 | 改为 |
|---|---|
| `Logger.CreateLocal("WebWiki")` | `Logger.CreateLocal("LiveWiki")` |
| 日志中 `[WebWiki] ...` 前缀 | `[LiveWiki] ...` |
| HttpListener 线程名 `"WebWiki-HttpListener"` | `"LiveWiki-HttpListener"` |

涉及：[src/WebWiki/WebWikiMod.cs:15](src/WebWiki/WebWikiMod.cs#L15)、[src/WebWiki/WebServer.cs:20,49](src/WebWiki/WebServer.cs#L20)、`WebWikiMod.cs` 的两处 `[WebWiki] 主线程...` 日志、`Endpoints/SpriteEndpoint.cs`、`Endpoints/StaticFileEndpoint.cs`、`LocalizationHelper.cs:45`。

`Logger.CreateLocal("WebViewBrowser")` 不改（独立模块）。

### 6. 调用点

外部对 `WebWikiMod` 的引用：

- [src/GameMods/GameLoadMod.cs:108-109](src/GameMods/GameLoadMod.cs#L108-L109) 的 `WebWikiMod.Initialize()` 与日志字符串
- [src/WebWiki/WikiRouter.cs:21](src/WebWiki/WikiRouter.cs#L21) `ModConfigKey.WebWikiPort, WebWikiMod.DefaultPort`

### 7. .gitignore

[.gitignore:8](.gitignore#L8) 注释行：`# Resources/webwiki/` → `# Resources/livewiki/`

### 8. 文档与历史 plans

- [doc/WebWiki-Design.md](doc/WebWiki-Design.md) → 重命名为 `doc/LiveWiki-Design.md`，文中所有 `WebWiki` / `src/WebWiki/` / `WebWikiDataProcessor` 替换为对应 LiveWiki 形式
- `.claude/plans/` 下 10 个含 `WebWiki` 的历史 plan 全部做替换（用户要求）：
  - `mighty-inventing-pixel.md`、`ethereal-finding-coral.md`、`cuddly-puzzling-grove.md`、`glittery-mixing-star.md`、`webwiki-webwikidatacache-datastore-data-moonlit-bengio.md`、`elegant-meandering-chipmunk.md`、`validated-gathering-eich.md`、`stateless-swinging-diffie.md`、`generic-sauteeing-candle.md`、`immutable-brewing-flamingo.md`
  - 历史 plan 文件名带 `webwiki` 的（`webwiki-webwikidatacache-...md`）保持文件名不变，只改内容——文件名是历史归档标识，重命名会丢失关联。

### 9. 不改动的范围（明确边界）

- `doc/userdoc/**` 中所有 "web wiki"（小写空格描述性词）—— 这是指**线上**公网 wiki，不是本模块名
- `Resources/WikiMod.html`（userdoc 构建产物，含上述描述）
- `WebView` / `WebViewBrowser` / `WebView2Runtime` / `WebView2Loader.dll` / `WebViewEnabled` / `WikiBrowser.exe` —— 嵌入浏览器模块
- `cswiki-gen` 仓库（这是上游静态站点生成器，跨仓库不归本次重构）
- Git 历史与 commit message

## 执行顺序

按依赖顺序，分 5 步：

1. **重命名目录**：`git mv src/WebWiki src/LiveWiki`、`git mv Resources/webwiki Resources/livewiki`、`git mv doc/WebWiki-Design.md doc/LiveWiki-Design.md`
2. **重命名文件**：`git mv src/LiveWiki/WebWikiMod.cs src/LiveWiki/LiveWikiMod.cs`、`git mv src/LiveWiki/WebWikiUpdatePatch.cs src/LiveWiki/LiveWikiUpdatePatch.cs`
3. **改 C# 标识符与字符串字面量**：在 `src/LiveWiki/` 内部 + `src/Core/ModConfigs.cs` + `src/GameMods/GameLoadMod.cs` 做替换
4. **改构建脚本**：`WikiMod.csproj` 中 `GenerateWebWikiManifest` Target、`WebWikiFiles` ItemGroup、路径常量
5. **改文档与归档**：`doc/LiveWiki-Design.md` 内容替换、10 份 `.claude/plans/*.md` 内容替换、`.gitignore` 注释行

每步结束都跑一次 `dotnet build` 确保不破坏编译——但实际编译失败只会在第 3 步之后才能跑，所以前两步完成后立即跟进第 3 步。

## 验证

1. `dotnet build` 通过，无 `WebWiki` / `webwiki` 残留导致的标识符或资源缺失错误
2. `grep -rni "webwiki" src/ Resources/ WikiMod.csproj .gitignore doc/WebWiki-Design.md doc/LiveWiki-Design.md 2>/dev/null` 应只在以下情况出现匹配：
   - `doc/userdoc/**`、`Resources/WikiMod.html` 中的描述性 "web wiki"（保留）
   - 历史 commit message（不可改）
3. 启动游戏，进入主菜单/游戏内：
   - BepInEx 控制台出现 `[LiveWiki]` 日志（不再有 `[WebWiki]`）
   - 浏览器访问 `http://localhost:24680/` SPA 正常加载
   - 命中 `/sprite/...` 端点能返回 PNG
   - `/api/version`、`/api/searchData` 等 API 正常返回
4. 检查 `BepInEx/config/WikiMod.cfg`，应出现 `[Features] LiveWikiEnabled` / `LiveWikiPort` 项；旧的 `WebWikiEnabled` / `WebWikiPort` 如已存在会被忽略（这是已知破坏性影响）

## 风险与回滚

- **破坏性**：已发布版本用户的 BepInEx 配置中 `WebWikiEnabled` / `WebWikiPort` 失效（用户已确认接受）
- **遗漏风险**：模块横跨 14+ 文件 + csproj + 构建产物路径，最终验证以 `grep -rni webwiki` 全仓库扫描兜底
- **回滚**：本次改动均在单个 commit 内，必要时 `git revert` 即可
