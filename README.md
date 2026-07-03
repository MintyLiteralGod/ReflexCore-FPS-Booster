#⚡ ReflexCore | Win32 Subsystem & Hot-Plug Hardware Optimization Engine

ReflexCore is a high-performance, asynchronous Win32 subsystem manipulation and registry optimization engine compiled in C# for the .NET 7.0 framework. The utility is engineered to execute granular overrides within the Windows NT Kernel Scheduler, reallocate Deferred Procedure Call (DPC) queue workloads, adjust the Ancillary Function Driver (AFD) socket stack, and enforce immediate, system-wide presentation layer changes.

Unlike crude, single-threaded system configuration scripts that freeze the host machine or require constant operating system reboots to evaluate values, ReflexCore leverages a fully asynchronous processing pipeline (Task.Run). It coordinates live Win32 API sub-system broadcasts with targeted hot-plug PowerShell hardware resets to apply low-latency optimizations instantaneously in volatile memory.

Intrusive kernel-level anti-cheat modules—including Riot Vanguard, BattlEye, Easy Anti-Cheat (EAC), and FACEIT AC—explicitly whitelist user-mode registry manipulation and native Win32 API loops, making ReflexCore 100% anti-cheat compliant across all competitive platforms.

📥 [**Download Verified Production Release v1.3.0 (Windows Installer)**](https://github.com/MintyLiteralGod/ReflexCore-FPS-Booster/releases/download/1.3.0/ReflexCore_Setup_v1.3.0.exe)

## 🧭 System Intercept Matrix & Execution Model
Plaintext
 [ Click: START OPTIMIZATION ]
               |
               v
 [ Async Pipeline Initialized ] ---> UI Thread Remains Responsive (0ms Freeze)
               |                     Button States Flip to "INJECTING HOOKS..."
               v
```
 +-------------------------------------------------------------------------+
 |                      BACKGROUND THREAD EXECUTION POOL                   |
 +-------------------------------------------------------------------------+
 |                                                                         |
 |  [NT Timer Layer]       ---> NtSetTimerResolution -> Locks 0.5ms Tick   |
 |                                                                         |
 |  [Win32 User32 Node]    ---> SystemParametersInfo -> Instantly Kills    |
 |                                                      Mouse Acceleration |
 |                                                                         |
 |  [Live KDLS Core Reset] ---> Injects Affinity -> PowerShell Hot-Plugs   |
 |                                                   USB Host Controllers  |
 |                                                                         |
 |  [Socket Stack Flush]   ---> TcpNoDelay Registry -> PowerShell Hot-Plugs|
 |                                                      Network Interface  |
 |                                                                         |
 |  [Watchdog Layer]       ---> Launches Loop -> EmptyWorkingSet Trims RAM |
 |                                             -> Explorer.exe Kiosk Logic |
 |                                                                         |
 +-------------------------------------------------------------------------+
               |
               v
 [ Pipeline Evaluation ]
               |
               +---> Has Staged Flags? (BCDEDIT Ticks / GPU HwSchMode)
                           |
                           +---> [ YES ] ---> Intercepts Loop -> Triggers Restart Prompt
                           |                                        |---> [ YES ] -> shutdown.exe -r -t 0
                           |                                        |---> [ NO ]  -> Defers to Next Boot
                           |
                           +---> [ NO ]  ---> Finalizes Run -> Flips Button to STOP State
```
⚙️ Granular Engine Architecture & API Specifications
1. Asynchronous Execution Pipeline (Task.Run)
Executing physical hardware lifecycle commands synchronously on the primary application thread creates severe thread starvation. When Windows waits for an external sub-process (like a shell re-initialization or driver reset) to yield, the User Interface (UI) message loop (WndProc) locks up completely, forcing the operating system to flag the application as "Not Responding."

ReflexCore neutralizes this design flaw by abstracting the entire optimization sequence inside a non-blocking asynchronous task wrapper:
```
C#
btnEngage.Click += async (s, e) => {
    if (!isOptimized) {
        isOptimized = true; ToggleInteractiveFieldsState(false);
        btnEngage.Enabled = false;
        btnEngage.Text = "INJECTING HOOKS..."; btnEngage.BackColor = Color.FromArgb(202, 138, 4);
        
        await ExecuteTuningPipelineAsync();
        
        btnEngage.Text = "STOP OPTIMIZATION"; btnEngage.BackColor = Color.FromArgb(180, 50, 50);
        btnEngage.Enabled = true;
    }
    // ... Shutdown sequence handlers
};
UI Responsiveness: When a user initializes the pipeline, the master button control instantly shifts to a yellow structural state (INJECTING HOOKS...) and disables itself to stop input double-submitting.

Thread Distribution: The execution block is dynamically pushed off the UI thread and scheduled onto the background thread pool via Task.Run(), allowing the real-time execution logger to paint diagnostic updates on screen smoothly without a single millisecond of interface hanging.

2. High-Precision NT Timer Alignment
The standard Windows NT kernel scheduler clock structures thread priority allocations around a default quantizing tick rate of 15.625 milliseconds to limit standby processing draw on mobile devices. On high-refresh-rate desktop displays (144Hz–600Hz), this massive interval variance skews frame presentation timings, resulting in thread block misalignment and acute mouse cursor drift.

ReflexCore establishes precise sub-millisecond thread timing alignment by combining explicit undocumented NT functions with legacy Multimedia timing layers:

C#
[DllImport("ntdll.dll", SetLastError = true)]
private static extern int NtSetTimerResolution(uint DesiredResolution, bool SetResolution, out uint CurrentResolution);

[DllImport("winmm.dll", EntryPoint = "timeBeginPeriod", SetLastError = true)]
public static extern uint TimeBeginPeriod(uint uPeriod);
The Pipeline Method: The engine issues a low-level call to NtSetTimerResolution, requesting a DesiredResolution value of exactly 5000 (computed in 100-nanosecond blocks, establishing a strict 0.5ms scheduling resolution ceiling).

```

The Intercept Failsafe: Because Windows will automatically restore default timer bounds if an executing thread enters a sleep or yield state, ReflexCore simultaneously runs TimeBeginPeriod(1) to anchor the Multimedia Class Scheduler Service (MMCSS). This forces the Windows kernel scheduler to recalculate and dispatch thread blocks exactly every 0.5ms without dropouts.

3. User32 Input Subsystem Optimization (Live 1:1 Parity)
Standard registry scripts that modify mouse tracking behavior try to change the coordinate matrix curves via deep Control Panel\Desktop hex strings. However, the native Windows desktop windowing subsystem only loads these registry configuration hives during user log-in cycles. Altering them via standard tools does absolutely nothing to your current active session unless you manually log out or reboot.

ReflexCore bypasses this limitation by coupling deep registry configurations with an instantaneous live subsystem parameter broadcast:

C#
[DllImport("user32.dll", SetLastError = true)]
[return: MarshalAs(UnmanagedType.Bool)]
public static extern bool SystemParametersInfo(uint uiAction, uint uiParam, int[] pvParam, uint fWinIni);
Immediate Implementation: When RawMouseInput is flagged, the application directly alters MouseSpeed, MouseThreshold1, and MouseThreshold2 strings inside the active registry configuration path.

Subsystem Re-Read Enforcement: The application immediately pushes an array map of { 0, 0, 0 } directly into the User32 layout manager via SystemParametersInfo(SPI_SETMOUSE, 0, mouseParams, SPIF_UPDATEINIFILE | SPIF_SENDCHANGE). This forces the kernel's active display thread to instantly re-read the configuration hive and tear down mouse smooth filtering live, granting the user immediate raw 1:1 cursor translation without forcing a log-out sequence.

4. Bulletproof Process Whitelisting & Memory Sanitation
Standard system memory dumpers or "RAM cleaners" crash essential operating system background trees because they indiscriminately force execution pages out of physical RAM chips. ReflexCore implements a protected heuristic process evaluation grid that safely preserves background task continuity.

The engine maintains a hardened string map hash table whitelisting priority utility handles (e.g., discord, spotify, teamspeak, guilded, steamwebhelper, nvcontainer, explorer, taskmgr, reflexcore, reflexcorefree), your explicit game targets, and core system nodes (explorer, taskmgr). The watchdog thread spins every 5 seconds, capturing active process maps and invoking a clean Win32 API flush via psapi.dll:

C#
[DllImport("psapi.dll")]
public static extern int EmptyWorkingSet(IntPtr hwProc);
Deep Engine Aware Safeguard: To guarantee that crucial user software is never accidentally disrupted, the application evaluates active process structures using a deep engine folder traversal path (\steamapps\, \riot games\, \epic games\, etc.).

DLL Fingerprinting: If a background process path isn't identified, the app scans its execution folder for 13 distinct game architecture signature dependencies (including UnityPlayer.dll, steam_api64.dll, bink2w64.dll, fmodstudio.dll, and EOSSDK-Win64-Shipping.dll). If any game fingerprint matches, the process is skipped automatically. If it's a generic application handle, EmptyWorkingSet is applied, forcing the NT memory manager to cleanly move dead execution pages to page-file swap nodes, instantly recovering clean blocks of physical memory for your game.

# 👑 Pro Suite Systems: Live Hardware Device Layer Modification
The ReflexCore Pro Suite interfaces with specialized Windows hardware classes and system queues. When authorized via encrypted Polar.sh customer portal keys, the execution paths shift from user-level app pruning to hot-plugging structural device driver parameters on the fly.

Provision a Cryptographic Pro Key via the Web Portal to unlock advanced hardware device layer parameters:

🔬 Live Kernel DPC Lane Shunting (KDLS via PowerShell Hot-Plug)
High-polling gaming peripherals operating at 4,000Hz or 8,000Hz throw massive amounts of Interrupt Requests (IRQs) at the CPU every second. Windows schedules these hardware calls to be handled by Core 0 and Core 1 by default. Because your game's frame processing code and rendering cycles rely heavily on those identical primary cores, your CPU undergoes constant severe context-switching latency, resulting in input drops and erratic frame times.

Ini, TOML
[Registry Path]
HKLM\SYSTEM\CurrentControlSet\Enum\PCI\[Device_Hardware_ID]\Device Parameters\Interrupt Management\Affinity Policy
Registry Mapping: The engine traverses the global PCI bus registry hive, finds the parent keys of your physical hardware devices, sets DevicePolicy to 4 (IrqPolicySpecifiedProcessors), and writes a strict binary affinity bitmask array (0xFC, 0xFF, 0x00...) into AssignmentSetOverride. This configuration isolates Core 0 and Core 1 completely from processing hardware interrupts.

Live Device Hot-Plug: Windows normally ignores device affinity changes until the system reboots. ReflexCore applies this change live by spinning up an active hot-plug process thread targeting the exact physical device classes:

PowerShell
Get-PnpDevice -Class USB | Disable-PnpDevice -Confirm:$false; Get-PnpDevice -Class USB | Enable-PnpDevice -Confirm:$false
This command hot-unplugs and re-plugs the active USB controller stack at the motherboard layer. Your mouse and keyboard will cycle and refresh their memory allocations in 2 seconds, forcing the Windows Hardware Abstraction Layer (HAL) to instantly shunt all high-frequency peripheral interrupts to secondary core clusters, giving your game's render thread a clean lane on your primary cores.

# 📡 Live TCP/IP Socket Offloading & Network Adapter Cycling
The default configuration of the Microsoft TCP/IP stack enforces Nagle’s Algorithm (TcpAckFrequency and TCPNoDelay). This protocol buffers tiny data packets in memory and delays sending them until a larger group is built or an acknowledgement packet returns from the server. This network optimization saves data bandwidth but causes severe latency spikes and bullet registration delays in competitive tactical shooters.

Adapter Traversal: ReflexCore Pro locates your network interface keys inside SYSTEM\CurrentControlSet\Control\Class\{4d36e972-e325-11ce-bfc1-08002be10318} and Tcpip\Parameters\Interfaces. It targets every active network adapter GUID on your motherboard and injects TcpAckFrequency = 1 and TCPNoDelay = 1.

Live Network Refresh: To force the operating system to immediately compile and run these new network routing matrices without a PC restart, the Pro pipeline invokes an integrated PowerShell network lifecycle hook:

PowerShell
Restart-NetAdapter -Name '*' -Confirm:$false
This live command forces all active network adapters to disconnect and immediately re-initialize their socket configurations. The entire network adapter routing table is refreshed live in 3 seconds, disabling delayed-ACK and guaranteeing instant, jitter-free transmission of game packets.

# 🎭 Dynamic Tournament Kiosk Mode
Even when minimized or backgrounded, the native Windows desktop environment framework (explorer.exe) frequently checks for updates to system tray notification icons, layout positions, taskbar widgets, and Windows background scaling.

ReflexCore Pro implements a persistent watchdog observer thread that runs at a high priority. The microsecond your game process assumes the primary foreground handle, ReflexCore completely terminates the explorer.exe process tree. This strips away all desktop shell overhead, dropping background UI processing down to 0%.

The engine maintains a safe tracking handle on the game's active Process ID. The exact millisecond you close your game, a Process.Start("explorer.exe") event is fired, instantly restoring your desktop environment, system tray, and taskbar without requiring a system restart.

# 🕵️ Full-Spectrum Telemetry & FSO Eradication
Microsoft's native Diagnostic Tracking Service (DiagTrack) and Connected User Experiences platform constantly poll hardware states and write log segments synchronously to disk, stealing essential I/O cycles. Concurrently, Windows Fullscreen Optimizations (FSO) force a hybrid borderless rendering state that introduces flip-model presentation lag.

ReflexCore Pro systematically rewrites these deep subkeys:

HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection -> Injects AllowTelemetry = 0

HKCU\System\GameConfigStore -> Injects GameDVR_FSEBehaviorMode = 2 (Globally disabling FSO anomalies to lock in pure, native hardware Exclusive Fullscreen performance).

# 🚦 Staged Boot Matrix & Intelligent Reboot Interception
Certain low-level operating system configurations alter parameters inside the Windows boot configuration data storage block (BCD) or re-configure how your discrete graphics card reads driver commands. These deepest system tweaks cannot be applied live in memory because they must load before the main Windows kernel boots.

ReflexCore handles these changes safely through a Staged Boot Matrix. The system runs all instant optimizations live, but if you choose to enable heavy boot-level parameters, the engine intercepts the final execution flow and presents you with a custom Windows dialog:
```
C#
if (requiresReboot) {
    var promptResult = MessageBox.Show(
        "Critical kernel architectures (HAGS, Dynamic Ticks) have been successfully staged, but physically require a full system reboot to inject into the bootloader.\n\nWould you like to restart your PC now?", 
        "System Reboot Required", MessageBoxButtons.YesNo, MessageBoxIcon.Warning);

    if (promptResult == DialogResult.Yes) {
        Process.Start(new ProcessStartInfo { FileName = "shutdown.exe", Arguments = "-r -t 0", CreateNoWindow = true, UseShellExecute = false });
    } else {
        Log("Pending reboot deferred by user. Live features remain active.");
    }
}
```
The features that trigger this staged reboot prompt are:

Disable OS Dynamic Ticks: Runs bcdedit.exe /set disabledynamictick yes. This stops the Windows kernel from putting unused CPU cores into low-power sleep states, which minimizes thread wake-up latency but requires a clean boot to modify the bootloader configuration.

Hardware-Accelerated GPU Scheduling (HAGS): Sets the registry parameter HwSchMode = 2 inside Control\GraphicsDrivers. This re-routes memory management commands from the CPU directly to your dedicated GPU's onboard scheduler, which requires a complete reload of the graphics driver stack during the boot sequence.

# 📥 Deployment & Operational Walkthrough
Because ReflexCore directly interfaces with system hardware registers and writes to secured HKEY_LOCAL_MACHINE registry hives, the application strictly requires Administrator privileges.

Download the production setup package [ReflexCore_Setup_v1.3.0.exe.](https://github.com/MintyLiteralGod/ReflexCore-FPS-Booster/releases/download/1.3.0/ReflexCore_Setup_v1.3.0.exe)

Run the installer. It will automatically request UAC escalation, map your architecture parameters, and install your files to {autopf}\LIFT Esports\ReflexCore.

Launch ReflexCore.exe. The application's main routine will evaluate your administrative token. If you aren't elevated, it will gracefully escalate the task using a secure runas verb loop.

Customize your target games in the Dashboard interface using the path browser or the multi-executable text configuration grid.

Pro Activation Layer: If you have acquired a lifetime license key via Polar.sh, navigate to the Keys tab and paste your alpha-numeric token string. The app securely contacts the Polar API gateway, verifies your status, and saves a cryptographically protected token to your local drive using DPAPI (DataProtectionScope.CurrentUser).

Navigate to the Tweaks panel, choose your optimization preferences, and return to the dashboard to click START OPTIMIZATION. The asynchronous engine will apply your chosen tweaks safely in the background.

## 📁 Configuration Note: All custom whitelists, game strings, toggle states, and visual preferences are written to a localized flat-file called "reflexcore.cfg" in the app directory. Deleting this file completely ## purges the application's local footprint and resets all settings to their original factory defaults.
💻 Technical Build & Compiler Reference
For system administrators, tournament managers, or engineers looking to build or audit the source binary directly from code:

Core Prerequisites:
SDK Version: .NET 7.0 Software Development Kit (SDK) or higher.

Development Environment: Visual Studio 2022 or JetBrains Rider.

Desktop Tools: Ensure the "Desktop Development with C#" workload is checked in your compiler settings to bundle the necessary WinForms rendering structures.

Navigate to your local repository folder and run this build profile:

Bash
# Clone the master source code tree from GitHub
git clone https://github.com/MintyLiteralGod/ReflexCore-FPS-Booster.git

# Move into the project root directory
cd ReflexCore-FPS-Booster

# Restore package references and build configurations
dotnet restore

# Publish a fully optimized, single self-contained application binary
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:PublishReadyToRun=true -p:IncludeNativeLibrariesForSelfExtract=true
⚠️ System Integrity & Subsystem Disclaimer
ReflexCore modifies vital core network routing pipelines, PCIe link-state registers, thread priority distribution matrixes, and kernel scheduling parameters. Although a clean shutdown routine is integrated into the system to gracefully restore default parameters when you close the application, running these optimizations naturally pushes your physical components to higher sustained processing thresholds and overrides thermal/power management safety ceilings.

The developer assumes no responsibility or liability for hardware degradation, file system anomalies, or operational instability resulting from the deployment of these configurations. Use at your own risk.
