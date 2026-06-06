# Output format

Unless the user asks for another format, return:

```text
Detected scope
- data_modality:
- analysis_claim:
- artifact:

Terminology ledger
| Canonical term | First-use definition | Variants seen | Decision |
|---|---|---|---|

Claim-evidence map
| Claim | Evidence tier | Support supplied | Missing input or boundary |
|---|---|---|---|

[Requested artifact]
[ready-to-use prose, figure plan, response strategy, audit, or checklist]

Reviewer-risk flags
- [specific risk or "None identified from supplied material"]

Missing inputs / placeholders
- [specific item or "None"]

中文核对
- [include when the user writes in Chinese or gives Chinese author notes]
```

For short requests, compress the terminology ledger and claim-evidence map, but
do not omit missing-input or risk flags.
