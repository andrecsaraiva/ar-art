# Wall Art AR V1

Modified files:
- index.html
- ar-view.html
- js/main.js
- css/styles.css

Expected asset structure:
- assets/models/quadro.glb
- assets/hdr/glasshouse_interior_4k_blur_exp_sat.hdr

What this version does:
- keeps the existing product-page / GLB viewer structure
- changes the model path to `./assets/models/quadro.glb`
- keeps the same HDR path
- adds AR buttons for wall placement
- uses `<model-viewer>` with:
  - `ar`
  - `ar-modes="webxr scene-viewer"`
  - `ar-placement="wall"`
  - `ar-scale="fixed"`
  - `xr-environment`

GLB preparation notes:
- The GLB should be real-world scale.
- Use meters as unit scale.
- The object should be centered around its origin.
- For wall placement, the back side of the model should face the negative Z direction.
- The front/artwork side should face positive Z.
- Put the pivot/origin at the center of the artwork/frame.
- Keep the back surface flat and close to Z=0 when possible.
- Apply transforms before export: Ctrl+A > All Transforms.
- Export as GLB named `quadro.glb`.


## V2 change

This version forces wall AR to use WebXR only:

```html
ar-modes="webxr"
ar-placement="wall"
```

Why:
- Scene Viewer may fall back to horizontal surface placement.
- If the object appears on a table/floor, the experience is probably not using WebXR wall placement.
- WebXR-only is stricter: if wall placement is unsupported on the device/browser, AR may not start, but it avoids the wrong table/floor placement.

Testing tips:
- Use Android Chrome.
- Use HTTPS.
- Test on a wall with texture/contrast, not a blank glossy wall.
- Move the phone slowly to let WebXR detect the vertical plane.
