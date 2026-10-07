---
layout: page
title: Quantum Nonlocality & SVMs
description: Machine learning classification of Local Hidden States (LHS) and quantum steerability boundaries using a 9D Fano representation.
img: assets/img/group_pic.jpg
importance: 1
category: Quantum Information
related_publications: false
---

### Overview

Quantum steerability represents an asymmetric quantum correlation situated in the hierarchy between entanglement and Bell nonlocality:

$$\text{Bell Nonlocal} \subset \text{Steerable (Non-LHS)} \subset \text{Entangled}$$

A bipartite state is unsteerable if and only if it admits a **Local Hidden State (LHS)** model. Analytically certifying the geometric boundary between steerable and unsteerable states is traditionally a computationally demanding task relying on Linear Programming (LP) algorithms with spherical polytope coverings (Nguyen et al., 2019; Porto et al., 2025).

Instead of deploying deep neural networks that operate as "black boxes" on measurement statistics, this project introduces **Support Vector Machines (SVMs) trained directly on the density matrices of two-qubit systems** to provide an efficient, geometrically interpretable classifier.

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-10 text-center">
    <img src="{{ '/assets/img/group_pic.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="MQC team at UNICAMP" style="width: 100%; max-height: 480px; object-fit: cover;">
    <div class="caption text-muted mt-2" style="font-size: 0.9rem;">
      Research presentation and collaboration with the Mathematical Foundations of Quantum Theory (MFQ) group and visiting speakers at UNICAMP (Campinas, Brazil).
    </div>
  </div>
</div>

---

### Key Methodology & Contributions

#### 1. Invariant 9D Fano Feature Representation
Mapping a complex $4 \times 4$ density matrix $\rho$ directly to machine learning vectors by flattening yields 32 real numbers (16 real, 16 imaginary). To achieve computational efficiency while preserving physical invariance under Local Unitary transformations, we expanded the state using the **Fano decomposition**:

$$\rho = \frac{1}{4} \left( I \otimes I + \mathbf{a} \cdot \boldsymbol{\sigma} \otimes I + I \otimes \mathbf{b} \cdot \boldsymbol{\sigma} + \sum_{i,j=1}^3 T_{ij} \, \sigma_i \otimes \sigma_j \right)$$

Applying Singular Value Decomposition (SVD) to the real $3 \times 3$ correlation matrix $T$ yields three singular values $(s_1, s_2, s_3)$. Combining these with Alice and Bob's local Bloch vectors $\mathbf{a}$ and $\mathbf{b}$ produces a compact **9-dimensional feature vector**:

$$\mathbf{x} = [a_1, a_2, a_3, \, b_1, b_2, b_3, \, s_1, s_2, s_3]^T$$

Because quantum steering is inherently asymmetric from Alice to Bob, the inclusion of local Bloch vectors alongside correlation singular values proved essential for capturing steerability directionality.

#### 2. Targeting the Geometric Boundary
In uniformly random Hilbert-Schmidt sampling, roughly 70% of generated entangled states are unsteerable, creating substantial class imbalance and leaving the critical boundary region unpopulated. 

To overcome this, we constructed a **boundary-targeted dataset of 10,000 states** (5,000 LHS and 5,000 non-LHS) generated using Julia (`MosekTools.jl`, `LinearAlgebra`, `HDF5.jl`). We deployed the depolarising map:

$$\rho^* = \eta \rho + (1 - \eta) \left( I_2 \otimes \mathrm{Tr}_A(\rho) \right)$$

By selecting states and tuning $\eta = v_{\text{lower}}$ and skewed visibility sampling, we actively pushed 2,000 states directly against the steerability boundary.

#### 3. Analytical Nonlocality Formula Extraction
Using a polynomial kernel of degree $d=2$, we trained the SVM to separate the classes in feature space. Extracting the trained weights yielded an **explicit, closed-form algebraic nonlocality formula** $f(\mathbf{a}, \mathbf{b}, \mathbf{s})$:

- **Asymmetry Learned**: Alice's quadratic terms ($a_i^2$) are strictly positive ($\approx +3.0$, pulling toward the unsteerable LHS region), while Bob's quadratic terms ($b_i^2$) are strictly negative ($\approx -5.7$, pulling toward steerability).
- **Coupled Correlations**: The cross-terms of the correlation singular values ($-10.05 s_1 s_2$ and $-9.53 s_1 s_3$) emerged as the dominant weights, proving that invariant inter-qubit correlations are the primary drivers of quantum nonlocality.

#### 4. Werner State Verification
Benchmarked against the family of Werner states $\rho_W(p) = p |\psi^-\rangle\langle\psi^-| + \frac{1-p}{4} I$, where the theoretical LHS threshold is known exactly at $p = 0.5$:
- Baseline model threshold: $p \approx 0.482$
- **Targeted boundary model threshold: $p \approx 0.508$**, confirming that boundary training accurately captures the physical geometry of steerability.

---

### Code & Data

- **GitHub Repository**: [TamarNoselidze/SVM-Nonlocality-Boundary](https://github.com/TamarNoselidze/SVM-Nonlocality-Boundary)
- **Pipelines**: Julia dataset generation (`CAPIBARA.jl`, `MosekTools.jl`) & Python Scikit-Learn training pipelines.

---

### References

1. Canabarro, A., Brito, S., & Chaves, R. (2019). *Machine Learning Nonlocal Correlations*. Physical Review Letters, 122(20), 200401. [DOI: 10.1103/PhysRevLett.122.200401](https://doi.org/10.1103/PhysRevLett.122.200401)
2. Fano, U. (1983). *Pairs of two-level systems*. Reviews of Modern Physics, 55(4), 855–874. [DOI: 10.1103/RevModPhys.55.855](https://doi.org/10.1103/RevModPhys.55.855)
3. Nguyen, H. C., Nguyen, H.-V., & Gühne, O. (2019). *Geometry of Einstein-Podolsky-Rosen Correlations*. Physical Review Letters, 122(24), 240401. [DOI: 10.1103/PhysRevLett.122.240401](https://doi.org/10.1103/PhysRevLett.122.240401)
4. Peres, A. (1996). *Separability Criterion for Density Matrices*. Physical Review Letters, 77(8), 1413–1415. [DOI: 10.1103/PhysRevLett.77.1413](https://doi.org/10.1103/PhysRevLett.77.1413)
5. Porto, L. E. A. et al. (2025). *Measurement incompatibility and quantum steering via linear programming*. [arXiv:2506.03045](https://arxiv.org/abs/2506.03045)
6. Selzam, N. von & Marquardt, F. (2025). *Discovering Local Hidden-Variable Models for Arbitrary Multipartite Entangled States and Arbitrary Measurements*. PRX Quantum, 6(2), 020317. [DOI: 10.1103/PRXQuantum.6.020317](https://doi.org/10.1103/PRXQuantum.6.020317)
