# Pipeline Health Runbook

Operational recovery procedure for the ORGAN-V autonomous content pipeline,
monitored by `.github/workflows/health-heartbeat.yml`.

## What the heartbeat checks

Every Monday at 12:00 UTC (and on manual `workflow_dispatch`) the heartbeat
verifies that the upstream weekly pipelines produced a successful run in the
last 7 days, plus that at least one auto-draft essay PR merged:

| Check | Repo | Workflow |
| --- | --- | --- |
| Weekly Metrics | `analytics-engine` | `weekly-metrics.yml` |
| Weekly Feeds | `reading-observatory` | `weekly-feeds.yml` |
| Weekly Intelligence | `essay-pipeline` | `weekly-intelligence.yml` |
| Essay Publication | `public-process` | auto-draft PRs merged |

When any check is not `success`, the heartbeat files (or updates) a
`health-check` issue and exits non-zero.

## Reading the result codes

- **`success`** — a run completed successfully in the window. Healthy.
- **`none`** — **no run occurred in the window.** This is the most common stall
  cause. GitHub **automatically disables `cron`-scheduled workflows after 60
  days of repository inactivity**. Low-touch upstream content repos cross that
  threshold and their weekly schedule goes dormant silently. No `weekly-*` run
  means no drafts, which is why "no auto-draft PRs merged" usually appears at
  the same time.
- **`failure`** — a run executed but errored. Usually an expired/rotated API key
  or token in the upstream repo, or an upstream bug.
- **`error`** — the heartbeat could not query the upstream API (repo missing,
  renamed, or token lacks read access).

## Recovery

### Automatic (preferred)

Set the `PIPELINE_DISPATCH_TOKEN` organization secret to a token (PAT or GitHub
App installation token) with `actions:write` on the content repos. When present,
the heartbeat **self-heals** on each run: for any `none`/`failure` check it
re-enables the workflow and triggers a fresh `workflow_dispatch` run. The
dispatch both backfills the missing week and counts as repository activity,
re-arming the 60-day cron clock. The actions taken are recorded in the issue
under **Automatic remediation attempted**.

The built-in `GITHUB_TOKEN` is scoped to `.github` only and **cannot** write to
other repos' Actions, so cross-repo self-heal requires this dedicated secret.

### Manual

Run per failing check (replace `<repo>`/`<workflow>` from the table):

```bash
# 1. Re-enable the schedule if a `none` result indicates it was auto-disabled
gh workflow enable <workflow> --repo organvm-v-logos/<repo>

# 2. Trigger a run now — backfills the week and re-arms the 60-day cron clock
gh workflow run <workflow> --repo organvm-v-logos/<repo>

# 3. Confirm the run started and watch its conclusion
gh run list --workflow <workflow> --repo organvm-v-logos/<repo> --limit 1
```

For a `failure` result, open the failing run's logs first and rotate any expired
secrets before re-dispatching:

```bash
gh run view --repo organvm-v-logos/<repo> --log-failed
```

For the **Essay Publication** check, a green `weekly-intelligence.yml` run should
re-open auto-draft PRs in `public-process`. If drafts exist but were not merged,
review and merge them (or check the auto-merge policy).

## Preventing recurrence

- Keep `PIPELINE_DISPATCH_TOKEN` set so stalls self-heal at the next heartbeat
  rather than waiting for human intervention.
- The weekly dispatch run is itself the keepalive — as long as the heartbeat can
  re-dispatch, the upstream crons never reach the 60-day inactivity cutoff.
- The heartbeat updates the existing open `health-check` issue instead of
  opening a new one each week, so a single issue tracks an ongoing stall until
  it clears.

## Incident log

| Date | Issue | Symptom | Root cause | Resolution |
| --- | --- | --- | --- | --- |
| 2026-06-01 | [#14](https://github.com/organvm-v-logos/.github/issues/14) | All three weekly checks `none`; no auto-draft PRs merged | Upstream `cron` schedules auto-disabled after 60 days of repo inactivity | Hardened heartbeat to self-heal (re-enable + re-dispatch) and authored this runbook; manual recovery steps above applied to re-arm the schedules |
