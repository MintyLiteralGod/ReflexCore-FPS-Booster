# ⚡ ReflexCore v1.3.6 (Stable Production Release)

> Competitive Esports Operating System Optimization Engine targeting the Windows NT Sub-Kernel and Hardware Abstraction Layer (HAL) live in Volatile Memory.

[![Build Status](https://img.shields.io/badge/Build-v1.3.6--Stable-00e673?style=for-the-badge&logo=windows&logoColor=white)]()
[![Platform](https://img.shields.io/badge/Platform-Windows--10%20%7C%2011-00f0ff?style=for-the-badge)]()
[![Privileges](https://img.shields.io/badge/Privileges-Administrator--Required-daaf37?style=for-the-badge)]()

ReflexCore is an advanced, deep-level system utility designed to bypass low-level operating system scheduling constraints, isolate high-frequency physical hardware interrupts, and neutralize latency micro-stutters during high-refresh esports scenarios.

---

## 🚀 Core Architectural Breakthroughs

### 1. Super KDLS Engine (High-Polling HID Isolation)
High-polling mice and mechanical keyboards (4,000Hz - 8,000Hz) flood the Windows subsystem with up to 8 packets per millisecond, triggering thread scheduling starvation on standard game loops. 
* **Queue Pool Expansion:** Reconfigures `mouclass` and `kbdclass` parameters, tripling queue buffer capacity to `300` packets to intercept overruns.
* **Bus Power Gating:** Injects structural `DisableSelectiveSuspend` parameters across root USB configurations, preventing hardware drop-down clock states.
* **Motherboard Core Isolation:** Automatically shunts peripheral interrupt requests away from Core 0 and Core 1 via PowerShell host lifecycle restarts.

### 2. High-Priority Task Scheduler Startup Hijack
Standard Windows Registry `Run` keys explicitly block administrative applications from launching on boot, breaking automation pipelines. Build v1.3.6 re-routes this execution chain:
* Integrates directly with the Windows Task Scheduler Subsystem.
* Schedules a high-priority `/RL HIGHEST` logon execution task bypass node.
* Executes fully elevated silent memory shunting sequences backgrounded before the user desktop even paints.

### 3. Targeted MSI-X Subsystem Shunting
Legacy line-based interrupts (`INTx`) force multiple pieces of high-throughput hardware to share narrow physical wire pins on your motherboard, causing serialization stalls.
* ReflexCore systematically scans device control nodes targeting *only* your display graphics class GUID (`{4d36e968-e325-11ce-bfc1-08002be10318}`).
* Safe-swaps the display controller into **Message Signaled Interrupts (MSI) Mode**, allowing your GPU to write data strings directly to memory-mapped CPU targets with zero peripheral collision risk.

### 4. Advanced Morphing UI Theme Subsystem
Build v1.3.6 features an isolated rendering layout matrix. Swapping structural profiles (Valorant, CS2, Apex, Overwatch) doesn't just change basic HEX colors—it rebuilds internal controls, panel shapes, border thickness tokens, and edge drawing algorithms completely.

---

## 🛠️ Compilation & Packaging Guidelines

ReflexCore Free/Pro requires compilation under the **.NET 7.0 Windows WindowsForms** workload parameter space.

### To Compile Into a Standalone Production Binary:
Execute this command string inside your root project terminal folder. This packages your dependencies, code files, and libraries into a singular self-contained, AOT-compiled executable asset:

```bash
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true /p:PublishReadyToRun=true /p:IncludeNativeLibrariesForSelfExtract=true
```

The native compilation output will be safely generated inside:
`.\bin\Release\net7.0-windows\win-x64\publish\ReflexCoreFree.exe`

---

## ⚙️ Baseline Calibration Controls

| Feature Flag | Subsystem Targeted | Deployment Pathway | Tier Profile |
| :--- | :--- | :--- | :--- |
| `DisableDynamicTicks` | Windows Bootloader | `bcdedit.exe /set` | Free Baseline |
| `OptimizeThreadPriority` | Win32 Multimedia | Registry Class | Free Baseline |
| `DisableNtfsTimestamps` | Storage Cache I/O | Registry FileSystem | Free Baseline |
| `RawMouseInput` | User Subsystem | `user32.dll` Hook | ⭐ Pro Suite |
| `EnableKDLS` | Motherboard USB Bus | PowerShell Hot-Plug | ⭐ Pro Suite |
| `EnableMSIShunt` | Display Class GUID | Registry PCI Vector | ⭐ Pro Suite |
| `OptimizeWin32Priority` | NT Sub-Kernel | Priority Control | ⭐ Pro Suite |
| `EnableTournamentMode` | Desktop Shell | Process Watchdog | ⭐ Pro Suite |

---

## 🔒 Automated Deployment Node Validation (Inno Setup)

ReflexCore distributes setups using advanced LZMA2-compressed Inno scripts. The installer configuration includes a native pre-flight `[Code]` block designed to query legacy machine records and run old uninstaller binaries fully silently in the background before unpacking files.

To prevent path duplication or conflicting installations, ensure your setup configuration structure matches this profile layout precisely:

```ini
[Setup]
AppId={9FAA846A-3715-4050-8FF8-6A2B45557F46}
AppName=ReflexCore
AppVersion=1.3.6
PrivilegesRequired=admin
OutputDir=.\Installer_Output
OutputBaseFilename=ReflexCore_Setup_v1.3.6
Compression=lzma2/ultra64
```

---

## 🔬 Technical FAQ Index

#### Q: Is ReflexCore safe to deploy along with kernel anti-cheats (Vanguard / FaceIt)?
**A:** Yes, 100%. ReflexCore is completely external. It modifies native Windows parameters, Registry settings, and driver alignment profiles using standard system hooks. It never opens handles, touches game binaries, or reads game memory.

#### Q: Why does my mouse cursor freeze for two seconds when initializing optimization?
**A:** To isolate peripheral interrupts from CPU Core 0, the Super DPC engine triggers an instant hardware cycle. It momentarily resets the motherboard's active USB host controllers via PowerShell to re-route memory channels safely without requiring a full PC reboot.

#### Q: Why did v1.3.6 replace the standard Registry Run key with Task Scheduler for autostart?
**A:** Windows completely blocks applications with administrative manifests from launching via the standard current-user Registry `Run` key at boot. Build v1.3.6 implements a high-priority task directly into the Task Scheduler subsystem using the `/RL HIGHEST` bypass protocol, ensuring seamless, silent elevation upon login.

#### Q: What exactly does the Win32 Priority Separation tweak modify?
**A:** It reconfigures the Windows NT sub-kernel allocation layout (`Win32PrioritySeparation = 38`). This forces the OS to grant exceptionally long, variable processor slices (quantums) directly to your active foreground game window instead of distributing processing power equally to background tasks.

#### Q: Why does 8,000Hz high-polling input generate micro-stutters in Unreal Engine?
**A:** At 8,000Hz, devices dump an exceptional 8 packets per millisecond into the Windows message queue. Standard engines parse this information sequentially inside their primary tick cycles, stalling frame composition logic. ReflexCore scales the Windows input class buffers to 300 frames to handle data flood overruns cleanly.

---

## 🤝 Contribution Guidelines
Contributions to optimize alternative physical device class vectors or adjust multimedia clock registers are welcome. Submit an issue file outlining your proposal or fork the workspace to generate a pull request targeting the production staging branch.

### Licensing
ReflexCore is distributed by LIFT Esports. Commercial unauthorized reproduction of the cryptographic Polar.sh license framework or theme layout libraries is restricted.
