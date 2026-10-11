---
layout: page
permalink: /repositories/
title: repositories
description: Open-source research code and software repositories.
nav: true
nav_order: 4
---

<style>
  /* Category headers styling - darker grey matching project guidelines */
  .repositories h2.category {
    color: #4b5563 !important;
    border-bottom: 1px solid #9ca3af !important;
    font-weight: 600 !important;
    padding-top: 0.5rem;
    margin-top: 2rem;
    margin-bottom: 1.25rem;
  }
  html[data-theme="dark"] .repositories h2.category {
    color: #9ca3af !important;
    border-bottom: 1px solid #4b5563 !important;
  }
  .repositories h2.category:first-of-type {
    margin-top: 0.5rem;
  }
  @media (min-width: 768px) {
    .repositories .repo {
      max-width: 50%;
      width: 50%;
    }
  }
</style>

<div class="repositories">
{% if site.data.repositories.github_users %}

  <h2 class="category">GitHub Users</h2>

  <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% for user in site.data.repositories.github_users %}
      {% include repository/repo_user.liquid username=user %}
    {% endfor %}
  </div>

  <hr>

  {% if site.repo_trophies.enabled %}
  {% for user in site.data.repositories.github_users %}
  {% if site.data.repositories.github_users.size > 1 %}

    <h4>{{ user }}</h4>
    {% endif %}
    <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% include repository/repo_trophies.liquid username=user %}
    </div>

  <hr>

  {% endfor %}
  {% endif %}
{% endif %}

{% if site.data.repositories.github_repos_quantum %}
  <h2 class="category">Quantum Information</h2>
  <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% for repo in site.data.repositories.github_repos_quantum %}
      {% include repository/repo.liquid repository=repo %}
    {% endfor %}
  </div>
{% endif %}

{% if site.data.repositories.github_repos_ml %}
  <h2 class="category">Machine Learning & AI</h2>
  <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% for repo in site.data.repositories.github_repos_ml %}
      {% include repository/repo.liquid repository=repo %}
    {% endfor %}
  </div>
{% endif %}

{% if site.data.repositories.github_repos_personal %}
  <h2 class="category">Personal Projects</h2>
  <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% for repo in site.data.repositories.github_repos_personal %}
      {% include repository/repo.liquid repository=repo %}
    {% endfor %}
  </div>
{% endif %}

{% if site.data.repositories.github_repos and site.data.repositories.github_repos_quantum == nil and site.data.repositories.github_repos_ml == nil and site.data.repositories.github_repos_personal == nil %}
  <h2 class="category">GitHub Repositories</h2>
  <div class="d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% for repo in site.data.repositories.github_repos %}
      {% include repository/repo.liquid repository=repo %}
    {% endfor %}
  </div>
{% endif %}
</div>
