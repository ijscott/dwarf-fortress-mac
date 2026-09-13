# Dwarf Fortress — macOS Installer

One-command installer for **Dwarf Fortress** on macOS with Steam Premium graphics, audio, and DFHack.

> Runs DF Classic (free) using the Steam Windows binary under Wine, with all Premium assets pulled from your Steam account.

## What you get

- ✅ Steam Premium graphics (graphical tilesets, creature sprites, UI art)
- ✅ Steam Premium audio (full soundtrack, SFX, ambience)
- ✅ DFHack 53.16-r1.1
- ✅ Double-clickable `Dwarf Fortress.app`
- ✅ Settings → Done works (no crash)

## Requirements

- macOS 12+
- [Homebrew](https://brew.sh)
- [Whisky](https://github.com/Whisky-App/Whisky/releases) — installed and opened at least once
- A Steam account that owns [Dwarf Fortress](https://store.steampowered.com/app/975370/Dwarf_Fortress/)

## Install

```bash
curl -fsSL https://raw.githubusercontent.com/ijscott/dwarf-fortress-mac/main/install.sh | bash
```

Or clone and run:

```bash
git clone https://github.com/ijscott/dwarf-fortress-mac.git
bash dwarf-fortress-mac/install.sh
```

The installer will:

1. Check prerequisites (Homebrew, SteamCMD, Whisky)
2. Download DF Classic base files from bay12games.com
3. Prompt for your Steam login to download Premium content (~1 GB)
4. Set up a Wine bottle with DXVK
5. Install DFHack
6. Patch audio/graphics configuration
7. Create `~/Applications/Dwarf Fortress.app`
8. Verify everything installed correctly

## Options

```bash
# Install to a custom directory
INSTALL_DIR=~/Games/DwarfFortress bash install.sh
```

The app always installs to `~/Applications/Dwarf Fortress.app`.

## How it works

DF Classic and DF Steam share the same codebase but the Classic binary ships without Premium assets. This installer:

- Uses the **Steam Windows binary** (downloaded via SteamCMD) which has the full audio/graphics engine
- Downloads Premium asset depots from Steam (requires your account)
- Runs everything under [Whisky](https://github.com/Whisky-App/Whisky)'s Wine with DXVK (D3D11 → Metal)
- Stubs out two Wine DLLs (`msvcp140_atomic_wait.dll`, `steam_api64.dll`) that Wine 7.7 doesn't implement correctly

## Troubleshooting

**Game doesn't launch:** Check `/tmp/df_launch.log` for Wine errors.

**Black title screen:** Make sure Whisky has been opened at least once so Wine libraries are downloaded.

**No audio:** Go to Settings → Sound in-game and confirm volumes are set. First launch may take a moment for DXVK shader compilation.

**Settings → Done crashes:** The installer patches this automatically. If it recurs, re-run the installer.

## Legal

You must own Dwarf Fortress on Steam. This installer downloads content you're licensed to use — it doesn't redistribute any game files.

Dwarf Fortress is © Bay 12 Games.
