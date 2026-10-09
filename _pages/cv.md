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

### Quantum Information Researcher
**UNICAMP & Sorbonne University**, Campinas & Paris | 05/2026 – Present  
*Research in different groups, across various topics such as quantum nonlocality, steerability classification, multipartite Bell scenarios, and quantum catalysis.*

<ul class="cv-research-list">
  <li>
    <strong>Quantum Nonlocality &amp; SVMs</strong>: Engineered a novel SVM pipeline to classify Local Hidden States (LHS) and quantum steerability by compressing 2-qubit density matrices into a 9-dimensional Fano feature representation. Extracted a novel algebraic formula to capture quantum nonlocality, overcame traditional LP bottlenecks by implementing convex optimisation pipelines using MOSEK, and presented findings to the UNICAMP physics department.<br>
    <a href="https://github.com/TamarNoselidze/SVM-Nonlocality-Boundary" target="_blank" rel="noopener noreferrer">GitHub Repository</a>
  </li>
  <li>
    <strong>Multipartite Bell Scenarios (paper in preparation)</strong>: Defining high-dimensional polytopes and applying vertex annotation (using PORTA, PANDA) to discover novel Bell inequalities. Using convex optimisation (in CVXPY), linear programming, and see-saw techniques to model complex quantum correlations.
  </li>
  <li>
    <strong>Quantum Catalysis (paper in preparation)</strong>: Investigating the catalytic power of quantum states across different dimensions, analysing entanglement as a novel thermodynamic and informational resource.
  </li>
</ul>

<br>

### Student Job | Tutoring
**Self-Employed** | 2025 – Present  
Providing private tuition for high school students in Mathematics and English. Specialising in advanced high school calculus, pre-calculus, algebra, and standardised test preparation (SAT). Mentoring students to strengthen mathematical problem-solving skills and intuition.

<br>

### AI Researcher
**Charles University**, Prague | 2024 – 2025  
*Bachelor’s research on adversarial deep learning and high-performance computing.*

- **Adversarial AI**: Achieved >75% attack success rate on Vision Transformer and CNN models by engineering adversarial patch attacks using PyTorch.
- **HPC Simulation**: Designed and implemented reproducible Python-based machine learning pipelines, consuming over 500 GPU days on the MetaCentrum cluster.
- **Scientific Workflow**: Collaborated in an agile research environment using Git for version control and documenting experimental results for academic publication.
- **Model Optimisation**: Integrated pre-trained models and applied optimisation techniques to improve reliability and performance on large image datasets.

[GitHub Repository](https://github.com/TamarNoselidze/Thesis)  
[Published Thesis](https://dspace.cuni.cz/handle/20.500.11956/200886)

---

## Education

### [Master of Science](https://www.sorbonne-universite.fr/)
**Sorbonne University** | Paris, France | 2025 – Present  
**Quantum Information (QI)**  
**Coursework**: Quantum Algorithms, Quantum Dynamics, Quantum Information Theory, Mathematical Algorithms & Complexity, Data Science & Statistical Learning, Photonic Quantum Computing, Quantum Cryptography.

<br>

### [Bachelor of Science](https://cuni.cz/)
**Charles University** | Prague, Czech Republic | 2021 – 2025  
**Computer Science - Artificial Intelligence**  
**Thesis**: *Adversarial Examples Against Vision Transformers* (Supervised by Doc. Mgr. Martin Pilát, Ph.D.)  
Focused on Artificial Intelligence and Machine Learning with a rigorous mathematical foundation.  
**Coursework**: Linear Algebra, Probability & Statistics, Graph Theory, Mathematical Analysis, Machine Learning, Computer Vision, NLP.

---

## Skills

- **Quantum & Optimisation**: Convex Optimisation, Linear Programming, See-Saw Technique, Hybrid ML-Quantum Algorithms, Bell Nonlocality
- **Optimisation & Scientific Tooling**: MOSEK, CVXPY, PORTA, PANDA, RANDA, NumPy, Pandas
- **Development & HPC**: Git/GitHub, Docker, Singularity (Containerisation), Bash, Linux, HPC Workflows (MetaCentrum)
- **Programming Languages**: Python, Julia, Java, C#, Haskell, MATLAB
- **Machine Learning**: PyTorch, Hugging Face Transformers, SVMs, Scikit-learn, Computer Vision, Adversarial Robustness

---

## Volunteering

### Co-Founder & Web Developer
**Long Swim to Freedom** | France & South Africa | 2026 – Present  
- Co-founded non-profit initiative in France alongside partners in South Africa, dedicated to rural child drowning prevention and rhino anti-poaching around the iSimangaliso Wetland Park.
- Designed and developed the organisation's official campaign website to mobilise international awareness, secure partnerships, and facilitate donations for community swimming programmes and ranger units.

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
