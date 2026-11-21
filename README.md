# Trans-Compartmental Tau–Amyloid Partitioning and the Neuro-Damköhler Index in Alzheimer's Disease (ADNI)

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![ADNI](https://img.shields.io/badge/Data-ADNI%20LONI-green.svg)](https://adni.loni.usc.edu/)

Official reproducible analysis code, summary tables, and publication figures for:

> **Otuya, B. G. (2026).** *Trans-Compartmental Tau–Amyloid Partitioning and the Neuro-Damköhler Index: A PET-Independent Axis of Macro-CSF Capacitance, Microglial Containment, and Cognitive Decline Across the Alzheimer’s Continuum.*

---

## Overview

Standalone blood biomarkers such as plasma p-tau217 accurately detect cerebral amyloidosis, yet they predominantly reflect static parenchymal plaque and tangle load. By coupling contemporaneous central cerebrospinal fluid (CSF; Roche Elecsys) and peripheral plasma (Fujirebio Lumipulse / Quanterix Simoa) draws across **$N = 411$ biologically stratified ADNI participants**, this study formulates:

1. **Neuro-Damköhler Index ($Da_{\text{Tau}}$):**
   $$Da_{\text{Tau}} = \ln\left(\frac{\text{Plasma p-tau217}}{\text{CSF p-tau181}}\right)$$
2. **Control-Anchored Kinetic Divergence ($\Delta Z_{\text{CN}}$):**
   $$\Delta Z_{\text{CN}} = Z_{\text{CN}}(\ln \text{Plasma p-tau217}) - Z_{\text{CN}}(\ln \text{CSF p-tau181})$$
3. **Identical-Analyte Partition Ratios ($\kappa_{A\beta40}$, $\kappa_{A\beta42}$)** and **Selectivity Index ($\Psi$)**.

### Key Verified Findings
* **Cross-Molecule Physical Convergence:** $\Delta Z_{\text{CN}}$ converges strongly with identical-analyte housekeeping $\kappa_{A\beta40}$ ($\rho = +0.680,\ p = 5.26 \times 10^{-41}$, $N=292$), whereas standalone plasma p-tau217 shows weak coupling ($\rho = +0.155$).
* **PET-Independent Macro-CSF Capacitance:** Controlling simultaneously for Amyloid-PET (`CENTILOIDS`), Tau-PET (`META_TEMPORAL_SUVR`), age, and sex ($N=278$), standalone plasma p-tau217 loses all association with MRI ventricular expansion ($p = 0.440$), while $\Delta Z_{\text{CN}}$ ($t = +6.30, p = 1.18 \times 10^{-9}$), $\kappa_{A\beta40}$ ($p = 1.02 \times 10^{-8}$), and $Da_{\text{Tau}}$ ($p = 2.65 \times 10^{-6}$) remain highly significant—including within amyloid-negative healthy controls (`CN Aβ−`, $p = 9.17 \times 10^{-5}$).
* **Microglial Containment & Astrocytic Mediation:** Central `CSF sTREM2` strongly tracks $\Delta Z_{\text{CN}}$ ($\rho = -0.488, p = 2.68 \times 10^{-7}$) but shows zero correlation with standalone plasma p-tau217 ($p = 0.503$). Plasma `GFAP` ($28.5\%$) and MRI `Ventricles/ICV%` ($12.2\%$) jointly mediate $40.7\%$ of $Da_{\text{Tau}}$-associated longitudinal cognitive decline velocity ($\Delta\text{ADAS13}/\text{year}$).
* **Multi-Era Replication & AD-Specific Survival:** All core physical associations replicate across independent Legacy (`ADNI1/GO/2`, $N=136$) and Modern 3T (`ADNI3`, $N=275$) study eras. Higher $Da_{\text{Tau}}$ predicts dementia conversion specifically in biologically confirmed $\text{MCI due to AD (A}\beta+)$ ($HR = 1.93, p = 3.88 \times 10^{-4}$, 4-year AUC $= 0.901$), surviving CKD-EPI 2021 `eGFR` adjustment.

---

## Repository Structure

```text
├── ADNI_NeuroDamkohler_Continuum_Analysis.ipynb   # Complete executed end-to-end analysis notebook
├── requirements.txt                               # Python dependencies
├── .gitignore                                     # Excludes raw ADNI patient CSVs (DUA compliance)
├── figures/                                       # Publication-grade 300-DPI figures (Figures 1–5)
│   ├── Figure1_Continuum_Specificity.png
│   ├── Figure2_TriModal_Physical_Validation.png
│   ├── Figure3_AD_Specific_Survival.png
│   ├── Figure4_Longitudinal_Velocity_and_GFAP.png
│   └── Figure5_PET_Independence_and_Mediation.png
└── tables/                                        # Summary output tables (Tables 1–3)
    ├── Table1_Continuum_Characteristics.csv
    ├── Table2_Cox_Survival_Matrix.csv
    └── Table3_PET_Adjusted_Ventricular_Capacitance.csv
```

---

## Data Availability & Reproducibility

In strict compliance with the ADNI Data Use Agreement (DUA), raw patient-level CSV files are **not** included in this repository. Qualified researchers can apply for access at [adni.loni.usc.edu](https://adni.loni.usc.edu/) and place the following ADNI tables into `data-20261119T152706Z-1-001/data/` (or update `DATA_DIR` in Cell 1 of the notebook):
- `UPENNBIOMK_ROCHE_ELECSYS` (CSF p-tau181, Aβ42, Aβ40)
- `UPENN_PLASMA_FUJIREBIO_QUANTERIX` (Plasma p-tau217, Aβ42, Aβ40, GFAP, NfL)
- `ADNIMERGE` (Clinical diagnoses, ADAS13, MMSE, APOE4, FreeSurfer MRI volumes)
- `UCBERKELEY_AMY_6MM` & `UCBERKELEY_TAU_6MM` (Amyloid-PET Centiloids & Tau-PET SUVR)
- `ADNI_HAASS_WASHU_LAB` (CSF sTREM2)
- `DTIROI_ROBUSTMEAN` (White-matter DTI tractography)
- `LABDATA` (Serum creatinine `RCT392` for CKD-EPI 2021 eGFR)

### Quick Start
```bash
pip install -r requirements.txt
jupyter notebook ADNI_NeuroDamkohler_Continuum_Analysis.ipynb
```
