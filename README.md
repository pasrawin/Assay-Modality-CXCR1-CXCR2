# Binding-vs-Antagonism-CXCR2
(This repository accompanies the manuscript currently under peer review)

## Overview
A major challenge in computer-aided drug design (CADD) and machine learning is the indiscriminate aggregation of bioactivity data. Often, data from public repositories (such as ChEMBL) aggregates static equilibrium binding affinity with downstream functional antagonism, which can confound predictive modeling.

This codebase provides a programmatic workflow to decouple public IC50 data into isolated binding and functional cohorts. By mapping out the distinct thermodynamic and physicochemical requirements of these two states, the pipeline demonstrates how targeted data curation can prevent algorithmic errors in AI-driven drug discovery.

### Computational Workflow
The pipeline executes the following steps:
1. **Data Retrieval:** Fetches and filters raw bioactivity data via the ChEMBL API.
2. **Structural Curation:** Performs Bemis-Murcko scaffold extraction to identify specific chemotypes driving binding vs. antagonism.
3. **Descriptor Calculation:** Calculates macroscopic physicochemical descriptors (MolWt, LogP, TPSA, HBD, HBA, *Fsp3*) utilizing RDKit.
4. **Machine Learning:** Trains a Random Forest classifier (utilizing SMOTE for class imbalance) to distinguish functional antagonists from simple binders.

## Usage
The entire workflow is consolidated into a single Jupyter Notebook. To reproduce the study:
1. Clone this repository to your local machine
2. Open CXCR1_2_Pipeline.ipynb in Jupyter Notebook or JupyterLab.
3. Select Kernel -> Restart & Run All.

The script will automatically download the required ChEMBL data, process the datasets, train the Random Forest model, and output the figures (PNG/SVG) and tables (CSV) directly into your working directory.

## Citation
Citation details will be updated upon the manuscript's publication.

## Support and Contact
If you have any questions regarding the code, data, or methodology, please contact: pasrawin.t@chula.ac.th

