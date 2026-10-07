---
layout: page
title: projects
permalink: /projects/
description: Research projects in quantum information, convex optimisation, and machine learning.
nav: true
nav_order: 2
display_categories: ["Quantum Information", "Machine Learning & AI"]
horizontal: false
---

<!-- pages/projects.md -->

<style>
  /* Category headers styling - darker grey */
  .projects h2.category {
    color: #4b5563 !important;
    border-bottom: 1px solid #9ca3af !important;
    font-weight: 600 !important;
    text-align: right;
    padding-top: 0.5rem;
    margin-top: 2rem;
    margin-bottom: 1.25rem;
  }
  .projects a,
  .projects a:hover,
  .projects a:visited {
    text-decoration: none !important;
  }
  .projects a h2.category {
    color: #4b5563 !important;
  }
  html[data-theme="dark"] .projects h2.category,
  html[data-theme="dark"] .projects a h2.category {
    color: #9ca3af !important;
    border-bottom: 1px solid #4b5563 !important;
  }
</style>

<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>

{% else %}

  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>

{% endif %}

{% endif %}
</div>
