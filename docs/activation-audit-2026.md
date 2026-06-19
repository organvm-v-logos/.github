# Activation Audit — `organvm-v-logos/.github`

Issue: [organvm-v-logos/.github#15](https://github.com/organvm-v-logos/.github/issues/15)

Audit date: 2026-06-19 · Verdict: **ACTUALLY-LIVE — ship now**

## Purpose

An *activation audit* answers one question honestly: is this repository
**genuinely live and doing its job**, or is it a frozen skeleton that merely
*looks* shipped? A repo can carry every expected file and still be inert — dead
workflows in the wrong directory, enforcement scripts that don't exist,
documentation that describes capabilities nothing implements.

This is a Pragma document: the honest account of what actually exists and runs,
verified against the files in the repository, not against intentions. Each asset
below was inspected and given one of three states:

- **LIVE** — present, non-stub, and wired so it actually executes or applies.
- **DEAD** — present but inert (never runs / nothing reads it).
- **MISSING** — referenced by the repo but absent.

## The shipped test

The defining function of an org `.github` repo is to publish the organization
profile and serve community-health defaults to every sibling repo. The shipped
test is therefore: **does the org profile render publicly, and are the defaults
real?**

- `profile/README.md` — present, 9.3 KB, substantive (identity, why-build-in-public,
  repository table, Mermaid architecture map, eight-organ context). This is the
  surface GitHub renders at `github.com/organvm-v-logos`. **PASS.**
- Community-health defaults (`CONTRIBUTING`, `CODE_OF_CONDUCT`, `SECURITY`,
  issue + PR templates) — present and non-stub; GitHub falls these through to
  every sibling repo that lacks its own. **PASS.**

**Shipped test: PASS.**

## Asset inventory

### Org profile & community health

| Asset | State | Evidence |
| --- | --- | --- |
| `profile/README.md` | LIVE | Org-profile surface; substantive, renders publicly |
| `README.md` | LIVE | Repo landing; links the governance assets |
| `CONTRIBUTING.md` | LIVE | Standard fork → branch → PR workflow, 59 lines |
| `CODE_OF_CONDUCT.md` | LIVE | 78 lines |
| `SECURITY.md` | LIVE | Advisory + email path, response timeline |
| `QUICK_START.md` | LIVE | Newcomer entry point, linked from both READMEs |
| `CODEOWNERS` | LIVE | `* @4444j99` |

### Templates

| Asset | State | Evidence |
| --- | --- | --- |
| `.github/ISSUE_TEMPLATE/bug_report.md` | LIVE | Valid frontmatter (`name`/`about`) |
| `.github/ISSUE_TEMPLATE/feature_request.md` | LIVE | Valid frontmatter |
| `.github/ISSUE_TEMPLATE/documentation.md` | LIVE | Valid frontmatter |
| `.github/ISSUE_TEMPLATE/first_contribution.md` | LIVE | Valid frontmatter |
| `.github/ISSUE_TEMPLATE/external_feedback.yml` | LIVE | Issue form for the external-validation ledger |
| `.github/ISSUE_TEMPLATE/config.yml` | LIVE | Contact links to corpus, essays, consult |
| `.github/PULL_REQUEST_TEMPLATE.md` | LIVE | Summary / type / checklist |

### Governance baselines

| Asset | State | Evidence |
| --- | --- | --- |
| `BRANCH_PROTECTION_BASELINE.md` | LIVE | Per-repo required-check matrix |
| `README_STANDARDS.md` | LIVE | Org-level README overlay, A/B/C profiles |
| `seed.yaml` | LIVE | Automation contract; `implementation_status: PRODUCTION` |
| `.githooks/pre-commit` | LIVE | Validates workflow YAML + issue-template frontmatter |

### Automation

| Asset | State | Evidence |
| --- | --- | --- |
| `.github/workflows/health-heartbeat.yml` | LIVE | Weekly cron + dispatch; monitors 4 sibling pipelines, self-heals stalls, files/updates a `health-check` issue |
| `.github/workflows/stale.yml` | LIVE | Weekly cron; `actions/stale@v10`, 60d→14d |
| `.github/workflows/dependabot-auto-merge.yml` | LIVE | Auto-merges patch/minor dependabot PRs |
| `.github/workflows/dispatch-receiver.yml` | LIVE | Receives 8 cross-org `repository_dispatch` event types |
| `.github/workflows/ci-minimal.yml` | LIVE | README presence, `seed.yaml` validity, secret scan |
| `.github/dependabot.yml` | LIVE | Monthly grouped `github-actions` updates |

All five `.github/workflows/*.yml` files are syntactically valid and the
pre-commit hook re-checks them on every relevant commit. The heartbeat is the
load-bearing one: it is the keepalive that prevents the upstream weekly content
crons from being auto-disabled after 60 days of inactivity
(see [`docs/ops/pipeline-health-runbook.md`](ops/pipeline-health-runbook.md)).

## Findings

Three gaps were found. None falsifies the actually-live verdict, but two
directly contradicted the "everything here runs" claim and were fixed in the
same change as this audit. The third needs an external source of truth and is
left open and visible.

1. **`workflows/stale.yml` was a dead duplicate (FIXED).** A second stale
   workflow lived at the repo-root `workflows/` path. GitHub only executes
   workflows under `.github/workflows/`, so this file never ran — and it pinned
   the older `actions/stale@v9` while the live copy is on `@v10`. It was pure
   dead weight that made the repo look like it had two stale sweeps when it has
   one. **Removed.**

2. **`README_STANDARDS.md` referenced a non-existent script (FIXED).** Its
   Enforcement section pointed at `./tools/audit_platform_standards.sh`; there is
   no `tools/` directory in this repo. The reference was repointed to the
   enforcement that actually exists here: the `.githooks/pre-commit` hook and the
   CI Minimal `validate` job.

3. **Essay-count drift across surfaces (OPEN).** `profile/README.md` states
   "40 published essays" in two places, its portfolio-hub footer says "49
   Essays", and the system `published_essays` variable reads 29. These cannot
   all be current. Reconciling them requires the live count from
   `public-process`, which is outside this governance repo, so this is flagged
   rather than guessed. Tracked for a follow-up that sets a single source of
   truth.

## Verdict

`organvm-v-logos/.github` is **actually-live**, not a frozen skeleton:

- The shipped test passes — the org profile and community-health defaults are
  real and public.
- Every claimed automation runs from the correct path with valid syntax.
- The two defects that undercut the live claim (a dead duplicate workflow and a
  dangling enforcement reference) are removed/corrected.

**Ship now.** One non-blocking follow-up remains: reconcile the published-essay
count to a single source of truth.
