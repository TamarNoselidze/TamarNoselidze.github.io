---
layout: page
title: Adversarial Examples Against Vision Transformers
description: Bachelor's thesis evaluating white-box attacks, universal G-Patches, novel Mini-Patch strategies, and cross-architecture transferability on HPC clusters.
img: assets/img/thesis_poster.jpg
importance: 4
category: Machine Learning & AI
related_publications: false
---

### Overview

While deep neural networks have achieved remarkable success in computer vision, their vulnerability to adversarial examples exposes critical security risks. This research comprises my **Bachelor's Thesis at Charles University** (Prague), investigating the adversarial robustness of **Vision Transformers (ViTs)** in comparison to traditional **Convolutional Neural Networks (CNNs)** under white-box gradient attacks and localised physical-world patch perturbations.

- **Institution**: Charles University, Faculty of Mathematics and Physics
- **Department**: Department of Theoretical Computer Science and Mathematical Logic
- **Thesis Supervisor**: [Doc. Mgr. Martin Pilát, Ph.D.](https://orcid.org/0000-0002-3714-3860)
- **Defended**: June 2025

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-6 text-center mb-3 mb-sm-0">
    <a href="{{ '/assets/img/thesis_defense.jpg' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/thesis_defense.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Tamar Noselidze at Bachelor's Thesis Defense" style="width: 100%; max-height: 440px; object-fit: cover; object-position: top; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Bachelor's thesis poster defense at Charles University (Faculty of Mathematics and Physics, Prague).
    </div>
  </div>
  <div class="col-sm-6 text-center">
    <a href="{{ '/assets/img/thesis_book.jpg' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/thesis_book.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Hardcover Bachelor's Thesis Manuscript" style="width: 100%; max-height: 440px; object-fit: cover; object-position: center; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Hardcover thesis manuscript: <em>Adversarial Examples Against Vision Transformers</em>.
    </div>
  </div>
</div>

---

### Core Experimental Frameworks

All experiments were benchmarked on the **ImageNetV2** dataset (1,000 classes) across two primary architectural families:
- **Vision Transformers**: ViT-B/16, ViT-B/32, ViT-L/16, and Swin-B.
- **Convolutional Networks**: ResNet50, ResNet152, and VGG16-BN.

#### 1. Baseline Gradient Attacks (CleverHans)
Evaluated standard white-box adversarial attacks across both families in targeted and untargeted settings:
- **Fast Gradient Sign Method (FGSM)**: ViTs exhibited higher vulnerability (~70% Attack Success Rate, ASR) compared to CNNs (~55% ASR).
- **Projected Gradient Descent (PGD)**: Demonstrated high effectiveness across all models, consistently achieving over **90% ASR**.

#### 2. Universal Generative Patches (G-Patch)
Implemented and expanded generative patch attacks based on GAN architectures (Shao, 2024), deploying universal patches at randomised locations per image:
- Trained generators for localised **64×64** (~8% image area) and **80×80** (~13% area) patches.
- Replicated state-of-the-art results, achieving **~75–90% ASR on ViTs** and **~80–95% ASR on CNNs**.

#### 3. Novel Mini-Patch Attacks
Designed a novel multi-patch framework training generators to create smaller patches distributed across several image locations (covering the same ~8% total area):
- **Random Placement**: Deploys smaller $16\times16$ or $32\times32$ patches randomly across 4 to 8 locations.
- **Corner-Point Targeting**: Exploits internal ViT tokenisation by aligning patches at the intersection of token grid corners, corrupting adjacent token representations simultaneously.
- **Token-Replacement**: Substitutes entire ViT patch tokens directly with adversarial inputs.
- **Key Finding**: The **corner-point** approach was the most consistent and effective, achieving **60–70% ASR on ViTs** and demonstrating that structured geometric alignment with token boundaries creates potent vulnerabilities.

#### 4. Transferability & Mixed Ensembles
- **Intra-family transfer** (e.g. ViT $\to$ ViT) proved significantly stronger than inter-family transfer (ViT $\to$ CNN).
- Training generators against **mixed-architecture ensembles** (combining ViTs and CNNs) substantially enhanced the generalisability and transferability of adversarial patches across unseen architectures.

---

### Supercomputing & HPC Infrastructure

To train hundreds of generative patch models and execute extensive cross-evaluation matrices, we engineered parallelised PyTorch pipelines on the Czech National Grid Infrastructure (**MetaCentrum**):
- **Compute Volume**: Consumed over **500 GPU days** across distributed cluster nodes.
- **Experiment Tracking**: Integrated automated logging with **Weights & Biases (W&B)** to monitor per-batch ASR, adversarial loss trajectories, and visual artifact quality.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/Thesis](https://github.com/TamarNoselidze/Thesis) (includes pre-trained generators and CleverHans / Patch pipelines)
- **Thesis Manuscript**: [Charles University Digital Repository](https://dspace.cuni.cz/handle/20.500.11956/200886)
- **Full Text PDF**: [Download Thesis PDF (6.4 MB)]({{ '/assets/pdf/thesis_final.pdf' | relative_url }})

---

### References

1. Noselidze, T. (2025). *Adversarial Examples Against Vision Transformers*. Bachelor's Thesis, Charles University Digital Repository. [dspace.cuni.cz/handle/20.500.11956/200886](https://dspace.cuni.cz/handle/20.500.11956/200886)
2. Shao, F. (2024). *Designing Physical-World Universal Attacks on Vision Transformers*. [OpenReview](https://openreview.net/forum?id=DqBPk7887N).
