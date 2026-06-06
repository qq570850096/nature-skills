# Solver and Study Reporting

Solver choices are part of the Methods because they determine numerical trust.

## Required Fields

- Study type: stationary, time-dependent, eigenfrequency, frequency-domain,
  parametric sweep, optimization, or coupled study.
- Solver strategy: direct/iterative, segregated/fully coupled, monolithic or
  partitioned coupling, nonlinear solver, stabilization.
- Tolerances: relative/absolute tolerance, nonlinear residual, contact/coupling
  tolerance, time-step settings.
- Time stepping: initial, minimum, maximum, adaptive/manual, output times.
- Parametric sweep: parameter ranges, sampling design, continuation strategy.
- Convergence: iterations, warnings, failed cases, reruns, solver log summary.
- Post-processing: derived values, cut lines, integration regions, averaging,
  peak extraction, unit conversion.

## Nonlinear and Contact Studies

Report:

- Load stepping or continuation.
- Contact formulation and stabilization.
- Penalty or augmented Lagrangian settings when they affect results.
- Penetration tolerance or convergence behavior.
- Sensitivity to friction/contact assumptions if central to the claim.

## Coupled Studies

Report:

- Coupling direction and variables.
- Mapping between fields and meshes.
- Coupling convergence criteria.
- Time-step synchronization.
- Whether each physics was verified independently.

## Wording

Avoid "default solver settings were used" when the solver is central to the
claim. If defaults were used, state which COMSOL version and which study type so
reviewers can interpret the defaults.
