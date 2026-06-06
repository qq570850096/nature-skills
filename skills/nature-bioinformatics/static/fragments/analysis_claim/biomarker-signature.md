# Analysis claim: biomarker or signature

## Safe claim structure

`A [gene/cell-state/signature] was associated with [phenotype/outcome] in
[cohort], and requires [validation boundary] before clinical use.`

## Required support

- Training/validation split or independent cohort.
- Outcome definition and covariates.
- Leakage controls, class balance, and performance metric.
- Biological interpretation separated from predictive performance.

## Risk controls

- Do not imply diagnostic or therapeutic utility without validation.
- Avoid reporting only AUC or accuracy without cohort and threshold context.
- Separate exploratory marker discovery from deployable biomarker claims.
