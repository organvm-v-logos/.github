# Weekly Signals Triage Ritual

> The recurring human-judgment ritual that turns automatically generated
> metrics into concrete weekly decisions and shipped fixes.
> Tracking issue: [organvm-v-logos/.github#4](https://github.com/organvm-v-logos/.github/issues/4).

ORGAN-V is the *Logos* organ — it works in the open and keeps an honest account
of what exists. Automation in
[`analytics-engine`](https://github.com/organvm-v-logos/analytics-engine)
produces signals every week. **Automation cannot decide what to do about them.**
Prioritization, tradeoffs, and the choice to ship — or deliberately not ship — a
fix require judgment. This directory is the decision record for that judgment.

- The **ritual** (process) is defined below.
- The **decision record** (every weekly cycle, its decisions, and the
  remediation it produced) lives in [`triage-log.md`](triage-log.md).

---

## Cadence

- **Weekly**, starting **Monday 2026-03-16**.
- Each cycle is labeled `Wn` and dated by the **Monday** the
  `weekly-signals` artifact is published.
- A cycle is *closed* when every signal classified `Act` has either shipped a
  remediation or been explicitly deferred with a reason.

## Inputs

These are produced by `analytics-engine` and are the canonical inputs to each
cycle:

| Input | What it carries |
|:------|:----------------|
| `analytics-engine/data/weekly-signals.json` | Machine-readable signal set: metric deltas, anomalies, threshold breaches. |
| `analytics-engine/data/weekly-signals.md` | Human-readable narration of the same signals. |
| `analytics-engine/data/system-engagement-*` | Engagement time-series (traffic, conversion path, referrers) backing the signals. |

**Evidence boundary.** Raw analytics exports are **not** committed to this
governance repository. This directory holds the *decisions* taken on those
signals and pointers back to the source artifact, not the raw data. Confidence
notes in the log distinguish directional evidence from statistically strong
proof, matching the convention in
[`docs/logos/distribution-conversion-experiments-2026.md`](../logos/distribution-conversion-experiments-2026.md).

## The triage process (one cycle)

1. **Pull** the week's `weekly-signals` artifact from `analytics-engine`.
2. **Classify** every signal into exactly one decision (taxonomy below).
3. **Open remediation** for each `Act` signal — a concrete, owned, datable work
   item (a follow-up issue or a direct change), not a note-to-self.
4. **Ship or defer.** Land the fix, or defer it with an explicit reason and a
   review date. Silence is not an allowed outcome.
5. **Record** the cycle in [`triage-log.md`](triage-log.md): signals, decisions,
   remediation items with status, and the cycle's publish-to-remediation latency.

### Decision taxonomy

Every signal gets exactly one label:

| Decision | Meaning | Produces |
|:---------|:--------|:---------|
| **Act** | Worth changing something now. | A remediation item with an owner and a target date. |
| **Watch** | Real but not yet actionable; needs another week (or N) of data to separate signal from noise. | A watch entry with the trigger that would promote it to `Act`. |
| **Ignore** | Explained, expected, or below the materiality bar. | A one-line rationale (so it is not re-litigated next week). |

A signal may be promoted `Watch → Act` in a later cycle; the log links the two
cycles when that happens.

## The remediation loop

The point of the ritual is *shipped* fixes, not a tidy backlog.

- Each `Act` signal becomes a remediation item with a state:
  **open → shipped** (or **deferred**, with reason + review date).
- Fixes ship in the relevant repo (`public-process`, `essay-pipeline`,
  `analytics-engine`, `editorial-standards`, …). The triage log records what
  shipped and where, with a pointer.
- A remediation item is only marked **shipped** when the change is merged and
  live — not when it is planned.

### Latency SLA

- **Metric:** *publish-to-remediation latency* — days from the Monday the signal
  was published to the day its remediation shipped.
- **Target:** **median ≤ 7 days** per rolling cycle.
- **Tracked** per cycle and as a rolling figure in
  [`triage-log.md`](triage-log.md#latency-rollup). The
  [June 5 outcome review](../../review.md) confirmed the ritual holding at
  **~6 days** and decided **MAINTAIN**.

## Integrity rules

Inherited from the [external-validation integrity rules](../external-validation/README.md#integrity-rules):

- Record decisions against **real** published signals; never invent a signal to
  justify a change you wanted to make anyway.
- Every `shipped` remediation must carry a pointer a third party can check.
- If a remediation is later reverted or found ineffective, strike it (keep it
  visible with a note) and reopen the signal in the current cycle.
- `Ignore` requires a written rationale; "no comment" is not a decision.

## How to run a cycle (checklist)

```
[ ] Pull this week's weekly-signals artifact from analytics-engine.
[ ] Classify every signal: Act / Watch / Ignore.
[ ] For each Act: open an owned, dated remediation item.
[ ] Ship the fix, or defer it with a reason + review date.
[ ] Append the cycle to triage-log.md (signals, decisions, remediation, latency).
[ ] Update the latency rollup.
[ ] Promote any Watch items whose trigger fired this week.
```

---

*ORGAN-V: Logos — Public Process. This is a Pragma document: the honest account
of decisions taken on real signals.*
