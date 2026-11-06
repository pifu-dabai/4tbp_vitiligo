markdown
# 4-tBP-associated vitiligo: computational AOP framework


## Overview

This repository contains the custom R, Python, and shell scripts used to generate the computational results reported in:

> **Huiwei Wang, Xin Lia, Mingxuan Ma, Henan Si, Bing Han, Lei Yao, Junfeng Zhou, Shuyue Yang, Wei Yang, Qin Hao*, Yu Zhen*, Shanshan Li*
.** *[Manuscript title].* npj [Journal name] (2026). https://doi.org/[manuscript DOI]

The study integrates bulk and single-cell transcriptomic analyses, ensemble machine learning, immune-cell deconvolution, molecular docking, and 100-ns molecular dynamics simulations to construct a putative adverse outcome pathway (AOP) linking predicted 4-tert-butylphenol (4-tBP) interactions with melanocyte dysfunction and immune microenvironment alterations in vitiligo. **No new experimental data were generated.**

## Repository organisation
├── 00_docs/ # R sessionInfo(), software versions
├── 01_bulk_transcriptomics/ # Preprocessing, DEG, WGCNA, target intersection, enrichment
├── 02_machine_learning/ # 127 ensemble model configurations, SHAP
├── 03_immune_deconvolution/ # CIBERSORT, gene–immune correlation
├── 04_single_cell/ # Seurat, annotation, Monocle3 / Monocle2 trajectory
├── 05_molecular_docking/ # AutoDock Vina input/configs
├── 06_molecular_dynamics/ # GROMACS .mdp, MMPBSA
└── 07_figures/ # Plotting scripts for main and supplementary figures

text

**Not deposited in this repository:** raw expression matrices are publicly available from GEO; large Seurat / trajectory objects and MD trajectories are available from the corresponding author or from the Zenodo archive associated with the DOI above.

## Software and environment

| Tool | Version | Purpose |
|---|---|---|
| R | 4.3.0 | Bulk transcriptomics, WGCNA, CIBERSORT, plotting |
| limma | 3.56.0 | Differential expression |
| WGCNA | 1.72 | Co-expression network analysis |
| Seurat | [version] | scRNA-seq processing and clustering |
| Monocle 3 | [version] | Trajectory inference |
| Monocle 2 | [version] | Trajectory inference |
| Python | [version] | SHAP, figure generation |
| AutoDock Vina | 1.2.0 | Molecular docking |
| GROMACS | 2022.2 | Molecular dynamics |
| gmx_MMPBSA | [version] | Binding free energy |

Full `sessionInfo()` output and Python package versions are provided in `00_docs/session_info.txt`.

## Quick start

1. Clone the repository:
   ```bash
   git clone https://github.com/pifu-dabai/4tbp_vitiligo.git
   cd 4tbp_vitiligo
Bulk transcriptomics (01_bulk_transcriptomics/): download GSE65127, GSE53146, GSE75819 from GEO, place raw files in a local data/ directory (not tracked), then run scripts in numeric order.

Machine learning (02_machine_learning/): after step 2, run 01_ensemble_models.R; SHAP analysis is in 02_SHAP_analysis.py.

Immune deconvolution (03_immune_deconvolution/): requires CIBERSORT LM22 matrix; see script header for input format.

Single-cell (04_single_cell/): download GSE298871, GSE203262, and PRJCA006797/OMIX691; run 01_seurat_processing.R → 02_cell_annotation.R → trajectory scripts.

Docking / MD (05_ and 06_): AlphaFold models for TYR (P14679), PCSK2 (P16519), KIT (P10721) and PDB 5M8O for TYRP1 are used as receptors; see configs/ and .mdp files for parameters.

Expected outputs: figures and summary tables corresponding to the manuscript; each script writes outputs to a local results/ directory (not tracked).

Data availability
Public datasets used: GSE65127, GSE53146, GSE75819 (bulk discovery), GSE205751 (bulk validation), GSE298871, GSE203262, PRJCA006797/OMIX691 (scRNA-seq). Chemical structure: PubChem CID 7393. Protein structures: AlphaFold (P14679, P16519, P10721) and PDB 5M8O. Details are given in the manuscript's Data Availability statement.

Code availability and DOI
This repository is archived on Zenodo under DOI [10.5281/zenodo.XXXXXXX]. The archived release corresponds to the version of the code used for the manuscript. A LICENSE file is included; please cite the DOI if you reuse these scripts.

Citation
If you use these scripts, please cite the manuscript and the Zenodo archive:

[Authors]. [Title]. npj [Journal] (2026). https://doi.org/[manuscript DOI]
Code archive: https://doi.org/10.5281/zenodo.XXXXXXX

Contact
Corresponding author: [Name, email]
Issues with the code: please open a GitHub issue.
