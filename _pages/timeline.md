---
layout: page
title: Timeline
permalink: /timeline/
description: A chronological log of conferences, travel, milestones, and more. Use the filters to show only what you want.
nav: true
nav_order: 5
---

<!-- _pages/timeline.md — events are stored in _data/timeline.yml -->

<style>
  .timeline-filters { display: flex; flex-wrap: wrap; gap: 0.5rem; margin: 0 0 2rem; }
  .timeline-filter {
    cursor: pointer; font-size: 0.8rem; text-transform: capitalize;
    padding: 0.25rem 0.85rem; border-radius: 2rem;
    border: 1px solid var(--global-divider-color);
    background: transparent; color: var(--global-text-color);
    transition: background 0.15s, color 0.15s, border-color 0.15s;
  }
  .timeline-filter.active {
    background: var(--global-theme-color);
    color: var(--global-hover-text-color);
    border-color: var(--global-theme-color);
  }
  .timeline-filter.timeline-all { font-weight: 600; }

  .timeline {
    position: relative; margin: 0 0 0 0.5rem; padding-left: 1.75rem;
    border-left: 2px solid var(--global-divider-color);
  }
  .timeline-item { position: relative; margin-bottom: 1.75rem; }
  .timeline-item::before {
    content: ''; position: absolute; left: -1.95rem; top: 0.3rem;
    width: 11px; height: 11px; border-radius: 50%;
    background: var(--global-theme-color);
    box-shadow: 0 0 0 3px var(--global-bg-color);
  }
  .timeline-meta { display: flex; gap: 0.6rem; align-items: baseline; }
  .timeline-date { font-size: 0.8rem; color: var(--global-text-color-light); }
  .timeline-cat { font-size: 0.68rem; text-transform: uppercase; letter-spacing: 0.06em; color: var(--global-theme-color); }
  .timeline-title { font-weight: 600; margin-top: 0.1rem; }
  .timeline-loc, .timeline-desc { font-size: 0.85rem; color: var(--global-text-color-light); }
</style>

{% assign cats = site.data.timeline | map: "category" | uniq | sort %}
{%- comment -%} Categories ON by default at page load. Any category not listed here starts hidden — click its pill (or All) to reveal it. Edit this list to taste. {%- endcomment -%}
{% assign default_categories = "conference,milestone" | split: "," %}
<div class="timeline-filters">
  <button type="button" class="timeline-filter timeline-all">All</button>
  {% for cat in cats %}
  <button type="button" class="timeline-filter{% if default_categories contains cat %} active{% endif %}" data-category="{{ cat }}">{{ cat }}</button>
  {% endfor %}
</div>

{% assign events = site.data.timeline | sort: "date" | reverse %}
<div class="timeline">
  {% for event in events %}
  <div class="timeline-item" data-category="{{ event.category }}">
    <div class="timeline-meta">
      <span class="timeline-date">{{ event.date | date: "%b %Y" }}</span>
      <span class="timeline-cat">{{ event.category }}</span>
    </div>
    <div class="timeline-title">
      {% if event.link %}<a href="{{ event.link }}">{{ event.title }}</a>{% else %}{{ event.title }}{% endif %}
    </div>
    {% if event.location %}<div class="timeline-loc">{{ event.location }}</div>{% endif %}
    {% if event.description %}<div class="timeline-desc">{{ event.description }}</div>{% endif %}
  </div>
  {% endfor %}
</div>

<script>
  (function () {
    var catFilters = Array.prototype.slice.call(document.querySelectorAll('.timeline-filter[data-category]'));
    var allBtn = document.querySelector('.timeline-filter.timeline-all');
    var items = Array.prototype.slice.call(document.querySelectorAll('.timeline-item'));
    function apply() {
      var active = {};
      catFilters.forEach(function (f) {
        if (f.classList.contains('active')) active[f.getAttribute('data-category')] = true;
      });
      items.forEach(function (it) {
        it.style.display = active[it.getAttribute('data-category')] ? '' : 'none';
      });
    }
    catFilters.forEach(function (f) {
      f.addEventListener('click', function () { f.classList.toggle('active'); apply(); });
    });
    if (allBtn) {
      allBtn.addEventListener('click', function () {
        // Master toggle: starts off; 1st click turns everything on, next turns everything off.
        var turnOn = !allBtn.classList.contains('active');
        catFilters.forEach(function (f) { f.classList.toggle('active', turnOn); });
        allBtn.classList.toggle('active', turnOn);
        apply();
      });
    }
    apply();
  })();
</script>
