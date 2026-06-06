# Model Claim: Stress-Strain

Use when claims depend on von Mises stress, principal stress, shear stress,
strain, strain energy, stress concentration, or safety factor.

Check:

- Is the reported quantity averaged, nodal, elemental, maximum, percentile, or
  extracted at a point/path/region?
- Are stress peaks near singularities, fixed constraints, point loads, sharp
  corners, or contact edges?
- Does mesh convergence monitor the stress quantity that supports the claim?
- Is the material model appropriate for the stress/strain range?
- Are failure criteria or allowable stress values supplied if safety is claimed?

Wording: "The model predicted a redistribution of stress..." is safer than
"the design eliminates failure" unless failure validation is supplied.
