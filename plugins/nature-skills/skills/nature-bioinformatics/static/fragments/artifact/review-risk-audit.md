# Artifact: review-risk audit

## Output job

Audit the manuscript, paragraph, result, or figure from a skeptical
bioinformatics reviewer perspective.

## Risk classes

- `fatal`: unsupported central claim, data leakage, irreproducible or missing
  core analysis, unavailable required data.
- `major`: missing sample-level statistics, weak annotation, overclaimed
  communication/trajectory/spatial result, incomplete Methods.
- `minor`: unclear wording, missing package version, figure readability, weak
  legend detail.

Return prioritized risks plus concrete repair actions. Open
`references/reviewer-risk-rubric.md` for the full rubric.
