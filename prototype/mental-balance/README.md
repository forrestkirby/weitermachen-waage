# Mental Balance Scale (Elementor HTML Widget)

This folder contains a non-plugin prototype for WordPress + Elementor.

## Files

- `elementor-snippet.template.html`: editable source with section markers (`root`, `config`, `styles`, `runtime`)
- `elementor-snippet.paste.html`: paste-ready single block for Elementor HTML widget
- `assets/scale-placeholder.svg`: dummy image (replace with customer scale artwork URL)

## How to embed in Elementor

1. Add an **HTML** widget to the target page.
2. Copy everything from `elementor-snippet.paste.html`.
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
- `persistSession`: `false`

## Behavior implemented

- Add item with `name` + `weight`
- Max 10 items
- Draggable/moveable items across:
  - left pan
  - right pan
  - depot
- Desktop drag-and-drop + pointer-based touch/mobile fallback
- Keyboard/button fallback per item (`Move left`, `Move right`, `Move to depot`)
- Clear all
- Live balance updates with beam tilt based on left/right weight delta

## Test checklist

- Add items 1..10 and verify add-block at item 11
- Verify weight validation (`1-10`)
- Verify name length validation (`maxNameChars`)
- Move items between all zones and verify tilt updates
- Use clear all and verify neutral state
- Test mobile, tablet, desktop

## Notes

- No server-side storage is used.
- Set `persistSession: true` to keep state for current browser session only.
- Replace `image.src` in config with the final customer image URL when available.
