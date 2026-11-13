---
layout: page
permalink: /contact/
title: Contact
description: Get in touch about collaborations, open roles, or technical questions.
nav: true
nav_order: 8
# TODO(Peter): create a free access key at https://web3forms.com (it is tied to heyinin1@msu.edu) and paste it below.
# While the value is still YOUR_WEB3FORMS_ACCESS_KEY the form is disabled and a note is shown instead.
web3forms_access_key: 68cea5da-cabe-4afa-9c99-2d77d49a75e1
---

I am graduating in January 2027 and actively seeking industry R&D scientist and postdoctoral positions in computational materials science, battery modeling, and electrochemical systems (based in the Detroit, MI area and open to relocation). Please reach out at [heyinin1@msu.edu](mailto:heyinin1@msu.edu) to discuss research collaborations, open roles, or technical questions.

<div class="social">
  <div class="contact-icons">{% social_links %}</div>
</div>

## Send a message

{% assign w3f_placeholder = "YOUR_WEB3FORMS_ACCESS_KEY" %}
{% if page.web3forms_access_key == w3f_placeholder or page.web3forms_access_key == nil or page.web3forms_access_key == "" %}
> ##### Contact form not active yet
> Messages sent from this form will not be delivered until it is set up. Please use email for now: [heyinin1@msu.edu](mailto:heyinin1@msu.edu).
{: .block-warning }
{% endif %}

<!-- TODO(Peter): create a free key at https://web3forms.com and paste it into `web3forms_access_key` in the front matter above. -->
<style>
  .contact-form label { display: block; font-weight: 500; margin-bottom: 0.25rem; }
  .contact-form .field { margin-bottom: 1rem; }
  .contact-form input[type="text"],
  .contact-form input[type="email"],
  .contact-form textarea {
    display: block; width: 100%; box-sizing: border-box; padding: 0.55rem 0.75rem; font: inherit;
    color: var(--global-text-color); background-color: var(--global-bg-color);
    border: 1px solid var(--global-divider-color); border-radius: 0.375rem;
  }
  .contact-form input:focus, .contact-form textarea:focus { outline: 2px solid var(--global-theme-color); outline-offset: 1px; }
  .contact-form button[type="submit"] {
    padding: 0.55rem 1.25rem; font: inherit; color: #fff; background-color: var(--global-theme-color);
    border: 0; border-radius: 0.375rem; cursor: pointer;
  }
  .contact-form button[type="submit"]:disabled { opacity: 0.5; cursor: not-allowed; }
</style>

<form action="https://api.web3forms.com/submit" method="POST" class="contact-form">
  <input type="hidden" name="access_key" value="{{ page.web3forms_access_key | default: w3f_placeholder }}">
  <input type="hidden" name="subject" value="New message from yininghe.github.io">
  <input type="hidden" name="from_name" value="yininghe.github.io contact form">
  <!-- honeypot: real visitors never see or tick this -->
  <input type="checkbox" name="botcheck" style="display: none;" tabindex="-1" autocomplete="off">

  <div class="field">
    <label for="contact-name">Name</label>
    <input type="text" id="contact-name" name="name" required autocomplete="name">
  </div>
  <div class="field">
    <label for="contact-email">Email</label>
    <input type="email" id="contact-email" name="email" required autocomplete="email">
  </div>
  <div class="field">
    <label for="contact-message">Message</label>
    <textarea id="contact-message" name="message" rows="6" required></textarea>
  </div>
  <button type="submit"
    {% if page.web3forms_access_key == w3f_placeholder or page.web3forms_access_key == nil or page.web3forms_access_key == "" %}disabled aria-disabled="true"{% endif %}>
    Send message
  </button>
</form>

## Guestbook

{% if site.giscus.repo and site.giscus.repo_id and site.giscus.category_id %}
<div id="guestbook">
  <script>
    (function () {
      var theme = document.documentElement.getAttribute("data-theme") === "dark" ? "{{ site.giscus.dark_theme }}" : "{{ site.giscus.light_theme }}";
      var s = document.createElement("script");
      s.src = "https://giscus.app/client.js";
      s.async = true;
      s.crossOrigin = "anonymous";
      s.setAttribute("data-repo", "{{ site.giscus.repo }}");
      s.setAttribute("data-repo-id", "{{ site.giscus.repo_id }}");
      s.setAttribute("data-category", "{{ site.giscus.category }}");
      s.setAttribute("data-category-id", "{{ site.giscus.category_id }}");
      s.setAttribute("data-mapping", "specific");
      s.setAttribute("data-term", "Guestbook");
      s.setAttribute("data-strict", "0");
      s.setAttribute("data-reactions-enabled", "{{ site.giscus.reactions_enabled }}");
      s.setAttribute("data-emit-metadata", "0");
      s.setAttribute("data-input-position", "{{ site.giscus.input_position }}");
      s.setAttribute("data-theme", theme);
      s.setAttribute("data-lang", "{{ site.giscus.lang }}");
      document.getElementById("guestbook").appendChild(s);
    })();
  </script>
</div>
{% else %}
Guestbook coming soon.
{% endif %}
