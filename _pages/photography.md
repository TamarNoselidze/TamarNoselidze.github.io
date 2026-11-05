---
layout: page
title: photography
permalink: /photography/
description: 35mm and medium format film photography — documenting light, grain, and moments on analogue film.
nav: true
nav_order: 5
images:
  spotlight: true
---

<!-- _pages/photography.md -->

<style>
  /* Header & Subtitle Styling */
  .photography-intro {
    margin-bottom: 2rem;
    font-size: 1.05rem;
    line-height: 1.6;
    color: var(--global-text-color-light, #6b7280);
  }

  /* Masonry Column Gallery */
  .photo-gallery {
    column-count: 1;
    column-gap: 1.5rem;
  }
  @media (min-width: 576px) {
    .photo-gallery {
      column-count: 2;
    }
  }
  @media (min-width: 992px) {
    .photo-gallery {
      column-count: 3;
    }
  }

  /* Photo Card Styling */
  .photo-card {
    break-inside: avoid;
    margin-bottom: 1.5rem;
    background: var(--global-card-bg-color, #ffffff);
    border: 1px solid var(--global-divider-color, rgba(0, 0, 0, 0.1));
    border-radius: 8px;
    overflow: hidden;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
    display: inline-block;
    width: 100%;
  }
  .photo-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  }

  /* Image Container & Spotlight Zoom */
  .photo-img-wrap {
    position: relative;
    overflow: hidden;
    background-color: rgba(0, 0, 0, 0.04);
  }
  .photo-img-wrap a.spotlight {
    display: block;
    cursor: zoom-in;
    text-decoration: none !important;
  }
  .photo-img-wrap img {
    width: 100%;
    height: auto;
    display: block;
    transition: transform 0.35s ease;
  }
  .photo-card:hover .photo-img-wrap img {
    transform: scale(1.025);
  }

  /* Card Content */
  .photo-info {
    padding: 1rem 1.15rem 1.15rem;
  }
  .photo-title {
    font-size: 1.05rem;
    font-weight: 600;
    color: #4b5563;
    margin-bottom: 0.5rem;
    line-height: 1.4;
  }
  html[data-theme="dark"] .photo-title {
    color: #e5e7eb;
  }

  /* Badges & Chips */
  .photo-badges {
    display: flex;
    flex-wrap: wrap;
    gap: 0.35rem;
    margin-bottom: 0.6rem;
  }
  .photo-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.35rem;
    font-size: 0.78rem;
    font-weight: 500;
    padding: 0.2rem 0.55rem;
    border-radius: 4px;
    background: rgba(107, 114, 128, 0.1);
    color: #4b5563;
  }
  html[data-theme="dark"] .photo-badge {
    background: rgba(156, 163, 175, 0.15);
    color: #9ca3af;
  }
  .photo-badge-film {
    background: rgba(27, 107, 58, 0.1);
    color: #1b6b3a;
    font-weight: 600;
  }
  html[data-theme="dark"] .photo-badge-film {
    background: rgba(46, 187, 119, 0.15);
    color: #2ebb77;
  }

  /* Caption Text */
  .photo-caption {
    font-size: 0.88rem;
    line-height: 1.5;
    color: var(--global-text-color-light, #6b7280);
    margin: 0;
  }

  /* Empty State Placeholder */
  .photography-empty-state {
    text-align: center;
    padding: 3.5rem 1.5rem;
    margin: 2rem 0;
    border: 2px dashed var(--global-divider-color, rgba(0, 0, 0, 0.15));
    border-radius: 10px;
    background: var(--global-card-bg-color, #fafafa);
  }
  .photography-empty-state .empty-icon {
    font-size: 3rem;
    color: #1b6b3a;
    margin-bottom: 1rem;
    opacity: 0.85;
  }
  html[data-theme="dark"] .photography-empty-state .empty-icon {
    color: #2ebb77;
  }
  .photography-empty-state h3 {
    font-size: 1.35rem;
    font-weight: 600;
    color: #4b5563;
    margin-bottom: 0.6rem;
  }
  html[data-theme="dark"] .photography-empty-state h3 {
    color: #9ca3af;
  }
  .photography-empty-state p {
    font-size: 0.95rem;
    color: var(--global-text-color-light, #6b7280);
    max-width: 540px;
    margin: 0 auto 0.75rem;
    line-height: 1.6;
  }
  .photography-empty-state code {
    background: rgba(107, 114, 128, 0.1);
    padding: 0.15rem 0.4rem;
    border-radius: 4px;
    color: var(--global-theme-color, #1b6b3a);
    font-size: 0.88rem;
  }
  html[data-theme="dark"] .photography-empty-state code {
    color: #2ebb77;
  }
  .photography-empty-state .empty-hint {
    font-size: 0.85rem;
    opacity: 0.85;
  }
</style>

<div class="photography-section">
  <p class="photography-intro">
    A collection of 35mm and medium format film captures — documenting light, grain, textures, and moments on analogue film.
  </p>

  {% assign configured_images = "" | split: "" %}
  {% assign has_photos = false %}

  <!-- Check for photos defined in _data/photography.yml -->
  {% if site.data.photography and site.data.photography.size > 0 %}
    {% assign has_photos = true %}
    {% for item in site.data.photography %}
      {% assign configured_images = configured_images | push: item.image %}
    {% endfor %}
  {% endif %}

  <!-- Check for any static photos placed in assets/img/photography/ -->
  {% assign static_photos = site.static_files | where_exp: "file", "file.path contains '/assets/img/photography/'" %}
  {% for file in static_photos %}
    {% assign filename = file.path | split: "/" | last %}
    {% unless filename == ".gitkeep" %}
      {% assign has_photos = true %}
    {% endunless %}
  {% endfor %}

  {% if has_photos %}
    <div class="photo-gallery">
      <!-- 1. Display metadata-enriched photos from _data/photography.yml -->
      {% if site.data.photography and site.data.photography.size > 0 %}
        {% for photo in site.data.photography %}
          {% if photo.image contains "/" %}
            {% assign photo_url = photo.image | relative_url %}
          {% else %}
            {% assign photo_url = '/assets/img/photography/' | append: photo.image | relative_url %}
          {% endif %}

          {% capture lightbox_desc %}{% if photo.film %}{{ photo.film }}{% endif %}{% if photo.camera %} · {{ photo.camera }}{% endif %}{% if photo.location %} · {{ photo.location }}{% endif %}{% if photo.year %} ({{ photo.year }}){% endif %}{% if photo.caption %}<br>{{ photo.caption }}{% endif %}{% endcapture %}

          <div class="photo-card">
            <div class="photo-img-wrap">
              <a class="spotlight"
                 data-group="film-gallery"
                 href="{{ photo_url }}"
                 data-title="{{ photo.title | default: 'Film Photograph' }}"
                 data-description="{{ lightbox_desc | strip }}">
                <img src="{{ photo_url }}"
                     alt="{{ photo.title | default: 'Film photograph' }}"
                     loading="lazy" />
              </a>
            </div>
            {% if photo.title or photo.film or photo.camera or photo.location or photo.year or photo.caption %}
              <div class="photo-info">
                {% if photo.title %}
                  <div class="photo-title">{{ photo.title }}</div>
                {% endif %}

                {% if photo.film or photo.camera or photo.location or photo.year %}
                  <div class="photo-badges">
                    {% if photo.film %}
                      <span class="photo-badge photo-badge-film" title="Film stock">
                        <i class="fa-solid fa-film"></i> {{ photo.film }}
                      </span>
                    {% endif %}
                    {% if photo.camera %}
                      <span class="photo-badge" title="Camera">
                        <i class="fa-solid fa-camera"></i> {{ photo.camera }}
                      </span>
                    {% endif %}
                    {% if photo.location %}
                      <span class="photo-badge" title="Location">
                        <i class="fa-solid fa-location-dot"></i> {{ photo.location }}
                      </span>
                    {% endif %}
                    {% if photo.year %}
                      <span class="photo-badge" title="Year">
                        <i class="fa-solid fa-calendar"></i> {{ photo.year }}
                      </span>
                    {% endif %}
                  </div>
                {% endif %}

                {% if photo.caption %}
                  <p class="photo-caption">{{ photo.caption }}</p>
                {% endif %}
              </div>
            {% endif %}
          </div>
        {% endfor %}
      {% endif %}

      <!-- 2. Display auto-discovered photos in assets/img/photography/ not yet in _data/photography.yml -->
      {% for file in static_photos %}
        {% assign filename = file.path | split: "/" | last %}
        {% unless configured_images contains filename or filename == ".gitkeep" %}
          {% assign photo_url = file.path | relative_url %}
          {% assign clean_title = filename | split: "." | first | replace: "_", " " | replace: "-", " " | capitalize %}

          <div class="photo-card">
            <div class="photo-img-wrap">
              <a class="spotlight"
                 data-group="film-gallery"
                 href="{{ photo_url }}"
                 data-title="{{ clean_title }}">
                <img src="{{ photo_url }}"
                     alt="{{ clean_title }}"
                     loading="lazy" />
              </a>
            </div>
            <div class="photo-info">
              <div class="photo-title">{{ clean_title }}</div>
              <div class="photo-badges">
                <span class="photo-badge photo-badge-film">
                  <i class="fa-solid fa-film"></i> 35mm
                </span>
              </div>
            </div>
          </div>
        {% endunless %}
      {% endfor %}
    </div>
  {% else %}
    <!-- Friendly empty state when no photos have been added yet -->
    <div class="photography-empty-state">
      <div class="empty-icon">
        <i class="fa-solid fa-camera-retro"></i>
      </div>
      <h3>Film Gallery Ready</h3>
      <p>
        Drop your film scans or photos into <code>photography/</code> (or <code>assets/img/photography/</code>) and they will automatically appear here.
      </p>
      <p class="empty-hint">
        You can also add film stock, camera, location, and captions in <code>_data/photography.yml</code>.
      </p>
    </div>
  {% endif %}
</div>

<!-- Spotlight JS Bundle for interactive lightbox zoom and navigation -->
<script src="https://cdn.jsdelivr.net/npm/spotlight.js@0.7.8/dist/spotlight.bundle.js" defer></script>
