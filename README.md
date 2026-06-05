# ⚡ Apex Legends DMA Hack v3.0 (QEMU/KVM) - Binary Release

[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-blueviolet?style=for-the-badge&logo=linux)](https://github.com/albatror/adkv-bin)
[![Language](https://img.shields.io/badge/Language-C%2B%2B-blue?style=for-the-badge&logo=c%2B%2B)](https://github.com/albatror/adkv)
[![Technology](https://img.shields.io/badge/Powered%20By-Memflow-orange?style=for-the-badge)](https://memflow.io/)
[![Version](https://img.shields.io/badge/Version-v3.0.3.55-green?style=for-the-badge)](https://github.com/albatror/adkv-bin)

**Pre-compiled binaries** for the high-performance Apex Legends DMA hack designed for **QEMU/KVM** environments. No compilation required — just download, configure, and run!

---

## 📦 What's Included

This binary release contains ready-to-use executables:
- **apex_dma** — Host-side server (Linux)
- **Overlay.exe** — In-game overlay already obfuscated (Windows guest)
- **Client.exe** — Client already obfuscated (Windows guest)
- **PML4/CR3** — Not BruteForce technique anymore
- **Memflow connectors** — Pre-built KVM/QEMU drivers
- **Offset dumper** — Utility to extract game offsets

No source code compilation necessary.

#
apex_dma SHA256          39aff601e5e30ef62dbfeb79d7fcd9811b14ea3f831720ca8e4e79d8f1dbc2a1
#
Client SHA256          26B578ABA5A426B2A157AEAA83B74126E53F46D97EBFB689176B3A2CF21C7A0F 
#
Overlay SHA256          33DEC0100865F1C9CF281D251A608298DE56644869899196CF8B5C01593A7D27 
#
r5dumper SHA256          5e34126b4fa0f1ecd89a8f8d10139837869d028a195425ae1f87a95b5b8a9bb7

---

## 🚀 Quick Start

### Prerequisites

#### Host (Linux)
- **Supported Distros:** Fedora, Ubuntu, Debian, Proxmox
- **Hardware:** Second PC or KVM-capable system for DMA
- **Memflow:** Pre-built binaries included
- **Root access:** Required to run the DMA server

#### Guest (Windows)
- **OS:** Windows 10 (Version 20H1 or earlier; 22H2 tested with CR3 fix)
- **Not recommended - test needed with new PML4/CR3:** Windows 11, Windows 23H2+
- **Resolution:** 2560x1440 (default) or 1920x1080 (manual config)
- **.NET Framework:** May be required for executables

---

## 📥 Installation

### 1. Download & Extract

```bash
# Download the latest release
unzip adkv-bin.zip
extract apex_dma to linux (host)
extract apex_guest to windows VM (guset)
```

### 2. Host Setup (Linux)

#### Load Memflow Module on host
```bash
# Load the memflow kernel module (required each boot)
sudo modprobe memflow

# Optional: Add to cron for automatic loading at startup
# (sudo crontab -e and add: @reboot /sbin/modprobe memflow)
```

#### Verify Memflow Installation
```bash
# Check if memflow connectors are available
ls -la ./memflow-connectors/
# You should see: memflow-qemu, memflow-kvm, etc.
```

### 3. Guest Setup (Windows)

**Obfuscation Warning** ⚠️
   ```
   CRITICAL: the Client.exe and Overlay.exe are already obfuscated to avoid detection by anti-cheat.
   ```

## ▶️ Running the Hack

1. **Start on Windows VM (Guest):**
   - Launch `Overlay.exe` first
   - Then launch `Client.exe`
   - **Note:** Nothing will appear initially — this prevents screenshot detection

2. **Start Game:**
```bash
wait until your enter in lobby
```

3. **Start Host Server (Linux host):**
```bash
cd adkv-bin/apex_dma/build
sudo -E ./apex_dma
```

**Output:**
```bash
[✓] Memflow initialized
[✓] KVM connector loaded
[✓] ...
```

### Step 3: Configure In-Game
- Press **INSERT** to open the menu
- Navigate to **Config** tab
- Adjust settings to your preference
- Click **Save** to persist settings to `Settings.txt`

---

## 🎮 Features Overview

### 🛡️ Visuals (ESP)
- **2D ESP Boxes** — Clear player outlines
- **Health/Shields** — Integrated status bars
- **Skeleton** — Real-time bone visualization
- **Glow** — Per-state color (Green=Visible, Red=Hidden, White=Knocked)
- **Player Info** — Name, level, distance, weapons, platform
- **Spectator List** — See who's watching you
- **Target Indicator** — DOT with configurable FOV
- **Item Glow** — Loba-style loot highlighting
- **FOV Circles** — Overlay for ADS/Hipfire/Triggerbot zones

### 🔫 Combat Features
- **Advanced Aimbot** — Smooth tracking with 6 smoothing modes
- **Dynamic Switching** — Auto-toggles between ADS and Hipfire
- **Target Priority** — Weighted FOV + distance selection
- **Lock On** — Prevents target switching mid-fight
- **No Recoil/Sway** — Automatic compensation
- **Aim Assist (RMB)** — Graduated pull with configurable strength
- **Triggerbot (LSHIFT)** — Configurable hitbox targeting
- **Ballistic Prediction** — Bullet speed & gravity compensation
- **Dead Zone** — Micro-correction suppression

### 🏃 Movement
- **Auto SuperGlide** — Perfect glides every time
- **Auto WallJump** — Smooth wall mechanics
- **BunnyHop (SPACEBAR)** — Effortless movement
- **Firing Range Mode** — Test in training area
- **1V1 Mode** — Battle friends in the training area

---

## ⌨️ Hotkeys

| Key | Action |
|-----|--------|
| **INSERT** | Open/Close Menu |
| **F1** | Toggle Full Suite (ESP + Glow + Items) |
| **F5** | Toggle ESP Only |
| **F8** | Toggle Item Glow Only |
| **F9** | Run Full Offset Dump |
| **F10** | Update Offsets Dynamically |
| **F4** | Emergency Close (Guest) |

---

## 💾 Settings & Configuration

### Default Config File
`Settings.txt` contains all saved settings:
```
[Aimbot]
Enabled=1
FOV=50
Smoothing=0
[ESP]
Enabled=1
ShowBoxes=1
ShowSkeleton=1
[Glow]
VisibleColor=0,255,0
HiddenColor=255,0,0
KnockedColor=255,255,255
```

### Modifying Settings
1. Edit `Settings.txt` directly (text editor)
2. Or modify in-game via **INSERT menu**
3. Click **Save** in the Config tab
4. Settings persist between sessions

---

## 🔧 Advanced Usage

### Changing Resolution
If you need to use **1920x1080** instead of default 2560x1440:
1. Edit `Settings.txt`
2. Locate resolution parameters
3. Update to your display size
4. Restart overlay

### Offset Dumping
```bash
Press F9 while in-game to dump current game offsets.
Useful for keeping up with game patches.
```

### Dynamic Offset Update
```bash
Press F10 to load offsets from Settings.txt into game memory.
Useful when offsets change between game updates.
```

---

## 📊 Smoothing Modes (Aimbot)

Select your preferred algorithm in **Config** tab:

| # | Mode | Best For |
|---|------|----------|
| 0 | **SmoothDamp** | AR / LMG (Spring-damper) |
| 1 | **Linear** | Direct/raw tracking |
| 2 | **Bezier** | Fast approach, gentle arrival |
| 3 | **Cubic Bezier** | Smooth acceleration/deceleration |
| 4 | **S-Curve** | Snipers (ultra-smooth) |
| 5 | **Auto** | Weapon-aware (picks automatically) |

---

## 🎯 Triggerbot Hitbox Options

Configure which bone to target:

| Option | Target Bone(s) |
|--------|----------------|
| Head | Bone 0 |
| Neck | Bone 1 |
| Upper Chest | Bone 2 |
| Lower Chest | Bone 3 |
| Stomach | Bone 4 |
| Hip | Bone 11 |
| NEAR3 | Bones 0, 1, 2 |
| NEAR6 | Bones 0–4, 11 |
| NEAR12 | 12 major bones |
| ALL | All 17 bones |

More info: [Bone IDs Reference](https://www.unknowncheats.me/wiki/Apex_Legends_Bones_and_Hitboxes)

---

## ⚠️ Important Safety Notes

### Anti-Cheat Warning ⚠️
- **Ban Risk:** Using cheats in online games **will result in permanent ban**
- **Use at Your own Risk:** No support for bans or account recovery
- **Obfuscation Required:** Always obfuscate binaries before online use

### Best Practices
1. ✅ Test in **Firing Range** first (isolated mode)
2. ✅ Use obfuscated binaries only
3. ✅ Keep the hack updated with game patches
4. ✅ Use reasonable settings (don't be obvious)
5. ❌ Never share unobfuscated binaries
6. ❌ Don't use in ranked matches if bannable

---

## 🐛 Troubleshooting

### Issue: "Memflow module not found"
```bash
# Solution: Load the module
sudo modprobe memflow

# Verify:
lsmod | grep memflow
```

### Issue: "Connection refused" (Linux to Windows)
```bash
# Ensure:
1. KVM bridge is configured correctly
2. Guest Windows has network access
3. Firewall isn't blocking communication
4. Run apex_dma with: sudo -E ./apex_dma
```

### Issue: "Overlay won't appear in-game"
```bash
1. Press INSERT — nothing should show initially
2. Start Apex Legends AFTER overlay is running
3. The overlay injects once the game is detected
4. If still nothing: check Client.exe console for errors
```

### Issue: Offsets out of date after game update
```bash
1. Restart the hack
2. Press F9 to dump new offsets
3. Close and restart Overlay/Client
4. Offsets auto-update to new values
```

### Memflow Setup Issues (FAQ)

**Q: Curl command gives "unrecognized protocol" error**

```bash
# Try removing the --proto parameter:
curl -sSf https://sh.memflow.io/ | sh

# Or if using WSL/minimal Linux:
sudo apt-get install -y curl
curl -sSf https://sh.memflow.io/ | sh
```

---

## 📚 Resources

- **Original Source:** [albatror/adkv](https://github.com/albatror/adkv)
- **Memflow Project:** [memflow.io](https://memflow.io/)
- **Community Discussion:** [UnknownCheats Thread](https://www.unknowncheats.me/forum/apex-legends/406426-kvm-vmread-apex-esp-aimbot.html)
- **Bone Reference:** [Apex Legends Bones & Hitboxes](https://www.unknowncheats.me/wiki/Apex_Legends_Bones_and_Hitboxes)

---

## 👏 Credits

Special thanks to:
- **Memflow Team** — DMA framework
- **Y33Tcoder, MisterY, Gerosity, ApexCV, KrackerCo, caochuang** — Contributors and community
- **Original author** — albatror

---

## 📋 System Requirements Summary

| Component | Requirement |
|-----------|-------------|
| **Host OS** | Linux (Fedora, Ubuntu, Debian, Proxmox) |
| **Host Hardware** | KVM-capable CPU, 8GB+ RAM |
| **Guest OS** | Windows 10 (20H1 or 22H2) |
| **Guest RAM** | 8GB+ |
| **Display** | 2560x1440 or 1920x1080 |
| **Network** | Host ↔ Guest communication |
| **Privileges** | Root access on host |

---

**Last Updated:** June 2026 | **Version:** 3.0.3.55

⚠️ **Disclaimer:** This tool is for educational and authorized testing purposes only. Unauthorized access to online game systems is illegal. Use responsibly.
