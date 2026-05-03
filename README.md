# Wall Art AR V6 - Clean Model-Viewer Wall

Modified files:
- index.html
- ar-view.html
- js/main.js

This version reverts from the custom Three.js/WebXR attempt back to the cleaner free model-viewer approach.

Key settings:
```html
ar-modes="webxr"
ar-placement="wall"
ar-scale="fixed"
xr-environment
```

What changed:
- Removed custom Three.js AR/debug page.
- Removed visible debug logs.
- Kept WebXR-only wall placement to avoid Scene Viewer table/floor fallback.
- Added clearer UX: user should point at the wall first, scan nearby references, then tap View on Wall.
- Added lightweight AR status messaging.

Limitations:
- It cannot force a blank white wall to be trackable.
- It cannot continuously recalculate placement after the browser has placed the object.
- It relies on WebXR/ARCore plane detection.
- For blank white walls, the practical workaround is scanning nearby contrast: corners, shadows, outlets, frames, furniture, baseboards, floor/wall edge.

Expected assets:
- assets/models/quadro.glb
- assets/hdr/glasshouse_interior_4k_blur_exp_sat.hdr

GLB prep:
- Real-world scale in meters.
- File name: quadro.glb.
- Back of artwork should face the wall.
- Front should face the camera.
- Origin/pivot centered on the artwork/frame.
- Apply transforms before exporting.
