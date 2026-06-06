# Artifact: Review-Risk Audit

Audit like a skeptical methods reviewer.

Return:

- Claim-evidence map.
- High/medium/low risk flags.
- Missing inputs.
- Fixes ranked by impact.
- Wording downgrades for unsupported claims.

Core risk triggers:

- No mesh convergence for the claim-critical quantity.
- Boundary conditions or material parameters are not justified.
- Simulation outputs are written as real-world measurements.
- Validation is absent but the claim is mechanistic, clinical, or design-final.
- Contact/coupling/nonlinear solver settings are missing.
- Figures show only contours without quantitative extraction.
- COMSOL version, physics interface, and solver settings are absent from Methods.
