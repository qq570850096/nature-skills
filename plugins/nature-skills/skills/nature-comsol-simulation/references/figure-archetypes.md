# Figure Archetypes for COMSOL/FEA Papers

Use figures to connect model contract, numerical trust, and claim.

## Core Panel Types

| Panel | Purpose | Risk if missing |
|---|---|---|
| Geometry/setup | Shows geometry, material regions, loads, constraints, contacts | Reviewers cannot judge physical realism |
| Mesh/refinement | Shows element quality and local refinement | Mesh independence is not credible |
| Primary field contour | Shows stress, displacement, temperature, pressure, mode, etc. | Needs scale/unit/comparable color limits |
| Quantitative extraction | Path, region average, histogram, force, energy, frequency table | Contours alone are too qualitative |
| Convergence | Mesh/time-step/solver convergence for claim output | Numerical artifact concern |
| Sensitivity | Material, load, boundary, contact, or parameter variation | Robustness concern |
| Validation | Experiment, benchmark, analytic solution, literature comparison | Real-world claim unsupported |
| Failure/instability boundary | Failed solver cases, nonconvergence, extreme parameter ranges | Overstates model scope |

## Visual Rules

- Comparative contours must share units and color scales.
- Colorbars need physical units and readable labels.
- Crop only after showing the full setup somewhere.
- Do not hide constraints, loads, contact regions, or interfaces.
- Use extracted values for claims; use contours for spatial context.
- For local maxima, report extraction method and singularity handling.

## Nature-Style Figure Logic

High-impact figures usually show:

1. Why the model is physically meaningful.
2. What the model predicts.
3. Why the prediction is numerically trustworthy.
4. Why the prediction matters beyond a single contour plot.
