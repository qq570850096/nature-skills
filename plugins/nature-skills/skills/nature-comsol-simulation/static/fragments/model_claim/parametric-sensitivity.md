# Model Claim: Parametric Sensitivity

Use when claims depend on parameter sweeps, sensitivity analysis, robustness,
uncertainty, design variables, or response surfaces.

Check:

- State parameter ranges, units, sampling design, baseline values, and whether
  ranges are physically or experimentally justified.
- Distinguish one-factor sweeps from global sensitivity or uncertainty analysis.
- Report monitored outputs and whether interactions between parameters were
  tested.
- Avoid causal language for monotonic trends unless supported by theory.
- For optimization, reserve held-out validation or independent checks if
  possible.

Wording: "within the tested range, stress was most sensitive to..." is safer
than "parameter X controls failure" without validation.
