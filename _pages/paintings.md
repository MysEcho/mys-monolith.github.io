---
layout: default
title: Paintings
---

<div class="paintings">
  {% for painting in site.static_files %}
    {% if painting.path contains 'assets/images/paintings' %}
      <div class="grid-item">
        <img src="{{ painting.path | relative_url }}" alt="Painting">
      </div>
    {% endif %}
  {% endfor %}
</div>
