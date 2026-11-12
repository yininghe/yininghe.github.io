---
# Example blog post. Drafts in _drafts/ are NOT published.
#
# To publish a post:
#   1. Copy this file to _posts/YYYY-MM-DD-your-title.md  (e.g. _posts/2027-02-01-my-first-post.md)
#   2. Edit the front matter below and write the body in Markdown.
#   3. To show the blog in the navbar, set `nav: true` (and `nav_order: 8`) in _pages/blog.md.
#
# To preview drafts locally: bundle exec jekyll serve --drafts
layout: post
title: Example post title
date: 2027-01-01 10:00:00
description: One-sentence summary shown in the blog list.
tags: [example]
categories: [notes]
giscus_comments: false # set to true once giscus ids are filled in _config.yml
related_posts: false
toc:
  sidebar: false
---

Write the post here using Markdown. Inline chemistry is easiest with HTML: H<sub>2</sub>, Na<sub>2x</sub>[Ni<sub>x</sub>Ti<sub>1−x</sub>]O<sub>2</sub>.

## A section

- a bullet
- another bullet

To add a figure from `assets/img/`:

{% raw %}
```liquid
{% include figure.liquid path="assets/img/research/h2-solubility.webp" class="img-fluid rounded z-depth-1" zoomable=true caption="A caption." %}
```
{% endraw %}
