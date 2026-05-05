# Imagery Dataset for Remaining Useful Life Estimation of Synthetic Fibre Ropes

**Authors:** Anju Rani · Daniel Ortiz-Arroyo · Petar Durdevic  
**Affiliation:** Department of Energy, Aalborg University, Esbjerg, Denmark  
**Dataset:** [Kaggle — DOI: 10.34740/kaggle/dsv/16105762](https://doi.org/10.34740/kaggle/dsv/16105762)

---

## Abstract

Remaining useful life (RUL) estimation of synthetic fibre ropes (SFRs) is critical for safe operation in offshore-crane, wind turbine installation, and heavy-load handling applications, where rope failure can result in catastrophic safety incidents and costly downtime. Despite growing research interest in data-driven condition monitoring, there is no publicly available image dataset that captures the complete degradation lifecycle of SFRs under controlled cyclic fatigue loading. To address this gap, we present a novel image dataset comprising approximately 34,700 high-resolution images of eleven Dyneema SK75/78 high-modulus polyethylene (HMPE) rope samples subjected to cyclic fatigue on a sheave-bend test stand at seven distinct axial load levels ranging from 60 kN to 280 kN. Ropes were loaded until mechanical failure, with fatigue lifetimes ranging from 695 cycles to 8,340 cycles. After every fixed number of sheave cycles (an inspection burst), ten images were captured at different cross-sectional positions along the rope, providing spatially representative sampling of surface degradation throughout the rope's entire service life. The images are annotated with the corresponding elapsed cycle count, enabling direct computation of RUL for any image in the sequence.

---

## Dataset Summary

| Rope   | Load    | Images | Cycles/Burst | Total Cycles |
|--------|---------|--------|--------------|--------------|
| Rope1  | 100 kN  | 3,746  | 20           | 7,492        |
| Rope2  | 60 kN   | 5,175  | 15           | 7,762        |
| Rope3  | 200 kN  | 2,100  | 10           | 2,100        |
| Rope4  | 150 kN  | 3,579  | 10           | 3,579        |
| Rope5  | 150 kN  | 3,547  | 10           | 3,547        |
| Rope6  | 100 kN  | 1,710  | 10           | 1,710        |
| Rope7  | 60 kN   | 8,340  | 10           | 8,340        |
| Rope8  | 250 kN  | 695    | 10           | 695          |
| Rope9  | 150 kN  | 3,638  | 10           | 3,638        |
| Rope10 | 280 kN  | 722    | 10           | 722          |
| Rope11 | 220 kN  | 1,415  | 10           | 1,415        |
| **Total** | **60–280 kN** | **~34,700** | **10–20** | — |

---
![Synthetic Fibre Rope Lifecycle](Image/RUL.pdf)

## RUL Labelling

Each image filename encodes the elapsed cycle count at the time of capture. The RUL for any image is computed as:

$$\text{RUL} = N_{\text{failure}} - N_{\text{elapsed}}$$

where $N_{\text{failure}}$ is the total sheave cycle count at mechanical failure for the rope specimen, and $N_{\text{elapsed}}$ is the cycle count at which the image was captured. This labelling scheme supports both continuous RUL regression and discrete life-stage classification (early life: RUL > 60%; mid life: 30–60%; late life: < 30%).

---
![Experimental Setup](Image/setup.pdf)

## Experimental Setup

Eleven Dyneema SK75/78 HMPE rope specimens (8 mm nominal diameter, 12-strand braided) were subjected to cyclic fatigue on a sheave-bend test stand. An axial tension load was applied while the sheave rotated back and forth, bending the rope over the pulley. After every fixed number of sheave cycles, rotation stopped and ten images were captured at different cross-sectional positions along the rope length. Testing continued until each rope reached complete mechanical failure.

| Parameter | Details |
|-----------|---------|
| Rope | Dyneema SK75/78, 8 mm, 12-strand braided |
| Load levels | 60–280 kN (7 levels) |
| Rope speed | 60 m/min |
| LCS length | 1000 mm |
| Cycles per burst | 10–20 (load-dependent) |
| Camera | Basler acA2000 GigE + C11-5020-12M-P lens |
| Resolution | 1920 × 1200 pixels |
| Image format | PNG (lossless) |
| Trigger | Software-triggered via PLC handshake; no fixed frame rate |
| Illumination | Aputure AL-MC RGBWW LED (strobe-synchronised) |
| Acquisition system | NVIDIA Jetson Nano P3450 · pypylon / OpenCV / pylogix |

---
## Repository Structure

```
.
├── main.pdf               # manuscript
├── references.bib         # BibTeX references
├── Image/
│   ├── RUL.pdf            # Figure 1: Lifecycle image strip (healthy to failure)
│   └── setup.pdf          # Figure 2: Sheave-bend test stand setup
└── README.md
```
---

## Related Work

This dataset complements our previously published defect classification dataset:

> Rani, A., Ortiz-Arroyo, D., & Durdevic, P. (2023). *Imagery dataset for condition monitoring of synthetic fibre ropes.* arXiv:2309.17058. https://arxiv.org/abs/2309.17058

> Rani, A., Ortiz-Arroyo, D., & Durdevic, P. (2024). *Defect detection in synthetic fibre ropes using Detectron2 framework.* Applied Ocean Research, 150, 104109. https://doi.org/10.1016/j.oceaneng.2024.104109

---

## Citation

If you use this dataset or paper, please cite:

```bibtex
@misc{rani2025rul,
    title        = {Imagery Dataset for Remaining Useful Life Estimation of Synthetic Fibre Ropes},
    author       = {Rani, Anju and Ortiz-Arroyo, Daniel and Durdevic, Petar},
    year         = {2025},
    archivePrefix= {arXiv},
    primaryClass = {cs.CV}
}
```

---

## Acknowledgement

This research was supported by Aalborg University, Liftra ApS, and Dynamica Ropes ApS in Denmark under the EUDP program through project grant number **64021-2048**.
