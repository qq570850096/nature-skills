# Reviewer-risk rubric

Use this file for pre-submission audits or reviewer-response strategy.

## Fatal risks

- Central claim depends on unsupported cell labels, inaccessible data, or
  irreproducible analysis.
- Clinical or biomarker claim has no independent validation or has data leakage.
- Mechanistic claim rests only on cross-sectional transcriptomic association.
- Human data access conditions are missing or impossible to verify.

## Major risks

- Sample/donor replication is unclear.
- Batch correction, integration, or clustering choices are underreported.
- DEG statistics ignore replicate structure or multiple testing.
- Trajectory, communication, or spatial niche claims are overphrased.
- Figures show embeddings/maps without sample-level quantification.
- Methods omit software, database, reference atlas, or key parameters.

## Minor risks

- Package versions are incomplete but core logic is clear.
- Figure legends omit some thresholds or abbreviations.
- Terminology drifts across cell labels, datasets, or signatures.
- Results wording is fluent but not tied tightly enough to figures.

## Repair actions

- Add evidence: marker table, pseudobulk statistics, validation cohort,
  sensitivity analysis, spatial quantification, or source-data table.
- Soften claim: mechanism -> association, interaction -> predicted signalling,
  lineage -> inferred ordering, biomarker -> candidate signature.
- Improve traceability: accession, code release, package versions, database
  release, parameter table.
