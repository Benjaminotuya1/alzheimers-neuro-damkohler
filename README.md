# Decomposing Trans-Compartmental Plasma-to-CSF Tau Partitioning Across the Alzheimer's Continuum (ADNI)

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![ADNI](https://img.shields.io/badge/Data-ADNI%20LONI-green.svg)](https://adni.loni.usc.edu/)

Official reproducible analysis notebook, summary tables, and publication figures for:

> **Otuya, B. G. (2026).** *Decomposing Trans-Compartmental Plasma-to-CSF Tau Partitioning Across the Alzheimer’s Continuum: Disentangling Global CSF Volumetric Dilution from Amyloid-Driven Kinetic Escalation and Neurovascular Mediation.*

## Key Verified Findings
* **Continuum Specificity ($N=409$):** $Da_{\text{Tau}}$ cleanly separates biologically confirmed $\text{MCI due to AD (A}\beta+)$ from non-AD $\text{MCI (A}\beta-)$ ($p_{\text{Holm}} = 1.05 \times 10^{-9}$), with non-AD MCI statistically indistinguishable from healthy $\text{CN A}\beta-$ controls ($p_{\text{Holm}} = 0.881$).
* **Global CSF Volumetric Dilution Decomposition:** Controlling simultaneously for Amyloid-PET, Tau-PET, age, and sex ($N=278$), standalone plasma p-tau217 loses significance for MRI ventricular capacitance ($p = 0.440$), whereas $\Delta Z_{\text{CN}}$ ($t=+6.30, p=1.18 \times 10^{-9}$) and $Da_{\text{Tau}}$ ($t=+4.80, p=2.65 \times 10^{-6}$) persist—yet adding `ln(CSF Aβ40)` as a global CSF dilution control completely attenuates both ratios ($p=0.592$ and $p=0.934$), proving that unnormalized plasma-to-CSF ratios import global CSF volumetric dilution rather than active trans-barrier efflux.
* **Joint Parallel Statistical Mediation (1,000x Bootstrap):** Co-modeling plasma GFAP and MRI Vent/ICV% simultaneously shows a significant **40.1%** combined indirect pathway for $Da_{\text{Tau}}$ ($N=298$, 95% CI $[+0.058, +0.226]$; GFAP unique $= 29.7\%$) versus a non-significant **17.3%** for standalone plasma p-tau217 ($N=299$, 95% CI $[-0.009, +0.172]$).
* **Multi-Era Replication & Survival:** All core associations replicate across independent Legacy (`ADNI1/GO/2`, $N=136$) and Modern 3T (`ADNI3`, $N=275$) eras. Standalone plasma p-tau217 remains the stronger raw survival predictor ($HR=2.30, C=0.801$), while $Da_{\text{Tau}}$ shows AD-specific prediction ($HR=1.93, p=3.88 \times 10^{-4}$, 4-year AUC $=0.901$, Schoenfeld PH $p=0.700$).

## Data Availability (ADNI DUA Compliance)
Raw patient-level ADNI CSV files are excluded per ADNI DUA. Apply for access at [adni.loni.usc.edu](https://adni.loni.usc.edu/) and run `ADNI_NeuroDamkohler_Continuum_Analysis.ipynb`.
