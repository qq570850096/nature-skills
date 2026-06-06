# COMSOL Reproducibility Guide

Use this for reproducibility checklists, data availability statements, and
reviewer replies about model access.

## Preferred Package

- COMSOL `.mph` files with version noted.
- Exported Java, MATLAB, or Python script when possible.
- Parameter table with units, sources, and ranges.
- Geometry source files and preprocessing notes.
- Material parameter sources and calibration data/scripts.
- Mesh settings and mesh-convergence tables.
- Solver logs, warnings, failed cases, and convergence histories.
- Exported raw data behind every figure and table.
- Post-processing scripts.
- Validation/benchmark datasets and error metrics.
- README with run order, software requirements, expected outputs, and known
  limitations.
- Checksums or release tag for files used in the manuscript.

## When `.mph` Cannot Be Shared

If proprietary or licensed components prevent sharing the full model, request:

- Exported model script or partial model.
- Full parameter table.
- Screenshots/tables of physics interfaces, mesh settings, and solver settings.
- Figure-source data and post-processing scripts.
- Validation data and benchmark description.
- A statement explaining access restrictions.

## Data Availability Wording Skeleton

```text
The COMSOL model files, parameter tables, mesh-convergence outputs, exported
figure data, and post-processing scripts are available at [repository/link].
The simulations were performed in COMSOL Multiphysics [version] using [modules].
Restrictions on [files] are due to [reason]; derived data sufficient to reproduce
the manuscript figures are provided in [location].
```

Never invent a repository link, DOI, accession, or checksum.
