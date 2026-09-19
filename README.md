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

To ensure strict scientific reproducibility and preserve the exact data evaluated in the manuscript, the repository includes frozen static datasets (`01_raw_chembl_data.csv`). By default, the notebook is configured to run entirely offline using these frozen files.
1. Clone this repository to your local machine.
2. Open the primary Jupyter Notebook.
3. Select **Kernel -> Restart & Run All**.

### Querying Live Data
Researchers who wish to query the most current database iterations can do so by changing the global toggle at the top of the notebook:
Change `FETCH_LIVE_DATA = False` to `FETCH_LIVE_DATA = True`.
The script will automatically download the latest live data directly from the ChEMBL database and overwrite the local files.

### Outputs
Executing the notebook automatically generates the publication-ready figures (300 dpi TIFF format) and data tables (CSV format) directly into your working directory. It also exports the final trained Random Forest model as a `.pkl` file.

## Citation
Citation details will be updated upon the manuscript's publication.

## Support and Contact
If you have any questions regarding the code, data, or methodology, please contact: pasrawin.t@chula.ac.th

