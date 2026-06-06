# GitHub Prior-Art Design Notes

Snapshot date: 2026-06-06. Star counts were checked through the GitHub API and
should be treated as time-sensitive metadata, not permanent facts.

This skill learns design patterns from public COMSOL and finite-element projects
without copying project content.

## COMSOL Automation and Agent Control

| Repository | Snapshot | Design lesson for this skill |
|---|---:|---|
| [`MPh-py/MPh`](https://github.com/MPh-py/MPh) | 528 stars; Pythonic scripting interface for COMSOL Multiphysics | Treat COMSOL models as scriptable objects. Publication support should ask for parameters, model files, scripts, exports, and provenance rather than only prose. |
| [`wjc9011/COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP) | 369 stars; COMSOL MCP project | AI-assisted COMSOL work needs explicit tool/session boundaries. A skill should expose model-state uncertainty instead of pretending the GUI/model was inspected. |
| [`svd-ai-lab/sim-cli`](https://github.com/svd-ai-lab/sim-cli) | 131 stars; CLI-first agent runtime for CAE solvers including COMSOL, Abaqus, and Ansys | Solver operations are safer when commands, plugins, logs, and output files are treated as first-class artifacts. |
| [`777gegewu/comsol-mcp`](https://github.com/777gegewu/comsol-mcp) | 103 stars; unofficial COMSOL MCP learning project | COMSOL automation often crosses GUI, Java shell, and model-session boundaries; the publication layer must not hide those boundaries. |
| [`jianyingwu/pfczm-comsol`](https://github.com/jianyingwu/pfczm-comsol) | 87 stars; phase-field cohesive-zone models in COMSOL | Specialized COMSOL models need calibrated constitutive parameters, verification examples, and reproducible implementation details. |

## Open FEM and Mechanical Simulation Ecosystem

| Repository | Snapshot | Design lesson for this skill |
|---|---:|---|
| [`KratosMultiphysics/Kratos`](https://github.com/KratosMultiphysics/Kratos) | 1,279 stars; modular multidisciplinary simulation framework | Use modular axes for simulation domains; multiphysics manuscripts need domain-specific assumptions and application-level checks. |
| [`FEniCS/dolfinx`](https://github.com/FEniCS/dolfinx) | 1,142 stars; next-generation FEniCS problem-solving environment | Reproducible simulation benefits from explicit problem definitions, versioned computational artifacts, and transparent numerical formulation. |
| [`precice/precice`](https://github.com/precice/precice) | 938 stars; coupling library for partitioned multiphysics/multiscale simulations | Coupled simulations require interface mapping, coupling convergence, solver partitioning, and time-step transparency. |
| [`sfepy/sfepy`](https://github.com/sfepy/sfepy) | 831 stars; finite-element Python project | Readable problem specifications help reviewers inspect equations, material regions, boundary conditions, and outputs. |
| [`OpenRadioss/OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss) | 809 stars; explicit/dynamic finite-element solver | Dynamic simulations require timestep stability, energy balance, contact settings, and failed-case reporting. |
| [`OpenSees/OpenSees`](https://github.com/OpenSees/OpenSees) | 773 stars; structural simulation platform | Structural papers need transparent calibration, constraints, loading protocols, and validation data. |

## Design Rules Extracted

1. **Contract first** - A simulation skill should operate like a machine-readable
   model contract: geometry, material, boundary conditions, mesh, solver, outputs,
   and validation before prose.
2. **Artifacts over assertions** - Prefer `.mph` files, exported Java/MATLAB/Python
   scripts, parameter tables, solver logs, exported figure data, and convergence
   tables over untraceable claims.
3. **Domain axes, not paper-section axes** - Simulation risk depends more on the
   physics domain and claim type than on whether the user asks for Results or
   Methods.
4. **Verification and validation are separate** - Mesh convergence and solver
   convergence do not validate real-world behavior; experiments do not prove
   numerical correctness.
5. **Coupling and contact need special treatment** - FSI, thermal-mechanical
   coupling, contact/friction, and fracture introduce nonlinear and interface
   risks that must be made visible.
6. **Reviewer gate is mandatory** - A strong output must include missing inputs
   and risk flags, not just polished manuscript language.

## Implementation Consequence

The skill uses:

- `simulation_domain` for physical context.
- `model_claim` for claim discipline.
- `artifact` for the requested publication output.
- On-demand references for mesh convergence, boundary conditions, solver study
  reporting, Methods reporting, figures, reviewer-risk audit, and COMSOL
  reproducibility.
