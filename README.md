# yininghe.github.io

Personal website of **Yining He**, Ph.D. candidate in Materials Science at Michigan State University: research, publications, teaching, and blog.

**Live site:** <https://yininghe.github.io>

Built with [Jekyll](https://jekyllrb.com/) and the [al-folio](https://github.com/alshedivat/al-folio) theme (MIT license, see [`LICENSE`](LICENSE)); hosted free on GitHub Pages.

## Editing the site

| To change… | Edit |
| --- | --- |
| About page (bio, photos, CV button) | `_pages/about.md` |
| Research projects | `_projects/*.md` (figures in `assets/img/research/`) |
| Publications | `_bibliography/papers.bib` (`selected={true}` shows a paper on About) |
| News | one file per item in `_news/` |
| CV (PDF) | replace `assets/pdf/CV_Yining_He.pdf`, same file name |
| Teaching, Contact, Blog pages | `_pages/teaching.md`, `_pages/contact.md`, `_pages/blog.md` |
| Blog posts | copy `_drafts/example-post.md` to `_posts/YYYY-MM-DD-title.md` |
| Social links | `_data/socials.yml` |
| Headshot | `assets/img/prof_pic.webp` (square, ~800 px) |
| Site settings, analytics, comments | `_config.yml` |
| Accent colour | `_sass/_themes.scss` |

Tab order is set by `nav_order` in each page's front matter.

## Preview and deploy

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000/
```

Pushing to `master` builds and publishes the site via [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml). Other branches do not deploy.

## Notes for maintainers

- Theme code lives in versioned al-folio gems pinned in `Gemfile`; this repo holds only content and configuration. The only local overrides are `_sass/_themes.scss` and `_includes/news.liquid` (tracked in `.al-folio-overrides.yml`; see [`AGENTS.md`](AGENTS.md)).
- To upgrade the theme, bump the pins, run `bundle update`, then `bundle exec al-folio upgrade audit`.
- Write chemical formulas as HTML (`H<sub>2</sub>`) in pages and as Unicode subscripts in `papers.bib`.
