# Kernelized Koopman Representation Geometry Governs Transient Amplification in Neural Dynamical Systems

[![NeurIPS 2026](https://img.shields.io/badge/NeurIPS%202026-NeurReps-4B44CE)](https://openreview.net/forum?id=ZKhFhmuyuq)
[![Proceedings Track](https://img.shields.io/badge/Track-Proceedings-2E8B57)](https://openreview.net/forum?id=ZKhFhmuyuq)
[![OpenReview](https://img.shields.io/badge/OpenReview-ZKhFhmuyuq-8A2BE2)](https://openreview.net/forum?id=ZKhFhmuyuq)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey)](https://creativecommons.org/licenses/by/4.0/)

Official repository accompanying:

## **Kernelized Koopman Representation Geometry Governs Transient Amplification in Neural Dynamical Systems**

**Himanshu Singh**  
Department of Meteorology and Atmospheric Science  
The Pennsylvania State University  
University Park, PA, USA

**Accepted at the NeurIPS 2026 Workshop on Symmetry and Geometry in Neural Representations (NeurReps), Proceedings Track — Sydney, Australia.**

> **TL;DR:** The same neural dynamics can acquire very different finite-time Koopman behavior solely because they are represented in different RKHS geometries.

---

## Overview

This work studies how **kernel representation geometry** shapes the finite-time behavior of Kernel Extended Dynamic Mode Decomposition (KEDMD) surrogates of the Koopman operator in neural dynamical systems.

The central observation is simple but important:

> **Spectrally similar Koopman surrogates can exhibit radically different finite-time amplification because the kernel changes the geometry in which the dynamics are represented.**

Across three neural dynamical systems and four standard kernels, we analyze this effect using:

- finite-time operator growth,
- kernel-induced RKHS geometry,
- pseudospectra,
- the Kreiss constant,
- and Pareto-style dominance diagnostics.

The experiments use the **same underlying neural dynamics and snapshot data** while changing only the kernel representation. This isolates representation geometry as the source of the observed hierarchy.

---

# Figure Gallery

The figures below are ordered by the main conceptual progression of the paper:

1. **Kernel geometry**
2. **Transient amplification**
3. **Pseudospectral sensitivity**
4. **Pareto / dominance diagnostics**

---

## 1. Kernel Representation Geometry

The four kernels induce visibly different local geometries around the same reference state. These differences propagate into the Gram matrix, the normalized KEDMD operator, and ultimately the finite-time amplification behavior.

<p align="center">
  <img src="figures/kernel-profiles/kernel_geometry_gallery_normals.png" width="900">
</p>

**Kernels studied**

- Laplace
- Matérn-3/2
- Rational Quadratic
- Gaussian RBF

A recurring empirical hierarchy across the paper is

**Laplace < Matérn-3/2 < Rational Quadratic < Gaussian RBF**

in transient amplification and related pseudospectral diagnostics.

---

## 2. Transient Amplification in Neural Dynamical Systems

We compare the finite-time amplification of the underlying neural dynamics with the growth produced by their kernel Koopman representations.

### Linearized Excitatory–Inhibitory Population Model

<p align="center">
  <img src="figures/LINEAR-EI/EI_exact_vs_KEDMD_transient_polished.png" width="900">
</p>

[PDF version](figures/LINEAR-EI/EI_exact_vs_KEDMD_transient_polished.pdf)

Even for a stable linearized E–I system with modest physical amplification, the learned kernel representations can generate substantially larger transient growth.

### Wilson–Cowan Population Dynamics

<p align="center">
  <img src="figures/W-C/WC_physical_vs_KEDMD_transient_polished.png" width="900">
</p>

[PDF version](figures/W-C/WC_physical_vs_KEDMD_transient_polished.pdf)

For the nonlinear Wilson–Cowan system, the physical response remains comparatively modest while the KEDMD representation-space growth separates strongly across kernels.

### FitzHugh–Nagumo Excitable Dynamics

<p align="center">
  <img src="figures/FH-N/FHN_physical_vs_KEDMD_transient_polished.png" width="900">
</p>

[PDF version](figures/FH-N/FHN_physical_vs_KEDMD_transient_polished.pdf)

The FitzHugh–Nagumo experiment shows the same representation-dependent ordering in a reduced excitable-neuron model.

---

## 3. Pseudospectral Diagnostics

Eigenvalues alone do not reveal the full finite-time behavior of a non-normal surrogate. We therefore analyze the pseudospectra of the normalized KEDMD operators.

### Linearized E–I

<p align="center">
  <img src="figures/pseudo-spectra/EI_KEDMD_pseudospectra_clean.png" width="760">
</p>

[PDF version](figures/pseudo-spectra/EI_KEDMD_pseudospectra_clean.pdf)

### Wilson–Cowan

<p align="center">
  <img src="figures/pseudo-spectra/WC_KEDMD_pseudospectra_clean.png" width="760">
</p>

[PDF version](figures/pseudo-spectra/WC_KEDMD_pseudospectra_clean.pdf)

### FitzHugh–Nagumo

<p align="center">
  <img src="figures/pseudo-spectra/FHN_KEDMD_pseudospectra_clean.png" width="760">
</p>

[PDF version](figures/pseudo-spectra/FHN_KEDMD_pseudospectra_clean.pdf)

These plots make visible the resolvent sensitivity that is hidden by the eigenvalue cloud alone. The associated Kreiss diagnostics provide a scalar summary of the same finite-time instability mechanism.

---

## 4. Pareto / Dominance Diagnostics

The dominance analysis compares kernels through multiple diagnostics simultaneously rather than reducing representation quality to a single scalar.

### Linearized E–I

<p align="center">
  <img src="figures/dominance/EI_pareto_dominance_neurreps.png" width="760">
</p>

[PDF version](figures/dominance/EI_pareto_dominance_neurreps.pdf)

### Wilson–Cowan

<p align="center">
  <img src="figures/dominance/WC_pareto_dominance_neurreps.png" width="760">
</p>

[PDF version](figures/dominance/WC_pareto_dominance_neurreps.pdf)

### FitzHugh–Nagumo

<p align="center">
  <img src="figures/dominance/FHN_pareto_dominance_neurreps.png" width="760">
</p>

[PDF version](figures/dominance/FHN_pareto_dominance_neurreps.pdf)

The Pareto analysis reinforces the main message: the observed kernel hierarchy is not an artifact of a single diagnostic, but persists across several complementary measures of representation-space distortion and finite-time growth.

---

## Main Takeaways

- **Kernel Koopman surrogates are not representation neutral.**
- The same neural dynamics can exhibit very different finite-time behavior after being represented in different RKHS geometries.
- **Spectral radius alone is insufficient** to diagnose finite-time reliability.
- Pseudospectra and Kreiss-type diagnostics reveal amplification mechanisms that are invisible from eigenvalues alone.
- Across the three neural systems studied here, the kernel hierarchy is remarkably consistent: **Laplace < Matérn-3/2 < Rational Quadratic < Gaussian RBF**.
- The results motivate representation-aware diagnostics before kernel Koopman models are used for prediction or perturbation-response analysis.

---

## Neural Dynamical Systems

The paper studies three canonical low-dimensional neural dynamical regimes:

- a **linearized excitatory–inhibitory population model**,
- the nonlinear **Wilson–Cowan population model**,
- and the **FitzHugh–Nagumo** model of neuronal excitability.

The repository is organized so that each system has its own transient-growth, pseudospectral, regularization-sensitivity, and diagnostic outputs.

---

## Reviewer Highlights

The NeurReps reviews emphasized both the mathematical consistency of the framework and the practical importance of the central message.

> “The reviewers agree the mathematics and evaluation appear sound.”

— Area Chair meta-review

> “The full proof chain ... holds up.”

— Reviewer RkqB

> “The central finding is genuinely useful on its own.”

— Reviewer RkqB

> “Spectral radius ≈ 1 can hide large finite-time amplification, and this is representation-dependent.”

— Reviewer DDTq

The reviews also highlighted the robustness checks in the appendices, including grid convergence, regularization sensitivity, and Pareto/mechanistic analysis.

### Reviewer-identified limitations

The reviewers also pointed to important directions for future work:

- understanding whether a kernel-level distance, smoothness, or bandwidth criterion can predict the observed hierarchy without testing every kernel;
- separating kernel-scale effects from the intrinsic representation-geometry mechanism;
- extending beyond low-dimensional hand-specified neural systems toward learned representations or neural data;
- and demonstrating downstream consequences in forecasting, control, or perturbation-response tasks.

These are natural next steps beyond the present paper.

---

## Repository Structure

```text
KEDMD_TA_SPIKES/
├── figures/
│   ├── LINEAR-EI/
│   │   ├── EI_exact_vs_KEDMD_transient_polished.{png,pdf}
│   │   └── ...
│   ├── W-C/
│   │   ├── WC_physical_vs_KEDMD_transient_polished.{png,pdf}
│   │   └── ...
│   ├── FH-N/
│   │   ├── FHN_physical_vs_KEDMD_transient_polished.{png,pdf}
│   │   └── ...
│   ├── kernel-profiles/
│   │   └── kernel_geometry_gallery_normals.{png,pdf}
│   ├── pseudo-spectra/
│   │   ├── EI_KEDMD_pseudospectra_clean.{png,pdf}
│   │   ├── WC_KEDMD_pseudospectra_clean.{png,pdf}
│   │   └── FHN_KEDMD_pseudospectra_clean.{png,pdf}
│   └── dominance/
│       ├── EI_pareto_dominance_neurreps.{png,pdf}
│       ├── WC_pareto_dominance_neurreps.{png,pdf}
│       └── FHN_pareto_dominance_neurreps.{png,pdf}
└── ...
```

---

## Paper and OpenReview

**OpenReview:**  
https://openreview.net/forum?id=ZKhFhmuyuq

The paper was accepted to the **NeurIPS 2026 Workshop on Symmetry and Geometry in Neural Representations (NeurReps), Proceedings Track**.

---

## Citation

If you use this work, please cite:

```bibtex
@inproceedings{singh2026kernelized,
  title     = {Kernelized Koopman Representation Geometry Governs Transient Amplification in Neural Dynamical Systems},
  author    = {Singh, Himanshu},
  booktitle = {NeurIPS 2026 Workshop on Symmetry and Geometry in Neural Representations (NeurReps), Proceedings Track},
  year      = {2026},
  url       = {https://openreview.net/forum?id=ZKhFhmuyuq}
}
```

---

## License

The OpenReview submission is available under **CC BY 4.0**. Please cite the paper when using material from this repository.

---

## Contact

**Himanshu Singh**  
Department of Meteorology and Atmospheric Science  
The Pennsylvania State University
