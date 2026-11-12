# yininghe.github.io

Personal academic portfolio of **Yining He** (Ph.D. candidate, Materials Science, Michigan State University), served at <https://yininghe.github.io>.

Built with [Jekyll](https://jekyllrb.com/) and the [al-folio](https://github.com/alshedivat/al-folio) v1 starter (MIT license, see [`LICENSE`](LICENSE)). In al-folio v1 the layouts, includes, styles and feature code live in versioned Ruby gems (pinned in [`Gemfile`](Gemfile)), so this repo only holds content and configuration. The only local overrides of gem files are `_sass/_themes.scss` (MSU-green accent), `_includes/news.liquid` (month + year dates) and `_layouts/cv.liquid` (PDF button from the page body); they are the documented user-site override mechanism and are tracked in `.al-folio-overrides.yml`. Note that `npm run lint:style-contract` flags `_sass/` (it is meant for the upstream starter). Don't add other `_layouts/`/`_includes/`/`_sass/` files without a reason (see [`AGENTS.md`](AGENTS.md)).

## Where things are

| To change…                         | Edit                                                                                                                                      |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Home page text, subtitle, "Beyond the lab" | `_pages/about.md`                                                                                                                 |
| Research project pages and cards   | `_projects/*.md` (card title/description/thumbnail are in the front matter; `importance` sets the order). Figures: `assets/img/research/` |
| Publications list                  | `_bibliography/papers.bib` (BibTeX; add `selected={true}` to show a paper on the home page)                                               |
| News items on the home page        | one file per item in `_news/` (copy an existing one; the date sets the order and shows as month + year; add `date_label: "2025"` to override the label)                                                             |
| CV page                            | `_data/cv.yml` (on-page CV) **and** replace `assets/pdf/CV_Yining_He.pdf` (the Download button; keep the file name)                        |
| Teaching page                      | `_pages/teaching.md`                                                                                                                      |
| Self-study notes                   | add the PDF to `assets/pdf/notes/`, then list it in `_pages/notes.md`                                                                     |
| Contact page, form, guestbook      | `_pages/contact.md`                                                                                                                       |
| Social links in icons/footer       | `_data/socials.yml`                                                                                                                       |
| Headshot                           | replace `assets/img/prof_pic.webp` (square, ~800px; configured under `profile:` in `_pages/about.md`)                                          |
| Site title, description, footer, plugins, analytics, giscus | `_config.yml`                                                                                                            |

Figures on project pages are `{% raw %}{% include figure.liquid ... %}{% endraw %}` blocks, grouped in Bootstrap rows (`col-md-4` for three across, `col-md-8` centered for a single plot). The home page sets `nav: false` because the navbar already hard-codes an "about" link. The accent colour is set in `_sass/_themes.scss` (`$accent-light`, `$accent-dark`).

Navbar order is set by `nav_order` in each page's front matter: about, research, publications, cv, teaching, notes, contact. The blog is hidden (`nav: false` in `_pages/blog.md`).

## Preview locally

```bash
bundle install
bundle exec jekyll serve          # http://localhost:4000/  (baseurl is empty, so no sub-path)
bundle exec jekyll serve --drafts # also shows posts from _drafts/
```

Responsive images need ImageMagick (`convert` on `PATH`). A one-off production-style build is `bundle exec jekyll build` (output in `_site/`).

## Adding a blog post

1. Copy `_drafts/example-post.md` to `_posts/YYYY-MM-DD-title.md` and edit it.
2. To show the blog in the navbar, in `_pages/blog.md` change `nav: false` to `nav: true` and add `nav_order: 8`.

## Deployment

Pushing to **`master`** runs [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml), which builds the site and publishes it with the **official GitHub Pages Actions flow** (`actions/upload-pages-artifact` + `actions/deploy-pages`). It does not use a `gh-pages` branch. Pushes to other branches (e.g. `redesign`) do not deploy.

One-time setup: in the GitHub repo go to **Settings → Pages → Build and deployment → Source** and choose **GitHub Actions**. The repo must be named `yininghe.github.io`; `url` is set in `_config.yml` and `baseurl` is intentionally empty.

## Placeholders to fill in (TODO)

- **Cloudflare Web Analytics** — paste the beacon token into `analytics.cloudflare` in `_config.yml` (free). While empty, no analytics script is rendered.
- **Contact form (Web3Forms)** — create a free key at <https://web3forms.com> and set `web3forms_access_key` in the front matter of `_pages/contact.md`. Until then the form is disabled and a note tells visitors to use email.
- **Guestbook (giscus)** — enable GitHub Discussions on the repo, install the giscus app, then copy `repo_id` and `category_id` from <https://giscus.app> into the `giscus:` block of `_config.yml`. Until both are set the Contact page shows "Guestbook coming soon". Per-post comments additionally need `giscus_comments: true` in a post.

## Updating the theme later

al-folio versions are pinned in `Gemfile` (and must be listed in `plugins:` in `_config.yml` too). To upgrade, bump the pins, run `bundle update`, and use the upgrade CLI: `bundle exec al-folio upgrade audit` (see [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) and the [al-folio docs](https://github.com/alshedivat/al-folio/tree/main/docs)).

## Notes on this setup

- Jupyter notebook rendering and the demo-only al-folio features (books, repositories, profiles, plugin catalog) were removed. The `docs/` and `test/` folders are the upstream starter's and are excluded from the site build.
- Chemical formulas in prose use HTML (`H<sub>2</sub>`) and Unicode subscripts in `papers.bib` (BibTeX math such as `$_2$` does not render in the publication list).
