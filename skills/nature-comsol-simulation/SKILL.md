---
name: nature-comsol-simulation
description: >-
  Nature-style publication support for COMSOL Multiphysics and mechanical
  engineering simulation manuscripts. Use when the user asks to write, audit,
  revise, or plan Results, Methods, figure panels, validation strategy,
  mesh-convergence reporting, boundary-condition review, solver-study reporting,
  reviewer-response strategy, reproducibility checklists, or literature-review
  plans for COMSOL, finite-element analysis, structural mechanics, solid
  mechanics, contact, fracture, thermal-mechanical, fluid-structure interaction,
  biomechanics, modal analysis, stress-strain, deformation, or engineering
  simulation papers. Also trigger on Chinese requests such as COMSOL论文,
  机械工程仿真, 有限元论文, 多物理场仿真, 网格收敛, 边界条件, 求解器设置,
  接触摩擦, 热-结构耦合, 流固耦合, 仿真审稿风险.
---

# Nature COMSOL Simulation Publication Router

This skill supports publication-facing COMSOL and mechanical-engineering
simulation work. It is not a replacement for COMSOL, a certified engineering
review, or a solver-execution pipeline. It helps turn author-provided model
evidence into bounded manuscript prose, Methods reporting, figure logic,
validation plans, reviewer-risk audits, response strategy, and reproducibility
checklists.

This skill has two layers:

- A **static layer** under `static/` with reusable rules and fragments for
  simulation domain, model claim, and output artifact.
- A **dynamic layer** (this file plus `manifest.yaml`) that detects the current
  request axes and loads only the needed fragments. Deep checklists stay in
  `references/` and are loaded on demand.

Do not apply COMSOL or finite-element publication rules from memory alone.
Always load the manifest and the relevant fragments from disk.

## Routing Protocol

Follow these steps every time the skill is invoked.

### 1. Load the manifest and core layer

Read [manifest.yaml](manifest.yaml). It declares the axes
(`simulation_domain`, `model_claim`, `artifact`) and maps each value to a file.

Also read every file listed under `always_load`. These include the shared
Nature-style reader workflow and the skill-local stance, workflow, and output
format.

### 2. Detect axis values

For each axis, decide the value using the manifest's `detect:` hint and the
user's input:

- `simulation_domain` - one of `solid-mechanics`, `structural-dynamics`,
  `contact-friction`, `thermal-mechanical`, `fluid-structure`,
  `biomechanics`, or `fracture-materials`. Default: `solid-mechanics`.
- `model_claim` - one or more of `stress-strain`, `deformation-displacement`,
  `modal-frequency`, `contact-pressure`, `thermal-stress`,
  `parametric-sensitivity`, `validation-calibration`, or
  `optimization-design`.
- `artifact` - one of `results`, `methods`, `figure-plan`,
  `review-risk-audit`, `response-strategy`, `reproducibility-checklist`, or
  `literature-review-plan`.

State the detected axis values in one short line before producing the output so
the user can correct scope cheaply.

### 3. Load matching fragments

Read the file mapped for each selected value. Do **not** load every fragment.
For combined requests, load only the relevant artifact and claim fragments.

### 4. Run the workflow

Apply the loaded material in this order:

1. Core stance - claim discipline, model-evidence tiers, and non-fabrication.
2. Simulation-domain fragment - domain-specific assumptions and reporting.
3. Model-claim fragment - what the model can and cannot support.
4. Artifact fragment - output shape and task-specific checks.
5. Core output format - ready-to-use text plus missing inputs and risk flags.

Never invent geometry, material parameters, boundary conditions, mesh size,
element type, solver settings, convergence results, validation data, statistics,
software version, figure panels, repository links, or reviewer comments. If a
claim needs metadata or validation that the user has not supplied, flag the gap
instead of smoothing it over.

### 5. Use references only when needed

The files under `references/` are deep references, not defaults. Open them on
demand per the `references.on_demand` table in the manifest, especially before
finalizing a mesh-convergence critique, boundary-condition critique, Methods
checklist, figure plan, reproducibility package, or reviewer-risk audit.

## Design Intent

Good COMSOL/manuscript support is not a prompt for prettier prose. It is a
domain contract linking model assumptions, solver settings, verification,
validation, and claim strength. This design adapts lessons from public COMSOL
automation and open finite-element repositories: scriptable provenance,
modular domain axes, convergence discipline, coupling transparency, and explicit
reviewer-risk gates.
