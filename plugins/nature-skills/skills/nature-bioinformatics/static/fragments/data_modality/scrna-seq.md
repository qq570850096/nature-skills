# Data modality: scRNA-seq

## Required context

- Species, tissue, disease/state, cohort or sample groups.
- Number of donors/samples, cells/nuclei after QC, and batch variables.
- Sequencing platform or assay, preprocessing pipeline, genome/reference build.
- QC filtering, doublet handling, ambient RNA handling, normalization, scaling,
  dimensionality reduction, clustering, and integration method when used.

## Publication logic

scRNA-seq supports cell-state, composition, expression, and inferred trajectory
claims. It does not by itself prove mechanism, lineage, or clinical utility.

## Common reviewer risks

- Treating cells as independent biological replicates.
- Reporting clusters without marker support or reference mapping.
- Hiding donor/sample imbalance behind large cell counts.
- Omitting multiple-testing correction for marker or DEG claims.
- Overinterpreting inferred cell-cell communication.
