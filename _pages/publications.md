---
layout: page
permalink: /publications/
title: publications
description: Preprints, thesis, and research papers in quantum information and machine learning.
nav: true
nav_order: 3
---

<!-- _pages/publications.md -->

<style>
  /* Darker grey for publication year headers */
  .publications h2.bibliography {
    color: #4b5563 !important;
    border-top: 1px solid #9ca3af !important;
    font-weight: 600 !important;
  }
  html[data-theme="dark"] .publications h2.bibliography {
    color: #9ca3af !important;
    border-top: 1px solid #4b5563 !important;
  }

  /* Yellow styling for 'In Prep' badges with readable dark text */
  .publications ol.bibliography li .abbr abbr[style*="f59e0b"],
  .publications ol.bibliography li .abbr abbr.in-prep {
    background-color: #f59e0b !important;
    color: #111827 !important;
    font-weight: 600 !important;
  }

  /* Light purple/pink styling for 'Report' badge */
  .publications ol.bibliography li .abbr abbr[style*="c084fc"],
  .publications ol.bibliography li .abbr abbr.report {
    background-color: #c084fc !important;
    color: #3b0764 !important;
    font-weight: 600 !important;
  }
</style>

<!-- Bibsearch Feature (commented out for now) -->
<!-- {% include bib_search.liquid %} -->

<div class="publications">

{% bibliography %}

</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    document.querySelectorAll(".publications ol.bibliography li .abbr abbr").forEach(function(el) {
      const text = el.textContent.trim().toLowerCase();
      if (text.includes("in prep")) {
        el.classList.add("in-prep");
        el.style.setProperty("background-color", "#f59e0b", "important");
        el.style.setProperty("color", "#111827", "important");
        el.style.setProperty("font-weight", "600", "important");
      } else if (text.includes("report")) {
        el.classList.add("report");
        el.style.setProperty("background-color", "#c084fc", "important");
        el.style.setProperty("color", "#3b0764", "important");
        el.style.setProperty("font-weight", "600", "important");
      }
    });
  });
</script>
