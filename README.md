# Pagger — All In One

A single self-contained page that decodes **and** generates Flipper Zero `.sub`
files for Retekess **T119 / TD157 / TD165 / TD174** pagers.

Combines the four separate tools from the original
[Pagger project](https://github.com/meoker/pagger) into one page:

- **Decode** a captured hex key into Station / Pager / Action numbers.
- **Generate** Key files (single pager), RAW files (ranges of pagers), and the
  special Turn-off / Desync files.

Pick the device from the dropdown at the top — every pane adapts to the
selected model's bit layout, protocol, TE and frequency.

## Hosting

Served as a static page via GitHub Pages — `index.html` at the repo root.

## Credit

Original tools and protocol reverse-engineering by
[meoker/pagger](https://github.com/meoker/pagger).
