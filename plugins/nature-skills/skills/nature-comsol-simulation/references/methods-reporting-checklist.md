# Methods Reporting Checklist

Use this before finalizing any COMSOL/FEA Methods section.

## Model Definition

- COMSOL Multiphysics version and modules.
- Physics interfaces and study type.
- Geometry source, simplification, dimensionality, and symmetry.
- Coordinate system, unit system, and reference configuration.
- Domain/material assignment.

## Material and Constitutive Model

- Material law and parameters.
- Parameter units and sources.
- Linear/nonlinear, isotropic/anisotropic, elastic/plastic/viscoelastic/
  hyperelastic/damage assumptions.
- Temperature, strain-rate, or frequency dependence when relevant.
- Calibration procedure and dataset if fitted.

## Boundary Conditions and Coupling

- Loads, constraints, displacement/pressure/temperature/flux inputs.
- Contact/friction definitions.
- Initial conditions.
- Coupling variables and interface mapping for multiphysics.
- Justification for simplified or idealized conditions.

## Mesh and Solver

- Element type/order and mesh-generation settings.
- Local refinement and mesh-quality checks.
- Mesh/time-step convergence method and monitored quantities.
- Solver type, tolerance, nonlinear settings, time stepping, and convergence
  criteria.
- Failed or unstable cases if they affect model scope.

## Outputs and Validation

- Derived values and post-processing definitions.
- Region/path/point extraction methods.
- Parameter sweep or optimization settings.
- Verification benchmark, validation experiment, or literature comparison.
- Error metrics and acceptance criteria.

## Availability

- `.mph` file, exported model script, parameter table, raw exported figure data,
  solver logs, validation data, and repository/accession if shareable.
