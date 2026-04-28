# 🎮 exFAT Image Builder

> Build PS5 exFAT and ffpkg game images — backport, patch, manage, convert

**by DecKerr97** · [Releases](https://github.com/kerrdec97/ps5-exfat-builder/releases) · [Issues](https://github.com/kerrdec97/ps5-exfat-builder/issues)

![Version](https://img.shields.io/badge/version-v1.7.0-4a9eff?style=flat-square)
![Platform](https://img.shields.io/badge/platform-Windows-lightgrey?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

---

## What is it?

A Windows GUI tool for PS5 homebrew — build exFAT and ffpkg game images, auto-backport games to older firmware, manage your game library, send payloads, monitor klogs, and much more. No command line required.

---

## Requirements

| Requirement | Notes |
|---|---|
| **Windows 10 / 11** (64-bit) | Required |
| **OSFMount** | Free — [download here](https://www.osforensics.com/tools/mount-disk-images.html) — required for exFAT builds |
| **.NET 8 Runtime** | Required for ffpkg builds only |
| **PS5 game dump** | Must contain `eboot.bin` in the root folder |

> ⚠️ The app requires **Administrator** privileges. It will prompt automatically on launch.

---

## Features

### 🔨 exFAT Tab
- Queue-based workflow — add multiple games at once or one at a time
- Game name, PPSA ID and version auto-detected
- Real-time progress — file count, GB written, MB/s, ETA
- Estimated build time before starting
- Pre-build checklist — drive root detection, write permissions, eboot.bin, space
- Force Dismount button — uses Windows shell eject
- Post-build dismount retry
- Build log auto-saved, queue save/load

### 📦 ffpkg Tab
- Full UFS2 ffpkg builder via UFS2Tool (bundled)
- Sector size locked at 512 — fixes Windows broken image bug
- Requires .NET 8

### 🧩 Backports Tab — Manual
- Apply backport files to game folder or mounted exFAT image
- Drag and drop, conflict preview, auto backup named after game + date
- File list auto-clears on new target

### ⚡ Backports Tab — Auto Backport (NEW in v1.7.0)
- Automatically patches PS5 ELF executables using the full decrypt/re-sign pipeline
- Powered by Backport.py by Nazky & BestPig — bundled, no install needed
- Select fakelib folder — applied to game/fakelib/ with originals backed up
- Originals snapshot taken before fakelib is applied — only real game files are backed up
- Target SDK selector (4–11) with firmware version labels
- Fakelib path saved automatically for future use
- Patched files applied back to game folder in correct paths
- Backup zips — originals and backported files saved as separate .zip files
- Accessible from Library tab — click any game → ⚡ Auto Backport

### ⚙️ Advanced Tab
- exFAT: cluster size, sector size, copy threads
- ffpkg: block size, fragment size, min free %, bytes per inode

### 🌐 17 Languages
English, Chinese, German, French, Spanish, Portuguese, Japanese, Korean, Russian, Arabic, Italian, Dutch, Polish, Turkish, Thai, Vietnamese, Indonesian

### 📚 Library Tab
- Scan progress bar — live folder count and games found
- Grid / list view with cover art
- Right-click → Add to exFAT Queue, Add to ffpkg Queue, ⚡ Auto Backport

### 💾 My Images Tab
- Scan for .exfat files
- 🔄 Convert to ffpkg — mounts exFAT, builds ffpkg, live progress bar
- Batch upload to PS5

### 🎮 PS5 Manager Tab
- Unified local vs PS5 view
- PS5 storage bar with colour coding

### 📡 FTP Upload / PS5 Browser Tabs
- Upload with live progress, cancel, auto-upload after build
- Full FTP browser — navigate, rename, move, delete, download, upload

### 🗂 File Manager Tab
- Mount .exfat images read-write
- Add, replace, delete files without rebuilding

### 📤 Extract Tab
- Extract .exfat back to a folder

### 📦 Payload Manager Tab
- Save and send .elf / .bin payloads to PS5 via TCP

### 📋 Klog Monitor Tab
- Stream PS5 kernel logs live via TCP
- Timestamps, pause/resume, keyword filter, export

### ⚙ Settings Tab
- OSFMount custom path, temp folder, logs folder
- PS5 FTP — IP, port, auto-detect
- Language, theme, notifications

### General
- Auto-update with retry logic and working directory fix
- Crash reporter — saves log, copies to clipboard
- End-of-tab indicator on every scrollable tab

---

## Building from source

```bash
pip install pyinstaller pillow
build.bat
```

---

## Troubleshooting

| Problem | Fix |
|---|---|
| OSFMount not detected | Settings → OSFMount → Browse for `osfmount.com` |
| Auto-update crashes on restart | Fixed in v1.6.3+ — update manually this time |
| ffpkg build fails | Install .NET 8 Runtime |
| Image runs out of space | Fixed in v1.6.2+ — size margins increased |
| Output not found after build | Check antivirus isn't quarantining .exfat files |
| FTP won't connect | Make sure homebrew FTP is running on PS5 |
| Crash on startup | Log at `~/exfat_builder_logs/` — share on GitHub Issues |

---

## Credits

| Contribution | Credit |
|---|---|
| PS5 Auto Backport pipeline (Backport.py, src/) | **Nazky** — [github.com/Nazky](https://github.com/Nazky) |
| PS5 Backport research & tools | **BestPig** — [github.com/BestPig](https://github.com/BestPig) |
| exFAT image creation (ShadowMountPlus) | **drakmor** — [github.com/drakmor/ShadowMountPlus](https://github.com/drakmor/ShadowMountPlus/releases) |
| ffpkg builder (UFS2Tool) | **SvenGDK** — [github.com/SvenGDK/UFS2Tool](https://github.com/SvenGDK/UFS2Tool) |
| Klog server | **ps5-payload-dev** — [github.com/ps5-payload-dev/klogsrv](https://github.com/ps5-payload-dev/klogsrv) |
| Inspiration | **NookieAI** and **stonemodder** (Porkfolio) |
| PS5 homebrew community | Everyone contributing to the scene |

---

## License

MIT — see [LICENSE](LICENSE)
