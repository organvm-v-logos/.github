# README Standards Overlay (ORGAN-V Logos)

This document is an organ-level overlay for README policy in `organvm-v-logos`.

## Canonical Upstream

Canonical full standards live in:
- `meta-organvm/.github/README_STANDARDS.md`

This overlay can add stricter local requirements but cannot weaken upstream
requirements.

## Local Profiles

Use the profile that matches the repository type.

### Profile A: Governance Repo (`.github`)

Required:
- `#` title
- `## Included Governance Assets`
- links to org governance docs (for example branch protection baseline)

### Profile B: Flagship Narrative Repo (`public-process`)

Required:
- `#` title
- `## Introduction`
- `## Methodology`
- `## Lessons Learned`

### Profile C: Code/Automation Repos

Applies to:
- `essay-pipeline`
- `editorial-standards`
- `analytics-engine`
- `reading-observatory`

Required:
- `#` title
- one context section: `## Overview` or `## Current State` or `## Introduction`
- one execution section: `## Development` or `## Setup` or `## Getting Started`

Recommended:
- `## Architecture`
- `## Testing` and/or validation commands
- CI badge near top

## Enforcement

Local minimum checks are enforced by:

```bash
./tools/audit_platform_standards.sh
```

Violations must be fixed in the same PR or tracked in a linked issue with owner
and due date.
