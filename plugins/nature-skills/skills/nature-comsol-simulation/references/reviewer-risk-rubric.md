# Reviewer-Risk Rubric

Use this rubric for review-risk audits and response strategy.

## High Risk

Likely to cause major revision or rejection when central to the paper:

- No validation for a real-world, clinical, safety, failure, or design-superiority
  claim.
- No mesh convergence for stress/contact/fracture/thermal-gradient quantities
  that drive the main claim.
- Boundary conditions are unrealistic, unjustified, or missing.
- Material parameters are unknown, guessed, or not sourced.
- Solver/contact/coupling instability is hidden.
- Figures are qualitative contours only while the claim is quantitative.
- The paper says "validated" when only numerical convergence was shown.

## Medium Risk

Likely reviewer question, usually fixable:

- COMSOL version or physics interface missing.
- Mesh convergence exists but monitors a secondary output.
- Parameter sweep lacks physically justified ranges.
- Sensitivity analysis missing for boundary/material assumptions.
- Validation data exist but sample size/error metric is unclear.
- Comparative contours use inconsistent scales or hidden extraction methods.

## Low Risk

Clean before submission:

- Missing units in figure labels.
- Derived-value locations not named.
- Repository/model availability statement is vague.
- Methods text uses "default settings" without enough context.
- Claim wording is stronger than evidence but easy to downgrade.

## Fix Ranking

1. Add missing validation or benchmark for central claims.
2. Add mesh/time-step/solver convergence for claim-critical outputs.
3. Add boundary/material sensitivity.
4. Revise figures to include setup, quantitative extraction, and convergence.
5. Expand Methods and reproducibility package.
6. Downgrade language where evidence cannot be added.
