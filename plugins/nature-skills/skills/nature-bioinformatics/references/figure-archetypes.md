# Figure archetypes for scRNA and spatial papers

Use this file for figure plans and figure-risk audits.

## scRNA-seq evidence ladder

1. Cohort/sample overview and QC summary.
2. Cell atlas: embedding plus cell-type composition.
3. Core finding: cell state, DEG, pathway, or signature.
4. Validation/sensitivity: marker heatmap, sample-level quantification,
   independent cohort, or orthogonal assay.
5. Mechanistic hypothesis: trajectory, communication, or regulatory analysis,
   labelled as inference unless validated.

## Spatial evidence ladder

1. Tissue section or region map with sample count.
2. Spatial distribution of cell states or expression.
3. Quantification across sections/samples.
4. Neighborhood/niche analysis with distance or region definition.
5. Histology, immunostaining, or orthogonal validation where available.

## Panel QA

- Every panel must answer a distinct scientific question.
- Embeddings and maps need sample-level quantification nearby.
- Legends must define cell types, regions, conditions, and statistical units.
- Avoid repeated UMAPs that only change color without changing the question.
- Use direct labels for stable cell types or tissue regions when possible.
