# Michael MacRaild academic profile

This is a GitHub Pages-ready Jekyll site inspired by [bogoli/-folio](https://github.com/bogoli/-folio), which is released under the MIT License.

## Publish with GitHub Pages

1. Create a GitHub repository named `michaelmacraild.github.io`.
2. Upload this folder's contents to the repository root.
3. On GitHub, open **Settings > Pages**, set **Source** to **Deploy from a branch**, and select the `main` branch and `/(root)` folder.
4. After deployment, the site will be available at `https://michaelmacraild.github.io`.

## Edit content

- Update the home page in `index.md`.
- Update the biography in `about.md` and research highlights in `spotlights.md`.
- Add publications in `publications.md` and archive updates in `news.md`. Keep the three latest items in `index.md` in sync.
- Update appointments, education, and skills in `cv.md`.
- See [the handover](ACADEMIC_PROFILE_HANDOVER.md) for editing conventions.

## Local preview

Install Ruby and Bundler, then run:

```powershell
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000`.