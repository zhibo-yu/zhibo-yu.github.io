# Zhibo Yu academic website patch

This package is designed for your existing al-folio repository:
https://github.com/zhibo-yu/zhibo-yu.github.io

## 1. Copy these files into the repository

Copy/replace:

- `_pages/about.md`
- `_pages/research.md`
- `_pages/publications.md`
- `_pages/cv.md`
- `_data/socials.yml`
- `_data/cv.yml`
- `_bibliography/papers.bib`

Then manually apply the small settings shown in `CONFIG_CHANGES.yml` to `_config.yml`.

## 2. Add your own assets

Put a professional photo here:

`assets/img/prof_pic.jpg`

Put your current CV PDF here:

`assets/pdf/Zhibo_Yu_CV.pdf`

The theme's `cv_pdf` setting will then provide the PDF button.

## 3. Important personal fields

In `_data/socials.yml`, replace/add:
- Google Scholar ID
- ORCID
- LinkedIn, if desired

Your Penn State email and GitHub username are already filled in.

## 4. Optional cleanup

For a focused academic site, consider hiding template pages you do not use by setting `nav: false`
in their YAML headers, especially Blog, Books, Repositories, and any demo pages.

## 5. Test locally

If Ruby/Bundler are already installed:

```bash
bundle install
bundle exec jekyll serve
```

Then visit:

http://localhost:4000

## 6. Commit and deploy

From the repository directory:

```bash
git status
git add _config.yml _pages _data _bibliography assets/img/prof_pic.jpg assets/pdf/Zhibo_Yu_CV.pdf
git commit -m "Update academic website"
git push origin main
```

Your repository's GitHub Actions deployment workflow runs on pushes to `main` or `master`,
so a successful push should trigger a new GitHub Pages deployment.

To inspect it on GitHub:
Repository -> Actions -> "Deploy site"

## 7. Normal editing workflow later

```bash
cd /path/to/zhibo-yu.github.io
git pull
# edit files
git status
git add .
git commit -m "Update research and publications"
git push
```
