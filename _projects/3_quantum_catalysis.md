---
layout: page
title: Quantum State Catalysis Across Dimensions
description: Computational investigation and dimensional scaling of catalytic power in entanglement-assisted LOCC state transformations.
img: assets/img/catalysis_poster.jpg
importance: 3
category: Quantum Information
related_publications: false
---

### Overview

In quantum resource theories, **entanglement catalysis** occurs when an auxiliary entangled state enables an otherwise forbidden state transformation under Local Operations and Classical Communication (LOCC) without being consumed or degraded:

$$|\psi_1\rangle \otimes |\phi\rangle \xrightarrow{\text{LOCC}} |\psi_2\rangle \otimes |\phi\rangle \iff \boldsymbol{\lambda}_1 \otimes \boldsymbol{\beta} \prec \boldsymbol{\lambda}_2 \otimes \boldsymbol{\beta}$$

While Nielsen's majorisation criterion ($\boldsymbol{\lambda}_1 \prec \boldsymbol{\lambda}_2$) dictates when deterministic LOCC transitions are possible, borrowing an auxiliary catalyst $|\phi\rangle$ with Schmidt spectrum $\boldsymbol{\beta}$ unlocks transitions between incomparable pairs.

This project is a computational investigation conducted with the **Mathematical Foundations of Quantum Theory (MFQ) group at UNICAMP (Campinas, Brazil)** to quantify and define **catalytic power** across dimensions.

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-12 text-center">
    <a href="{{ '/assets/pdf/catalysis_poster.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/catalysis_poster.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Quantum State Catalysis Research Poster" style="width: 100%; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.9rem;">
      Research poster presented on entanglement catalysis and dimensional scaling at UNICAMP (Campinas, Brazil). Click image to view full vector PDF.
    </div>
  </div>
</div>

---

### Research Team

- **Tamar Noselidze** (LIP6, Sorbonne Université – CNRS, France)
- **Project Supervisor**: **[Marcelo Terra Cunha](https://www.ime.unicamp.br/~tcunha/)** (UNICAMP, Brazil)
- **Co-Authors**: **Cristhiano Duarte** (Federal University of Juiz de Fora, Brazil), **Carlos Vieira** (LIP6, Sorbonne Université – CNRS, France), **Enzo Visintin** (Columbia University, USA)

---

### Methodology & Numerical Simulations

- **Unbiased Dirichlet Sampling**: Generated datasets of 20,000 and 40,000 pure bipartite state probability vectors drawn uniformly from Dirichlet distributions to prevent sampling bias.
- **Incomparable Pair Evaluation**: Filtered state pairs that violate direct Nielsen majorisation and tested reachability under candidate 2-dimensional ($\boldsymbol{\beta} = (p, 1-p)$) and 3-dimensional ($\boldsymbol{\beta} = (a, b, 1-a-b)$) catalysts.
- **Quantifying Catalytic Power**: Measured catalytic power as the fraction of otherwise-impossible conversions successfully enabled by a candidate catalyst across dimensions $d = 4, 8, 12$.

---

### Key Findings

1. **Dimensional Scaling**: Catalytic power increases monotonically with target dimension $d$. Incomparable pair prevalence rises from 37% ($d=4$) to 64% ($d=12$).
2. **Partial Entanglement Optimality**: Effective catalysts strictly avoid the extremes of maximal entanglement or product states. For 2D catalysts, the optimal parameter shifts systematically with dimension:
   - $d = 4$: optimal $p^* \approx 0.65$ (catalysing 2.4% of incomparable pairs)
   - $d = 8$: optimal $p^* \approx 0.68$ (catalysing 4.3% of incomparable pairs)
   - $d = 12$: optimal $p^* \approx 0.70$ (catalysing 4.8% of incomparable pairs)
3. **Simplex Interior in 3D**: Optimal 3-dimensional catalysts lie strictly in the interior of the probability simplex (never on an edge or vertex), achieving higher catalysing ratios (up to 7.26% at $d=12$).

<div class="my-3">
  <a href="{{ '/assets/pdf/catalysis_poster.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" class="btn btn-sm z-depth-0" style="border: 1.5px solid var(--global-theme-color); color: var(--global-theme-color); font-weight: 600; padding: 0.4rem 0.9rem;">
    <i class="fa-solid fa-file-pdf mr-1"></i> View Full Research Poster (PDF)
  </a>
</div>

---

### Code & Repository

- **GitHub Repository**: [TamarNoselidze/Quantum-Catalysis](https://github.com/TamarNoselidze/Quantum-Catalysis) *(Active research repository — work in progress)*

---

### References

1. Jonathan, D., & Plenio, M. B. (1999). *Entanglement-assisted local manipulation of pure quantum states*. Physical Review Letters, 83(17), 3566. [arXiv:quant-ph/9905071](https://arxiv.org/abs/quant-ph/9905071)
2. Lipka-Bartosik, P., Wilming, H., & Ng, N. H. Y. (2023). *Catalysis in quantum information theory*. [arXiv:2306.00798](https://arxiv.org/abs/2306.00798)
3. Bandyopadhyay, S., Halder, S., & Sengupta, R. (2022). *Conditions for local transformations between sets of quantum states*. Physical Review A, 105(6), 062212. [DOI: 10.1103/PhysRevA.105.062212](https://doi.org/10.1103/PhysRevA.105.062212)
4. Cunden, F. D., Facchi, P., Florio, G., & Gramegna, G. (2020). *Volume of the set of LOCC-convertible quantum states*. Journal of Physics A: Mathematical and Theoretical, 53(17), 175303. [DOI: 10.1088/1751-8121/ab7b21](https://doi.org/10.1088/1751-8121/ab7b21)
