# Model Verification Checklist

Verification asks: did the numerical model solve the intended equations
correctly enough for the claim?

## Minimum Questions

- What equations, physics interfaces, or COMSOL modules are being solved?
- Is there an analytic solution, canonical benchmark, manufactured solution, or
  literature benchmark for the same physics?
- Which outputs are benchmarked: displacement, stress, reaction force, frequency,
  pressure, temperature, contact area, or coupled response?
- Is the error metric defined: absolute error, relative error, norm, slope,
  frequency difference, phase error, or experimental uncertainty band?
- Are units and coordinate frames consistent across model and benchmark?

## Verification Evidence

Strong evidence:

- Analytic or benchmark comparison with error metric.
- Mesh/time-step/solver convergence for claim-critical outputs.
- Conservation or balance checks: force balance, energy balance, heat balance,
  mass balance, or reaction-force consistency.
- Sensitivity to solver tolerances, contact penalties, coupling tolerances, and
  time-step choices when relevant.

Weak evidence:

- "The model converged" without monitored quantities.
- One screenshot of a contour plot.
- Validation against one experiment while numerical convergence is unreported.

## Reporting Template

Use:

```text
Model verification was assessed by [benchmark/convergence/balance check].
The monitored quantities were [outputs], selected because they directly support
[claim]. Agreement/convergence was evaluated using [metric and threshold].
```

Do not use "validated" for these checks unless real-system validation is also
provided.
