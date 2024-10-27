---
layout: single
title: "My Paintings"
permalink: /paintings/
author_profile: true
---

<div class="paintings-grid">
  {% raw %}
  {% for painting in site.data.paintings %}
    <div class="painting-card">
      <img src="{{ painting.image | relative_url }}" alt="{{ painting.title }}">
      <div class="painting-info">
        <h3>{{ painting.title }}</h3>
        <p class="medium">{{ painting.medium }}</p>
        <p class="year">{{ painting.year }}</p>
      </div>
    </div>
  {% endfor %}
  {% endraw %}
</div>