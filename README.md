# Readout

A menu bar instrument panel for your Mac — network, disk, temperatures, fans,
CPU and memory, in as many slots as you want to give it. Plus optional fan
control, for free.

**This repository is the download and issue tracker. The source is not public.**

---

## Install

**Homebrew** (recommended — gets you upgrades):

```
brew tap back2business/tap
brew install --cask back2business/tap/readout
```

**Or by hand:**

1. Download `Readout-x.y.z.zip` from [Releases](../../releases).
2. Drag `Readout.app` into your Applications folder and open it.
3. Widgets appear in your menu bar. That's the app — no Dock icon, no window.

The app is signed and notarized by Apple, so it opens without a Gatekeeper
detour.

**Requirements:** Apple Silicon Mac (M1 or later), macOS 14 or newer.

---

## What you get

Each widget is its own menu bar item, so you can ⌘-drag them anywhere and turn
on only the ones you care about — one slot or four, your call.

| Widget | Shows |
|---|---|
| **Network** | upload / download rates, optional sparkline |
| **Disk** | read / write activity, free space |
| **CPU + Memory** | usage, split by efficiency and performance cores |
| **Temp + Fans** | hottest sensor, fan RPM |

By default they use the standard frosted menu bar style, so they stay legible
on any wallpaper. Prefer color? There's a toggle for that.

Click any widget for the full dashboard.

### Finding what's hogging things

- **Network by app** — see which apps are actually using your connection, with
  rolling five-minute totals. Anything moving unusual volume gets flagged, so
  the "why is something uploading gigabytes" question has an answer.
- **Memory by app** — the heaviest processes, called out as likely culprits
  when your Mac starts leaning on swap.
- **Every temperature sensor** your Mac exposes (63 of them on an M1 Max), with
  readable names instead of codes like `PMU tdev7`.

### Fan control

Off by default. Turn it on in **Settings → Fans** and approve the helper once,
then choose:

- **Auto** — macOS decides, same as always.
- **Curve** — draw your own temperature-to-speed curve. Quiet when cool,
  aggressive when hot.
- **Manual** — a speed slider.
- **Max** — for long exports and renders.

**Your fans can't get stranded.** Speeds are clamped to what your hardware
allows; if Readout quits, crashes, or freezes, the helper puts fans back on
automatic within 15 seconds on its own. Any sensor hitting 95 °C forces
automatic control immediately, regardless of your settings. These paths are
tested, not just designed — see the release notes for measured numbers.

---

## Privacy

Readout sends nothing anywhere. No telemetry, no analytics, no network calls
of any kind. Diagnostics stay in `~/Library/Logs/Readout.log` and a local
failure journal you can read, copy, or delete.

---

## Something wrong?

Open an [issue](../../issues). If it's misbehaving, **Settings → Health →
Copy diagnostics** puts everything useful on your clipboard — paste that in.

Running an **M3, M4, or newer** Mac? Fan control uses a different write path on
those chips that hasn't been verified on real hardware yet. If you try it,
a [hardware report](../../issues/new?template=hardware-report.yml) would be
genuinely useful.

---

## Related

- [Brightness Controller](https://github.com/back2business/brightness-controller-releases)
  — one slider for every screen on your Mac, also free.
