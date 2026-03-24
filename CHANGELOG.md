# Changelog

All notable changes to the Prypco Watermark Portal are documented here.

Format: `[version] YYYY-MM-DD — summary`

---

## [1.0.0] 2026-03-24 — Initial Release

### Added
- **Remove Watermark** tab with brush-based masking and OpenCV.js Telea inpainting
- Paint / Erase brush modes with adjustable size (4–120px)
- Adjustable inpainting radius (1–30)
- Batch queue for multiple images — each image retains its own mask
- Auto-advance queue option after inpainting
- Before / After preview toggle
- Per-image result download

- **Add Prypco Watermark** tab with live canvas preview
- Configurable text, font size (10–300), color, opacity (1–100%), rotation (−180° to +180°)
- 9-point position grid
- Tiled diagonal watermark pattern
- Output format selector (same as input / JPEG / PNG / WebP)
- Batch apply with ZIP download for multiple images

- Drag-and-drop upload on both tabs
- Toast notification system
- Dark navy sidebar, Prypco amber accent, professional UI
- OpenCV.js loading screen with spinner

### Technical
- Single self-contained `index.html` — no server, no build tools
- Hosted on GitHub Pages (free)
- OpenCV.js WASM inpainting with mask dilation for cleaner edges
- Safe `FileReader.readAsDataURL` pipeline (avoids `file://` canvas taint)
- All OpenCV Mats explicitly deleted to prevent WASM memory leaks
- UI thread yielded before inpainting to allow "Processing…" state to render
