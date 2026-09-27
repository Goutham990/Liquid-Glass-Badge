# 🪟 Liquid Glass Badge

<div align="center">

**Turn your GitHub profile into an interactive liquid-glass card you can sign and download.**

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-Visit_Site-4f9cf9?style=for-the-badge)](https://goutham990.github.io/Liquid-Glass-Badge/)
[![GitHub Stars](https://img.shields.io/github/stars/Goutham990/Liquid-Glass-Badge?style=for-the-badge&color=ffca28)](https://github.com/Goutham990/Liquid-Glass-Badge/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen?style=for-the-badge)](LICENSE)
[![Made with WebGL](https://img.shields.io/badge/Made_with-WebGL-e34f26?style=for-the-badge&logo=webgl)](https://www.khronos.org/webgl/)

</div>

---

## ✨ Preview

> A stunning liquid-glass card powered by a custom WebGL GLSL fragment shader — hover, drag, sign, and download.

---

## 🎯 Features

| Feature | Description |
|---|---|
| 🔮 **Liquid Glass Shader** | Custom WebGL GLSL fragment shader with realistic optical refraction, frosted blur, specular bevel highlights, and superellipse rounded-box math |
| 👤 **GitHub Profile Loader** | Fetches any public GitHub profile via the GitHub REST API — avatar, name, bio, repos, followers, location, and join year |
| 📊 **Contribution Heatmap** | Renders a 7-row contribution graph using real yearly data from the GitHub Contributions API |
| ✍️ **Signature Pad** | Draw your own signature directly on the glass card with smooth pointer/touch support |
| 🖼️ **4 Background Presets** | Built-in procedural backgrounds — Meadow, Cosmic Nebula, Sunset Glow, and Aurora Emerald |
| 📁 **Custom Background Upload** | Upload any local image file as the background without CORS restrictions |
| 💧 **Liquidness Slider** | Fine-tune the frosted-glass whiteness and refraction intensity from 0% to 100% |
| 🖱️ **Draggable Card** | Freely drag the glass card anywhere on the desktop viewport |
| 💾 **High-Res PNG Export** | Download a crisp 2x resolution PNG with the liquid glass background, profile data, and signature baked in |
| 📱 **Responsive Layout** | Full mobile support — card and panel stack vertically on small screens |

---

## 🚀 Getting Started

### Option 1 — Open Directly
Just open `index.html` in any modern browser. No build step or server required.

### Option 2 — Local Dev Server
`ash
# Using Python (built-in)
python -m http.server 3000

# Then visit:
# http://localhost:3000/index.html
`

### Option 3 — Live Demo
Visit the deployed GitHub Pages site:
👉 **[https://goutham990.github.io/Liquid-Glass-Badge/](https://goutham990.github.io/Liquid-Glass-Badge/)**

---

## 🛠️ Tech Stack

`
├── HTML5 / Vanilla CSS / Vanilla JavaScript
├── WebGL 1.0 (GLSL Fragment Shader)
│   ├── Superellipse rounded-box SDF (pow-6 metric)
│   ├── 9×9 multi-tap lens blur (81 samples)
│   ├── Background image cover-UV remapping
│   └── Specular bevel gradient lighting
├── GitHub REST API v3 (public, no auth needed)
├── GitHub Contributions API (jogruber.de)
└── Google Fonts — Plus Jakarta Sans
`

---

## ⚙️ How It Works

### WebGL Liquid Glass Shader
The entire background is rendered on a full-screen canvas via a custom GLSL fragment shader. For each pixel:

1. **SDF distance** from the card boundary is computed using pow(|d.x|, 6) + pow(|d.y|, 6) — this gives natural rounded-corner glass shapes.
2. A **frosted blur** samples the background texture across a 9x9 tap grid, weighted by the SDF.
3. **Specular rim highlights** (the chamfered glass edges) are computed from a secondary SDF band.
4. A **vertical gradient** simulates ambient light hitting the top/bottom of the glass pane.
5. All effects are blended with the raw background using smoothstep for a natural transition.

### Profile Card
- Fetches `https://api.github.com/users/{username}` — no API key needed for public profiles.
- Contribution data from `https://github-contributions-api.jogruber.de/v4/{login}?y={year}`.
- The card is rendered as a plain HTML div — the glass effect underneath it is computed by the WebGL shader reading the card's getBoundingClientRect() position each frame.

### Download Engine
- Reads pixels directly from the WebGL canvas using ctx.drawImage(glCanvas, ...).
- Re-renders all card text, panels, avatar, contribution canvas, and signature canvas onto a 2x off-screen canvas.
- Exports as a lossless PNG.

---

## 🗂️ Project Structure

`
Liquid-Glass-Badge/
├── index.html       # Entire app — HTML + CSS + WebGL shader + JS
└── README.md        # This file
`

All code lives in a single self-contained `index.html` for maximum portability.

---

## 📸 Background Presets

| Preset | Description |
|---|---|
| 🌸 **Meadow** | Sky-blue gradient with procedural flowers and grass stems |
| 🌌 **Cosmic** | Dark space with glowing nebula orbs and star dust |
| 🌅 **Sunset** | Deep twilight-to-orange gradient with a warm sun glow and horizon silhouette |
| 🟢 **Aurora** | Night mountains under rippling aurora borealis bands |

You can also upload any image from your device using **Upload Custom Background**.

---

## 🙏 Inspiration & Credits

- Inspired by [Bubbbly.com](https://bubbbly.com/app/github-glass-badge.html)
- GitHub Contributions data via [jogruber/github-contributions-api](https://github.com/jogruber/github-contributions-api)
- Font: [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans) by Tokotype

---

## 📄 License

MIT © [Goutham990](https://github.com/Goutham990)

---

<div align="center">
  <sub>Built with ❤️ using raw WebGL — no frameworks, no libraries, just glass.</sub>
</div>
