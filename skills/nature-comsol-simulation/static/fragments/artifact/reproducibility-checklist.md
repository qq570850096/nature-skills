# Artifact: Reproducibility Checklist

Produce a traceability checklist for COMSOL/FEA publication packages.

Check:

- COMSOL version, modules, OS, and external scripts/packages.
- `.mph` model file or exported Java/MATLAB/Python script.
- Parameter table with units, sources, and ranges.
- Geometry source files and preprocessing steps.
- Material property sources and calibration scripts/data.
- Mesh settings, mesh files if exported, and convergence table.
- Solver settings, logs, convergence history, failed cases, and warnings.
- Post-processing scripts and exported raw data behind figures.
- Validation datasets, benchmark cases, and error metrics.
- Repository/access conditions, license, checksums, and README instructions.

When proprietary COMSOL files cannot be shared, request a reproducibility bundle
with exported model scripts, parameter tables, figure data, and enough settings
for reviewers to inspect the model contract.
