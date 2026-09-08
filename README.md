# Personal website

Static site for GitHub Pages — plain HTML + one CSS file, no build step.

## Structure

```
index.html            about page: profile, bio, news, selected publications
publications.html     full publication list, grouped by year
assets/css/main.css   all styling (light + dark, responsive)
assets/img/           prof_pic.svg and publication/thumbnail/*
assets/pdf/cv.pdf     linked from the "cv" nav item
```

## Local preview

```
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Use a server rather than opening the files
directly — paths are absolute (`/assets/...`) so they match GitHub Pages.

## Deploying

Push to a repo named `<username>.github.io`, then enable Pages on the default
branch. No Jekyll config is needed; add an empty `.nojekyll` file if you ever
add directories starting with an underscore.

## Filling in content

Placeholders are marked with `<!-- TODO -->` comments:

- **Profile** — `assets/img/prof_pic.jpg` (square, 800×800, EXIF stripped).
  Regenerate from a source photo with:
  `magick SRC.jpeg -crop WxH+X+Y +repage -resize 800x800 -strip -quality 88 assets/img/prof_pic.jpg`
- **Social links** — the `.profile-social` block in `index.html`. To add a
  Google Scholar icon, re-add the academicons stylesheet to `<head>` and use
  `<i class="ai ai-google-scholar"></i>`.
- **Bio** — the three paragraphs in `.about-content`.
- **News** — copy a `<li class="news-item">` block; newest first.
- **Publications** — copy a `<li>` from `.bibliography` in either page. Drop
  unneeded `.pub-link` chips (project / pdf / code / bibtex), and put teaser
  images in `assets/img/publication/thumbnail/`.
- **CV** — replace `assets/pdf/cv.pdf`.
