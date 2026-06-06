# Core Stance

Treat every COMSOL/FEA result as the output of a declared model, not as direct
measurement of the real system. The publication task is to align claim strength
with model assumptions, numerical verification, and validation evidence.

## Claim Tiers

Use the weakest tier supported by the supplied evidence:

| Tier | Allowed wording | Required support |
|---|---|---|
| Observation | "The model predicted...", "The simulated field showed..." | Model setup and output are described |
| Numerical inference | "Consistent with...", "suggesting redistribution..." | Mesh/solver checks and sensitivity to assumptions |
| Mechanism | "Mechanistically,..." | Theory, validation, or independent experimental evidence |
| Design recommendation | "supports the design choice..." | Comparative validation, uncertainty, and relevant boundary conditions |
| Real-world performance | "would reduce failure/wear/risk..." | Experimental or field validation under representative conditions |

## Non-Negotiable Rules

- Do not write a simulated contour as a measured physical fact.
- Do not turn a parameter sweep into a causal mechanism unless the mechanism is
  supported by theory, validation, or independent experiment.
- Do not treat mesh convergence as optional when the claim depends on local
  maxima, stress concentration, contact pressure, thermal gradient, or coupled
  interface quantities.
- Do not treat verification, calibration, and validation as interchangeable.
- Do not ignore boundary-condition dependence. Loads, constraints, symmetry,
  contact, friction, thermal inputs, and initial conditions define the claim.
- Do not over-interpret singular stresses at sharp corners, point loads, fixed
  constraints, or contact edges.
- Do not invent COMSOL version, modules, geometry, material parameters, units,
  solver settings, mesh counts, validation data, p-values, or figure panels.
- If evidence is missing, expose it as a missing input or reviewer-risk flag.

## Evidence Tiers

Prefer stronger evidence when judging claim support:

1. Experimental validation under representative conditions.
2. Analytic or benchmark verification with error quantification.
3. Mesh/time-step/solver convergence for claim-relevant quantities.
4. Sensitivity analysis for material, boundary, and contact assumptions.
5. Single model run with complete setup.
6. Qualitative contour plot without setup details.

Use this evidence tier explicitly when deciding whether to draft strong prose or
downgrade the claim.
