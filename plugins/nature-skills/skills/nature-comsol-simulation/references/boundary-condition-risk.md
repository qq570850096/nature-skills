# Boundary-Condition Risk Guide

Boundary conditions define the model's physical world. Treat them as part of the
claim, not as implementation detail.

## Inputs to Expose

- Loads: magnitude, direction, distribution, time/frequency history, source.
- Constraints: fixed, prescribed displacement, symmetry, periodic, elastic
  support, remote constraint, rigid connector.
- Contact: pair definition, normal behavior, tangential/friction law,
  coefficient, penalty/stabilization, allowed separation/sliding.
- Thermal: heat flux, convection coefficient, radiation, temperature, contact
  conductance, heat source, initial condition.
- Fluid/FSI: inlet/outlet, pressure, flow rate, wall condition, turbulence,
  coupling interface, pressure mapping.
- Initial conditions: stress, displacement, temperature, velocity, pre-load.

## Risk Patterns

| Pattern | Why reviewers object |
|---|---|
| Fully fixed boundary where real support is compliant | Overconstrains stiffness and stress |
| Point load or sharp constraint | Creates stress singularity |
| Symmetry used without showing load/geometric symmetry | Can suppress real modes or deformation |
| Friction coefficient assumed without source | Contact pressure and shear become arbitrary |
| Simplified thermal boundary | Thermal gradients and stresses become scenario-specific |
| Patient/device loading not representative | Clinical or design claims overreach |

## Audit Prompt

Ask: if this boundary condition changed within a plausible range, would the
paper's main conclusion remain true? If not, the manuscript needs sensitivity
analysis or softer wording.
