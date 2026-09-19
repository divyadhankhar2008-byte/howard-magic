# Howard Magic

A Hogwarts-inspired hand-magic web experience. The site can request camera access after the visitor presses **Start camera**, or it can be played with mouse/touch as a fallback.

## Run locally

Camera APIs require a secure context. `localhost` is treated as secure by browsers.

```bash
python3 -m http.server 8000
```

Open <http://localhost:8000> in a browser and press **Start camera**.

## Deploy

This is a static site: deploy `index.html` to GitHub Pages, Netlify, Vercel, Cloudflare Pages, or any HTTPS web host. The deployed URL must use `https://`; camera permission will not work on a normal insecure HTTP URL.

For GitHub Pages:

1. Open repository **Settings → Pages**.
2. Choose **Deploy from a branch**.
3. Select `main` and the `/ (root)` folder.
4. Save and open the generated HTTPS URL.
5. Press **Start camera** and approve the browser permission prompt.

## Camera behavior and browser security

A web page cannot silently open a camera merely because somebody clicked a link. Browsers require a secure origin and an explicit user gesture before `getUserMedia()` can be used. This project requests permission immediately when the visitor clicks **Start camera**, displays useful errors, stops the stream when the experience is exited, and never uploads or records camera data.

If permission was previously denied, use the browser's site settings to reset camera permission and reload the page. Camera access can also be unavailable inside some embedded previews; open the deployed HTTPS URL directly in the browser.

## Files

- `index.html` — self-contained application, styling, camera permission flow, demo fallback, and interaction.
