---
layout: default
title: Projects
permalink: /projects/
---

<h1>Projects</h1>

<div class="gallery-container">
  <div class="project-gallery" style="display:flex; flex-wrap:wrap; gap:20px;">
    {% for project in site.projects %}
      <div class="gallery-item" style="width:300px; text-align:center;">
        <a href="{{ project.url | relative_url }}">
          <img src="{{ project.image | relative_url }}" 
               alt="{{ project.title }}"
               style="width:100%; border-radius:6px;">
          <p style="margin-top:8px; font-weight:600;">{{ project.title }}</p>
        </a>
      </div>
    {% endfor %}
  </div>
</div>