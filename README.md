# Particle Heart (Hand Tracking + 3D Particles)

A single-file web experience that uses **MediaPipe Hands** for hand tracking and **Three.js** for a large **3D particle system**. Move your hand to **rotate/scale** the particles and use finger gestures to morph the particle shape between:

- ❤️ Heart
- ★ 3D star
- ⬤ Smooth sphere

## Demo
Open the project in your browser and allow camera permissions.

## Project Structure
- **`PARTICLE HEART.html`** — Everything is contained in this one HTML file (Three.js rendering + MediaPipe hand tracking).

## How it Works
- **Three.js** renders ~18,000 colored particles (`THREE.Points`) with additive blending.
- **MediaPipe Hands** detects hand landmarks from your webcam.
- Finger gesture logic drives shape switching and particle interaction.

### Gestures (as implemented)
Based on the number of extended fingers (tips vs. lower joints):
- **1 extended finger** → *push / swirl* particles near the fingertip
- **2 extended fingers** → switch to **3D star**
- **3 extended fingers** → switch to **smooth sphere**
- **0 or 4+ extended fingers** → switch back to **heart**

Rotation and scale are influenced by the fingertip position and thumb–index distance.

## Requirements
- Modern browser supporting:
  - WebRTC camera access (`getUserMedia`)
  - WebGL
  - MediaPipe Hands WASM/JS loading from CDN

## Running
Because the project is a single HTML file with CDN dependencies, you can run it by simply opening:

- `PARTICLE HEART.html`

If your browser blocks camera access for `file://` URLs, serve it via a local web server.

### Quick local server (recommended)
From the project folder, run any simple static server (example using Python):

```bash
python -m http.server 8000
```

Then open:

- http://localhost:8000/PARTICLE%20HEART.html

## Notes / Troubleshooting
- If camera access is denied, click the browser’s permission prompt and reload.
- Performance depends on GPU/CPU; the particle count is high (~18k points).
- If MediaPipe fails to load, check your connection to the CDN URLs used in the HTML.

## Credits
Built using:
- [MediaPipe Hands](https://developers.google.com/mediapipe)
- [Three.js](https://threejs.org/)

