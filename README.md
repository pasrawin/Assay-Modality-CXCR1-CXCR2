# Binding-vs-Antagonism-CXCR2
This repository contains the computational pipeline for the programmatic retrieval, curation, and machine learning analysis of CXCR1 and CXCR2 modulators. This code accompanies the manuscript (currently submitted for publication).

## Overview
The indiscriminate aggregation of heterogeneous assay data (e.g., treating equilibrium binding affinity as synonymous with functional modulation) fundamentally confounds predictive molecular modeling. This codebase programmatically decouples public IC50 data from the ChEMBL database into isolated binding and functional cohorts to map out distinct thermodynamic and topological requirements. 

It includes the computational steps to:
1. Fetch and filter raw bioactivity data via the ChEMBL API.
2. Perform Bemis-Murcko scaffold extraction to identify specific chemotypes.
3. Calculate macroscopic physicochemical descriptors (MolWt, LogP, TPSA, HBD, HBA, Fsp3) using RDKit.
4. Train a Random Forest classifier (with SMOTE oversampling) to distinguish functional antagonists from simple binders.

## Usage
The entire workflow is consolidated into a single Jupyter Notebook. To reproduce the study:
1. Clone this repository to your local machine.
2. Open CXCR1_2_Pipeline.ipynb in Jupyter Notebook or JupyterLab.
3. Select Kernel -> Restart & Run All.

The script will automatically download the required ChEMBL data, process it, and output the figures (PNG/SVG) and tables (CSV) directly into your working directory.

## Citation
Citation details will be updated upon the manuscript's publication.

## Support and Contact
If you have any questions regarding the code, data, or methodology, please contact: pasrawin.t@chula.ac.th

