# Consensus Selection of Alternatives (CSA): Reproducibility Package

This repository contains the data, processed outputs, scripts, and figures used to reproduce the computational results reported in the manuscript:

**Consensus Selection of Alternatives (CSA): A Reliability-Weighted Score Integration Framework for Multi-Criteria Decision Making**

## Overview

The repository implements a reproducible workflow for evaluating the Consensus Selection of Alternatives (CSA) framework in a multi-criteria decision-making (MCDM) setting. The workflow includes:

- a defense-inspired benchmark dataset
- processed benchmark files
- benchmark comparison against Borda Count and mean normalized score aggregation
- robustness analysis under weighting, normalization, leave-one-method-out, and rank-reversal style scenarios
- cross-domain external validation using an open PV technology decision matrix

The repository is designed to reproduce the tables and figures reported in the manuscript.

## Repository structure

```text
csa-mcdm-consensus-ranking/
├─ README.md
├─ LICENSE
├─ CITATION.cff
├─ requirements.txt
├─ environment.yml
├─ .gitignore
├─ data/
│  ├─ raw/
│  │  ├─ CSA_Supplementary_Illustrative.xlsx
│  │  └─ pv_external_matrix.csv
├─ processed/
│  ├─ metadata.json
│  ├─ criteria_master.csv
│  ├─ subcriteria_master.csv
│  ├─ alternatives_master.csv
│  ├─ alternative_scores_long.csv
│  ├─ method_outputs_master.csv
│  └─ reliability_weights_master.csv
├─ scripts/
│  ├─ audit_now.py
│  ├─ build_inputs_now.py
│  ├─ extract_results_now.py
│  ├─ compute_baselines_now.py
│  ├─ robustness_now.py
│  ├─ freeze_tables_now.py
│  ├─ external_validation_now.py
│  └─ external_pv_now.py
├─ outputs/
│  ├─ audit_now/
│  ├─ core_now/
│  ├─ baselines_now/
│  ├─ robustness_now/
│  ├─ external_validation_now/
│  ├─ external_pv_now/
│  └─ frozen_tables_now/
└─ figures/
   ├─ Figure_1_CSA_workflow.png
   ├─ Figure_2_benchmark_comparison.png
   ├─ Figure_3_robustness_heatmap.png
   ├─ Figure_4_rank_shift.png
   └─ Figure_5_external_validation_real.png

Main benchmark dataset

The main benchmark dataset is stored as:
	•	data/raw/CSA_Supplementary_Illustrative.xlsx

This dataset contains the benchmark structure used in the manuscript, including:
	•	criteria weights
	•	alternative scores
	•	method-specific outputs
	•	CSA outputs
	•	reliability, RMSE, Spearman, and CSI sheets

External validation dataset

The external validation dataset is stored as:
	•	data/raw/pv_external_matrix.csv

This file contains the PV technology decision matrix used for the cross-domain external validation reported in the manuscript.

Computational workflow

Run the scripts in the following order:
	1.	audit_now.py
	2.	build_inputs_now.py
	3.	extract_results_now.py
	4.	compute_baselines_now.py
	5.	robustness_now.py
	6.	freeze_tables_now.py
	7.	external_validation_now.py
	8.	external_pv_now.py

Reproducing the tables and figures

Main manuscript mapping
	•	Table 4 -> outputs/frozen_tables_now/Table_4_final.csv
	•	Table 5 -> outputs/frozen_tables_now/Table_5_final.csv
	•	Table 6 -> outputs/frozen_tables_now/Table_6_final.csv
	•	Table 7 -> outputs/external_pv_now/Table_7_final_real_external.csv
	•	Figure 1 -> figures/Figure_1_CSA_workflow.png
	•	Figure 2 -> figures/Figure_2_benchmark_comparison.png
	•	Figure 3 -> outputs/robustness_now/figures/Figure_3_robustness_heatmap.png
	•	Figure 4 -> outputs/robustness_now/figures/Figure_4_rank_shift.png
	•	Figure 5 -> outputs/external_pv_now/figures/Figure_5_external_validation_real.png

Minimal execution examples
python scripts/audit_now.py --xlsx "data/raw/CSA_Supplementary_Illustrative.xlsx" --outdir "outputs/audit_now"
python scripts/build_inputs_now.py --xlsx "data/raw/CSA_Supplementary_Illustrative.xlsx" --outdir "data/processed"
python scripts/extract_results_now.py --xlsx "data/raw/CSA_Supplementary_Illustrative.xlsx" --outdir "outputs/core_now"
python scripts/compute_baselines_now.py --corecsv "outputs/core_now/core_method_outputs.csv" --outdir "outputs/baselines_now"
python scripts/robustness_now.py --corecsv "outputs/core_now/core_method_outputs.csv" --outdir "outputs/robustness_now"
python scripts/freeze_tables_now.py --corecsv "outputs/core_now/core_method_outputs.csv" --baselinecsv "outputs/baselines_now/baseline_comparison_summary.csv" --robustcsv "outputs/robustness_now/table6_input.csv" --outdir "outputs/frozen_tables_now"
python scripts/external_validation_now.py --corecsv "outputs/core_now/core_method_outputs.csv" --outdir "outputs/external_validation_now"
python scripts/external_pv_now.py --csv "data/raw/pv_external_matrix.csv" --outdir "outputs/external_pv_now"

Data and code availability

This repository provides the data, processed outputs, scripts, and figures required to reproduce the computational results reported in the manuscript. The repository includes the main benchmark dataset, the external PV validation matrix, and the full script chain used to generate the reported tables and figures.

Citation

If you use this repository, please cite the associated manuscript and repository release.
