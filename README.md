# AeroTester — Browser wind tunnel

A static GitHub Pages app for local STL viewing and airflow-field visualization. Uploads and simulation stay in the browser.

## Features
- STL file upload (binary or ASCII)
- Three.js orbit camera, fit/reset
- External flow and internal-mask mode
- Rotation X/Y/Z fields + presets; apply rotation, then explicitly run solver
- 2D D2Q9 BGK Lattice-Boltzmann field solver runs in a Web Worker
- Cached results for identical flow configuration
- Velocity and approximate pressure coloring; streamlines
- Display/camera actions do not run the solver

## GitHub Pages
Repository Settings → Pages → Source: **GitHub Actions**. Push to `main` and the workflow deploys automatically.

Live site (after Pages has been enabled): https://the-name-royce-was-taken.github.io/aero-tester/

## Running locally
Serve the root folder over HTTP (the Three.js ES modules need HTTP):

```bash
python -m http.server 8000
```

Then open http://localhost:8000

## Accuracy & limitations
This is a **2D projected** D2Q9 BGK flow visualization—not 3D CFD. STL triangles are projected into the X–Z plane and rasterized into an obstacle mask. The internal mode treats the projected silhouette as a fluid-region approximation. The solver does not implement mesh repair, boundary-layer refinement, turbulence models, validated force integration, or engineering-grade 3D pressure. Use for qualitative visualization/learning only, not engineering decisions.

AeroTester uses Three.js from jsDelivr CDN. A network connection is required for the Three.js module.
