---
layout: page
title: Research
permalink: /research/
description: My main research projects.
nav: true
nav_order: 1
display_categories: [current, past]
horizontal: false
---

<div class="projects">
{%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized = site.research | where: "category", category -%}
  {%- assign sorted_research = categorized | sort: "importance" %}
  <div class="grid">
    {%- for project in sorted_research -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
{% endfor %}
</div>