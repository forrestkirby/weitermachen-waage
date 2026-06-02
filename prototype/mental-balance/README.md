# Mental Balance Scale (Elementor HTML Widget)

This folder contains a non-plugin prototype for WordPress + Elementor.

## Files

- `elementor-snippet.template.html`: editable source with section markers (`root`, `config`, `styles`, `runtime`)
- `assets/scale-placeholder.svg`: sketch to upload to WordPress Media Library (replace with final artwork when ready)

## How to embed in Elementor

1. Add an **HTML** widget to the target page.
2. Copy everything from `elementor-snippet.template.html`.
3. Paste into the widget and save.
4. Clear page cache/CDN cache if needed.

## Configuration

Edit the JSON inside `<script type="application/json" id="mbs-config">`.

Recommended defaults:

- `maxItems`: `10`
- `maxNameChars`: `40`
- `minWeight`: `1`
- `maxWeight`: `10`
- `maxTiltDeg`: `18`
- `tiltFactor`: `1.8`
- `persistSession`: `false` (set `true` to keep state for the current browser session only)
- `showDepot`: `false` (set `true` to show the depot area and “In Ablage” move button)

### Scale image (WordPress)

1. Upload `assets/scale-placeholder.svg` (or final artwork) to **Media → Library**.
2. Copy the file URL from the media item.
3. Set `image.src` in config to that full URL (not a repo-relative path).

Example:

```json
"image": {
  "src": "https://example.com/wp-content/uploads/2026/06/scale-placeholder.svg",
  "alt": "Waage Illustration"
}
```

## Behavior implemented

- Add item with `name` + `weight` (German UI, Du form)
- Max 10 items
- Draggable/moveable items between left and right pans (depot optional via `showDepot`)
- Only the beam bar tilts; pans and chips stay level for readability
- Per-pan **Gesamt** total badge at the top of each pan
- Desktop drag-and-drop + pointer-based touch/mobile fallback
- Keyboard/button fallback per item (`Nach links`, `Nach rechts`; depot button when `showDepot` is true)
- Clear all
- `prefers-reduced-motion`: beam stays level

## Test checklist

- Add items 1..10 and verify block at item 11
- Verify weight validation (`1-10`)
- Verify name length validation (`maxNameChars`)
- Move items left/right; verify beam tilts, pans stay level, **Gesamt** updates
- On viewport &lt; 700px: chip weight appears below title
- Depot hidden when `showDepot: false`
- Use clear all and verify neutral state
- Test mobile, tablet, desktop

## Notes

- No server-side storage is used.
- Re-enable depot: set `showDepot: true` in config (depot logic remains in JS).
