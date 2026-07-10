<p align="center">
  <img src="ReflexCore-Web/reflex.ico" alt="ReflexCore" width="72" height="72" />
</p>

<h1 align="center">REFLEXCORE</h1>

<p align="center">
  <strong>Windows performance orchestration for competitive gaming.</strong><br/>
  Kill micro-stutter. Isolate 8K input. Boost foreground play — without injecting into games.
</p>

<p align="center">
  <a href="https://reflexcore.xyz"><img src="https://img.shields.io/badge/Website-reflexcore.xyz-00e673?style=for-the-badge" alt="Website" /></a>
  <a href="https://reflexcore.xyz/#pro"><img src="https://img.shields.io/badge/Pro-REFLEX99-d1b464?style=for-the-badge" alt="Pro" /></a>
  <a href="https://discord.gg/34pCtCpQJv"><img src="https://img.shields.io/badge/Discord-Support-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.5.0-ff0040?style=flat-square" alt="v1.5.0" />
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11%20x64-0078d4?style=flat-square&logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/.NET-8.0-512bd4?style=flat-square&logo=dotnet&logoColor=white" alt=".NET 8" />
  <img src="https://img.shields.io/badge/games-350%2B%20catalog-00e673?style=flat-square" alt="350+ games" />
</p>

---

## What is ReflexCore?

ReflexCore is a **native Windows optimizer** built for players who care about frame pacing, input latency, and high-polling mice. It watches your foreground game, applies reversible OS-level tweaks, and backs off when you're done — **no DLL injection, no anti-cheat evasion, no sketch.**

Think of it as a **competitive play orchestrator**: power plans, MMCSS, USB queues, UE config tuning, and a click-through performance HUD — all from one neon control panel.

```
   ┌─────────────┐     foreground      ┌──────────────────┐
   │  Your Game  │ ◄────────────────── │  ReflexCore      │
   │  (UE/FPS)   │   detect + profile  │  Orchestrator    │
   └─────────────┘                     └────────┬─────────┘
          ▲                                     │
          │         one-shot engage             ▼
          └─────────────── OS tweaks ─── timer / MMCSS / USB / DWM
```

---

## v1.5.0 highlights

| Feature | What it does |
|--------|----------------|
| **350+ game catalog** | Embedded `games.manifest.json` — nicknames, process names, instant O(1) foreground match |
| **Universal 4K / 8K orchestration** | Tiered play profiles for catalog titles, Unreal Engine, and Splitgate |
| **Performance HUD** | Click-through overlay — 6 positions, 6 esports themes (Neon, Cyber, Toxic, Gold, Purple, Minimal) |
| **Auto Game Profile** | Power plan + UE tuning when a matched title hits foreground |
| **CPU anti-stutter guard** | Throttle off, sleep inhibit, priority boost during play |
| **WM_INPUT isolation** | At 4K+ on UE/Splitgate, ReflexCore stops sampling mouse so your game isn't starved |
| **One-shot session engage** | No per-tick re-apply churn — fixes mouse/timer freeze regressions |
| **Minecraft-safe affinity** | JVM / UWP titles skip harmful CPU pinning |
| **Safety Center** | Registry backup, restore point, HUD controls, honest system state |
| **ReD Theme Matrix** | Multiple UI skins — cycle live from the sidebar |

---

## Free vs Pro

| | **Free** | **Pro** |
|---|:---:|:---:|
| Baseline Windows tweaks (ticks, NTFS, Nagles, MMCSS, Game DVR, power plan) | ✅ | ✅ |
| 350+ game auto-detection & foreground boost | ✅ | ✅ |
| Performance HUD + theme matrix | ✅ | ✅ |
| UE config tuning & cache clean | ✅ | ✅ |
| 4K / 8K orchestration (safe paths) | ✅ | ✅ |
| Recommended competitive preset | ✅ | ✅ (full kernel stack) |
| **KDLS** — Kernel DPC Lane Shunting | — | ✅ |
| **8K Shield** — deep mouse queues + WM_INPUT isolation | — | ✅ |
| **MSI interrupt routing** | — | ✅ |
| **Win32 quantum priority** | — | ✅ |
| **Max USB polling** / IRQ steering | — | ✅ |
| **DXGI low-latency** / WDDM queue trim | — | ✅ |
| **VRAM flush** / auto RAM purge | — | ✅ |
| **Tournament mode** (quiet background) | — | ✅ |
| **Splitgate 8K Extreme** (opt-in) | — | ✅ |

> **Pro lifetime:** [$9.99 at reflexcore.xyz](https://reflexcore.xyz/#pro) — use promo code **`REFLEX99`** at checkout.  
> Activate in-app: **Activate License Key** (Polar-backed, 7-day offline grace).

---

## Splitgate & Unreal 8K

For **Splitgate** and other **UE4/UE5** titles at **7500+ Hz** polling:

- **Safe path (default / Recommended):** neutral OS timer + native assist INI — no fighting UE's render clock
- **8K Extreme (Pro, opt-in):** 768 mouse / 256 keyboard queues, USB IRQ isolation, KDLS, DWM/WDDM boost, 50% render INI

Extreme mode shows a one-time warning and writes game INI — **restart the game** after enabling.

---

## Download & run

1. Get the latest build from **[reflexcore.xyz](https://reflexcore.xyz/#download)** or [GitHub Releases](https://github.com/MintyLiteralGod/hiddencore/releases)
2. Run `ReflexCore-Setup-1.5.0.exe` (or `ReflexCore.exe` from a publish folder)
3. Accept the **UAC Administrator** prompt — kernel/registry tweaks require elevation
4. Hit **START OPTIMIZER**, launch your game, watch the HUD light up

**Discord:** [discord.gg/34pCtCpQJv](https://discord.gg/34pCtCpQJv)

---

## Build from source (Windows)

```powershell
cd "C:\Users\Kaedyn VR\Documents\ReflexCoreFree"
git fetch origin
git checkout cursor/flawless-8k-4k-orchestrator-7e1b
git pull origin cursor/flawless-8k-4k-orchestrator-7e1b

# Dev run
dotnet run --project ReflexCore.csproj

# Release installer (publish + Inno Setup)
powershell -NoProfile -ExecutionPolicy Bypass -File ".\build-release.ps1" -SelfContained -Inno
```

Or double-click **`BUILD_INSTALLER.cmd`** in the project root.

Full installer docs: [`Installer/README.md`](Installer/README.md)  
Ship checklist: [`SHIPPING.md`](SHIPPING.md)

### Common build gotchas

| Problem | Fix |
|--------|-----|
| `dotnet-tools.json` blocked (Mark of the Web) | `Unblock-File -LiteralPath ".\.config\dotnet-tools.json"` |
| Scripts disabled | Use `BUILD_INSTALLER.cmd` or `-ExecutionPolicy Bypass` |
| Inno "No files found" line 68 | Run publish first — don't compile `.iss` before `dotnet publish` |
| Hundreds of CS0101 errors | Run `.\scripts\verify-clean-sources.ps1` — likely duplicate `GameCatalog.cs` |
| MSB4025 project file invalid | Run `.\repair-project.ps1` or restore `ReflexCore.csproj` from git |

Always build with **`ReflexCore.csproj`** — not legacy `ReflexCoreFree.csproj` or `Form1.cs`.

---

## Safety & fair play

ReflexCore is **external-only**:

- No process injection
- No anti-cheat bypass
- No EAC/BE evasion tooling

Follow your game's publisher and tournament rules. Disable overlays or system tweaks if a league forbids them.

Config lives beside the exe as `ReflexCoreConfig.json`. Safety Center can snapshot registry state before you go wild.

---

## Project layout

```
ReflexCore.csproj          Main app (.NET 8 WinForms)
Program.cs                 UI shell + optimization engines
GameCatalog.cs             350+ game index
games.manifest.json        Embedded game database
HighPollingPlayOrchestrator.cs   4K/8K profile routing
SplitgatePlayEngine.cs     Splitgate / UE play coordinator
PerformanceHudEngine.cs    Click-through gaming overlay
Installer/                 Inno Setup script
ReflexCore-Web/            reflexcore.xyz site assets
build-release.ps1          Publish + installer pipeline
```

---

## Links

| | |
|---|---|
| **Website** | [reflexcore.xyz](https://reflexcore.xyz) |
| **Pro license** | [reflexcore.xyz/#pro](https://reflexcore.xyz/#pro) |
| **Updates** | [reflexcore.xyz/version.json](https://reflexcore.xyz/version.json) |
| **Discord** | [discord.gg/34pCtCpQJv](https://discord.gg/34pCtCpQJv) |

---

<p align="center">
  <sub>Built for players who feel the difference between 240 FPS and <em>stable</em> 240 FPS.</sub><br/>
  <sub>ReflexCore v1.5.0 — © ReflexCore</sub>
</p>
