# Andrzejki — Digital Wax Pouring Game

A lightweight, browser-based Andrzejki fortune-telling game for an internal Secret Escapes / Travelist activity. It uses static HTML, CSS, JavaScript, and illustrated assets; **no AI model, database, login, build tooling, or backend is required**.

## How the game works

1. **Welcome:** Read the introduction and start the game.
2. **Choose your candle:** Select one of six colours, each linked to a company value.
3. **Pour the wax:** Watch the illustrated GIF for **3 seconds** (approximately two plays of the original 1.5-second GIF).
4. **See the wax:** A colour-specific wax shape appears in the water. Select **Hold Up to the Light**.
5. **Reveal your fortune:** A randomly chosen shadow illustration appears **next to** its text on desktop, or above its text on mobile. Select **Pour Again** to restart.

Each candle has **three possible outcomes**, making **18 fortunes** in total. The selected colour controls which group of three fortunes can be drawn. The draw is random and runs entirely in the browser.

| Candle | Value |
| --- | --- |
| Red | Be Brave |
| Blue | Keep It Simple |
| Yellow | Be Good People |
| Green | Make It Matter |
| Purple | Win & Lose Together |
| Orange | Take Care of Every Trip |

## File layout and correct extensions

Keep the following folder names and filename extensions **exactly as shown**. Names are case-sensitive on services such as GitHub Pages.

```text
index.html
README.md
assets/
  background.jpeg
  bowl_background.jpeg
  up_bowl_background.jpeg
  wax_pour.gif
  Candles/
    candle_red.png
    candle_blue.png
    candle_yellow.png
    candle_green.png
    candle_purple.png
    candle_orange.png
  Wax pours/
    waxpour_red.png
    waxpour_blue.png
    waxpour_yellow.png
    waxpour_green.png
    waxpour_purple.png
    waxpour_plane.png      # Orange wax illustration's existing filename
  Shadows/
    shadow_red_lion.jpeg
    shadow_red_star.jpeg
    shadow_red_door.jpeg
    shadow_blue_arrow.jpeg
    shadow_blue_paperplane.jpeg
    shadow_blue_bridge.jpeg
    shadow_yellow_handshake.jpeg
    shadow_yellow_shield.jpeg
    shadow_yellow_heart.jpeg
    shadow_green_mountain.jpeg
    shadow_green_compass.jpeg
    shadow_green_hourglass.jpeg
    shadow_purple_champagne.jpeg
    shadow_purple_web.jpeg
    shadow_purple_puzzle.jpeg
    shadow_orange_plane.jpeg
    shadow_orange_suitcase.jpeg
    shadow_orange_globe.jpeg
```

**Important filename fix:** The original ZIP supplied for review contained filenames such as `background.png.jpeg`, `shadow_red_lion.png.jpeg`, `candle_red.png.png`, and `wax_pour.gif.gif`. This updated HTML expects the corrected names above:

- Rename `*.png.jpeg` to `*.jpeg` (**JPEGs stay JPEGs**).
- Rename `*.png.png` to `*.png` (**PNGs stay PNGs**).
- Rename `wax_pour.gif.gif` to `wax_pour.gif`.
- Rename the original `Index.html` to **`index.html`** (lowercase).

If you instead choose the extension `.jpg`, change all corresponding `.jpeg` references in `index.html` to `.jpg`. **Renaming a JPEG file to `.png` does not convert its image format.**

The assets themselves are not included in these two replacement files; keep your existing, resized assets in their folders.

## Run locally

Because the game uses only relative asset paths, it can be served as a simple static site. For reliable testing, run a local web server from the directory containing `index.html`:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`. Check the browser's developer console / Network tab for missing image errors (404s).

## Publish

For **GitHub Pages**, commit `index.html`, `README.md` and the `assets/` directory in the publishing branch/folder. In **Settings → Pages**, select the appropriate branch and root folder. Once published, open the generated HTTPS URL and test it on desktop and mobile.

For **Happeo**, link to the hosted HTTPS game from your post, or test a page's iframe embed if your Happeo configuration permits it. A normal Happeo post should not be assumed to execute arbitrary HTML/JavaScript.

## Edit the game

All game logic is at the bottom of `index.html`:

- `valueNames`: Display names for the six values.
- `waterWaxImages`: Colour → water-wax PNG asset.
- `fortunesData`: Colour → list of three shadow JPEGs and their associated fortune texts.
- `startPour()`: The transition delay is currently `3000` milliseconds.
- `.result-layout`: Desktop side-by-side shadow/text layout; mobile stacked layout in the media query.

To change a fortune, edit the relevant `text` string in `fortunesData`. To change a shadow, update its `img` path. Do not change the mapping unless you also update the relevant assets.

## Pre-publication checks

- [ ] All `.jpeg`, `.png`, and `.gif` file paths match files in the repository exactly.
- [ ] All six candle images appear and are selectable.
- [ ] The wax-pouring GIF plays for 3 seconds and transitions to the water screen.
- [ ] All six water-wax assets display correctly.
- [ ] All 18 shadow images load and their fortune text appears next to/below the image.
- [ ] Test keyboard navigation (Tab, Enter / Space) and narrow mobile screens.
- [ ] Test the deployed HTTPS game and any Happeo link/embed.
- [ ] Confirm that company references and artwork may be distributed publicly if the repository is public.


## Fixed asset package (November 2026)

This package contains corrected original artwork rebuilt from the transparent source assets. It repairs the missing background and shadow images in the deployed version, and restores actual transparency for candles and wax shapes. Files must be **extracted** from the ZIP before upload. Do not upload the ZIP itself to GitHub Pages.

- `index.html` lives at the repository root.
- Keep `assets/background.jpeg`, `assets/bowl_background.jpeg`, and `assets/up_bowl_background.jpeg` directly in `assets/`.
- Keep `assets/wax_pour.gif` directly in `assets/`.
- `assets/Candles/`, `assets/Shadows/`, and `assets/Wax pours/` must be spelled precisely with the same capitalisation and spaces.
- The corrected transparent PNGs **must not** be flattened onto a white background when resized later.
- The game is wider on desktop (max-width 1120px), while its mobile layouts remain responsive.
