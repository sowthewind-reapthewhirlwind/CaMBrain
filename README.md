# CaMBRAIN — Project Page

Static project page for *CaMBRAIN: Real-time, Continuous EEG Inference with Causal State Space Models*.

Template: based on the **[Nerfies](https://nerfies.github.io/)** academic project page convention (also used by [3D Gaussian Splatting](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/) and most CRCV lab pages, e.g. [GAEA](https://ucf-crcv.github.io/GAEA/)).

## Deploy to GitHub Pages

1. Create a public repo named `cambrain` (or whatever you'd like the URL slug to be).
2. Copy everything in this folder into the repo's root.
3. Settings → Pages → **Source: Deploy from a branch** → Branch: `main` / `(root)` → Save.
4. ~30 seconds later, your site is live at `https://<your-username>.github.io/cambrain/`.

For the CRCV lab convention specifically (matching e.g. `ucf-crcv.github.io/GAEA/`), ask Dr. Shah whether you can push to the `UCF-CRCV` GitHub org instead — same files, but the URL becomes `https://ucf-crcv.github.io/cambrain/`, which looks more official.

## File layout

```
.
├── index.html
├── README.md
└── assets/
    ├── ContinuousEEG.mp4               (the demo video, 2.2 MB)
    ├── ContinuousEEG-poster.jpg        (poster frame shown before play)
    ├── teaser.png                       (Figure 1 from the paper, downsized)
    ├── architecture.png                 (Figure 2, vector-rendered from CONBA.pdf)
    └── logos/
        ├── crcv_ucf.jpg                (combined CRCV + UCF logo, official from UCF-CRCV/GAEA repo)
        ├── ucf.png                     (UCF Pegasus + UCF wordmark, extracted from combined)
        └── llu.png                     (Loma Linda University official emblem, provided by author)
```

## About the logos

**CRCV (affil 1)**: `assets/logos/crcv_ucf.jpg` is the **official combined lab logo**, pulled from the [UCF-CRCV/GAEA](https://github.com/UCF-CRCV/GAEA) repo's `Assets/` folder. It's the exact file the CRCV lab uses on its other paper pages (GAEA, TF-CoVR, etc.).

**UCF (affil 2)**: `assets/logos/ucf.png` is the UCF Pegasus + UCF wordmark, extracted from the left portion of the combined CRCV logo above. If you want a higher-resolution standalone UCF mark, grab one from <https://www.ucf.edu/brand/brand-assets/logo-identity-system/> — use the **Primary Mark** (Pegasus + UCF wordmark), NOT the Knights athletic logo.

**LLU (affil 3)**: `assets/logos/llu.png` is the official Loma Linda University emblem (maroon shield with the "To Make Man Whole" motto). All three logos are now local files with no external dependencies.

## Toggle the "Soon" buttons live

Each of the Paper / arXiv / Code buttons is currently a disabled `<span class="btn disabled">`. To activate one:

1. Find the relevant `<span>` block in `index.html`.
2. Replace `<span class="btn disabled">` with `<a class="btn" href="YOUR_URL" target="_blank" rel="noopener">`.
3. Replace the closing `</span>` with `</a>`.
4. Delete the `<span class="pill">Soon</span>` line.

## Update the BibTeX once arXiv announces

In `index.html`, find `id="bibtex-block"` and update the entry. Replace:
```bibtex
journal = {arXiv preprint},
year    = {2026},
note    = {Preprint forthcoming}
```
with:
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

## Author Google Scholar links

The author names link to Google Scholar profiles via `<a href="...">` tags. Currently only Mubarak Shah's link is filled in (`scholar.google.com/citations?user=p8gsO3gAAAAJ`). The other authors have `href="#"` placeholders — replace each with the author's Scholar / personal URL.

## Tech notes

- Single HTML file, single CSS block, ~15 lines of JS for the BibTeX copy button. No build step, no bundler, no dependencies beyond Google Fonts (loaded at runtime).
- Font: Noto Sans (loaded from Google Fonts). For offline-first audiences, self-host the WOFF2 files from <https://fonts.google.com>.
- Video uses `preload="metadata"`, so the poster JPG loads immediately but the MP4 only downloads on play.
- `<meta property="og:image">` points at the poster JPG, so link previews on Twitter / Slack / Discord show the demo frame.
- Template credit footer links to Nerfies, per the convention.
