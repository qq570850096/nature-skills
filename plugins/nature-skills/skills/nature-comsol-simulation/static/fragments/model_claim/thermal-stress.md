# Model Claim: Thermal Stress

Use when claims depend on temperature gradients, thermal expansion, residual
stress, thermal cycling, heat-induced deformation, or thermoelastic coupling.

Check:

- Temperature field and mechanical field must refer to the same operating
  condition and coupling assumption.
- Report thermal boundary conditions, heat-transfer coefficients, contact
  conductance, and temperature-dependent material properties when used.
- Mesh/time-step convergence should monitor both thermal gradients and stresses.
- Thermal safety or fatigue claims need material limits and validation.

Wording: "the coupled model predicted elevated stress near the thermal gradient"
is safer than "thermal failure is prevented" without validation.
