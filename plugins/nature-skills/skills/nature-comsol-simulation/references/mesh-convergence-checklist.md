# Mesh-Convergence Checklist

Mesh convergence must be tied to the output that supports the paper's claim.

## What to Request

- Element type and order.
- Mesh levels: coarse, medium, fine, and optional extra-fine.
- Final element count and degrees of freedom.
- Local refinement regions and rationale.
- Monitored quantities: peak stress, averaged stress, displacement, frequency,
  contact pressure, reaction force, temperature gradient, energy release rate,
  crack path, etc.
- Convergence criterion: percent change, absolute tolerance, plateau, Richardson
  extrapolation, or uncertainty band.
- Whether the color-map contour visibly changes across mesh levels.

## Claim-Specific Requirements

| Claim | Monitor |
|---|---|
| Peak stress or stress concentration | Prefer region/path average or percentile plus peak; inspect singularities |
| Displacement or stiffness | Displacement at defined point/region and reaction force |
| Modal frequency | First N eigenfrequencies and mode-shape consistency |
| Contact pressure | Integrated force, contact area, pressure distribution, peak/average pressure |
| Thermal stress | Temperature gradient and stress at critical region |
| Fracture/damage | Crack path, energy release, process-zone resolution, length-scale dependence |

## Red Flags

- Only displacement converged while the claim relies on local stress.
- Mesh levels change geometry/contact behavior.
- Peak stress increases without bound near a singularity.
- No local refinement at contact, crack tip, interface, or fillet.
- No time-step convergence for transient/dynamic/coupled simulations.
- Mesh convergence is hidden in supplementary text without monitored quantities.

## Safer Wording

Use "mesh-independent for the monitored displacement output" rather than
"mesh-independent" if only displacement was tested.
