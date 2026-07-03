# 🏎️ ReflexCore (v1.2.5)

**Brought to you by LIFT Esports // Developed by MintyLiteralGod**

[![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)](https://reflexcore.xyz/)
[![Framework](https://img.shields.io/badge/framework-.NET%207.0--windows-purple.svg)](https://dotnet.microsoft.com/)
[![License](https://img.shields.io/badge/license-Proprietary-gold.svg)](https://reflexcore.xyz/)
[![Anti-Cheat](https://img.shields.io/badge/Anti--Cheat-Safe%20/%20Compliant-green.svg)](#-anti-cheat-compliance)

Engineered by **MintyLiteralGod** and backed by the **LIFT Esports** organization, **ReflexCore** is a low-level system tuning engine. It bypasses default Windows scheduling constraints, optimizes bare-metal hardware subsystems, and forces sub-millisecond physical tracking. 

While the Free tier provides a flawless baseline environment, the **Pro Suite** unlocks premium, esports-tier kernel-level parameters required to achieve complete competitive dominance.

🔗 **Official Domain:** [reflexcore.xyz](https://reflexcore.xyz/)

---

## ⚡ Complete Feature Breakdown & Explanations

### 🟢 Free Core Baseline Features
*These optimizations prepare your operating system for competitive play by clearing out background bottlenecks.*

* **0.5ms Timer Forcing & Platform Clock Lockdown:** By default, Windows scales its internal clock resolution between 1ms and 15.6ms to save power, causing inconsistent game engine ticks. ReflexCore forces a rigid, physical **0.5ms scheduling heartbeat** (`NtSetTimerResolution`), drastically tightening mouse input consistency and network packet polling intervals.
* **Process Purge Matrix:** Background trackers, web helper layers, and telemetry loops steal valuable CPU cycles. ReflexCore's purge matrix forcefully terminates non-essential tasks at runtime while using an immutable, hardcoded whitelist to safely protect your core communication stack (`Discord.exe`, `Spotify.exe`, `Steam.exe`, and critical system processes).
* **VRAM & Standby Cache Flusher:** Over long gaming sessions, Windows hoards unmapped "standby" data in your RAM and VRAM, leading to catastrophic 1% low FPS drops and sudden stutters. This engine violently empties these working sets, ensuring your GPU always has instant access to clean, bare-metal memory cells.
* **DirectX Pipeline Locker:** Modern titles often stutter mid-match due to on-the-fly shader compilation. This feature writes driver-level overrides (`ShaderCacheMaxKB`), forcing the system to store pre-compiled pipelines and completely neutralizing engine-level asset load stutters.
* **Suppress OS Dynamic Ticks:** Prevents the Windows kernel from turning off CPU clock ticks during idle fractions of a second. This keeps your processor in an aggressive, un-throttled state, ready to process input instantly without core-waking lag.
* **Elevate Multimedia Interrupt Priority:** Tweaks the NT scheduler's multimedia class handles, forcing Windows to prioritize hardware polling threads and rendering loops above generic operating system tasks.

---

### 👑 Premium Pro Suite Upgrades
*The absolute pinnacle of PC optimization. Pro Suite shifts your hardware out of consumer power-saving modes and drops them into an aggressive, low-latency esports configuration.*

> [!TIP]
> **Why Top-Tier Pros Upgrade:** Free optimization apps only close background windows. ReflexCore Pro completely restructures how your CPU, GPU, and Network Adapter communicate with the Windows Kernel to save fractions of a millisecond on every single frame.

* **🧬 Kernel DPC Lane Shunting (KDLS):** High-polling peripherals (**4000Hz and 8000Hz mice**) completely flood your system with microsecond hardware interrupts, choking your CPU. KDLS rewrites your device PCI affinity maps (`SYSTEM\CurrentControlSet\Enum\PCI`), forcefully shunting non-essential hardware interrupts completely away from **Core 0 and Core 1**. This isolates your primary CPU cores exclusively for raw mouse tracking and your game's main render loop—completely eliminating micro-stutters.
* **🌐 Network Bufferbloat & Nagle's TCP Elimination:** Standard Windows networking groups packets together before sending them to save bandwidth, introducing micro-latency jitter. Pro Suite forces `TcpAckFrequency` and `TCPNoDelay` registers to `1`, instructing your network card to instantly dispatch every single packet the microsecond it's generated. 
* **🚀 Maximize Global System Responsiveness:** Consumer Windows reserves up to 20% of your CPU capacity for background system services and multimedia network throttling. Pro Suite rewrites the `SystemProfile` registry to bypass this cap entirely, forcing the kernel to dedicate **100% of your hardware's raw computing output** to your active game.
* **🔌 Force Hidden "Ultimate Performance" Power Scheme:** Windows hides its most powerful power grid plan from normal users. Pro Suite forcefully unparks your CPU cores, disables all PCIE link state power-saving slowdowns, and locks your processor clocks at their maximum rated frequencies without down-throttling.
* **🎮 Telemetry Overlay & Game DVR Suppressor:** Windows Game Bar and DVR recording background threads constantly take screenshots and log telemetry in the background. Pro Suite systematically deletes these deep policy registers, freeing up GPU hardware encoding pipelines.
* **🖥️ Force Hardware-Accelerated GPU Scheduling (HAGS API):** Forces Windows to hand over memory scheduling duties directly to your GPU's dedicated processor instead of routing it through the OS framework, slicing input lag cleanly at high frame rates.
* **🖱️ Enforce 1:1 Pure Mouse Input Parity:** Completely flattens the hidden Windows mouse precision acceleration curves inside the desktop subsystem. This locks in raw, predictable, mechanical muscle memory tracking without sudden software-induced velocity shifts.

---

## 📊 Feature Comparison Matrix

| Technical Optimization Node | Free Core Engine | Pro Suite License ($14.99) |
| :--- | :---: | :---: |
| **0.5ms System Timer Override** | ✔ | ✔ |
| **DirectX Shader Pre-Caching Flags** | ✔ | ✔ |
| **Standby RAM & VRAM Dynamic Flush** | ✔ | ✔ |
| **Background Process Purge Matrix** | ✔ | ✔ |
| **Kernel DPC Lane Shunting (KDLS)** | ❌ *Locked* | **👑 UNLOCKED** |
| **Nagle's TCP Latency Jitter Elimination**| ❌ *Locked* | **👑 UNLOCKED** |
| **100% CPU Dedication (SystemProfile)** | ❌ *Locked* | **👑 UNLOCKED** |
| **Windows Game DVR Overlay Suppression** | ❌ *Locked* | **👑 UNLOCKED** |
| **Hidden "Ultimate Performance" Power Plan**| ❌ *Locked* | **👑 UNLOCKED** |
| **Hardware-Accelerated GPU (HAGS) Force** | ❌ *Locked* | **👑 UNLOCKED** |
| **1:1 Mouse Input Curve Flattening** | ❌ *Locked* | **👑 UNLOCKED** |
| **Persistent Tray-Boot & Watchdog Loop** | ❌ *Locked* | **👑 UNLOCKED** |

---

## 📦 Installation & Deployment

### Official Executable Build
Get the verified standalone package instantly from our direct build tree:

👉 **[Download ReflexCore Setup v1.2.5 (.exe)](https://github.com/MintyLiteralGod/ReflexCore-FPS-Booster/releases/download/OFFICIALRELEASE1.2.2/ReflexCore_Setup_v1.2.5.exe)**

### Compiling Natively via CLI
If you prefer auditing and building the project binary manually:

1. Open your command terminal inside your repository path:
   ```cmd
   cd C:\Path\To\ReflexCoreFree
Build a flattened production release directory using the .NET compiler:

DOS
dotnet publish -c Release
Locate your compiled binary bundle gathered inside:

Plaintext
\bin\Release\net7.0-windows\publish\ReflexCoreFree.exe
[!IMPORTANT]
ReflexCore handles low-level platform timers and kernel configurations. It explicitly requires Administrator Privileges to execute. If elevation is blocked, the engine will safely drop out to protect user state configurations.

# 🛡️ Anti-Cheat & League Compliance
### ReflexCore is designed purely at the Windows subsystem tier, making it 100% safe and authorized for all major competitive platforms and anti-cheat layers.

### Zero Memory Injection: The engine performs no runtime memory manipulation, patch injection, or handle-hooking on running game clients. It does not touch your game files.

### Pure OS Registry Tweak Architecture: It limits all execution adjustments entirely to native, built-in Windows environment parameters before game architectures even launch.

### Verified Safe Environments: Fully compliant with Valve Anti-Cheat (VAC), Riot Vanguard, EasyAntiCheat (EAC), BattlEye, and FACEIT systems.

# ❓ Frequently Asked Questions (FAQ)
### Q: Is the $14.99 Pro Suite license a subscription?
### A: No. It is a one-time, lifetime purchase. Once you secure your cryptographic license key via our secure checkout gateway, you own that optimization slot forever. All future v1.X engine updates and feature expansions are completely free.

### Q: Can I run this alongside normal game booster apps?
### A: You can, but you won't need to. Standard game boosters just clear your clipboard and close your browser. ReflexCore operates at a raw kernel tier—handling things like CPU Core Shunting (KDLS) and 0.5ms Clock lockdowns that commercial software cannot touch.

### Q: What exactly does KDLS do for my aim?
### A: If you own a modern gaming mouse pulling at 4000Hz or 8000Hz, your input device is bombarding your CPU with data thousands of times per second. Windows normally tries to handle these requests on the same CPU core rendering your game, causing micro-stutters and sudden mouse desync mid-fight. KDLS forcefully redirects all non-esports hardware signals onto secondary cores, giving your mouse raw, un-throttled access to your processor for perfect pixel-to-sensor tracking.

### Q: How do I apply my Pro Suite key?
### A: Simply download the Free build, click the "Enter Pro Key" button inside the classic Steam-themed interface, and paste your key. The application instantly validates your license node offline and securely unlocks your premium kernel configurations on the fly.
