# External Contributor Outreach and First-Contributor Conversions, 2026

Issue: [organvm-v-logos/.github#6](https://github.com/organvm-v-logos/.github/issues/6)

Window: 2026-03-20 to 2026-04-10

Purpose: turn the improved newcomer runway into first-time external pull
requests, while keeping an auditable account of outreach, review response time,
and first-contributor cycle time.

Evidence boundary: the June 5, 2026 outcome review records that issue #6
produced `+4 merged PRs from first-time contributors` and that first-contributor
cycle time was under 14 days. This file is the repo-side ledger for the
underlying outreach and PR evidence. Direct-message outreach, email threads, and
private community notes should not be committed verbatim; record the minimal
durable pointer needed for review.

## Acceptance Criteria Coverage

| Criterion | Target | Repo-side status | Evidence |
| --- | ---: | --- | --- |
| Outreach touches to relevant contributors / communities | >= 10 | Evidence needed | Append qualifying entries to the outreach ledger below. |
| First-time external contributors submit PRs | >= 3 | Reported met | [June 5 outcome review](../../review.md) records `+4 merged PRs from first-time contributors`; PR links still need to be attached below for independent verification. |
| Median first-review response time | < 3 business days | Evidence needed | Append PR review timestamps below and calculate median business-day response. |
| Median first-contributor cycle time | < 14 days | Reported met | [June 5 outcome review](../../review.md) records cycle time under 14 days; PR timestamps still need to be attached below for independent verification. |

## Outreach Touch Ledger

A touch qualifies when it is directed at a relevant contributor, community, or
maintainer group and includes a concrete invitation to take a first contribution
step. Generic broadcast analytics, stars, follows, and passive pageviews do not
count.

**Status: 0 / 10 qualifying touches recorded in this repository.**

| # | Date | Channel / community | Target fit | Invitation / issue path | Evidence pointer | Verified by |
|:-:|:-----|:--------------------|:-----------|:------------------------|:-----------------|:------------|
| - | - | - | - | - | _No qualifying touches recorded yet._ | - |

<!-- TEMPLATE ROW:
| 1 | 2026-03-20 | GitHub issue comment / Discord / email / forum | Docs contributor interested in Jekyll onboarding | Invited them to first-contribution issue NN and linked Quick Start | https://... or private-log:YYYY-MM-DD#N | @maintainer |
-->

## First-Contributor PR Ledger

A first-contributor PR qualifies when the author is external to the creator and
the organvm automation system, had not previously contributed to the target
repository, and opened a pull request during or as a direct result of the
outreach window.

**Status: outcome review reports 4 merged first-contributor PRs; 0 / 3 PR links
recorded in this repository.**

| # | PR | Contributor | First review sent | Cycle closed | Business days to first review | Calendar days to close | Verified by |
|:-:|:---|:------------|:------------------|:-------------|------------------------------:|-----------------------:|:------------|
| - | - | - | - | - | - | - | _Attach PR evidence._ |

<!-- TEMPLATE ROW:
| 1 | https://github.com/organvm-v-logos/<repo>/pull/NN | @handle | 2026-03-24 | 2026-04-02 | 2 | 9 | @maintainer |
-->

## Median Calculations

When the PR ledger has at least three qualifying rows:

1. Sort `Business days to first review` ascending and record the median.
2. Sort `Calendar days to close` ascending and record the median.
3. Update the acceptance table above from `Evidence needed` to `Met` only when
   the calculated values satisfy the issue thresholds.
4. Link this file in the closing issue comment for
   [#6](https://github.com/organvm-v-logos/.github/issues/6).

## Operating Notes

- Use the [Quick Start guide](../../QUICK_START.md) as the landing path for
  new contributors who need repository orientation.
- Use the
  [First Contribution issue template](../../.github/ISSUE_TEMPLATE/first_contribution.md)
  for scoped work that should take less than one focused day.
- Use the [pull request template](../../.github/PULL_REQUEST_TEMPLATE.md) to
  keep review expectations explicit.
- Do not count creator-authored, bot-authored, or in-system-agent-authored pull
  requests as external first-contributor conversions.
- Do not commit private outreach text, private email addresses, or private
  community member identities without permission.

## Closeout Standard

This issue should be closed only after the ledger contains:

- at least 10 outreach touch rows,
- at least 3 first-time external PR rows,
- a median first-review response under 3 business days, and
- a median first-contributor cycle time under 14 days.

The June 5 outcome review is enough to preserve the reported result, but the
ledger rows are the durable evidence needed for an independent reviewer to verify
the issue.
