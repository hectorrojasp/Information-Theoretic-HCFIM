# Information-Theoretic HCFIM Geometry for Data-Limited EEG Screening

Reproducible Jupyter notebooks supporting the study **“Information-Theoretic HCFIM Geometry for Data-Limited EEG Screening of Alzheimer’s Disease and Frontotemporal Dementia.”**

The workflow maps resting-state EEG signals into entropy–complexity–Fisher information (HCFIM) coordinates and evaluates regional, lateralized, spectral, classification, robustness, and sensitivity analyses at the participant level.

## Scope

The repository provides the analysis notebooks used to generate and validate the results reported in the manuscript. The analyses are exploratory and preclinical. They do not constitute a diagnostic system or establish a clinically validated biomarker.

## Repository structure

```text
core/
  01_hcfim_eeg_paper_reproducible.ipynb
  02_hcfim_eeg_lateralized_v1_analysis.ipynb
  03_hcfim_eeg_bootstrap_ci_v1.ipynb
  04_hcfim_eeg_topomap_contrasts_v1.ipynb
  10_repeated_primary_validation_and_enhanced_spectral_baseline.ipynb

validation/
  05_reviewer_revision_analyses.ipynb
  06_confirmatory_sensitivity_analyses.ipynb
  07_ad_vs_ftd_differential_validation.ipynb
  08_embedding_dimension_selection_validation.ipynb
  09_band_adapted_ordinal_delay_validation.ipynb
  11_duration_sex_confounder_validation.ipynb
  12_feature_duplicate_count_fdr_stability_auc_audit.ipynb

reporting/
  13_publication_figure_consistency_repairs.ipynb
  14_review_grids_preprocessing_top_features_ablations.ipynb
```

The numbering reflects the recommended execution order. Some later notebooks consume intermediate results produced by earlier analyses.

## Data

The analyses use the public OpenNeuro dataset **ds004504**, comprising eyes-closed resting-state EEG from participants with Alzheimer’s disease, frontotemporal dementia, and healthy controls. Dataset files are not redistributed in this repository.

Download the dataset separately and preserve its BIDS structure, including `participants.tsv` and the released `derivatives/` directory.

## Path configuration

The notebooks contain no machine-specific absolute paths. They first attempt to locate the repository and dataset from their relative directory structure. If automatic discovery is not suitable, define either or both of these environment variables before starting Jupyter:

- `HCFIM_PROJECT_ROOT`: root directory of the analysis repository.
- `HCFIM_DATASET_ROOT`: root directory of the ds004504 dataset.

Example dataset layout:

```text
HCFIM_PROJECT_ROOT/
  notebooks/
  src/
  data/
    ds004504/
      participants.tsv
      derivatives/
```

## Running the notebooks

1. Create a Python environment containing the scientific packages imported by the notebooks.
2. Download ds004504 and configure its location as described above.
3. Start Jupyter from the repository or one of its subdirectories.
4. Run the notebooks in numerical order when rebuilding the complete analysis.

The published copies have intentionally been stripped of cell outputs and execution counters. This keeps the repository compact and prevents local paths or stale results from being embedded in the files. Executing the notebooks regenerates the corresponding tables, figures, and analysis artifacts.

Computationally intensive validation notebooks may require substantial runtime. Fixed random seeds and participant-level validation procedures are specified within the relevant notebooks.

## Reproducibility principles

- Participant-level separation prevents epochs from the same participant appearing in both training and test partitions.
- Feature selection and model fitting are performed within the validation workflow where applicable.
- Confirmatory and sensitivity analyses address multiplicity, permutation testing, embedding dimension, ordinal delay, recording duration, sex, feature duplication, selection stability, and alternative spectral baselines.
- Results should be interpreted together with the limitations and analysis hierarchy stated in the manuscript.

## Citation

If you use this workflow, please cite the accompanying article and the original ds004504 dataset publication. The final journal citation and DOI can be added here once available.

## Disclaimer

This software is provided for research and methodological evaluation. It is not intended for clinical diagnosis, treatment decisions, or device-specific deployment. Independent external validation is required before translational use.
