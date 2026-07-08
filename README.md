# studio-tools
# Studio Tools — Belmont AET

**Live URL:** https://bradwintersmusic-cloud.github.io/studio-tools/

Four-tab audio utility suite built entirely on the Web Audio API. No external data dependencies or libraries.

---

## Overview

All tools run entirely in the browser. Microphone access is requested only when a mic-dependent tool is activated. A shared mic manager coordinates stream access across tools.

---

## Tab 1 — Tempo / Delay Calc

**Tap Tempo**
- Large tap button with flash feedback
- Averages last 8 taps within a 2.5-second rolling window
- Manual BPM input field
- Reset button clears tap history

**Live Beat Detection**
- Shared mic input with sensitivity slider (1–10)
- Energy-based onset detection with median interval smoothing
- Continuously updates BPM display and delay calculator
- Start/Stop toggle

**Metronome**
- Synthesized square-wave click
- Pulse indicator bar
- Auto-stops when switching tabs or backgrounding the page

**Delay Calculator**
- Note values: 1/1 through 1/128
- Dotted values toggle (×1.5)
- Auto-updates from tap tempo or manual BPM

**Polyrhythm Reference**
- Triplets (3:2), 3-over-4, 5-over-4, 7-over-4
- All values update with BPM

---

## Tab 2 — Key / Frequency

**Key Detection**
- Krumhansl-Schmuckler algorithm
- Analyses rolling audio buffer every 2 seconds
- Confidence percentage display
- Hold button locks detected key
- Apply to Chart button updates root key dropdown and rerenders frequency table

**Key / Note / Frequency Table**
- Root key selector (all 12 chromatic notes)
- Scale: Major or Natural Minor
- A4 reference pitch: 432 / 440 / 442 / 444 Hz
- Displays all scale degree notes from 20Hz–20kHz grouped by octave
- Frequency range descriptions per note

---

## Tab 3 — Tuner / Signal Generator

**Tuner**
- YIN algorithm pitch detection
- 4096-sample buffer for accurate bass/guitar tracking (20Hz–2kHz range)
- Semicircular needle display with smoothed ballistics
- In-tune zone: ±5 cents (green)
- Flat = blue needle, Sharp = gold needle
- Holds last detected note when signal drops below noise floor
- Independent mic stream (not shared with analysis tools)

**Signal Generator**
- Waveforms: Sine, Square, Sawtooth, Triangle, White Noise, Pink Noise, Brown Noise
- Frequency: 20Hz–20kHz with logarithmic slider (1kHz at center)
- Volume: 0–100%
- Frequency and volume inputs sync between slider and number field
- Auto-stops when tuner is enabled

---

## Tab 4 — Analysis

All analysis tools share a single mic stream managed by the Enable/Disable Mic button.

**Frequency Analyzer**
- Visualization: Bar graph or filled curve toggle
- Range: Full (20Hz–20kHz) or Focused (20Hz–10kHz) toggle
- Logarithmic frequency axis
- Peak hold: None / 3-second / Persistent (shared with level meter)
- Color gradient: green (low) → gold (mid) → red (high)

**Level Meter**
- Dorrough-style dual horizontal meters (L and R, mirrors mono input)
- Peak indicator: instant attack, 1.7-second hold, exponential decay
- RMS fill: fast attack, slow release (~300ms)
- Clip indicator latches at 0dBFS until mic is restarted
- Integrated LUFS: rolling 10-second window
- Relative SPL: slow-smoothed RMS with +94dB offset (uncalibrated)

---

## Mic Behavior

- Tuner has its own independent mic stream
- Beat detection, key detection, and analysis tools share a mic stream via the shared mic manager
- All mic streams release automatically when switching tabs or backgrounding the browser

---

## Tech Stack

- Static HTML / CSS / JS
- Web Audio API (all audio processing)
- No external libraries or data dependencies
- GitHub Pages hosting

---

## Repo

`bradwintersmusic-cloud/studio-tools`
Maintained by Belmont University AET — Mike Curb College of Entertainment & Music Business