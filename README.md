# Steam Play Hours Simulator

> An alternative runnable placeholder for games in your Steam library so you can let the actual game rest while still accumulating play hours in Steam.

This application is a lightweight, distraction-free timer that **replaces** a game's executable to fool Steam into thinking the game is running. While it runs, Steam records active playtime for that entry. The window simply shows an always‑advancing elapsed counter in `DD : HH : MM : SS` with subtle animation and optional offset. It does **not** hook, fake processes, touch the filesystem beyond normal library usage, or communicate over the network.

Use it if you've migrated stores, lost legacy hours, or want to preserve hardware/energy by not keeping a heavy game executable open just to accumulate time. Close it any moment—no state is persisted unless you extend it.

---

## ⚠️ IMPORTANT WARNINGS ⚠️

**READ CAREFULLY BEFORE USING:**

1. **🚨 THIS MODIFIES YOUR GAME FILES** - You will be renaming the original game executable and replacing it with SteamTimer. Make backups first!

2. **🚨 YOU CANNOT PLAY THE ACTUAL GAME** while using SteamTimer. This tool is purely for accumulating hours when you're NOT playing.

3. **🚨 STEAM WILL THINK THE GAME IS RUNNING** - This fools Steam's process detection. Use responsibly.

4. **🚨 POTENTIAL TOS VIOLATIONS** - Purposefully inflating playtime may violate platform Terms of Service, achievements integrity expectations, or community norms. You alone are responsible for how you use this tool.

5. **🚨 VERIFY GAME EXECUTABLE LOCATION** - Make absolutely sure you're modifying the correct executable that Steam launches, not a launcher or updater.

6. **🚨 REVERTING** - To play the game again, you'll need to rename the original executable back to its original name and remove SteamTimer.exe.

---

## Disclaimer

You alone are responsible for how you use this tool. It transmits nothing; it just counts locally. However, manipulating playtime tracking may have consequences with your Steam account or game community standing. **USE AT YOUR OWN RISK.**

---
**Project Meta**

| Item | Value |
|------|-------|
| Language | Python 3.11+ (tested) |
| GUI Toolkit | PySide6 (Qt 6) |
| Primary Dependency | `PySide6>=6.7.0,<7.0.0` |
| Packaging (example) | PyInstaller (`--onefile --windowed`) |
| License | The Unlicense (Public Domain) |
| Platforms | Windows (primary), should also run on macOS / Linux with Qt libs |
| Author Credit | CodeKokeshi |
| Project Type | Single-file utility (no persistence) |

---

## Quick Start
```powershell
python -m venv .venv
.# Activate virtual environment
./.venv/Scripts/Activate.ps1
pip install -r requirements.txt
python main.py
```

## Features
- Clean dark UI built with PySide6 (Qt 6)
- Large live-updating timer (days:hours:minutes:seconds)
- Optional starting offset (`--offset-hours` or `--offset-seconds`)
- Always-on-top toggle
- Reset (with confirmation)
- Subtle animated pulse (can disable via `--no-accent-pulse`)
- Compact mode (`--compact`)

## Advanced Run Examples

### Start with an offset (existing hours)
```powershell
python main.py --offset-hours 12.5
# or
python main.py --offset-seconds 4500
```

### Disable pulsing animation
```powershell
python main.py --no-accent-pulse
```

### Compact window
```powershell
python main.py --compact
```

## Build a Standalone EXE
Install PyInstaller:
```powershell
pip install pyinstaller
```
Build:
```powershell
pyinstaller --noconfirm --onefile --windowed --name "Steam Play Hours Simulator" main.py
```
The executable will appear under `dist/Steam Play Hours Simulator.exe`.

(If the name with spaces causes issues adding to Steam, you can rename the EXE.)

## How to Use with Steam Games

**⚠️ CRITICAL: Follow these steps exactly. Make backups before modifying any files! ⚠️**

### Step 1: Locate the Game Executable
Find the actual game executable (.exe) that Steam launches. This is typically in:
- Steam library folder: `C:\Program Files (x86)\Steam\steamapps\common\[GameName]\`
- Right-click the game in Steam > Properties > Installed Files > Browse
- Look for the main `.exe` file (not launchers, updaters, or other utilities)

**⚠️ IMPORTANT:** Make sure this is the EXACT executable that Steam runs, not a launcher!

### Step 2: Rename the Original Game Executable
Rename the original game's `.exe` file by adding extra characters at the end.

**Example:**
- Original: `game.exe`
- Renamed: `game_original.exe` or `game.exe.bak`

This preserves the original game file so you can restore it later.

### Step 3: Replace with SteamTimer
1. Build or download `SteamTimer.exe` (see "Build a Standalone EXE" section below) or download from the releases.
2. Rename `SteamTimer.exe` to match the **original game executable name** exactly
   - Example: If the game was `game.exe`, rename SteamTimer to `game.exe`
3. Copy this renamed file to the game's directory (where you renamed the original)

**This fools Steam into thinking SteamTimer is the actual game!**

### Step 4: Launch Through Steam
1. Launch the game normally through Steam
2. Steam will now run SteamTimer instead of the actual game
3. The timer window will appear and start counting
4. Steam will accumulate play hours while the timer runs
5. The app displays elapsed time (it's just a timer, not actually playing the game)

### Reverting Back to Normal
To play the actual game again:
1. Delete or rename the `SteamTimer.exe` from the game directory
2. Rename the original game executable back to its original name
   - Example: `game_original.exe` → `game.exe`
3. Launch normally through Steam

## Command Line Help
```powershell
python main.py --help
```

## License
Released under **The Unlicense**. Public domain dedication—do anything you want; attribution appreciated but not required.

See `LICENSE` for the full text.
