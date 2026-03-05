# Branch Protection Baseline

Apply this baseline to default branches (`main`) for all ORGAN-V repositories.

## Required Settings

1. Require a pull request before merging.
2. Require approvals: minimum 1.
3. Dismiss stale approvals when new commits are pushed.
4. Require conversation resolution before merge.
5. Require status checks to pass before merge.
6. Restrict force-pushes and deletion on protected branches.
7. Require linear history (optional but recommended).

## Required Status Checks (by repo)

### `public-process`
- `Public Process CI / validate`

### `essay-pipeline`
- `Essay Pipeline CI / test`

### `analytics-engine`
- `Analytics Engine CI / test` (or equivalent job name in workflow)

### `reading-observatory`
- `Reading Observatory CI / test` (or equivalent job name in workflow)

### `editorial-standards`
- `Editorial Standards CI / validate` (or equivalent job name in workflow)

### `.github`
- `ORGAN-V CI Minimal / validate` (or equivalent job name in workflow)

## Ownership

- Repo admin applies settings.
- Any exception requires linked issue + explicit expiry date.
