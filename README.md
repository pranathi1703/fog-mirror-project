# Fog Mirror

A webcam mirror that fogs up when you breathe on it. Draw on the glass with a pinch, wipe it with your fist, and watch it recognise the shapes you draw.

**[Live demo](https://pranathi1703.github.io/fog-mirror-project/)** · single HTML file · no backend · no build step

![Fog Mirror demo](assets/demo.gif)

## Privacy

Camera and microphone are processed on your device and nothing is uploaded. Saved memories are stored in your browser (IndexedDB) and only when you press save. The only network requests are the two MediaPipe scripts and model files loaded from the jsDelivr CDN.

## How to use

| Do this | To get this |
|---|---|
| Breathe near the mic, or hold **Space** | Fog forms around your mouth |
| Pinch thumb and index finger | Draw on the glass |
| Make a fist | Wipe a wide area |
| Two fists | Wipe a circle between your hands |
| Open palm | Pause fog and drawing |
| Peace sign | Switch to neon mode |
| Thumbs up (hold) | Reset the mirror |

Keys: `C` clear · `S` save · `Ctrl+Z` undo · `Ctrl+Shift+Z` / `Ctrl+Y` redo · `1–4` mirror modes · `Esc` close panel / exit.

Draw a **heart, circle, star, triangle, smile or line** and the mirror reacts.

## Modes

classic · neon · frozen · dream

## Fog physics (v3.1)

Fog is a low-resolution density grid, not a bitmap. Each frame, breath deposits moisture around the mouth, the fog diffuses and sags slightly, and it evaporates at slightly different rates in different regions. Stronger and longer breaths make denser, wider fog. Repeated breaths accumulate up to a ceiling so the mirror stays usable. Wiped glass resists re-fogging for a few seconds. The settings panel exposes intensity, dissipation and restore delay.

## Versions

| Release | Highlights |
|---|---|
| v1.0 | Webcam, fog, breath interaction |
| v2.0 | Gestures and shape recognition |
| v3.0 | Mirror modes, memories, settings, undo |
| v3.1 | Density-grid fog physics, faster rendering, adaptive resolution |

## Run locally

Camera access needs HTTPS or `localhost`, so serve the folder instead of double-clicking the file:

```bash
git clone https://github.com/pranathi1703/fog-mirror-project.git
cd fog-mirror-project
python3 -m http.server 8000
```

Open `http://localhost:8000/fog.html` and allow camera and microphone access. An internet connection is needed for hand and face tracking.

## Browser support

Best in current Chrome and Edge. Firefox and Safari work for fog, mic and Space, but check hand tracking on your device. If rendering is slow, the app lowers its render resolution automatically on high-DPI screens.

## Troubleshooting

- **No camera prompt:** use `localhost` or HTTPS.
- **Hand tracking unavailable:** the MediaPipe CDN scripts were blocked or you are offline.
- **Fog too weak or too strong:** adjust mic sensitivity and fog intensity in settings (gear icon).
- **Microphone detects loudness only:** it cannot prove you are breathing, so loud room noise can trigger fog.

## Tech

HTML, CSS and JavaScript · Canvas 2D · MediaDevices and Web Audio APIs · IndexedDB · [MediaPipe](https://developers.google.com/mediapipe) Hands and Face Detection

## Project structure

```text
fog-mirror-project/
├── fog.html        the whole app
├── index.html      copy of fog.html for GitHub Pages
├── assets/demo.gif
├── LICENSE
└── README.md
```

## License

MIT, see [LICENSE](LICENSE).
