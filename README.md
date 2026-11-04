# Our Home in 3D

An interactive, dollhouse-style 3D model of our apartment, built with [Three.js](https://threejs.org/). It runs entirely in the browser, with no build step, no backend and no dependencies to install. Open it on a phone or a computer, switch cameras like a video, and watch two animated people walk around the home.

## Features

- **Rooms:** living room, balcony, corridor, bathroom, kitchen and bedroom, laid out from real photos.
- **Camera presets:** aerial, top-down, one per room, a 360° spin, and *follow him / follow her*.
- **Animated people:** two characters walk between rooms using a simple waypoint path. Leave **Auto** on, or send either of them to a room with the **Mover a** buttons.
- **Interactive objects:** tap doors to open or close them, tap the glowing bulbs to switch lights, tap the TV to turn it on or off, tap a person to follow them.
- **Day / night** toggle, plus automatic light and dark UI.

## Controls

| Action | Mouse | Touch |
| --- | --- | --- |
| Orbit | Drag | One finger drag |
| Zoom | Scroll wheel | Pinch |
| Interact | Click | Tap |

## Project structure

```
casa-3d/
├── index.html   # the whole app (HTML + CSS + JS)
└── README.md
```

## Run locally

Just open `index.html` in a browser. An internet connection is needed once to load Three.js from a CDN.

Or serve it locally:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Publish for free on GitHub Pages

1. Create a new repository on GitHub (for example `casa-3d`).
2. Upload the files from this folder:

   ```bash
   git init
   git add .
   git commit -m "Initial commit: 3D home"
   git branch -M main
   git remote add origin https://github.com/<your-username>/casa-3d.git
   git push -u origin main
   ```

3. In the repository go to **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then **Save**.
5. After a minute your site is live at `https://<your-username>.github.io/casa-3d/`.

### Other free hosts

- **Netlify Drop:** drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop).
- **Cloudflare Pages / Vercel:** connect the GitHub repository; no build command is needed and the output directory is `/`.

## Customize

Everything lives in `index.html`.

| What | Where |
| --- | --- |
| Page title | `const TITLE` at the top of the script |
| Walls, floors, doors | `floor(...)`, `wall(...)` and `door(...)` calls (units are meters, `x` goes right, `z` goes toward the viewer) |
| Furniture | the `// sala`, `// cocina`, `// baño`... blocks, built from `box(width, height, depth, x, y, z, material)` |
| People | `person('Name', { skin, top, bot, shoe, cap })` |
| Walking routes | `N` (waypoints) and `E` (connections) |
| Camera presets | the `CAMS` object |

### Color palette

| Use | Color |
| --- | --- |
| Walls | `#F6F3EE` |
| Floor tiles | `#F3F3F1` |
| Black furniture | `#1B1B1F` |
| Sofa | `#8FA6A5` |
| Blanket | `#4F86C6` |
| Balcony floor | `#B5654A` |
| UI accent | `#2F6FED` (light) / `#6C9BFF` (dark) |

## Privacy tip

If the repository or site is public, avoid putting your exact address in the title or README. Use a generic name instead.

## License

MIT. Use it, change it and share it.
