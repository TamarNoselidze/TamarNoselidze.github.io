---
layout: page
permalink: /cv/
title: CV
nav: true
nav_order: 1
---

<style>
  .post-header {
    display: flex;
    align-items: center;
    gap: 1.25rem;
    flex-wrap: wrap;
    margin-bottom: 2rem;
  }
  .post-header .post-title {
    margin-bottom: 0 !important;
  }
  .post-header .post-description {
    display: none;
  }
  .cv-pdf-btn {
    border: 1.5px solid var(--global-theme-color) !important;
    color: var(--global-theme-color) !important;
    font-size: 0.95rem !important;
    font-weight: 600 !important;
    padding: 0.45rem 1rem !important;
    border-radius: 6px !important;
    display: inline-flex !important;
    align-items: center !important;
    gap: 0.45rem !important;
    text-decoration: none !important;
    line-height: 1.4 !important;
    box-shadow: none !important;
    transition: all 0.2s ease-in-out !important;
  }
  .cv-pdf-btn:hover {
    background-color: var(--global-theme-color) !important;
    color: #ffffff !important;
  }
  .cv-research-list {
    padding-left: 1.25rem;
    margin-top: 0.75rem;
    margin-bottom: 1.5rem;
  }
  .cv-research-list > li {
    margin-bottom: 1.15rem;
    line-height: 1.6;
  }
</style>

<div id="cv-btn-container" style="margin-top: -1rem; margin-bottom: 1.5rem;">
  <a id="cv-download-btn" href="{{ '/assets/pdf/Tamar_Noselidze_CV.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" class="btn cv-pdf-btn">
    <i class="fa-solid fa-file-pdf"></i> Download CV (PDF)
  </a>
</div>

<script>
  (function() {
    function moveCvBtn() {
      const btn = document.getElementById('cv-download-btn');
      const header = document.querySelector('.post-header');
      const container = document.getElementById('cv-btn-container');
      if (btn && header) {
        header.appendChild(btn);
        if (container) container.remove();
      }
    }
    if (document.readyState === 'loading') {
      document.addEventListener('DOMContentLoaded', moveCvBtn);
    } else {
      moveCvBtn();
    }
  })();
</script>

## Experience

### Quantum Information Research Intern
**The State University of Campinas (UNICAMP)**, Campinas, Brazil | 05/2026 – Present  

<ul class="cv-research-list">
  <li>
    <strong>Quantum Nonlocality &amp; SVMs</strong>: Engineered a novel SVM pipeline to classify Local Hidden States (LHS) and quantum steerability by compressing 2-qubit density matrices into a 9D Fano representation. Extracted a novel algebraic formula to capture nonlocality, overcame LP bottlenecks using MOSEK, and presented findings to UNICAMP physics department. [<a href="https://github.com/TamarNoselidze/SVM-Nonlocality-Boundary" target="_blank" rel="noopener noreferrer">Code</a>]
  </li>
  <li>
    <strong>Multipartite Bell Scenarios (Paper in preparation)</strong>: Defining high-dimensional polytopes and applying vertex annotation (PORTA, PANDA) to discover novel Bell inequalities. Modelling quantum correlations via convex optimisation (CVXPY), linear programming, and see-saw techniques.
  </li>
  <li>
    <strong>Quantum Catalysis (Paper in preparation)</strong>: Investigating catalytic power of quantum states across dimensions, analysing entanglement as a novel thermodynamic and informational resource.
  </li>
</ul>

<br>

### Student Job | Tutoring
**Self-Employed** | 2025 – Present  
Providing private tuition for high school students in Mathematics and English. Specialising in advanced high school calculus, pre-calculus, algebra, and standardised test preparation (SAT). Mentoring students to strengthen mathematical problem-solving skills and intuition.

<br>

### AI Researcher – Bachelor’s Research
**Charles University**, Prague, Czech Republic | 2024 – 2025  

- **Adversarial AI**: Achieved >75% attack success rate on Vision Transformer and CNN architectures by engineering adversarial patch attacks using PyTorch. [<a href="https://github.com/TamarNoselidze/Thesis" target="_blank" rel="noopener noreferrer">Code</a>] [<a href="https://dspace.cuni.cz/handle/20.500.11956/200886" target="_blank" rel="noopener noreferrer">Thesis</a>]
- **HPC Simulation**: Designed and deployed reproducible Python-based machine learning pipelines, consuming over 500 GPU days on the MetaCentrum supercomputing cluster.
- **Model Optimisation**: Integrated pre-trained models and applied optimisation techniques to improve reliability and performance across large-scale image datasets.
- **Scientific Workflow**: Collaborated in an agile research team, leveraging Git for version control and systematically documenting experimental methodologies for academic publication.

---

## Education

### [Master of Science](https://www.sorbonne-universite.fr/)
**Sorbonne University** | Paris, France | 2025 – Present  
**Quantum Information (QI)**  
**Relevant Coursework**: Quantum Algorithms, Quantum Dynamics, Quantum Information Theory, Mathematical Algorithms & Complexity, Data Science & Statistical Learning, Photonic Quantum Computing, Quantum Cryptography.

<br>

### [Bachelor of Science](https://cuni.cz/)
**Charles University** | Prague, Czech Republic | 2021 – 2025  
**Computer Science – Artificial Intelligence**  
**Thesis**: *Adversarial Examples Against Vision Transformers* (Supervisor: Doc. Mgr. Martin Pilát, Ph.D.)  
Focused on Artificial Intelligence and Machine Learning with a rigorous mathematical foundation.  
**Relevant Coursework**: Linear Algebra, Probability & Statistics, Graph Theory, Mathematical Analysis, Machine Learning, Computer Vision, Natural Language Processing.

---

## Skills

- **Quantum Computing**: Quantum Algorithms, Quantum Information Theory, Hybrid Quantum-Classical Algorithms, Quantum Cryptography
- **Mathematical Optimisation**: Convex Optimisation, Linear Programming, Semidefinite Programming (SDP), MOSEK, CVXPY, PORTA, PANDA, NumPy, Pandas, SciPy
- **Machine Learning**: PyTorch, Hugging Face Transformers, Scikit-learn, Vision Transformers (ViTs), Adversarial Robustness, Computer Vision
- **Programming Languages**: Python (Advanced), Julia, C#, Java, Haskell, MATLAB, Bash
- **Software & Infrastructure**: Git/GitHub, Docker, Singularity (Containerisation), Linux, High-Performance Computing (HPC Workflows)

---

## Volunteering

### Co-Founder & Web Developer
**Long Swim to Freedom** | France & South Africa | 2026 – Present  
- Co-founded non-profit initiative dedicated to rural child drowning prevention and rhino anti-poaching around the iSimangaliso Wetland Park.
- Designed and developed the campaign website to mobilise international awareness, secure partnerships, and facilitate donations for community swimming programmes and ranger units.

<br>

### Volunteer Tutor
**Helping Hand (NGO)** | Tbilisi, Georgia | 2020 – 2023  
- Developed strong interpersonal skills by working with diverse groups and adapting to challenging environments.
- Maintained high levels of patience and encouragement while managing multiple tasks simultaneously.

---

## Languages

- **English**: Fluent
- **Georgian**: Native
- **Russian**: Intermediate
- **French**: Beginner
