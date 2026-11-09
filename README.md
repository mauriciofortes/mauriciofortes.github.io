# Gayeon Kim — personal website

Single-page academic CV site. No build step: `index.html` is the whole site.

```
100_gy_website/
├── index.html        # the site (copy of CV_final.html + photo fallback)
├── CV_final.html     # original source, kept untouched
└── images/
    ├── profile.jpg   # ← add your profile photo here (square works best)
    └── ...           # gallery images (see below)
```

## Local preview

```bash
cd /nas/07_Team_Brain/gy/100_gy_website
python3 -m http.server 8000
# open http://localhost:8000
```

## Adding photos / certificates to the Gallery

1. Put the image in `images/` (e.g. `images/ksnm-best-poster.jpg`).
2. In `index.html`, find `const GALLERY = [` and set `src` for that item,
   e.g. `src: "images/ksnm-best-poster.jpg"`.
3. Items with an empty `src` show an "Image to be added" placeholder card.
   `cat` is one of `award`, `conference`, `project`.

If `images/profile.jpg` is missing, the photo circle is hidden automatically.

## Deploy with GitHub Pages (free, https://trlily.github.io)

```bash
cd /nas/07_Team_Brain/gy/100_gy_website
git init -b main
git add index.html images README.md
git commit -m "Personal website"
gh repo create trlily.github.io --public --source=. --push
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / root**.
The site appears at `https://trlily.github.io` within a minute or two.

To update later: edit `index.html`, then `git commit -am "update" && git push`.

Custom domain (optional): add a `CNAME` file containing the domain
(e.g. `gayeonkim.com`) and point the domain's DNS to GitHub Pages.
