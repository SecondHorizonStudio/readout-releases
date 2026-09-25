# Readout

A menu bar instrument panel for your Mac: network, disk, temperatures, fans,
CPU and memory, in one menu bar item. Per-app network attribution, threshold
alerts, and optional fan control that fails safe. Free.

Website: [macreadout.com](https://macreadout.com)

**This repository is the download and issue tracker. The source is not public.**

---

## Install

**Homebrew** (recommended, since it handles upgrades):

```
brew install --cask secondhorizonstudio/tap/readout
```

**Or by hand:**

1. Download `Readout-x.y.z.zip` from [Releases](../../releases).
2. Drag `Readout.app` into your Applications folder and open it.
3. Readout appears in your menu bar. That's the app: no Dock icon, no window.

The app is signed and notarized by Apple, so it opens without a Gatekeeper
detour.

**Requirements:** macOS 14 or newer. Built for Apple Silicon; Intel Macs are
partially supported (no performance/efficiency core split, fewer
temperature sensors, fan control untested).

---

## What you get

By default every widget you turn on shares **one** menu bar item, divided by
hairlines, so four widgets take less room than two separate apps would. Turn
off "Combine into one menu bar item" in Settings if you'd rather ⌘-drag each
one on its own.

| Widget | Shows |
|---|---|
| **Network** | upload / download rates, optional sparkline |
| **Disk** | read / write activity, free space |
| **CPU + Memory** | usage, split by efficiency and performance cores |
| **Temp + Fans** | hottest sensor, fan RPM |
| **UTC clock** | 24-hour UTC time, off by default |

Widgets use the standard frosted menu bar style, so they stay legible on any
wallpaper. Prefer color? There's a toggle for that.

Click the menu bar item for the full dashboard; right-click it for the menu.

### Finding what's hogging things

- **Network by app:** which apps are using your connection, with live rates
  and rolling five-minute totals. Anything that uploads more than 50 MB or
  downloads more than 500 MB inside that window is flagged in orange.
- **Memory by app:** the same figure as Activity Monitor's Memory column,
  with each app's helper processes counted with it (Safari's web content
  counts as Safari). An optional Swap tab ranks apps by paging activity,
  because macOS doesn't report which process owns swap.
- **CPU by process:** everything at 0.1% of a core or above, with an
  estimate of whether each app's work leans on the performance or the
  efficiency cores.
- **Every temperature sensor** your Mac exposes (28 on an M1 Max, after
  deduplication), with readable names instead of codes like `PMU tdev7`.
  Celsius or Fahrenheit.

### Alerts

Set a threshold on CPU load, temperature, memory used, memory pressure or
free disk space in **Settings → Alerts**, choose how long it has to hold
(ten seconds to an hour), and Readout posts one notification per episode.
It re-arms only after the value recovers with a margin, so a reading
hovering at the line is one alert, not a stream. Off until you add a rule.

### Fan control

Off by default. Turn it on in **Settings → Fans** and approve the helper once,
then choose:

- **Auto:** macOS decides, same as always.
- **Curve:** draw your own temperature-to-speed curve. Quiet when cool,
  aggressive when hot.
- **Manual:** a speed slider.
- **Max:** for long exports and renders.

**Your fans can't get stranded.** Speeds are clamped to what your hardware
allows, inside the helper. If Readout crashes, the helper puts the fans back
on automatic in under a second; if it freezes, a dead-man switch does it
within 20 seconds (18 when measured). Any CPU sensor reaching 95 °C forces
automatic control regardless of your settings, and if temperatures stop
arriving for 30 seconds in a non-automatic mode, the fans go back to
automatic too. A fanless Mac simply has no Fans section.

---

## Updates

Once a day Readout asks GitHub whether a newer release exists (you can turn
this off in **Settings → General**). A new version posts one notification,
once. Nothing is downloaded until you choose to update:

- **Homebrew installs** are pointed at
  `brew upgrade --cask secondhorizonstudio/tap/readout`.
- **Direct installs** can click **Download and install**: Readout fetches the
  release, verifies it is signed by the same developer identity (anything
  else is refused), swaps itself, and relaunches. **Open release page** is
  there if you'd rather do it by hand.

---

## Privacy

No telemetry, no analytics, no account. The only network request Readout
makes on its own is that daily update check: an anonymous request to GitHub
that sends nothing about you or your Mac. Diagnostics stay on your disk, in
`~/Library/Logs/Readout.log` and a failure journal you can read, copy, or
delete.

---

## Something wrong?

Open an [issue](../../issues). **Settings → Health → Report a problem…**
opens the bug form with your diagnostics already filled in, for you to read
before you submit; **Copy diagnostics** puts the same text on your clipboard.

Verified end to end on an M1 Max MacBook Pro. Running an **M3, M4, or newer**
Mac, an Intel Mac, a fanless Mac, or a desktop? Those paths are written to
fail safe but haven't been confirmed on real hardware. Run
`/Applications/Readout.app/Contents/MacOS/Readout --compat` and paste the
output into a [hardware report](../../issues/new?template=hardware-report.yml).

---

## Related

- [Brightness Controller](https://brightnesscontroller.com): one slider for
  every screen on your Mac, also free.
