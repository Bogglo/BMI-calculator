# Responsive BMI Calculator — README

A single-page, responsive BMI (Body Mass Index) calculator built with plain HTML, CSS and JavaScript.  
Designed to default to dark mode, work well on both mobile and desktop, and include an inline SVG chart + radial gauge. Uses a PNG favicon placed at the project root.

Live preview / demo
- View the live site here: https://checkbmi.pages.dev

---

## Features
- Calculate BMI from weight and height (supports cm, m, ft/in).
- Category classification: Underweight, Normal, Overweight, Obese.
- Responsive layout — compact mobile view and expanded desktop view.
- Animated, accessible SVG chart (desktop) and radial gauge (mobile).
- Default dark theme (persisted in localStorage, users can toggle).
- Small client-side state: stores last inputs in localStorage.
- Fully client-side — no build step or server required.

---

## Project layout (recommended)
Place these files as shown:

```
project-root/
├─ index.html              # Main app (HTML + inline CSS/JS)
├─ README.md               # This file
├─ favicon.png             # Recommended favicon (place at project root)
├─ favicon-32x32.png       # optional (better browser coverage)
├─ favicon-16x16.png       # optional
├─ apple-touch-icon.png    # optional (180×180)
├─ images/                 # optional: other images if needed
│  └─ (e.g. bmi-chart.png) # optional graphic, not required for current UI
└─ assets/                 # optional: if you want to split CSS/JS
   ├─ css/
   └─ js/
```

Notes:
- The app expects `favicon.png` at project root and the HTML uses:
  ```html
  <link rel="icon" type="image/png" href="favicon.png">
  ```
- `images/` is optional — the inline SVG chart is used by default. Add static chart PNGs only if you want.

---

## Quick start
1. Copy `index.html` into your project root.
2. Place `favicon.png` into the project root (see the "Favicon" section for guidance).
3. Open `index.html` in your browser (double-click or serve via a static server).

No build step is required.

---

## Favicon — create and add a PNG
We recommend using a PNG favicon (project root `favicon.png`). Suggested workflow:

1. Create a clean icon (SVG preferred) or generate a high-res PNG (1024×1024) with a transparent background. Keep design simple and bold (no text).
2. Produce resized PNGs (ImageMagick examples):
   - If you have a 1024×1024 source:
     ```bash
     magick convert favicon-1024.png -resize 512 favicon-512.png
     magick convert favicon-1024.png -resize 256 favicon-256.png
     magick convert favicon-1024.png -resize 128 favicon-128.png
     magick convert favicon-1024.png -resize 64  favicon-64.png
     magick convert favicon-1024.png -resize 32  favicon-32x32.png
     magick convert favicon-1024.png -resize 16  favicon-16x16.png
     # choose one as the "favicon.png" (e.g. 32x32)
     cp favicon-32x32.png favicon.png
     ```
   - If you have an SVG:
     ```bash
     magick convert favicon.svg -resize 1024 favicon-1024.png
     ```
3. Place `favicon.png` at the project root. Optionally include `favicon-32x32.png` and `favicon-16x16.png` for better compatibility.

Optional head markup to include multiple sizes:
```html
<link rel="icon" type="image/png" sizes="32x32" href="favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="apple-touch-icon.png">
```

If you prefer an automated tool, use:
- https://realfavicongenerator.net
- https://favicon.io

---

## Accessibility & UX notes
- Inputs use semantic elements and support Enter key submission.
- Chart/gauge elements include ARIA attributes and meaningful alt/labels.
- Dark mode is default — user preference is persisted in localStorage; toggling is available.
- BMI is a screening tool only. The app shows advice text but is not medical advice.

---

## Customization
- To change the default theme (light/dark), edit the script that reads/writes `localStorage.theme`.
- To replace the desktop SVG with a static image (PNG), place it in `images/` and update the `.chartWrap` block to use:
  ```html
  <img src="images/bmi-chart.png" alt="BMI range chart" class="chartImg" loading="lazy">
  ```
- To split inline CSS/JS into files, move them into `assets/css/` and `assets/js/` and include links in `index.html`. See `assets/README-ASSETS.txt` if present.

---

## Development tips
- Serve with a static server to avoid file:// quirks:
  - Python 3:
    ```bash
    python -m http.server 8000
    ```
  - Node (serve):
    ```bash
    npx serve .
    ```
- Clear browser cache when testing `favicon.png` changes (browsers aggressively cache favicons).

---

## License
Use as you wish. If you publish or share, a short attribution is appreciated.

---

If you want, I can:
- add the live preview link into the page footer,
- generate a sample SVG favicon for conversion to PNG,
- or create a small zip containing index.html + README + placeholder favicon.
