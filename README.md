# CaMBRAIN — Project Page

Static project page for *CaMBRAIN: Real-time, Continuous EEG Inference with Causal State Space Models*.

## Quick deploy to GitHub Pages

1. Create a new public repo, e.g. `cambrain` or `cambrain.github.io`.
2. Copy everything in this folder into the repo root (or into a `/docs` folder).
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main`, folder `/ (root)`** (or `/docs` if you used that).
4. Wait ~30 seconds. Your site is at `https://<user>.github.io/<repo>/`.

No build step — it's plain HTML/CSS/JS. The Google Fonts CSS is loaded from `fonts.googleapis.com` at runtime.

## File layout

```
.
├── index.html
├── README.md
└── assets/
    ├── ContinuousEEG.mp4               (2.2 MB, the demo video)
    ├── ContinuousEEG-poster.jpg        (poster frame the video shows before play)
    └── logos/
        ├── crcv.svg                    (placeholder — swap for official)
        ├── ucf.svg                     (placeholder — swap for official)
        └── llu.svg                     (placeholder — swap for official)
```

## Logos: replace the placeholders

The three SVGs in `assets/logos/` are clean text placeholders in each institution's brand colors. They look intentional, not "broken-image." Swap them with the official files when you have a minute:

| Slot                          | Where to grab the official file                                                |
|-------------------------------|--------------------------------------------------------------------------------|
| `assets/logos/crcv.svg`       | Right-click the logo in the header of <https://www.crcv.ucf.edu/> → Save Image |
| `assets/logos/ucf.svg`        | UCF Brand portal: <https://www.ucf.edu/brand/brand-assets/logo-identity-system/> — use the **Primary Mark** (Pegasus + UCF wordmark) for academic context, NOT the athletic Knights logo |
| `assets/logos/llu.svg`        | LLU Brand portal: <https://home.llu.edu/about-llu/visual-identity> — the **LLU School of Medicine** mark is the right one for Dr. Gireesh's Neurology affiliation |

You can drop in `.svg` (vector — best), `.png` (use 2× resolution, ≥120px tall, transparent background ideal), or `.webp`. The HTML uses the filename `crcv.svg` / `ucf.svg` / `llu.svg`; if you save a different extension, also update the `src=` paths in `index.html` (search for `assets/logos/`).

If you want to keep the placeholders for now, the site will display them as-is — they're sized and colored to match the layout.

## Mark items as "Coming Soon" / live

The Paper / arXiv / Code buttons currently render as disabled "Coming Soon" pills. To switch any of them live:

1. Open `index.html` and find the relevant `<span class="btn soon">` block.
2. Replace `<span class="btn soon" aria-disabled="true">` with `<a class="btn" href="YOUR_URL" target="_blank" rel="noopener">`.
3. Replace the closing `</span>` with `</a>`.
4. Delete the `<span class="pill">Coming Soon</span>` line.

Each block is already commented in the markup so they're easy to spot.

## Update the BibTeX once arXiv is live

In `index.html`, find `id="bibtex"` and update the entry. Replace `journal = {arXiv preprint}` and the `note` line with something like:

```bibtex
journal = {arXiv preprint arXiv:2606.XXXXX},
year    = {2026}
```

## Local preview

```bash
cd path/to/this/folder
python3 -m http.server 8080
# open http://localhost:8080
```

## Tech notes

- Fonts: Fraunces (variable serif) + IBM Plex Sans + IBM Plex Mono, loaded from Google Fonts. If your audience may be offline-first, self-host them by downloading from <https://fonts.google.com> and updating the `<link>` in `index.html`.
- The EEG-trace animation at the top of the hero is a pure CSS `@keyframes` translate on an inline SVG path — no JS, no canvas.
- Video tag uses `preload="metadata"` so the poster JPG loads immediately but the 2.2 MB MP4 only downloads on play.
- `<meta property="og:image">` points at the poster JPG so link previews on Twitter/Slack/Discord show the demo frame.
- Single HTML file, single CSS block, ~15 lines of JS for clipboard copy. No build tools, no bundler, nothing to install.
