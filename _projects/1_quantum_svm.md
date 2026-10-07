---
layout: page
title: Quantum Nonlocality & SVMs
description: Machine learning classification of Local Hidden States (LHS) and quantum steerability boundaries using a 9D Fano representation.
img: 
importance: 1
category: Quantum Information
related_publications: true
---

### Overview

In quantum information theory, characterizing the boundary between local and nonlocal correlations—specifically **steerability** and **Local Hidden State (LHS)** models—is traditionally a computationally intensive task relying on semidefinite programs (SDPs) and linear programming (LP).

In this project conducted between **UNICAMP & Sorbonne University**, we developed a novel machine learning pipeline using **Support Vector Machines (SVMs)** to classify quantum states and extract analytical approximations for their nonlocality boundaries.

### Key Contributions & Methodology

- **Fano Feature Representation**: Compressed 2-qubit density matrices into an invariant 9-dimensional Fano parameter representation, dramatically reducing feature space complexity while preserving geometric and entanglement properties.
- **Convex Optimization with MOSEK**: Overcame classical linear programming bottlenecks by formulating efficient convex optimization pipelines in Python using MOSEK and CVXPY.
- **Algebraic Boundary Extraction**: Successfully fitted high-accuracy SVM decision hyperplanes and extracted a novel algebraic formula approximating the quantum steerability boundary.
- **Presentation**: Presented finalized findings and analytical derivations to the physics department at the University of Campinas (UNICAMP).

### Code & Repository

Check out the code and data on GitHub:
- Repository: [TamarNoselidze/SVM-Nonlocality-Boundary](https://github.com/TamarNoselidze/SVM-Nonlocality-Boundary)
