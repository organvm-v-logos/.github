# README Standards

Canonical README standards for all repositories in `organvm-v-logos`.

## Canonical Location

This file in `.github` is the source of truth for README standards for this org.

If this policy is later promoted across multiple organs, upstream it to
`meta-organvm/.github` and keep this file as a mirror with an explicit link to
the upstream canonical policy.

## Profiles

Use the profile that matches the repository type.

### Profile A: Governance Repo (`.github`)

Required:
- `#` title
- `## Included Governance Assets`
- Links to org-level governance docs (for example branch protection baseline)

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
- One context section: `## Overview` or `## Current State` or `## Introduction`
- One execution section: `## Development` or `## Setup` or `## Getting Started`

Recommended:
- `## Architecture`
- `## Testing` and/or validation commands
- CI badge near top

## Enforcement

The minimum required items above are enforced by:

```bash
./tools/audit_platform_standards.sh
```

Any violation should be fixed in the same PR or tracked in a linked issue with
an owner and due date.
