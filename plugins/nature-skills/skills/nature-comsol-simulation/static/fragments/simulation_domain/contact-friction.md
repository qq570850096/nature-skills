# Simulation Domain: Contact and Friction

Use for contact pressure, wear-related interpretation, joint mechanics,
interface sliding, sealing, indentation, or frictional load transfer.

Check:

- Contact formulation, contact pair definition, normal penalty/augmented
  Lagrangian settings, friction law, and friction coefficient source.
- Local mesh refinement at contact edges and high-gradient contact patches.
- Solver convergence, load stepping, stabilization, penetration tolerance, and
  sensitivity to contact settings.
- Whether contact pressure is being interpreted as wear, damage, adhesion, or
  interface strength without additional model/experiment.
- Whether sharp edges or rigid constraints create nonphysical stress peaks.

Allowed strong claim: predicted contact-pressure redistribution under defined
contact assumptions.

Risky claim: reduced wear, improved sealing, or lower damage without wear law,
surface characterization, or experimental validation.
