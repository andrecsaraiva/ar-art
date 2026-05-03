# Wall Art AR V3 - Custom WebXR

Modified files:
- index.html
- ar-view.html
- js/main.js

Expected asset structure:
- assets/models/quadro.glb
- assets/hdr/glasshouse_interior_4k_blur_exp_sat.hdr

What changed from V2:
- AR camera is now custom Three.js + WebXR instead of model-viewer AR.
- The artwork is NOT created automatically.
- The user must tap Place on Wall when WebXR finds a wall/surface.
- Added Manual Place for blank white walls.
- Added Move, Reset, Size controls and Exit AR.

Why:
- model-viewer AR may place the object on the first detected surface.
- Custom WebXR gives us control over when the model is placed.
- Blank white walls often have no feature points, so hit testing can fail.
- Manual Place creates a usable fallback for plain walls.

GLB prep:
- File name: quadro.glb
- Folder: assets/models/quadro.glb
- Use real scale in meters.
- Pivot/origin at center of the frame/poster.
- Front of the artwork should face +Z.
- Back should face -Z.
- Apply transforms before export.


## V4 debug fix

This version changes the AR page imports from unpkg example modules to esm.sh modules and adds a visible debug log.

Why:
- if the module import failed, the Start Wall AR button would look broken because the click handler was never attached.
- this page now prints boot, model loading, HDR loading, WebXR support, and AR start errors directly on the page.
