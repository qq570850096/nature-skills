---
name: nature-bioinformatics
description: >-
  Nature-style bioinformatics publication support for scRNA-seq, spatial
  transcriptomics, and single-cell multiomics manuscripts. Use when the user
  asks to write, audit, or revise bioinformatics Results, Methods, figure plans,
  reviewer-response strategy, data/accession checklists, or review-risk audits
  for single-cell or spatial papers. Also trigger on general bioinformatics
  publication requests even without the word "Nature", including scRNA-seq,
  spatial transcriptomics, single-cell multiomics, cell annotation, differential
  expression, trajectory/pseudotime, cell-cell communication, ligand-receptor
  analysis, batch integration, biomarker signatures, 生物信息学论文, 单细胞, 空间转录组,
  细胞注释, 拟时序, 细胞通讯, 差异表达, and 生信审稿风险.
---

# Nature Bioinformatics Publication — Router

This skill supports publication-facing bioinformatics work. It is not a full
analysis-execution pipeline. It helps convert author-provided evidence into
bounded manuscript prose, figure logic, reviewer-risk audits, response strategy,
and data/accession checklists for scRNA-seq, spatial transcriptomics, and related
single-cell multiomics papers.

This skill is split into two layers:

- A **static layer** under `static/` with reusable core rules and fragments for
  data modality, analysis claim, and output artifact.
- A **dynamic layer** (this file plus `manifest.yaml`) that detects the current
  request axes and loads only the needed fragments. Deep checklists and rubrics
  stay in `references/` and are loaded on demand.

Do not apply bioinformatics rules from memory alone. Always load fragments from
disk as described below.

## Routing protocol

Follow these five steps every time the skill is invoked.

### 1. Load the manifest and core layer

Read [manifest.yaml](manifest.yaml). It declares the axes
(`data_modality`, `analysis_claim`, `artifact`) and maps each value to a file.

Also read every file listed under `always_load`. These include the shared reader
workflow, paper-type taxonomy, ethics, terminology ledger, and the skill-local
stance, workflow, and output format.

### 2. Detect the axis values

For each axis, decide the value using the manifest's `detect:` hint and the
user's input:

- `data_modality` — `scrna-seq`, `spatial-transcriptomics`, or
  `single-cell-multiomics`. Default: `scrna-seq`.
- `analysis_claim` — one or more of `cell-annotation`,
  `differential-expression`, `trajectory-pseudotime`,
  `cell-cell-communication`, `spatial-niche`, `integration-batch-effect`, or
  `biomarker-signature`.
- `artifact` — one of `results`, `methods`, `figure-plan`,
  `review-risk-audit`, `response-strategy`, or
  `data-availability-checklist`.

State the detected axis values in one short line before producing the output so
the user can correct scope cheaply.

### 3. Load the matching fragments

Read the file mapped for each selected value. Do **not** load every fragment.
For combined requests, load only the relevant artifact and claim fragments.

### 4. Run the workflow

Apply the loaded material in this order:

1. Core stance — claim discipline, evidence tiers, and non-fabrication rules.
2. Data-modality fragment — modality-specific QC and reporting expectations.
3. Analysis-claim fragment — what can and cannot be concluded from the analysis.
4. Artifact fragment — output shape and task-specific checks.
5. Core output format — ready-to-use text plus missing inputs and risk flags.

Never invent sample sizes, cohorts, marker genes, accession numbers, software
versions, statistics, validation experiments, figure panels, or reviewer
comments. If a claim needs validation or metadata that the user has not supplied,
flag the gap instead of smoothing it over.

### 5. Reach for references only when needed

The files under `references/` are deep references, not defaults. Open them on
demand per the `references.on_demand` table in the manifest, especially before
finalizing a review-risk audit, Methods checklist, figure plan, or accession
package.

## Why this split

- The router stays small and cheap to load.
- The manifest leaves room for future modalities such as bulk RNA-seq, ATAC-seq,
  variant calling, proteomics, and microbiome without rewriting the skill.
- The design borrows the best public patterns: broad scientific-skill
  cataloguing, medical/bioinformatics task axes, specification-first
  reproducibility, and explicit audit gates, while keeping the Nature-style
  output discipline of this repository.
