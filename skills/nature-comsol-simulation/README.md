# nature-comsol-simulation

`nature-comsol-simulation` is a Nature-style publication skill for COMSOL
Multiphysics and mechanical-engineering simulation manuscripts. It helps authors
write and audit Results, Methods, figure plans, reviewer responses,
reproducibility packages, validation strategy, mesh-convergence reporting, and
literature-review plans.

The skill is intended for COMSOL/finite-element papers in solid mechanics,
structural dynamics, contact/friction, thermal-mechanical coupling,
fluid-structure interaction, biomechanics, fracture, and materials simulation.
It is not a solver, a substitute for COMSOL, or an engineering certification
tool. It works from the evidence the user provides and turns that evidence into
bounded publication artifacts.

## Design logic

The core idea is that simulation manuscripts fail when claims outrun the model
contract. A polished paragraph cannot fix a missing boundary condition, an
unreported mesh-convergence test, an unvalidated material model, or a contour
plot that is interpreted as a mechanism.

This skill therefore routes every request through three axes:

| Axis | What it captures | Examples |
|---|---|---|
| `simulation_domain` | The physics and engineering context | solid mechanics, structural dynamics, contact/friction, thermal-mechanical, FSI, biomechanics, fracture/materials |
| `model_claim` | The type of conclusion the manuscript wants to make | stress-strain, deformation, modal frequency, contact pressure, thermal stress, parametric sensitivity, validation, optimization |
| `artifact` | The publication output the user needs | Results, Methods, figure plan, review-risk audit, response strategy, reproducibility checklist, literature-review plan |

This router structure keeps the skill extensible. A future module can add
electromagnetics, acoustics, MEMS, batteries, CFD, porous media, or geomechanics
without rewriting the entire skill.

## What this skill enforces

| Area | Rule |
|---|---|
| Claim discipline | Do not present numerical association, contour contrast, or parameter sweep trend as mechanism unless supported by validation or theory |
| Model transparency | Geometry, material law, boundary conditions, contacts, mesh, solver, units, and outputs must be traceable |
| Verification | Separate model verification from experimental validation |
| Mesh convergence | Report the monitored quantity, mesh levels, element order, local refinement, convergence tolerance, and sensitivity of the claim |
| Boundary conditions | Treat loads, constraints, symmetry, contact, thermal inputs, and initial conditions as claim-defining assumptions |
| Solver reporting | State study type, nonlinear settings, time stepping, coupling strategy, convergence criteria, and failed/unstable cases when relevant |
| Reproducibility | Track COMSOL version, physics interfaces, parameter tables, `.mph` files or scripts, exported data, solver logs, and repository/package access |
| Reviewer risk | Output missing inputs and risk flags instead of smoothing uncertainty into confident prose |

## GitHub prior art absorbed

The design learns from public COMSOL and finite-element projects without copying
their content:

| Project | What we learned |
|---|---|
| [`MPh-py/MPh`](https://github.com/MPh-py/MPh) | COMSOL models should be treated as scriptable, inspectable objects with parameter and export provenance |
| [`wjc9011/COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP) | AI-assisted COMSOL work needs explicit session/tool boundaries and should not hide GUI or model-state uncertainty |
| [`svd-ai-lab/sim-cli`](https://github.com/svd-ai-lab/sim-cli) | Solver operations become safer when commands, logs, plugins, and outputs are first-class artifacts |
| [`KratosMultiphysics/Kratos`](https://github.com/KratosMultiphysics/Kratos) | Multiphysics work benefits from modular domain separation and explicit application-level assumptions |
| [`sfepy/sfepy`](https://github.com/sfepy/sfepy) | A readable finite-element problem specification helps reviewers see equations, materials, regions, and boundary conditions |
| [`precice/precice`](https://github.com/precice/precice) | Coupled simulations need interface mapping, coupling convergence, and solver-partition transparency |
| [`OpenRadioss/OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss) | Dynamic-event simulation needs energy balance, contact settings, timestep stability, and failure-mode reporting |
| [`OpenSees/OpenSees`](https://github.com/OpenSees/OpenSees) | Structural simulation papers should expose model calibration, constraints, loading protocol, and validation data |
| [`FEniCS/dolfinx`](https://github.com/FEniCS/dolfinx) | Reproducible simulation benefits from clear weak-form/problem definition and versioned computational artifacts |

See [`references/prior-art-design-notes.md`](references/prior-art-design-notes.md)
for the detailed research notes and star snapshot used when this skill was
designed.

## How to use

Copy the whole skill folder together with `skills/_shared/` into your local
skills directory, or install the complete `nature-skills` plugin bundle.

Then ask naturally:

```text
Use nature-comsol-simulation to audit this COMSOL solid-mechanics Results section.
```

```text
帮我检查这个 COMSOL 热-结构耦合模型的 Methods，重点看网格收敛、边界条件和审稿风险。
```

```text
Reviewer says our contact-pressure simulation does not prove wear reduction.
Please draft a response strategy and list the extra evidence we need.
```

## Required input for best results

You do not need to provide everything at once, but the skill will explicitly
flag whatever is missing:

| Category | Useful inputs |
|---|---|
| Model setup | COMSOL version, module/physics interface, study type, geometry, dimensionality, symmetry assumptions |
| Materials | Material model, parameters, units, source of parameters, linear/nonlinear assumptions, anisotropy/viscoelasticity/plasticity |
| Boundary conditions | Loads, constraints, contact pairs, friction coefficient, thermal inputs, initial conditions, coupling interfaces |
| Mesh | Element type/order, mesh levels, local refinement, monitored quantity, convergence tolerance, final element count |
| Solver | Stationary/time-dependent/eigenfrequency, nonlinear settings, tolerances, timestep strategy, segregated/fully coupled settings |
| Validation | Analytic benchmark, experimental measurement, literature benchmark, calibration dataset, uncertainty/error metric |
| Outputs | Figures, tables, extracted values, parameter sweeps, sensitivity analysis, failure or instability cases |
| Publication target | Journal, section, claim, figure panel, reviewer comment, or desired output type |

## Example output shape

For a Results request, the skill should return:

1. Detected axes.
2. Claim-evidence map.
3. Ready-to-use Nature-style Results paragraph.
4. Missing inputs.
5. Reviewer-risk flags.
6. Optional figure or Methods fixes.

## Example prompt

```text
Use nature-comsol-simulation.

Task:
1. Audit whether our COMSOL stress and deformation figures support the claimed
   mechanical advantage of the new implant design.
2. Write a concise Nature-style Results paragraph.
3. List missing inputs and reviewer-risk flags.

Evidence:
- Solid Mechanics, stationary study.
- Two designs: baseline and porous lattice.
- Output: von Mises stress and displacement contours.
- Mesh convergence: three mesh levels, but only displacement was monitored.
- Validation: compression test planned, not yet completed.
```

Expected behavior: the skill should write usable Results text, but it should
downgrade any design-superiority or failure-resistance claim until stress
convergence and experimental validation are supplied.
