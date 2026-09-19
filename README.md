# Modality-Specific Curation of CXCR1 and CXCR2 Modulators
*(This repository accompanies the manuscript currently under peer review)*

## Overview
A major challenge in computer-aided drug design (CADD) and machine learning is the indiscriminate aggregation of bioactivity data. Public repositories frequently aggregate data derived from simple receptor occupancy assays with data derived from downstream cell-based functional assays. This aggregation introduces assay-selection bias and confounds predictive modeling.
This codebase provides a programmatic workflow to decouple public IC50 data into isolated binding and functional cohorts. By mapping the distinct physicochemical properties associated with these two assay modalities, the pipeline demonstrates how targeted data curation prevents systemic algorithmic errors in computational drug discovery.

### Computational Workflow
The analytical pipeline executes the following steps:
1. **Data Retrieval and Standardization:** Fetches raw bioactivity data via the ChEMBL API. Standardizes chemical structures utilizing RDKit (stripping salts, neutralizing charges) and aggregates duplicate records using the median pIC50 value.
2. **Modality-Specific Curation:** Programmatically partitions the dataset into a binding cohort and a functional cohort. Strict exclusion rules are applied to prevent assays with functional readouts from contaminating the binding cohort.
3. **Cheminformatics Profiling:** Calculates macroscopic physicochemical descriptors (MolWt, LogP, TPSA, NumHDonors, HBA, Fsp3) and extracts Bemis-Murcko scaffolds.
4. **Machine Learning Validation:** Trains a Random Forest classifier utilizing balanced class weights to discriminate the assay cohorts. The pipeline implements a strict scaffold-split cross-validation (GroupShuffleSplit) to prevent analog data leakage, followed by 95% confidence interval bootstrapping and a 1000-iteration label-permutation control.

## Usage
The entire workflow is consolidated into a single Jupyter Notebook. 

To ensure reproducibility and preserve the evaluated data, the repository includes static datasets and the analytical pipeline encompassing initial ChEMBL data retrieval through model generation. By default, the notebook is configured to execute offline utilizing the `01_raw_chembl_data.csv`  file to reproduce the manuscript results.
1. Clone this repository to your local machine.
2. Open the primary Jupyter Notebook.
3. Select **Kernel -> Restart & Run All**.

### Querying Live Data
Researchers querying current database iterations must change the global toggle at the top of the notebook from `FETCH_CHEMBL_NEW = False` to `FETCH_CHEMBL_NEW = True`.
This action retrieves the latest data from the ChEMBL database and overwrites the local files.

### Outputs
Executing the notebook generates intermediate datasets encompassing standardized molecules and curated cohorts exported as CSV files. The pipeline produces summary data tables formatted as CSV files and figures formatted as 300 dpi TIFF files. The trained Random Forest (RF) model is exported as a `.pkl` file into the designated directory. 

## Citation
Citation details will be updated upon the manuscript's publication.

## Support and Contact
If you have any questions regarding the code, data, or methodology, please contact: pasrawin.t@chula.ac.th

