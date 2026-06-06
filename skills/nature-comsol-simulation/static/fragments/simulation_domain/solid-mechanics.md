# Simulation Domain: Solid Mechanics

Use for static or quasi-static stress, strain, displacement, stiffness, and
load-bearing claims in COMSOL Solid Mechanics or related FEA.

Check:

- Geometry dimensionality, symmetry, constraints, and load path.
- Material model: linear elastic, hyperelastic, plastic, viscoelastic,
  anisotropic, damage, or user-defined.
- Units and parameter provenance for elastic modulus, Poisson ratio, yield
  stress, density, damping, and thickness.
- Mesh refinement near stress concentrations, holes, fillets, contact edges,
  interfaces, and load/constraint application regions.
- Whether local peak stress is a numerical artifact or a claim-relevant quantity.

Allowed strong claim: comparative stress/displacement behavior under specified
loads when mesh and solver checks support it.

Risky claim: real failure resistance, durability, or safety margin without
material failure criteria and validation.
