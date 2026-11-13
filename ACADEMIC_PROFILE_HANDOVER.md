# Academic Profile Website Handover

**Site:** Michael MacRaild academic profile  
**Source folder:** `academic-profile/`  
**Live site:** `https://michaelmacraild.github.io/`  
**Platform:** GitHub Pages with Jekyll and hand-authored Markdown/HTML

This document records the website structure, the design/content conventions
already established, and the usual updates to make as new research outputs,
talks, appointments, or images become available.

## Site Structure

| Location | Purpose |
|---|---|
| `index.md` | Homepage: identity, links, academic journey, short biography, and the three most recent news items. |
| `about.md` | Longer biography, academic background, thesis link, and graduation photographs. |
| `spotlights.md` | Three project-based research highlights with figures and DOI links. |
| `publications.md` | Full reverse-chronological publication record. |
| `news.md` | Full reverse-chronological news archive. |
| `cv.md` | Appointments, education, teaching/leadership, presentations, and technical skills. |
| `_layouts/default.html` | Shared page shell, header navigation, footer, and stylesheet link. |
| `_config.yml` | Jekyll site title, description, URL/base URL, and Markdown configuration. |
| `assets/css/style.scss` | Entire custom visual system and responsive styling. |
| `assets/img/` | Headshot, graduation photographs, and research-spotlight figures. |
| `Gemfile` | Ruby/Jekyll dependencies for local preview. |

## Current Design and Content Pattern

The site deliberately uses a restrained academic visual style: off-white
background, dark text, teal accent colour, serif body typography, compact
Arial navigation/labels, thin dividers, and square imagery. The layout is
fully responsive, including the homepage hero and mobile navigation.

The homepage is intentionally an academic profile rather than a landing page:

- Identity block: role, affiliation, contact, GitHub, LinkedIn, Google Scholar,
  and ORCID.
- Square headshot beside the name.
- Three-point academic journey: 2018 Manchester MMath & Physics; 2024 Leeds
  PhD/MSc; present Manchester Research Associate.
- Brief research description and a three-item latest-news list.

Keep this compact layout. Long explanations and full chronology belong on the
About, Publications, News, or CV pages rather than the homepage.

## Routine Updates

### New publication

1. Verify the citation from an authoritative source: publisher page, DOI,
   Crossref record, or the authors' accepted citation. Do not infer title,
   authors, journal, or DOI from a partial URL.
2. Add the item at the top of the matching year in `publications.md` using the
   established one-line `<li>` pattern:

   ```html
   <li><span class="publication-year">2026</span><span class="publication-title">Paper title.</span><span class="item-meta">Author, A., <strong>MacRaild, M.</strong>, and Co-author, B. <em>Journal Name</em>, volume, article number.</span><a class="doi-link" href="https://doi.org/...">DOI: ...</a></li>
   ```

3. Use `<strong>MacRaild, M.</strong>` to highlight Michael's authorship.
4. Preserve the actual author order and the journal's punctuation/capitalisation.
5. Add a corresponding item at the top of `news.md`, using a useful short
   description and the DOI or publisher page as the link.
6. If it is among the three newest updates, add a short version to the top of
   the latest-news list in `index.md` and remove the fourth item. The homepage
   list is manual; it does not automatically read from `news.md`.

The latest publication added in this work is:

> Xue et al. (including Michael MacRaild), *Risk-informed framework for in
> silico regulatory evaluation of medical devices*, **Device** (2026), article
> 101303. DOI: `10.1016/j.device.2026.101303`.

### New talk, conference, award, or milestone

- Add the full update at the top of `news.md`, in month/year order.
- Add the presentation to `cv.md` under **Presentations** when applicable.
- Update the homepage latest-news list only when it belongs in the latest three.
- Keep news prose personal, factual, and brief. Use a public link only where it
  adds value, such as a conference recording, DOI, award announcement, or
  project page.

### Appointment, qualification, or skills change

- Update the homepage role line in `index.md` if the current title or
  institution changes.
- Update the current position in `cv.md` and add a news item for a meaningful
  appointment or degree milestone.
- Update `about.md` where the narrative biography would otherwise become stale.
- Update `_config.yml` `description` if the one-line site description changes.

### Research spotlight

- Add or revise a `<section class="spotlight-detail">` in `spotlights.md`.
- Place a web-appropriate PNG or JPG in `assets/img/`.
- Use `{{ '/assets/img/filename.ext' | relative_url }}` for asset links so the
  page remains portable under GitHub Pages.
- Include concise text and a direct DOI/publisher link. The existing spotlights
  cover PComA flow-diverter assessment, reduced-order modelling, and simulation
  acceleration.

### Images

- The homepage and About headshot both use `assets/img/profile.jpg`.
- Graduation images are `assets/img/UoM.jpg` and `assets/img/UoL.JPG`.
- Research figures currently used are `pcoma-ist-results.png`,
  `rom-cover-graphic.png`, and `vascular-flow-review.png`.
- Keep display dimensions square for portraits/gallery images and use
  informative `alt` text. The stylesheet uses `object-fit: cover` for portraits
  and `object-fit: contain` for spotlight figures.

## Navigation and URLs

Navigation is defined once in `_layouts/default.html`. The current primary
pages are:

```text
/about/
/spotlights/
/publications/
/news/
/cv/
```

Each page declares its `permalink` in front matter. When creating a new page,
add compatible front matter, add a navigation link only when it merits a
top-level section, and use `relative_url` for internal links/assets.

## Styling Guidance

Use the existing classes in `assets/css/style.scss` rather than adding inline
styles. Main reusable patterns are:

| Content | Classes / structure |
|---|---|
| Small uppercase label | `eyebrow` or `section-label` |
| Page introduction | `lead` |
| Publication/CV list | `item-list`, `publication-year`, `publication-title`, `item-meta`, `doi-link` |
| News archive | `news-list news-list-full` |
| Homepage recent news | `home-news` containing `news-list` |
| Research highlight | `spotlight-detail`, `spotlight-figure` |

Keep the existing teal palette and spacing system. The homepage hero stacks at 960 px and the mobile layout starts at 620 px.
Check both widths when changing a grid or image treatment.

## Deployment and Checking

The published repository is expected to be named `michaelmacraild.github.io`.
GitHub Pages deploys the repository root from the `main` branch. This local source copy has no Git metadata. Locate the publishing checkout
or upload the edited source files to the repository root. Commit source files
only. The handover is excluded from the generated site.

For a local preview, from `academic-profile/`:

```powershell
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000`.

If Ruby/Jekyll is unavailable, check edited Markdown/HTML files for diagnostics
in VS Code and inspect the deployed pages after pushing. A stale browser cache
can make a successful Pages deployment appear unchanged; use a hard refresh
(`Ctrl+F5`) or a cache-busted URL before assuming the deployment failed.

## Practical Editing Rules

- Preserve existing manual wording unless an update requires changing it.
- Keep lists reverse chronological.
- Treat bibliographic metadata as factual data: use verified sources before
  adding it.
- Use direct DOI links where possible rather than fragile search URLs.
- Do not add a bibliography generator unless there is a clear requirement; the
  current site intentionally uses readable hand-authored citations.
- Keep source images in `assets/img/` and avoid external image URLs for core
  page content.
- Validate all new external links and check that newly added content appears in
  both the relevant archive and the homepage where appropriate.
