# Default stance

## Publication support, not analysis fabrication

Use this skill to help authors write, audit, and revise bioinformatics
manuscript material. Do not run an unstated analysis in your head, invent
statistics, or fill in missing metadata.

## Evidence tiers

Classify every claim before writing:

| Tier | Meaning | Safe language |
|---|---|---|
| Observation | A pattern appears in the provided analysis output | observed, detected, enriched, associated |
| Inference | A computational method suggests a state or relationship | suggests, indicates, is consistent with |
| Mechanism | A causal biological process is supported by direct or orthogonal evidence | demonstrates, supports a mechanism in which |
| Clinical implication | A finding is linked to diagnosis, prognosis, therapy, or patient stratification | may inform, warrants validation, is associated with |

Do not promote a lower tier to a higher tier for rhetorical force.

## Non-negotiable checks

- Sample and cohort structure: donors, samples, batches, conditions, replicates.
- QC: filtering, doublet removal, ambient RNA, mitochondrial/ribosomal thresholds,
  sequencing depth or spot/cell capture quality.
- Normalization/integration: method, covariates, batch variables, and checks that
  biology was not erased.
- Statistics: test/model, multiple-testing correction, effect size or ranking,
  and analysis population.
- Validation: independent cohort, orthogonal assay, marker confirmation,
  perturbation, spatial co-localization, or literature support when relevant.
- Traceability: software, package versions, reference atlas, database release,
  accession IDs, code repository, and figure source data.

## Boundaries

- Ligand-receptor analysis generates interaction hypotheses unless validated.
- Pseudotime is an inferred ordering, not elapsed biological time.
- Spatial proximity is not physical interaction by itself.
- Cell-type labels are annotations, not facts, unless supported by markers,
  reference mapping, and domain rationale.
- Biomarker or clinical claims need independent validation and leakage-aware
  modelling.
