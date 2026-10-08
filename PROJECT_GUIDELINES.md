# Portfolio Design & Maintenance Guidelines

This document records the conventions, style choices, and architectural decisions established for Tamar Noselidze's portfolio website. Any agent or developer working on this codebase should adhere to these guidelines.

---

## 1. Language & Spelling
- **Dialect**: **British English** throughout all pages, project descriptions, publications, and CV content.
  - Examples: *optimisation* (not optimization), *modelling* (not modeling), *specialisation* (not specialization), *catalysing* (not catalyzing).

---

## 2. Color Palette & Visual Theme
- **Primary Accent**: Dark forest green:
  - Light mode: `#1b6b3a`
  - Dark mode: `#2ebb77`
- **Section Headers (Years, Categories)**: Dark slate grey (`#4b5563` in light mode, `#9ca3af` in dark mode) instead of bright green for cleaner visual hierarchy.
- **Publication Badges**:
  - `In Prep`: Soft yellow background (`#fef08a`), dark amber text (`#854d0e`).
  - `Report`: Soft lavender/purple background (`#c084fc`), dark purple text (`#3b0764`).
- **Profile Photo**: Rectangular / square crop (`border-radius: 4px;`), no oval masks.

---

## 3. LaTeX & Math Rendering Rules
- **Bra-Ket Notation**: **Never use literal ASCII pipe characters (`|`)** inside inline or block math (e.g. avoid `$|\phi\rangle$`).
  - **Reason**: Jekyll's Kramdown parser (GFM mode) interprets `|` as a Markdown table column delimiter before MathJax processes the page, wrapping the text into a broken HTML table.
  - **Standard**: Always use LaTeX commands `\lvert` and `\rvert` or `\vert`:
    - Use `$\lvert \phi \rangle$` instead of `$|\phi\rangle$`.
    - Use `$\lvert \psi^- \rangle \langle \psi^- \rvert$` instead of `$|\psi^-\rangle\langle\psi^-|$`.

---

## 4. Projects Page Structure
- **Frontmatter**: Always set `related_publications: false` to prevent Jekyll from auto-appending a duplicate bibliography section.
- **References**: Use a single manual `### References` header at the bottom of each project page for consistent citations.
- **Image Assets**: High-resolution project figures (e.g., conference posters, group photos) reside in `assets/img/`, with full-resolution PDFs in `assets/pdf/`.

---

## 5. Publications & CV
- **Publications Filter Bar**: Hidden via `d-none` on the search input in `_pages/publications.md`.
- **CV Page**: Clean unboxed layout; Experience section placed before Education; "Download CV" button styled prominently beside the page title.
