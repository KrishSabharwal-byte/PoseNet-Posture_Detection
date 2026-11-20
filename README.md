# ⚡ Real-Time PoseNet Posture & Skeleton Detection 🧘‍♂️🎥

[![p5.js](https://img.shields.io/badge/p5.js-ED225D?style=for-the-badge&logo=p5.js&logoColor=white)](https://p5js.org/)
[![ml5.js](https://img.shields.io/badge/ml5.js-5B21B6?style=for-the-badge&logo=tensorflow&logoColor=white)](https://ml5js.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> A real-time, browser-based human pose estimation and posture tracking web application built with **p5.js** and **ml5.js (PoseNet)**, featuring an interactive **React Bits Waves** animated monochrome background.

---

## 📸 Demo Preview

```
+-------------------------------------------------------------------+
|                     PoseNet Posture Detection                     |
|                                                                   |
|         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~         |
|         ~        .---. [Interactive Wave Mesh] ~         ~       |
|         ~       ( o o )                                   ~       |
|         ~      .-'---'-.                                  ~       |
|         ~     / |     | \   [17 Skeleton Keypoints]       ~       |
|         ~       |     |                                   ~       |
|         ~      /       \                                  ~       |
|         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~         |
|                                                                   |
+-------------------------------------------------------------------+
```

---

## ✨ Key Features

- 🎯 **Real-Time 17-Keypoint Detection**: Tracks facial landmarks (eyes, nose, ears) and body joints (shoulders, elbows, wrists, hips, knees, ankles) via your webcam at high FPS.
- 🦴 **Dynamic Skeletal Rigging**: Connects detected landmarks with smooth real-time skeleton lines for posture analysis and movement tracking.
- 🌊 **React Bits Interactive Waves Background**: Integrated silk-wave spring-physics animation with live cursor repulsion and organic wave propagation.
- 📱 **Clean Responsive Glassmorphic UI**: Focused 50% viewport presentation with subtle ambient glow and centered modern dark aesthetic.
- 🕶️ **AR Filter Ready**: Includes modular support for image and accessory overlays (glasses, masks, hats) synced directly to nose and eye positions.
- 🚀 **Zero Backend Required**: Runs 100% client-side in the browser using WebGL and TensorFlow.js under the hood — completely private with no video data leaving your device.

---

## 🛠️ Built With

| Technology | Purpose |
| :--- | :--- |
| **[ml5.js](https://ml5js.org/)** | High-level machine learning library providing pre-trained PoseNet models |
| **[p5.js](https://p5js.org/)** | Creative coding library for HTML5 canvas rendering and video capture |
| **[HTML5 Canvas & Vanilla JS](https://developer.mozilla.org/)** | Spring-physics wave simulation and real-time mouse repulsion |
| **[CSS3](https://developer.mozilla.org/)** | Glassmorphism, responsive viewport layout, and typography |

---

## 📂 Project Structure

```bash
PoseNet/
│
├── index.html        # Main HTML shell, responsive styling & React Bits Waves engine
├── sketch.js         # p5.js & ml5.js PoseNet model initialization, keypoints & skeleton draw loop
├── images/           # Assets for AR overlays (filters, accessories)
│   ├── shahrukh.png
│   ├── spects.png
│   └── cigar.png
└── README.md         # Project documentation
```

---

## 🚀 Quick Start & Installation

Because the application accesses your webcam via `navigator.mediaDevices.getUserMedia`, modern browsers require the page to be served over `http://localhost` (a local server) rather than double-clicking the file (`file:///`).

### Option 1: VS Code Live Server (Easiest) 💻
1. Open this project directory in **Visual Studio Code**.
2. Install the **[Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)** extension if you haven't already.
3. Right-click `index.html` and click **"Open with Live Server"**.
4. Allow browser camera permissions when prompted.

---

### Option 2: Python HTTP Server 🐍
If you have Python installed:

```bash
# Clone the repository
git clone https://github.com/your-username/posenet-posture-detection.git

# Navigate to the project directory
cd posenet-posture-detection

# Start a local server (Python 3)
python -m http.server 5500
```
Open your browser and navigate to `http://localhost:5500`.

---

### Option 3: Node.js / npx serve 🟢
```bash
npx serve .
```

---

## 🧠 How It Works

1. **Camera Feed Capture**: p5.js initiates a webcam stream using `createCapture(VIDEO)` and hides the raw HTML video element.
2. **PoseNet Inference**: ml5.js binds PoseNet to the webcam stream, feeding each frame to a convolutional neural network (MobileNet architecture).
3. **Keypoint Mapping**: The model returns estimated keypoint positions with confidence scores.
4. **Canvas Rendering**:
   - `image(capture, 0, 0, width, height)` renders the video feed on the canvas.
   - Loops through `singlePose.keypoints` to draw red joint markers.
   - Loops through `skeleton` pairs to draw skeletal tracking lines.
5. **Background Physics**: An independent, lightweight HTML5 Canvas loop calculates spring physics and cursor repulsion for the flowing wave grid.

---

## 🎮 AR Filter Customization

To activate fun AR accessories on the detected face, uncomment lines in `sketch.js`:

```javascript
// Inside draw() in sketch.js:
image(specs, singlePose.nose.x - 35, singlePose.nose.y - 50, 80, 80);
```

Place your own PNG graphics into the `images/` directory to create custom interactive face and body filters!

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the project (`git checkout -b feature/AmazingFeature`)
2. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
3. Push to the branch (`git push origin feature/AmazingFeature`)
4. Open a Pull Request

---

## 📜 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

## ⭐️ Acknowledgements

- [ml5.js Community](https://ml5js.org/) for making machine learning accessible for creative coders.
- [Processing Foundation](https://processingfoundation.org/) for p5.js.
- [React Bits](https://reactbits.dev/) for the wave mesh animation inspiration.
