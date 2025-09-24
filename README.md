# AR Photo Cards (MindAR + A‑Frame)

Free, browser‑based AR that plays a video when you point your phone at a printed photo.

## What you need
- Modern phone (Chrome/Edge/Firefox/ Safari)
- Good, contrasty photos (avoid glossy glare if possible)
- Videos: `video1.mp4`, `video2.mp4`, ...

## 1) Create image targets (.mind)
You can use either the online Target Compiler or the local CLI.

### Option A: Online Target Compiler (easiest)
1. Open `https://hiukim.github.io/mind-ar-js-doc/tools/compile/`
2. Upload 1–4 images (JPG/PNG). Prefer sharp, textured photos.
3. Download the resulting `targets.mind`
4. Put `targets.mind` next to `index.html`

### Option B: Local CLI (if available)
The old `mind-ar-cli` may not be published in npm for some regions. If it’s available for you:

```bash
npm install -g mind-ar-cli
mindar build photo1.jpg photo2.jpg photo3.jpg photo4.jpg
# Produces targets.mind with 4 targets (indexes 0..3)
```

If that fails, use the Online Target Compiler (Option A).

## 2) Place files
Keep all files together:
```
index.html
targets.mind
video1.mp4
video2.mp4
music.mp3   # optional background music
```

Edit `index.html` if you need more targets/videos.

## 3) Test locally
Double‑click `index.html` on desktop for a quick check, but camera permissions may be blocked by file:// on some browsers. Prefer a local server:

```bash
# Python 3
python -m http.server 8080
# or Node
npx http-server -p 8080
```
Visit `http://localhost:8080` on your phone (same Wi‑Fi), or scan the LAN IP.

## 4) Deploy for free
### GitHub Pages
1. Create a repo and add these files
2. Commit/push
3. In GitHub → Settings → Pages → Deploy from branch → select `main` and `/ (root)`
4. Open the Pages URL (e.g., `https://yourname.github.io/ar-cards/`)

### Netlify/Vercel
Drag‑and‑drop the folder or connect your repo. No build step required.

## 5) Print and use
- Print your photo cards with good size (A6–A5 works well)
- In bright, non‑reflective light, open your hosted link on mobile
- Point the camera at a photo; the mapped video should appear in place

## Tips for reliability
- Use images with rich features (edges, corners, textures). Avoid plain backgrounds.
- Keep videos around 720p for smooth playback.
- The first tap enables camera/audio due to mobile autoplay policies.
- If videos don’t play sound on iOS, ensure you tapped the Start button and the device isn’t in Silent mode.

## Map of targets to videos
- `targetIndex: 0` → `video1.mp4`
- `targetIndex: 1` → `video2.mp4`
(Extend in `index.html` as needed.)

## Customization
- Change video size by editing `<a-video width="..." height="...">`
- Add more targets: duplicate the `<a-entity mindar-image-target ...>` block and add more `<video>` assets with unique IDs.

---
Credits: MindAR by Hiukim. This project uses `mindar-image-aframe` via CDN.
