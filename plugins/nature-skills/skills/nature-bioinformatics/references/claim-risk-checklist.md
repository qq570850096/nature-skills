# Claim-risk checklist

Use this file before finalizing Results prose, figure claims, or reviewer-risk
audits.

## Claim downgrades

| Proposed wording | Use only if | Safer default |
|---|---|---|
| "drives" | perturbation, temporal, or mechanistic validation supports causality | is associated with / may contribute to |
| "communicates with" | validated ligand-receptor or spatial/functional evidence exists | is predicted to signal to |
| "differentiates into" | lineage tracing, time course, or strong developmental evidence exists | follows an inferred trajectory toward |
| "diagnostic biomarker" | independent validation and clinical performance are supplied | candidate marker/signature |
| "new cell type" | robust markers, replication, and expert/atlas support are supplied | transcriptionally distinct cell state |

## Required boundaries by claim type

- Cell annotation: label confidence and ambiguous markers.
- DEG/pathway: comparison group, correction method, and cell type.
- Trajectory: root choice, method, and validation status.
- Communication: database/method and prediction status.
- Spatial niche: sample/section replication and spatial quantification.
- Biomarker: training/validation separation and leakage controls.

## Red flags

- Large cell count but no donor/sample replication.
- UMAP-only evidence for central conclusions.
- Marker genes or accession numbers that appear for the first time in the
  assistant output.
- Clinical implication without cohort-level validation.
- Causal verbs attached to cross-sectional transcriptomic data.
