# ⚡ ReflexCore v1.3.7 (Stable Production Release)

> Competitive Esports Operating System Optimization Engine targeting the Windows NT Sub-Kernel and Hardware Abstraction Layer (HAL) live in Volatile Memory.

[![Build Status](https://img.shields.io/badge/Build-v1.3.7--Stable-00e673?style=for-the-badge&logo=windows&logoColor=white)]()
[![Platform](https://img.shields.io/badge/Platform-Windows--10%20%7C%2011-00f0ff?style=for-the-badge)]()
[![Framework](https://img.shields.io/badge/Framework-.NET_7.0_AOT--Ready-512bd4?style=for-the-badge&logo=dotnet&logoColor=white)]()
[![Privileges](https://img.shields.io/badge/Privileges-Administrator--Required-daaf37?style=for-the-badge)]()

ReflexCore is a low-level, deep-system architecture tuner engineered to forcefully bypass OS scheduling bottlenecks, isolate high-frequency physical hardware IRQs, and neutralize rendering micro-stutters during maximum-refresh esports scenarios.

---

## 📊 Feature Matrix: Free vs. Pro Suite

ReflexCore is distributed in two operational tiers. The **Free** tier handles safe, baseline file-system and OS clock adjustments. The **Pro Suite** requires cryptographic node activation and drops low-level hardware constraints to handle raw 8K packet routing and memory flushing.

| System Optimization Module | Target Subsystem / Win32 API | Free Baseline | ⭐ Pro Suite |
| :--- | :--- | :---: | :---: |
| **Dynamic Tick Disablement** | Windows Bootloader (`bcdedit`) | 🟢 Active | 🟢 Active |
| **Multimedia Thread Priority** | Win32 MMCSS Profiles | 🟢 Active | 🟢 Active |
| **NTFS Metadata Suspension** | Storage Cache I/O Controller | 🟢 Active | 🟢 Active |
| **8K Polling Shield** | Dedicated Background Worker Thread | 🔴 Locked | 🟢 Active |
| **Max Polling Overdrive** | Kernel DMA Pacing / Bus Overrides | 🔴 Locked | 🟢 Active |
| **Super KDLS Engine** | Motherboard USB Bus (`powershell`) | 🔴 Locked | 🟢 Active |
| **GPU MSI-X Shunting** | Display Class GUID (`PCI Enum`) | 🔴 Locked | 🟢 Active |
| **Win32 Priority Separation** | NT Sub-Kernel Allocation | 🔴 Locked | 🟢 Active |
| **Raw Mouse Input Parity** | User Subsystem (`user32.dll`) | 🔴 Locked | 🟢 Active |
| **Network Throttling Override** | TCP/IP Stack (`TCP_NODELAY`) | 🔴 Locked | 🟢 Active |
| **Hardware Accelerated GPU** | WDDM Driver Register (`HwSchMode`) | 🔴 Locked | 🟢 Active |
| **Tournament Kiosk Mode** | Desktop Shell (`explorer.exe` Watchdog) | 🔴 Locked | 🟢 Active |
| **Volatile Memory Flusher** | `EmptyWorkingSet` Cache Sweeper | 🔴 Locked | 🟢 Active |
| **DirectX Shader Lock** | Driver Pre-Caching Limits | 🔴 Locked | 🟢 Active |

---

## 🚀 Core Architectural Breakthroughs

### 1. 8K Shield: Independent Input Polling Matrix
Windows standard UI thread architectures inherently bottleneck at 8,000Hz peripheral polling. By forcing 8 hardware interrupts per millisecond, the OS message pump starves the game's execution engine, resulting in massive context-switching stalls.
* **The Solution:** ReflexCore v1.3.7 injects a dedicated, high-priority background Win32 message loop utilizing `RegisterRawInputDevices`. It decouples raw cursor telemetry completely from the desktop rendering queue, intercepting overruns and delivering pure data arrays directly to the engine without halting thread states.

### 2. Maximum Overdrive: Kernel DMA Pacing Unlock
By default, the Windows Hardware Abstraction Layer artificially paces hardware DMA (Direct Memory Access) frame limits to save power and reduce heat on commercial systems.
* **The Solution:** Engaging Max Polling Overdrive flips the undocumented `DmaPacing = 0` registry flag and maxes out `ThreadPriorityOverdrive` variables. This executes a nuclear un-pinning of your kernel buses, routing data transfers immediately at hardware-max electrical boundaries. *(Warning: Extreme hardware load).*

### 3. Targeted MSI-X Subsystem Shunting
Legacy line-based hardware pins (`INTx`) force massive PCIe throughput components to serialize data on shared motherboard bridges. 
* **The Solution:** ReflexCore explicitly queries `CurrentControlSet\Enum\PCI` specifically for your display graphics class GUID (`{4d36e968-e325-11ce-bfc1-08002be10318}`). It writes `MSISupported = 1` to safe-swap your GPU controller into isolated Message Signaled Interrupts (MSI) Mode, entirely mitigating multi-device interrupt collisions.

### 4. Advanced GDI+ Morphing UI Subsystem
We don't use bloated web-frameworks like Electron or Chromium Embedded Framework. ReflexCore v1.3.7 implements pure GDI+ WinForms vector drawing pipelines. The UI renders dynamic 3D geometric math—like the spinning 3D perspective Gyro Logo and glassmorphism panel arrays—using fractional memory footprints that scale securely around the core optimization routines.

---

## 💻 Deployment & Installation Guides

ReflexCore can be installed via our automated setup wrapper or manually deployed by system administrators for portable configurations.

### Method A: Automated Deployment (Recommended)
Download `ReflexCore_Setup_v1.3.7.exe` from the Releases page. The installer utilizes advanced LZMA2 compression and includes a native pre-flight `[Code]` block designed to query legacy machine records and silently wipe older versions before unpacking fresh configurations.

### Method B: Manual / Portable Installation
For advanced users who prefer not to use Inno Setup installers, ReflexCore operates perfectly as a portable executable.

1. **Extract the Binary:** Download the raw `ReflexCore.exe` release asset and place it in a secure, permanent directory (e.g., `C:\Program Files\ReflexCore\`).
2. **Run as Administrator:** Right-click the binary and select **Run as Administrator**. The application cannot interface with the NT Kernel without elevated privileges.
3. **Manual Autostart Configuration (Optional):** If you wish to configure ReflexCore to start silently with Windows without using the built-in GUI toggle, open an elevated PowerShell window and execute the following Task Scheduler bypass hook:

```powershell
$action = New-ScheduledTaskAction -Execute 'C:\Program Files\ReflexCore\ReflexCore.exe' -Argument '--silent-inject'
$trigger = New-ScheduledTaskTrigger -AtLogOn
Register-ScheduledTask -TaskName 'ReflexCore_Autostart' -Action $action -Trigger $trigger -RunLevel Highest -Force
```

---

## 🛠️ Compilation Guidelines

ReflexCore requires compilation under the **.NET 7.0 Windows WindowsForms** workload parameter space.

### To Compile Into a Standalone Production Binary:
Execute this command string inside your root project terminal folder. This packages your dependencies, code files, and libraries into a singular self-contained, AOT-compiled executable asset:

```bash
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true /p:PublishReadyToRun=true /p:IncludeNativeLibrariesForSelfExtract=true
```

The native compilation output will be safely generated inside:
`.\bin\Release\net7.0-windows\win-x64\publish\ReflexCoreFree.exe`

---

## 🔬 Technical FAQ Index

#### Q: Is ReflexCore safe to deploy along with ring-0 anti-cheats (Vanguard / FaceIt)?
**A:** Yes, 100%. ReflexCore is completely external. It modifies native Windows parameters, Registry configuration files, and Win32 driver alignment profiles using documented system hooks. It never opens handles, touches game binaries, or reads game memory spaces.

#### Q: Why does my mouse cursor freeze for two seconds when initializing Super KDLS?
**A:** To successfully isolate peripheral interrupts from CPU Core 0, the Super DPC engine triggers an instant hardware cycle flush. It momentarily resets the motherboard's active USB host controllers via PowerShell to re-route memory channels safely without requiring a full PC reboot.

#### Q: Why did v1.3.7 replace the standard Registry Run key with Task Scheduler for autostart?
**A:** Windows intentionally blocks applications possessing administrative UAC manifests from launching via the standard current-user Registry `Run` keys at system boot. Build v1.3.7 implements a dynamic, high-priority background task directly into the Task Scheduler subsystem using the `/RL HIGHEST` execution protocol, ensuring a seamless, silent elevation upon Windows login.

#### Q: What exactly does the Win32 Priority Separation tweak modify?
**A:** It explicitly reconfigures the Windows NT sub-kernel allocation layout (`Win32PrioritySeparation = 38`). This forces the OS to grant exceptionally long, variable processor slices (quantums) directly to your active foreground game window, instead of attempting to distribute processor load equally to noisy background threads.

#### Q: Why does 8,000Hz high-polling input generate micro-stutters without the 8K Shield?
**A:** At 8,000Hz, devices dump an exceptional 8 packets per millisecond into the Windows message queue. Standard engines parse this UI thread sequentially inside their primary tick cycles, immediately stalling frame composition logic. The 8K Shield module moves input sorting to a parallel execution layer, feeding games clean coordinates without bogging down the drawing logic.

---

## 🤝 Contribution Guidelines
Contributions to optimize alternative physical device class vectors or adjust multimedia clock registers are welcome. Submit an issue file outlining your proposal or fork the workspace to generate a pull request targeting the production staging branch.

### Licensing
ReflexCore is distributed by LIFT Esports. Commercial unauthorized reproduction of the cryptographic Polar.sh license framework or theme layout libraries is restricted.
