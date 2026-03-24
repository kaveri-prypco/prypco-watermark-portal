# Prypco Watermark Portal

A standalone, browser-based web app for removing and adding watermarks to images — no server, no install, just open the URL.

🌐 **Live:** https://kaveri-prypco.github.io/prypco-watermark-portal/

---

## Features

### ✂ Remove Watermark
- Paint a mask over the watermark area using the brush tool
- AI-powered inpainting (OpenCV.js / Telea algorithm) intelligently fills the region
- Adjustable brush size and inpaint radius
- Before / After toggle to review results
- Batch queue — process multiple images sequentially, each with its own mask
- Auto-advance to next image after processing

### ✦ Add Prypco Watermark
- Upload single or bulk images (JPG, PNG, WebP)
- Fully configurable: text, font size, color, opacity, rotation, position
- 9-point position grid (TL / TC / TR / CL / CC / CR / BL / BC / BR)
- Tiled pattern mode for diagonal repeat watermark
- Live preview updates instantly as you adjust settings
- Single image → direct download; multiple images → ZIP download

---

## Usage

Open the portal in any modern browser (Chrome or Edge recommended):

```
https://kaveri-prypco.github.io/prypco-watermark-portal/
```

Or run locally — see [Local Development](#local-development) below.

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| UI        | Vanilla HTML / CSS / JavaScript |
| Inpainting | [OpenCV.js 4.8.0](https://docs.opencv.org/4.8.0/) — WASM, runs in browser |
| Batch ZIP  | [JSZip 3.10.1](https://stuk.github.io/jszip/) |
| Downloads  | [FileSaver.js 2.0.5](https://github.com/eligrey/FileSaver.js) |
| Fonts      | [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts |
| Hosting    | GitHub Pages (free) |

No build tools, no npm, no backend. Single HTML file.

---

## Project Structure

```
prypco-watermark-portal/
├── index.html          # Main application (entire app in one file)
├── assets/
│   └── logo/           # Place Prypco logo files here (for future logo watermark feature)
├── docs/
│   └── screenshots/    # UI screenshots for documentation
├── CHANGELOG.md        # Version history
└── README.md           # This file
```

---

## Local Development

Since this is a single HTML file with no build step, just open it directly:

```bash
# Option 1 — Open file directly in browser (Chrome/Edge)
start index.html

# Option 2 — Serve with Python (avoids any file:// quirks)
python -m http.server 8080
# Then open http://localhost:8080

# Option 3 — Serve with Node.js
npx serve .
# Then open http://localhost:3000
```

---

## Updating the Portal

Edit `index.html`, then deploy:

```bash
git add index.html
git commit -m "feat: describe your change here"
git push
```

GitHub Pages updates within ~30 seconds.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

---

## Notes

- **First load** takes ~5–10 seconds while OpenCV's WebAssembly compiles (cached after first visit)
- **Inpainting quality** depends on background complexity — works best on uniform or gradient backgrounds
- **Large images** (> 4MP) may cause a brief UI freeze during inpainting; this is normal
- **WebP output** is not supported in Safari — falls back to PNG automatically

---

## Roadmap

- [ ] Logo-based Prypco watermark (upload logo file)
- [ ] Watermark removal from known fixed-position stamps
- [ ] Undo / redo history for mask editing
- [ ] Side-by-side split-screen before/after view
- [ ] Drag to reorder batch queue
