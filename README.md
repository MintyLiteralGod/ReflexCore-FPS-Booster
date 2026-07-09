# ReflexCore Free v1.3.8

Windows performance toolkit for competitive play — timer resolution, input isolation, network tweaks, and 8K polling support. Built for WinForms on .NET 8 (`net8.0-windows`, win-x64).

**Website:** [https://reflexcore.xyz/](https://reflexcore.xyz/)  
**Buy Pro:** [https://reflexcore.xyz/#pro](https://reflexcore.xyz/#pro) · Polar checkout (code `REFLEX99`)  
**Discord:** [https://discord.gg/34pCtCpQJv](https://discord.gg/34pCtCpQJv)

---

## Requirements

- Windows 10/11 x64
- Administrator privileges (affinities, registry, power plans, scheduled tasks)
- .NET 8 SDK to build from source

---

## Free features

| Feature | What it does |
|--------|----------------|
| **Disable OS Dynamic Ticks** | Stops CPU sleep/clock throttling via `bcdedit` dynamic tick control |
| **Optimize Thread Priority** | Raises multimedia / hardware polling responsiveness |
| **Disable NTFS Access Stamps** | Cuts drive I/O from last-access timestamp updates on game folders |
| **Quick actions** | Flush DNS, wipe temp files, restart Explorer |
| **Game executable targets** | Track which `.exe` names get raw-input / affinity focus |
| **Live telemetry strip** | Input delta, DWM raw-input state, thread pacing, hardware state |
| **Stable presets** | One-click baseline toggle set for Free |
| **Run on startup** | Elevated Task Scheduler entry (`ReflexCoreStartupTask`) |
| **System tray** | Minimize to tray while optimization is active |
| **License tab** | Activate a Pro key or open the purchase page |

---

## Pro features

Unlocked after license activation (Polar). Purchase CTA in-app:

**⭐ PURCHASE PRO KEY (REFLEXCORE.XYZ)** → [https://reflexcore.xyz/#pro](https://reflexcore.xyz/#pro)

| Feature | What it does |
|--------|----------------|
| **Disable Nagle’s Algorithm** | Lower TCP packet latency |
| **Maximize System Responsiveness** | Disables network throttling index |
| **Disable GameDVR / Game Bar** | Removes overlay capture overhead |
| **Ultimate Performance power plan** | Forces Windows high-performance power scheme |
| **Force HAGS** | Hardware-accelerated GPU scheduling |
| **Raw mouse (1:1)** | Disables Windows mouse acceleration |
| **SUPER KDLS** | 1024-frame USB / input buffer injection for high polling |
| **GPU MSI-X shunt** | Exclusive high-vector MSI-X routing for the GPU |
| **Win32 priority / affinity shunt** | Process affinity + priority separation |
| **RIDEV_NOLEGACY 8K Shield** | Raw Input swallow (desktop cursor suppressed under game focus) |
| **Full 8K Isolation** | UE5-oriented core shunt + Game Mode kill + isolator engines |
| **Background app purge** | Closes noisy background / telemetry processes |
| **VRAM / standby flush** | Empties working sets and standby memory |
| **DirectX shader pre-cache lock** | Stabilizes DX pipeline allocations |
| **Disable telemetry (DiagTrack)** | Turns down Windows diagnostics services |
| **Disable Fullscreen Optimizations** | Global FSO off for target executables |
| **Tournament Kiosk Mode** | Suspends `explorer.exe` during play (kiosk-style) |
| **Pro themes** | Visual theme profiles (when unlocked) |

### Engines used by Pro / 8K paths

- **CoreIsolatorEngine** — reserves cores 0–1 for USB IRQs; pins games off those cores  
- **RawInputEngine** — `RIDEV_NOLEGACY` mouse inject / restore  
- **HardwareTweakerEngine** — ASPM / wake-state tweaks  
- **MemoryPurgerEngine** — standby / working-set purge  
- **AntiCheatWatchdog** — detects conflicting input filters (e.g. RawAccel)  
- **GameModeManager** — disables Windows Game Mode / GameDVR keys  
- **AudioBufferShuntEngine** — low-latency audio buffer routing  
- **BurstOverdriveEngine** — CPU throttle floor/ceiling via `powercfg`  
- **NetworkInterruptSteeringEngine** — RSS queue steering  
- **CacheAffinityMappingEngine** — cache-lane affinity for the active game  
- **DirectFlipOverdriveEngine** — DirectFlip / independent flip registry path  

---

## Buy Pro

1. Open **LICENSE** in the app, or visit [https://reflexcore.xyz/#pro](https://reflexcore.xyz/#pro).  
2. Checkout on Polar (site price: **$9.99**, was $14.99). Use code **`REFLEX99`** when offered.  
3. Paste your key → **ACTIVATE LICENSE**.  
4. Restart the app so Pro themes and locks refresh.

In-app button label: **PURCHASE PRO KEY (REFLEXCORE.XYZ)**.

---

## Build & publish

```bat
cd "C:\Users\Kaedyn VR\Documents\ReflexCoreFree"
dotnet tool restore
dotnet build -c Release -r win-x64
dotnet publish -c Release -r win-x64 --self-contained
```

Release builds run **Obfuscar** after compile and replace the intermediate DLL so single-file publish embeds the obfuscated assembly.

Helpers (if needed on Windows):

- `restore-tools.bat` — recreate / unblock `.config\dotnet-tools.json`  
- `fix-csproj.bat` — strip UTF-8 BOM from `ReflexCoreFree.csproj` (MSB4025)

### Installer (Inno Setup)

1. Publish as above.  
2. Open `ReflexCoreFree-Setup.txt` in Inno Setup Compiler.  
3. Source path expects:

`C:\Users\Kaedyn VR\Documents\ReflexCoreFree\bin\Release\net8.0-windows\win-x64\publish\*`

Output: `...\ReflexCoreFree\installer\ReflexCore_Setup_v1.3.8.exe`

---

## Website

Static site in `ReflexCore-Web/`:

| File | Role |
|------|------|
| `index.html` | Marketing site (download, features, Pro, FAQ) |
| `banner.jpg` | Hero art |
| `reflex.ico` | Favicon |
| `sitemap.xml` / `robots.txt` | SEO |

Deploy the contents of `ReflexCore-Web/` to the host for [reflexcore.xyz](https://reflexcore.xyz/).

---

## Safety notes

- Requires **Administrator**.  
- **8K Shield** and **Tournament Mode** change desktop / Explorer behavior — use only when you understand the impact.  
- Set mouse DPI to **1600+** in your vendor software (Synapse, G HUB, iCUE, Wootility, etc.) when using high polling.  
- Create a restore point before aggressive registry / BCD changes if you are unsure.

---

## License / publisher

Installer publisher: **Lift Engineering**  
Product: **ReflexCore** · Version **1.3.8**
