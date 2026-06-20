# WikiMod

*Card Survival: Fantasy Forest* 的 BepInEx 模组。内置 Wiki、地图、数值显示、角色信息面板、快速查找、脚本系统、万能修改器、徽章系统等。

## 安装

1. 安装 [BepInEx 5](https://github.com/BepInEx/BepInEx)
2. 把 `WikiMod.dll` 放入游戏目录下的 `BepInEx/plugins`
3. 启动游戏，在设置中开关主要功能；高级功能在万能修改器（默认 `` ` `` 键）中查看

## 文档

- **玩家文档**：解压 zip 后双击 `WikiMod.html`，或在游戏内"WikiMod 介绍"中查看
- **简化功能总览**（供 Mod 发布站、Wiki、论坛复制粘贴）：[doc/Introduction.md](doc/Introduction.md)
- **脚本系统指南**：[doc/scriptguide/zh/scriptguide.md](doc/scriptguide/zh/scriptguide.md)（英文版同目录 `en/scriptguide.md`）

## 开发

```bash
dotnet build                # Debug
dotnet build -c Release     # Release
```

构建会自动生成 `Resources/WikiMod.html`（需要 PowerShell 7+）。开发约定见 [CLAUDE.md](CLAUDE.md)。
