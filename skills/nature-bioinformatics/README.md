# nature-bioinformatics

A publication-facing bioinformatics skill for scRNA-seq, spatial
transcriptomics, and single-cell multiomics manuscripts. It helps draft or audit
Results, Methods, figure plans, reviewer-response strategy, and data/accession
checklists with Nature-style claim discipline.

This is not a full analysis-execution pipeline. It assumes the user provides
analysis outputs, figures, notes, or reviewer comments, then checks whether the
proposed manuscript claim is supported by the supplied evidence.

## What it does

- Builds a claim/evidence/boundary map for single-cell and spatial results.
- Separates computational observation, biological interpretation, mechanism, and
  clinical implication.
- Flags missing sample, cohort, QC, batch, validation, and statistical details.
- Drafts ready-to-use prose while preserving explicit missing-input and risk
  flags.
- Plans scRNA/spatial figures as evidence ladders rather than decorative panels.
- Audits repository/accession readiness for data and code.

## Key rules enforced

| Domain | Core rule |
|---|---|
| Causality | Do not turn association, enrichment, pseudotime, or spatial proximity into causal mechanism without validation |
| Cell annotation | Require marker support, reference atlas or expert rationale, and ambiguity flags |
| Differential expression | Require group definition, model/test, multiple-testing correction, effect size or ranking, and biological interpretation limits |
| Trajectory | Treat pseudotime as inferred ordering, not chronological time, unless independently validated |
| Cell-cell communication | Treat ligand-receptor output as a hypothesis, not confirmed interaction |
| Spatial niche | Require spatial coordinate evidence and region/cell-type definitions before claiming niche structure |
| Integration | Do not hide biological signal under batch correction; report method, batch variables, and integration checks |
| Reproducibility | Track software, versions, parameters, database releases, accession IDs, and code/data availability |

## Reference files

```text
skills/nature-bioinformatics/
├── README.md
├── Readme-zh.md
├── SKILL.md
├── manifest.yaml
├── static/
│   ├── core/
│   └── fragments/
├── references/
│   ├── claim-risk-checklist.md
│   ├── figure-archetypes.md
│   ├── methods-reporting-checklist.md
│   ├── prior-art-design-notes.md
│   ├── repository-accession-guide.md
│   └── reviewer-risk-rubric.md
└── evals/
    └── evals.json
```

## Example workflow

For a request such as "帮我写单细胞 Results", the skill:

1. Detects axes such as `scrna-seq`, `cell-annotation` plus
   `differential-expression`, and `results`.
2. Builds a terminology ledger for cell types, genes, datasets, packages, and
   abbreviations.
3. Maps each proposed claim to sample, QC, statistic, validation, and figure
   support.
4. Drafts bounded Results prose.
5. Returns missing inputs and reviewer-risk flags instead of inventing details.

## Design provenance

The architecture is a design synthesis, not a copied prompt bundle. It keeps the
router-style structure of `nature-skills` while absorbing design lessons from
public scientific, medical, and bioinformatics skill projects:

| Project | Lesson adopted here |
|---|---|
| [`K-Dense-AI/scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills) | Broad scientific-skill cataloguing and extensible task taxonomy |
| [`FreedomIntelligence/OpenClaw-Medical-Skills`](https://github.com/FreedomIntelligence/OpenClaw-Medical-Skills) | Wide medical/bioinformatics coverage and clinical-adjacent scope boundaries |
| [`ClawBio/ClawBio`](https://github.com/ClawBio/ClawBio) | Specification-first reproducibility and traceable analysis contracts |
| [`GPTomics/bioSkills`](https://github.com/GPTomics/bioSkills) | Bioinformatics routing by data modality and analysis task |
| [`aipoch/medical-research-skills`](https://github.com/aipoch/medical-research-skills) | Audit gates, veto-style checks, and dynamic quality evaluation |

Those lessons are expressed as modality/claim/artifact axes, missing-input
flags, reviewer-risk rubrics, and reproducibility fields for software, database
release, accession, code, and data traceability.
