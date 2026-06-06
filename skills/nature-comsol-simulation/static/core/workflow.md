# Core Workflow

Run this workflow end to end unless the user asks only for a tiny edit.

1. **Classify scope** - Detect `simulation_domain`, `model_claim`, and
   `artifact` from the manifest.
2. **Inventory evidence** - Extract geometry, material model, boundary
   conditions, mesh, solver, outputs, validation, and target claim from the
   user's input.
3. **Map claim to evidence** - State what the model directly shows, what it
   suggests, and what it cannot yet prove.
4. **Check numerical trust** - Look for mesh convergence, solver convergence,
   time-step convergence, contact/coupling stability, and sensitivity analyses
   relevant to the claim.
5. **Check physical trust** - Look for material provenance, boundary-condition
   realism, validation data, calibration, uncertainty, and benchmark comparison.
6. **Draft or audit** - Produce the requested artifact using bounded language.
7. **Expose gaps** - List missing inputs and reviewer-risk flags, with severity
   and concrete fixes when useful.
8. **Preserve traceability** - Keep all numbers, file names, versions,
   repositories, and validation claims tied to user-provided evidence.

If the user supplies a COMSOL export, figure, table, or Methods text, use it as
the source of truth. If values conflict, call out the conflict instead of
selecting the most convenient version.
