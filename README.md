# Pagger — All In One

A single self-contained HTML page (`index.html`, no build step, no dependencies)
that decodes **and** generates Flipper Zero `.sub` files for Retekess
**T119 / TD157 / TD163 / TD165 / TD174** pagers, and can push them straight to a
Flipper over Bluetooth.

It unifies the separate tools from the original
[Pagger project](https://github.com/meoker/pagger) into one page. Pick the device
in the **Device** pane and the generator adapts to that model's bit layout,
protocol, TE and frequency.

> **TD163 is provisional.** Its layout was reverse-engineered and verified against
> the UberGuidoZ TD163 captures (SMC5326 · 25-bit · TE ~213 µs · 433.92 MHz), and
> low pager numbers decode correctly. But Retekess rates the TD163 to 998 — which
> needs a wider field than the verified captures cover — so **high pager numbers
> aren't trustworthy yet**, and no real turn-off/cancel command has been captured
> (see the Special-file note below). Treat TD163 output as experimental until
> confirmed against your own hardware.

## What it does

- **Send to Flipper** *(Bluetooth · experimental)* — connect to a Flipper over
  Web Bluetooth, write the last generated file to `/ext/subghz/pagger/`, mirror
  the device screen, drive it with an on-screen D-pad, and transmit — no cable or
  manual import. **Android Chrome only**; disconnect the official Flipper app
  first. The Download button is always available as a fallback.
- **Decode** a captured 6-hex-digit key into Station / Pager / Action numbers.
  Every model is decoded at once; impossible rows are ruled out and a "signal
  fingerprint" (frequency · protocol/bit · TE) is shown to match against the
  Flipper read screen. **Use** loads a row into the generator.
- **Generate** a RAW `.sub` calling every pager across a station/pager range,
  with a repeat count (single pager = set *from*/*to* equal). _(For **TD163** the
  RAW timing isn't verified, so it emits a decoded **SMC5326 key** `.sub` instead
  of RAW.)_
- **Special file** — per model: a **Turn-off** broadcast (T119 / TD157 / TD165)
  or a **Desync** command (TD174). For **TD163** this is **not verified** — no
  cancel command has been reverse-engineered yet, so the button just sends a normal
  call to pager 0 (and is labelled as such). Capture a real cancel press and the
  proper code can be added.

## Hosting

Static page — serve `index.html` from any web host (e.g. GitHub Pages at the repo
root). Ships with a PWA `manifest.webmanifest` and icons for install-to-homescreen.

## Credit

Original tools and protocol reverse-engineering by
[meoker/pagger](https://github.com/meoker/pagger).
