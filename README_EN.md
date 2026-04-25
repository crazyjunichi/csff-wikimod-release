# 📚 Welcome to WikiMod

## How to Use
Install BepInEx and place WikiMod.dll in the Plugin folder.
After entering the game, you can enable or disable the main mod features from the game’s Settings menu.
More advanced features can be enabled in Anything Mod (default hotkey: `).

## Latest Update V2.6.3 (2026/04/19)
- Compatible with 0.62d
- Added buttons in the F2 screen to copy debug info and open the save-report folder
- [Anything Mod] Fixed missing essence dropdown when generating cards
- [Anything Mod] Added a quick-action button toggle; highlight and hotkeys apply only when enabled
- [Anything Mod] Compatible with ModCore loading flow to support mod item queries
- [Anything Mod] Fixed errors when dragging sliders in Anything Mod
- [Anything Mod] Supports resetting a single hotkey independently
- [Detail Tooltip] Fixed incorrect display of skill decay names
- [Detail Tooltip] Sorted skill decay entries
- [Detail Tooltip] Fixed incorrect attribute transfer display
- [Detail Tooltip] Fixed errors when value change rate is 0
- [Detail Tooltip] Fixed incorrect hour display in NPC respawn conditions
- [Detail Tooltip] Added current-value display when conditions are not met

## ✨ Main Features

### 📖 Built-in WIKI
Click the question mark on most interfaces to open the built-in wiki.
- Shows commonly used information
- Mod-compatible (can display mod card info)

### 🗺️ Game Map
Press `M` in any in-game interface to open the map.
A simplified nearby map is shown in the exploration interface.

#### 🌍 Outdoor Map
- Shows locations of home, farms, traps, and wild animals
- Shows landmarks, plants/animals, and explorable items for each location
- Shows detailed farm/trap status, such as crop maturity and trap trigger state
- Shows built roads
- Shows hunting fences
- Shows animal burrows (fox dens, badger dens)
- Shows caves and carcasses
- Shows animal heatmap. Hover an animal icon to see its common routes; higher frequency appears redder.
- Click the map to move directly to destination, with support for auto-stop when encountering animals.
- Can display map capacity and current map attributes.

#### 🏢 Indoor Map
- Shows multi-floor room structure
- Shows items in each room
- Click room to move quickly

### 🌱 Highlight Crop Status
- Displays water/fertilizer/acidity/soil quality of farms and gardens as progress bars
- Shows safe ranges for each attribute

### 🔔 Alerts
- Alert when animals are about to pass by
- Alert when traps are triggered
- Custom alerts

### 📊 Advanced Character Info Panel
- Press `C` to open
- Overview: shows character info, game records, common statuses, perks
- Equipment: grouped by body part, supports unequip/equip; shows related status effects
- Wounds: grouped by body part; shows related status effects
- Magic: shows current magic equipment, current status bonuses, related status effects
- Skills: categorized display; shows combat move unlock progress
- Physique: shows physical attributes and related effects
- Mind: shows mental status and related effects
- Digestion: shows digestive system status and related effects
- Infection: shows various infection statuses and related effects
- Chemistry: shows various compound/chemical statuses and related effects

### 🔢 Full Detail Tooltip
- Hover to view related values for cards, statuses, perks, and action buttons
- Correctly displays trap chance, action conditions, food score, etc.
- Supports showing unlock conditions for locked cards
- Supports showing conversion pause reasons, container inner liquids, and liquid conversions
- Supports showing compound statuses, phase change timing, and passive status effects
- Supports showing follow-up changes caused by actions and conditions that may reduce required time
- Supports showing attribute transfer and respawn conditions for inactive NPCs
- Supports showing card creation time (can be enabled in advanced settings)

### 🔍 Quick Find
- Press `Alt` to open
- Supports Chinese, pinyin, and initials for search
- In scene view, defaults to searching scene items and jumping to them (including in containers, blueprints, and equipment)
- In blueprint view, search and jump to target blueprints
- In map view, search tags and drops, and highlight matched maps.

### ⚙️ Anything Mod
Press ` (the key below ESC) to activate.

- Search any in-game data
- Get any item with custom stats and enchantments
- Modify any data on existing cards
- View/modify any status and clear staleness. Supports status locking.
- View/modify NPC status and move NPC near player
- Supports changing save mode (Safe / Checkpoint / Realistic)
- Supports save repair and unlocking all blueprints
- Freely shift game time while keeping seasons in sync
- Adjust global rates: blueprint research time / food spoilage speed / skill staleness / animal respawn speed / farm growth speed / garden growth speed / crop Product / garden product / map environment capacity / encounter difficulty
- Fast build and move tools
- Add or remove character perks after game start
- Force complete quests
- Supports modifying feature hotkeys (including native game UI hotkeys)
- Supports getting cards x10
- Supports saving status-lock settings for automatic locking after re-entering the game
- Supports adjusting NPC respawn rate; NPCs can respawn at full health
- Supports speeding up time animations
- Supports "Exit Without Saving"
- Supports Developer Mode for viewing debug data
- Supports not stacking cards with different names
- Supports deleting all cards (delete buttons clickable on all cards when enabled)
- Supports fast house entry (no enter/exit popup confirmation when enabled)
- Supports configuring detail-tooltip delay time to avoid tooltip flickering
- Supports showing active other-mod versions and related configurations
- Supports changing detail-tooltip fonts
- Supports pressing Enter to directly execute the first button action on cards
- More experimental features can be found in More Settings

### ⚡ Quick Add Items
In blueprint/container slot UI, right-click to open menu and quickly add available items.
- Can display item attributes
- Can sort by attribute preference, e.g. prioritize high-quality items

### 📈 Useful Information Display
- Current season, date, and total survival time
- Current temperature
- Current moon phase
- Weather forecast
- Weight info
- Blueprint info
- Salad score
- Highlight crop status

### 🏷️ More Useful Features

- Quick backpack bar
- Support renaming almost all cards
- Can add 6-hour sleep option in rest interface (duration adjustable in advanced settings)
- Hold CTRL + click the arrow on a card to move the whole stack
- Support displaying card attribute change arrows
- Support optimizing default card placement on the ground
- Support disabling animal tracks/blood trails
- Supports updating Chinese translation files
- Show critical marker on weight progress bar


## 📝 Changelog
### V2.6.3 (2026/04/19)
- Compatible with 0.62d.
- Added buttons in the F2 screen to copy debug info and open the save-report folder.
- [Anything Mod] Fixed missing essence dropdown when generating cards.
- [Anything Mod] Added a quick-action button toggle; highlight and hotkeys apply only when enabled.
- [Anything Mod] Compatible with ModCore loading flow to support mod item queries.
- [Anything Mod] Fixed errors when dragging sliders in Anything Mod.
- [Anything Mod] Supports resetting a single hotkey independently.
- [Detail Tooltip] Fixed incorrect display of skill decay names.
- [Detail Tooltip] Sorted skill decay entries.
- [Detail Tooltip] Fixed incorrect attribute transfer display.
- [Detail Tooltip] Fixed errors when value change rate is 0.
- [Detail Tooltip] Fixed incorrect hour display in NPC respawn conditions.
- [Detail Tooltip] Added current-value display when conditions are not met.

### V2.6.0 (2026/04/19)
- [Anything Mod] Supports modifying native game hotkeys
- [Anything Mod] Supports getting cards x10
- [Anything Mod] If NPC respawn rate is modified, NPCs will respawn at full health
- [Anything Mod] Supports defining a hotkey to directly execute the first button action on cards
- [Achievement Badges] Fixed Brewing and Life badges defaulting to quality 0
- [Achievement Badges] Fixed colored lights disappearing after being put away
- Optimized downloading Chinese translation files

### V2.5.4 (2026/04/16)
- Supports updating Chinese translation files.
- [Map] Fixed an issue where roads and hunting fences under construction were also shown on the map.
- [Detail Tooltip] Shows NPC respawn conditions.
- Fixed a potential crash on the loading screen.

### V2.5.2 (2026/04/16)
- [Detail Tooltip] Shows attribute transfer.
- [Anything Mod] Fixed an incorrect upper limit when modifying card attributes.
- Added more null checks for better stability.

### V2.5.1 (2026/04/16)
- Compatible with game 0.62.

### V2.5 (2026/04/09)
- Added Quick Backpack Bar. A quick backpack entry is now shown near the character carry-weight UI; hover shows equipped backpacks and click opens quickly.
- Added remembered on-field card positions. When sorting cards by dragging, relative positions are remembered; cards prefer previous positions when placed again. (Still controlled by "Optimize Card Placement".)
- [Detail Tooltip] Supports liquid change rate and change time display.
- [Detail Tooltip] Supports liquid conversion display inside containers.
- [Detail Tooltip] Supports decay speed display for seasonings/coatings.
- [Detail Tooltip] Supports displaying follow-up changes caused by actions.
- [Map] Added "Unlock All Maps" option. When disabled, only visited maps are shown. Note: this option is OFF by default, and players must enable it manually in game settings to view all maps.
- [Achievement Badges] Added a badge recycle device. If badge quality is unsatisfactory, badges can be recycled and recrafted.
- [Achievement Badges] Added Harvest Badge and Brewing Badge.
- [Achievement Badges] Adjusted crafting requirements for Painting Badge and Cooking Badge.
- [Achievement Badges] Added new badge rewards: Sunny Doll, Color Lights, Dimensional Box, and Muscle Statue.
- [Anything Mod] Anything Mod is now enabled by default.
- [Anything Mod] Added "Developer Mode" toggle. When enabled, some debug data can be viewed.
- [Anything Mod] Added "Detail Tooltip Default Expanded" toggle. When enabled, detailed display is shown by default, and can still be switched to compact via hotkey.
- [Anything Mod] Added "Do Not Stack Cards with Different Names" toggle. When enabled, different logs and different meats no longer stack.
- [Anything Mod] Added "Allow Deleting All Cards" toggle. When enabled, delete buttons are clickable for all cards.
- [Anything Mod] Added "Enable Fast Enter House" toggle. When enabled, entering/exiting houses no longer requires popup confirmation.
- [Anything Mod] Added "Card Tooltip Delay Time" configuration to prevent card number flickering. If issues occur, adjust back to 0.
- [Anything Mod] Added "Other Mod Config" feature to display active other-mod versions and related configurations.
- [Anything Mod] Supports change detail-tooltip fonts.
- [Anything Mod] Fixed an issue where story perks could not be removed correctly.
- [BugFix] Fixed cases where CTRL stack move did not work.

### V2.4 (2026/03/28)
- Added WikiMod achievement series (badges, mysterious statues, rewards)
- [Detail Tooltip] Shows attribute requirements in blueprint conditions
- [Detail Tooltip] Fixed missing display of transferred attribute values
- [Detail Tooltip] Fixed missing display of inner-item change rates during conversions
- [Anything Mod] Supports locking status values and saving auto-lock for next game launch
- [Anything Mod] Environment modifier now supports freely shifting game time while keeping seasons in sync
- [Anything Mod] Added "Speed Up Time Animation" option in More Settings
- [Anything Mod] Added "Exit Without Saving" option in More Settings
- [Map] Optimized map node tooltip details and added current attributes display
- [BugFix] Fixed time hints disappearing after loading a save

### V2.3 (2026/03/22)
- [Detail Tooltip] Action tooltips now show conditions that may reduce required time
- [Detail Tooltip] Card tooltips now show passive status effects
- [Detail Tooltip] NPC tooltips now show animal burrow locations
- [Anything Mod] Added a save repair tool to fix void environments and incorrect environment cards
- [Anything Mod] Save editing now supports unlocking all blueprints
- [Map] Optimized auto-walk to reduce risk of save corruption
- [Map] Improved map screen opening speed
- [Map] Indoor map now displays more room types
- [BugFix] Fixed crops in gardens not displaying progress bars

### V2.2.1 (2026/03/21)
- Fixed crops in gardens not displaying progress bars

### V2.2 (2026/03/20)
- [Detail Tooltip] Shows unlock conditions for locked cards
- [Detail Tooltip] Shows reasons for paused conversions
- [Detail Tooltip] Shows liquids inside containers
- [Detail Tooltip] Shows compound statuses related to status effects
- [Detail Tooltip] Displays status phase change duration
- [Detail Tooltip] Syncs food score with game algorithm, temporarily fixing incorrect scoring for seasoned food
- [Detail Tooltip] Supports displaying card creation time (can be enabled in advanced settings)
- [Detail Tooltip] Fixed incomplete status effect display
- [Detail Tooltip] Optimized quality calculation formula display
- Build Tool can rename rooms, automatically updating the room's main card name and all door names leading to the room
- Added option to show Detail Tooltip only when holding CTRL
- Extended 6-hour light sleep option to various bed types
- Added more error tolerance for better compatibility with other mods
- Fixed blueprint requirement hints including unavailable items

### V2.1 (2026/03/17)
- Added Environment Settings to adjust some global rates in-game. (Entry: Anything Mod -> World Environment Settings)
- Added Move Tool to migrate any object (including rooms) on current map to other maps in one click. (Entry: Anything Mod -> Move Tool)
- Added Build Tool to quickly build rooms, expand rooms, remodel rooms, and add furniture. (Entry: Anything Mod -> Build Tool)
- Added cave and carcass icons on map
- Added map capacity display on map UI and scene card tooltips
- Added 6-hour snooze option in rest interface with configurable duration
- Added mod introduction panel
- Added version compatibility check
- Fixed incorrect prompt display for actions such as fishing
- Fixed incorrect prompt display for forest beast encounters
- Fixed crop progress bars affecting card dragging

### V2.0 (2026/03/12)
- Brand-new numeric tooltip display (covers more scenes and more data). By default this overrides other tooltip mods and can be disabled in settings.
- Added Quick Find feature. Supports searching current map cards, target blueprints, and related maps
- Map now supports hunting fences, animal burrows, and animal heat areas
- Added crop status progress bars and safety thresholds
- Added critical marker on weight progress bar
- Anything Mod now supports changing save mode (Safe / Checkpoint / Realistic)
- Added shortcut key customization for Anything Mod features
- Fixed unreasonable auto-pathing routes on map UI.

### V1.5 (2026/02/04)
- Advanced character info page (press `C`)
- Support renaming all cards
- Show moon phase
- Fixed incorrect animal track toggle
- Fixed issue where modifier could not enchant items
- Fixed field compatibility issues with game version 0.58

### V1.4 (2026/01/28)
- Support detailed encounter logs (off by default)
- Support disabling animal tracks (off by default)
- Support loading wiki Chinese translation patch
- Added dedicated toggle for inactive NPC display on map
- Anything Mod supports editing avatar nickname
- Correctly display max carry weight
- Added focus/delete by card type
- Fixed error when opening Anything Mod if card does not exist
- Fixed occasional blueprint display issues

### V1.3 (2026/01/20)
- Added card stat-change arrow indicators
- Added scene carry-weight display
- Fixed save issue caused by teleport
- Fixed inability to disable trap alarms

### V1.2 (2026/01/18)
- Added alerts (animal incoming alert, trap triggered alert) (off by default)
- Added auto card placement on card entry (off by default)
- Added Ctrl + click arrow to move whole stack
- Indoor map supports click-to-move by room
- Anything Mod updates:
    - Support modifying/deleting card instances (must be enabled in Settings -> Experimental Features)
    - Support sorting on-field cards (must be enabled in Settings -> Experimental Features)
    - Support force-completing quests (must be enabled in Settings -> Experimental Features)
    - Support teleport from map UI (must be enabled in Settings -> Experimental Features)
    - Support perk removal
    - Support custom alerts
    - Support pinning entries to Anything home
    - Fixed inability to modify statuses

### V1.1.0 (2026/01/11)
- Added Anything Mod
- Optimized map, added cave map jump, and detailed trap/crop status display
- Added blueprint info display

### V1.0.6 (2026/01/6)
- Move directly to destination from map
- Show NPC respawn time
- Adjusted sun/moon/stars
- Show weather forecast
- Show weight info

### V1.0.4 (2025/12/05)
- Support official map data
- Map displays detailed animal data and behavior preview
- Optimized date display
- Show detailed temperature info
- Optimized indoor map display

### V1.0.3 (2025/08/10)
- Added quick add item feature
- Added mod settings
- Added food score display
- Indoor map can switch to outdoor map

### V1.0.2 (2025/07/31)
- Added indoor map
- Compatible with CSTI; built-in wiki supports mods
- Added material hints on blueprint UI
- Added date/temperature hints
- Fixed incorrect zoom in exploration map
- Adjusted part of color scheme

### V1.0.1 (2025/07/27)
- Added display for triggered traps / mature fields
- Fixed incorrect display on paved areas

### V1.0.0 (2025/07/20)
- Press M to open in-game map
- Added built-in wiki on card/status detail pages
- Added nearby map display in exploration interface
