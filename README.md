# Job Market Site

Plain HTML/CSS/JS — no build step, no Jekyll, no dependencies. Easiest thing to
deploy and easiest to keep editing over the next few months.

## File structure
```
index.html        ← the whole site (Masthead / Research / Teaching)
css/style.css     ← all styling
js/main.js        ← tiny bit of JS (footer year, if used)
papers/           ← put your JMP + working paper PDFs here
assets/photo.jpg  ← put your photo here (used top-left in the masthead)
cv.pdf            ← put your CV here (linked from the masthead)
```

## Page structure
1. **Masthead** — photo (top-left) beside your name, affiliation, short bio,
   and contact line (email, CV, Google Scholar, GitHub, LinkedIn)
2. **Research** — three groups: Publications, Working Papers (JMP is visually
   flagged and its abstract is open by default), Work in Progress. Each entry
   can have a link to the PDF and a collapsible "+ Abstract" dropdown.
3. **Teaching** — simple list of courses/roles

Add your photo as `assets/photo.jpg` (roughly square, e.g. 400×400px works
well) — until you do, that spot shows a placeholder graphic automatically.

Currently all the text (name, bio, paper titles, abstracts) is placeholder
content to be replaced with the real thing — nothing is in `[brackets]`
anymore, so just find-and-replace the fake text directly in `index.html`.

## Get it on GitHub Pages (10 minutes)

1. Create a new **public** repo on GitHub, e.g. `yourusername.github.io`
   (using exactly this name gives you the site at `https://yourusername.github.io`
   with no extra path — nicest for a job market URL).
   If you'd rather use a normal repo name like `job-market-site`, that's fine
   too, your site just lives at `https://yourusername.github.io/job-market-site/`.

2. From inside this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial job market site"
   git branch -M main
   git remote add origin https://github.com/yourusername/yourusername.github.io.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Source → Deploy from a branch → main / (root)**.
   Wait ~1 minute, then visit the URL GitHub gives you.

4. (Optional) Custom domain: add a `CNAME` file in the repo root containing just
   your domain (e.g. `giovannilastname.com`), then point your domain's DNS
   `A`/`ALIAS` records at GitHub Pages per
   [GitHub's docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Updating the site later
Once it's live, any future change is just:
```bash
git add .
git commit -m "Describe what changed"
git push
```
GitHub Pages redeploys automatically within a minute or two of the push.

## Design notes
- Palette/type live as CSS variables at the top of `style.css` (`--bg`,
  `--ink`, `--link`, etc.) — change once, updates everywhere. Background is
  currently warm ivory (`#F7F5F0`).
- Abstracts use the native HTML `<details>`/`<summary>` element — no
  JavaScript needed for the dropdown behavior.
- Everything is a single page, single column, no nav bar — matching the
  classic minimal academic-site look.
