---
layout: page
title: Multipartite Bell Scenarios
description: Polytope facet enumeration and vertex annotation (PORTA, PANDA) to discover novel Bell inequalities in multipartite quantum systems.
importance: 2
category: Quantum Information
related_publications: true
---

### Overview

Bell inequalities define the supporting hyperplanes (facets) of local correlation polytopes. In multipartite scenarios with multiple parties, measurement settings, and outcomes, characterising the boundary between classical local realism and quantum correlations leads to combinatorial explosion and severe geometric complexity.

This research was initiated during my **M1 research internship at UNICAMP (Campinas, Brazil)** under the supervision of **[Rafael Rabelo](https://www.ime.unicamp.br/~mfq/people/rabelo/)** (Mathematical Foundations of Quantum Theory group), and continues as an ongoing collaboration between UNICAMP and Sorbonne Université.

---

### Research Highlights & Methodology

- **Polytope Modelling & Facet Enumeration**: Constructing high-dimensional correlation polytopes and deploying combinatorial algorithms (**PORTA**, **PANDA**, and **RANDA**) to carry out vertex annotation and facet enumeration for multi-qubit and multi-setting Bell scenarios.
- **Convex Optimisation & SDP Relaxations**: Implementing linear programming and semidefinite programming (SDP) relaxations using **CVXPY** and specialized interior-point solvers to model high-dimensional quantum correlations.
- **See-Saw Optimisation**: Applying iterative see-saw optimisation algorithms to alternate between measurement operators and quantum states, maximising quantum violations of candidate Bell inequalities.
- **Status**: Paper in preparation — *Multipartite Bell Scenarios: High-Dimensional Polytopes and Novel Bell Inequalities* (UNICAMP & Sorbonne University, 2026).

---

### Code & Repository

- **GitHub Repository**: [TamarNoselidze/Bell-Inequality-Scenarios](https://github.com/TamarNoselidze/Bell-Inequality-Scenarios) *(Active research repository — work in progress)*

---

### Key References

1. Temistocles, T., Rabelo, R., & Cunha, M. T. (2018). *Measurement compatibility in Bell nonlocality tests*. [arXiv:1806.09232](https://arxiv.org/abs/1806.09232)
2. Cope, T. & Colbeck, R. (2018). *Bell Inequalities From No-Signalling Distributions*. [arXiv:1812.10017](https://arxiv.org/abs/1812.10017)
3. Pironio, S., Bancal, J.-D., & Scarani, V. (2011). *Extremal correlations of the tripartite no-signaling polytope*. [arXiv:1101.2477](https://arxiv.org/abs/1101.2477)
4. Elliott, M. B. (2009). *A linear program for testing local realism*. [arXiv:0905.2950](https://arxiv.org/abs/0905.2950)
