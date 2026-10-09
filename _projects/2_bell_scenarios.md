---
layout: page
title: Multipartite Bell Scenarios
description: Computational search for new Bell inequalities in a three-party scenario with partially compatible measurements, using polytope enumeration (PORTA, PANDA), symmetry reduction, and linear programming.
img: assets/img/polytope.jpg
importance: 2
category: Quantum Information
related_publications: false
---

### Overview

Bell inequalities define the supporting hyperplanes (facets) of local correlation polytopes; quantum systems that violate them are certified to be non-classical. This project conducts a computational search for novel, tight Bell inequalities in a tripartite scenario with **partially compatible measurements**: Alice has two dichotomic measurements, Charlie has two, and Bob has three ($B_0, B_1, B_2$) exhibiting a compatibility chain where $B_0$ with $B_1$ and $B_1$ with $B_2$ can be jointly measured, but $B_0$ with $B_2$ cannot.

The behaviour is described by **53 correlators across 8 measurement contexts**, aiming to characterise the local polytope facets and identify inequalities violated more strongly by entangled quantum states than known benchmarks.

Initiated during my research internship at **UNICAMP (Campinas, Brazil)** under the supervision of **[Rafael Rabelo](https://www.ime.unicamp.br/~mfq/people/rabelo/)** (MFQ group), this work continues as an active collaboration between UNICAMP and Sorbonne Université.

- **Stack & Tools**: Python (NumPy, SciPy, CVXPY), Julia, PORTA, PANDA, Linear Programming & LP Duality, Group Theory (orbit classification)
- **Status**: Paper in preparation — *Multipartite Bell Scenarios: High-Dimensional Polytopes and Novel Bell Inequalities* (UNICAMP & Sorbonne University, 2026).

---

### Key Methodology & Results

- **53-Dimensional Polytope Modelling**: Formulated the scenario as a 53-dimensional polytope. The no-signalling set is bounded by 128 positivity inequalities ($8\text{ contexts} \times 16\text{ outcomes}$), all certified as facets.
- **Large-Scale Vertex Enumeration (PORTA)**: Enumerated **107,712 vertices**, comprising 128 local deterministic points and 107,584 non-local (PR-box-like) extremal points, with complete numerical validation.
- **Symmetry Reduction & Orbit Classification**: Constructed the scenario's symmetry group (outcome flips, $A_0 \leftrightarrow A_1$, $C_0 \leftrightarrow C_1$, $B_0 \leftrightarrow B_2$, Alice $\leftrightarrow$ Charlie; order 2,048), reducing the 107,712 vertices to **97 equivalence classes**. Validated using **PANDA** symmetry-aware enumeration in under 3 minutes on 10 cores, and expanded the group to order 8,192 via additional measurement relabellings.
- **Exact Locality Testing via LP**: Designed a linear program to decide classicality. Identified that a correlator formulation erroneously classified ~31% of non-local points due to non-signalling artefacts, resolved it by re-formulating in joint probabilities (returning the exact Elitzur–Popescu–Rohrlich local content with zero errors across 1,500 test points).
- **Tight Bell Inequalities from Dual LP**: For non-local vertices $b$, maximised $s \cdot b$ subject to $s \cdot v \le 1$ for all 128 local vertices $v$. Tested across 400 random non-local vertices; every dual optimum yielded a genuine facet of the local polytope with quantum violations between 3.0 and 4.0.
- **Literature Replication**: Successfully replicated the bipartite foundational results of Temistocles, Rabelo & Terra Cunha (Phys. Rev. A, 2019).

---

### Ongoing & Next Steps

- **Facet Classification**: Executing the dual LP across all 96 non-local classes to eliminate redundant facets and classify distinct inequality orbits by symmetry.
- **Quantum Violation Optimisation**: Applying see-saw optimisation to compute maximal quantum violations for GHZ and W states subjected to white noise.
- **Benchmarking**: Evaluating noise resilience thresholds against standard benchmarks (e.g. Mermin's inequality threshold for noisy GHZ at $\alpha > 1/2$).

---

### Code & Repository

- **GitHub Repository**: [TamarNoselidze/Bell-Inequality-Scenarios](https://github.com/TamarNoselidze/Bell-Inequality-Scenarios) *(Active research repository)*

---

### References

1. Temistocles, T., Rabelo, R., & Cunha, M. T. (2019). *Measurement compatibility in Bell nonlocality tests*. Phys. Rev. A 99, 042120. [arXiv:1806.09232](https://arxiv.org/abs/1806.09232)
2. Cope, T. & Colbeck, R. (2018). *Bell Inequalities From No-Signalling Distributions*. [arXiv:1812.10017](https://arxiv.org/abs/1812.10017)
3. Pironio, S., Bancal, J.-D., & Scarani, V. (2011). *Extremal correlations of the tripartite no-signaling polytope*. [arXiv:1101.2477](https://arxiv.org/abs/1101.2477)
4. Elliott, M. B. (2009). *A linear program for testing local realism*. [arXiv:0905.2950](https://arxiv.org/abs/0905.2950)
