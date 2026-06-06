# Methods reporting checklist

Use this file to audit or draft bioinformatics Methods.

## Data and preprocessing

- Data source, accession, species, tissue, cohort, and sample groups.
- Sequencing platform, reference genome/build, and alignment/quantification
  tools.
- Cell/nucleus or spot filtering thresholds.
- Doublet detection, ambient RNA correction, mitochondrial/ribosomal thresholds,
  and low-quality sample exclusion.

## Analysis methods

- Normalization, feature selection, dimensionality reduction, clustering, and
  integration.
- Annotation method: marker genes, reference atlas, label transfer, manual review.
- DEG/statistical model, replicate unit, covariates, and multiple-testing
  correction.
- Pathway/gene-set database name and release when supplied.
- Trajectory, communication, spatial, or multiomic method and key parameters.

## Reproducibility

- Software names and versions when provided.
- Random seeds or deterministic settings when relevant.
- Code repository, environment file, notebooks/scripts, and figure source data.
- Third-party data version and date accessed when relevant.

## Wording rule

If a Methods field is missing, write a placeholder or a missing-input bullet.
Do not invent a popular tool, threshold, or version.
