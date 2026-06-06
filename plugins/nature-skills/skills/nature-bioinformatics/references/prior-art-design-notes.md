# Prior-art design notes

This skill is a design synthesis, not a copy of any public repository.

## Projects reviewed

| Project | What this skill learned |
|---|---|
| [`K-Dense-AI/scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills) | Large scientific-skill catalogues need clear taxonomy and future-proof task axes. |
| [`FreedomIntelligence/OpenClaw-Medical-Skills`](https://github.com/FreedomIntelligence/OpenClaw-Medical-Skills) | Medical/bioinformatics coverage should expose domain boundaries instead of pretending one prompt fits clinical, genomics, drug discovery, and devices equally. |
| [`ClawBio/ClawBio`](https://github.com/ClawBio/ClawBio) | Bioinformatics skills benefit from specification-first reproducibility: software, environments, demo data, checksums, and traceable contracts. |
| [`GPTomics/bioSkills`](https://github.com/GPTomics/bioSkills) | Bioinformatics work is best routed by data modality and analysis task, such as single-cell, differential expression, pathway analysis, variant calling, or metagenomics. |
| [`aipoch/medical-research-skills`](https://github.com/aipoch/medical-research-skills) | Medical research skills need audit gates and dynamic quality checks, not just fluent prose generation. |

## Patterns adopted

- Broad scientific-skill catalogues show that a biomedical skill suite needs
  task and domain axes, not a single monolithic prompt.
- Medical-skill collections show that clinical, genomics, drug-discovery, and
  bioinformatics workflows need different evidence and safety boundaries.
- Bioinformatics-first skill collections show that data modality and analysis
  task are better routing axes than manuscript section alone.
- Specification-first bioinformatics projects show that reproducibility fields,
  environment metadata, demo data, checksums, and validated scripts are useful
  when the skill moves from publication support into execution.
- Medical research skill audits show that a skill should include veto gates and
  dynamic evaluation, not only instructions for fluent output.

## How this skill uses those lessons

- It keeps `SKILL.md` short and router-like.
- It uses `manifest.yaml` for modality, claim, and artifact routing.
- It keeps audit rubrics and reporting checklists in on-demand references.
- It requires missing-input flags for reproducibility-critical fields.
- It remains publication-facing for v1, leaving execution scripts for future
  versions when the pipeline scope is explicit.
