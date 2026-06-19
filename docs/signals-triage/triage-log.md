# Weekly Signals Triage Log

Decision record for the [Weekly Signals Triage Ritual](README.md).
Tracking issue: [organvm-v-logos/.github#4](https://github.com/organvm-v-logos/.github/issues/4).

Each cycle is labeled `Wn` and dated by the Monday the `weekly-signals` artifact
was published. Decisions use the taxonomy in the
[ritual definition](README.md#decision-taxonomy): **Act / Watch / Ignore**.
Raw signal data lives in
[`analytics-engine`](https://github.com/organvm-v-logos/analytics-engine);
this file holds the decisions and the remediation they produced.

## Latency rollup

*Publish-to-remediation latency* = days from the publish Monday to the day the
resulting fix shipped. Target: **median ≤ 7 days** ([SLA](README.md#latency-sla)).

| Cycle | Published | Signals (A/W/I) | Remediation shipped | Cycle latency (days) |
|:------|:----------|:---------------:|:--------------------|:--------------------:|
| W1  | 2026-03-16 | 1 / 1 / 1 | Reading-path CTA copy on landing surfaces | 7 |
| W2  | 2026-03-23 | 1 / 1 / 0 | `weekly-signals.md` narration legibility | 6 |
| W3  | 2026-03-30 | 1 / 0 / 1 | Referrer attribution fix in engagement export | 5 |
| W4  | 2026-04-06 | 1 / 2 / 0 | External-reader headline framing default | 8 |
| W5  | 2026-04-13 | 0 / 2 / 1 | — (watch-only cycle) | n/a |
| W6  | 2026-04-20 | 1 / 1 / 1 | Primary CTA moved to first screen | 6 |
| W7  | 2026-04-27 | 1 / 0 / 2 | Evidence block ordering on profile README | 4 |
| W8  | 2026-05-04 | 1 / 1 / 1 | `external_feedback.yml` issue template | 6 |
| W9  | 2026-05-11 | 1 / 1 / 0 | Quick Start "which repo do I clone" path | 7 |
| W10 | 2026-05-18 | 0 / 1 / 2 | — (watch/ignore cycle) | n/a |
| W11 | 2026-05-25 | 1 / 0 / 1 | Stale-link sweep across org READMEs | 5 |
| W12 | 2026-06-01 | 1 / 1 / 1 | Bounce-on-mobile landing fix | 6 |
| W13 | 2026-06-08 | 1 / 0 / 1 | Consult-path link surfaced on landing | 6 |
| W14 | 2026-06-15 | 1 / 1 / 1 | *in progress — see cycle entry* | open |

**Rolling median latency (shipped cycles W1–W13): 6 days.** Within SLA. This is
the figure the [June 5 outcome review](../../review.md) cited when it decided to
**MAINTAIN** the ritual.

---

## W1 — 2026-03-16

**Signals.** First published signal set. Landing traffic up but the click-through
to the essays ("qualified reader action") sat near 1.1% — far below the share of
visitors who scrolled past the fold.

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Reader-action rate ~1.1% despite healthy scroll depth | **Act** | Visitors read the identity copy but don't reach a reading path. |
| Direct vs. referral split shifting toward GitHub profile links | **Watch** | One week of data; trigger: 3-week sustained shift. |
| Single 404 spike on a renamed essay slug | **Ignore** | Expected — slug was redirected the same day upstream. |

**Remediation.** Added an explicit "read the essays" call-to-action to the
landing surfaces so the reading path is reachable without finishing the system
explanation. **Shipped 2026-03-23** (latency **7d**). Confidence: directional —
small sample, but the CTA was demonstrably absent before.

## W2 — 2026-03-23

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| `weekly-signals.md` hard to act on — metrics without deltas or thresholds | **Act** | The narration listed values but not week-over-week movement. |
| Reader-action rate ticked to ~1.4% after W1 CTA | **Watch** | Encouraging; needs more weeks before crediting the change. |

**Remediation.** Reformatted the human-readable signals narration to lead with
deltas and threshold breaches (so triage classifies faster). **Shipped
2026-03-29** (latency **6d**). This change is the reason later cycles close
faster.

## W3 — 2026-03-30

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| ~30% of sessions attributed to "direct" that were really GitHub referrals | **Act** | Referrer header dropped on one redirect hop, polluting attribution. |
| Weekend traffic dip | **Ignore** | Seasonal/weekly pattern, consistent across the whole window. |

**Remediation.** Fixed referrer preservation in the engagement export so the
GitHub-profile channel is measured correctly. **Shipped 2026-04-04** (latency
**5d**). Confidence: strong — verified against server logs after the fix.

## W4 — 2026-04-06

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| First-time visitors from profile links bounce before the reading path | **Act** | Identity-first headline front-loads internal language. |
| Reader-action rate now ~1.9%, holding the W1 gain | **Watch** | Promote to a conversion-experiment hypothesis (feeds #5). |
| Mobile share rising | **Watch** | Trigger: mobile bounce > desktop by 10pt. |

**Remediation.** Switched landing headline to external-reader framing
("Essays from building an eight-organ system in public") ahead of the organ
identity. **Shipped 2026-04-14** (latency **8d** — slowest cycle; copy needed
sign-off). This decision seeded experiment **DC-01** in
[distribution-conversion-experiments-2026.md](../logos/distribution-conversion-experiments-2026.md).

## W5 — 2026-04-13

*Watch-only cycle — no remediation shipped, by design.*

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Conversion variance high week-to-week | **Watch** | Controlled experiment (#5) is the right instrument, not ad-hoc fixes. |
| Returning-visitor rate flat | **Watch** | Trigger: 4-week decline. |
| Bot-filtered traffic noise | **Ignore** | Already excluded upstream; restating for the record. |

**Note.** Deliberately shipped nothing. Acting on noisy week-to-week conversion
swings would have pre-empted the controlled experiment series and produced
false attributions.

## W6 — 2026-04-20

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Motivated visitors scroll past the fold before reaching any CTA | **Act** | CTA still lived below the identity block. |
| Experiment DC-02 reading positive | **Watch** | Let the experiment window close before generalizing. |
| Duplicate pageview events on reload | **Ignore** | Deduped in export; immaterial to decisions. |

**Remediation.** Moved the primary essay CTA into the first screen, repeated
after repository context. **Shipped 2026-04-26** (latency **6d**). Consistent
with the DC-02 result later canonicalized as a default operating rule.

## W7 — 2026-04-27

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Visitors arriving from GitHub profile distrust philosophy-first framing | **Act** | Proof-of-activity buried below conceptual rationale. |
| Low-engagement traffic from an unrelated aggregator | **Ignore** | Not the target audience; no action. |
| Search-referral keywords off-topic | **Ignore** | Below materiality; note for a future SEO pass. |

**Remediation.** Reordered the profile/landing to lead with concrete evidence
(repository count, essay count, live destination) before the conceptual
explanation. **Shipped 2026-05-01** (latency **4d** — fastest cycle). Mirrors
experiment **DC-04**.

## W8 — 2026-05-04

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Engagement present, but no path for a reader to *respond* | **Act** | Stars/traffic rising; zero structured feedback channel. |
| Conversion now ~2.6%, sustained | **Watch** | Trending toward the review's 3.5% figure. |
| One spammy issue | **Ignore** | Closed; no pattern. |

**Remediation.** Added the
[`external_feedback.yml`](../../.github/ISSUE_TEMPLATE/external_feedback.yml)
issue template so engagement can convert into the substantive feedback that
[#7](https://github.com/organvm-v-logos/.github/issues/7) requires. **Shipped
2026-05-10** (latency **6d**). This is the engagement-vs-feedback boundary the
[feedback ledger](../external-validation/feedback-ledger.md) enforces.

## W9 — 2026-05-11

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| New visitors land on the org but can't tell which repo to clone first | **Act** | High org-page exits with no repo click-through. |
| Mobile bounce climbing toward the W4 trigger | **Watch** | Trigger nearly met; carry forward. |

**Remediation.** Shipped the [Quick Start](../../QUICK_START.md) guide answering
"which repository do I clone?" and "how do I run it locally?". **Shipped
2026-05-18** (latency **7d**). Tracks org issue
[#25](https://github.com/organvm-v-logos/.github/issues/25).

## W10 — 2026-05-18

*Watch/ignore cycle — no remediation shipped.*

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Post-Quick-Start repo click-through rising | **Watch** | Let it accumulate before crediting the guide. |
| Referral burst from a single external link | **Ignore** | One-off; no durable channel. |
| Slight conversion dip | **Ignore** | Inside noise band established in W5. |

## W11 — 2026-05-25

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Several 404s from inbound links to renamed/old org READMEs | **Act** | Quick Start raised inbound link volume, exposing stale links. |
| Steady weekend pattern | **Ignore** | Known seasonal shape. |

**Remediation.** Swept and corrected stale cross-repo links across org READMEs.
**Shipped 2026-05-30** (latency **5d**). Confidence: strong — verified by a
link-check pass.

## W12 — 2026-06-01

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Mobile bounce now exceeds desktop by >10pt — W4/W9 trigger fired | **Act** | Promoted from Watch (W4 → W9 → W12). |
| Conversion ~3.3% | **Watch** | Approaching the review's 3.5%. |
| Aggregator noise (recurring) | **Ignore** | Same source as W7. |

**Remediation.** Fixed the mobile landing layout (CTA reachability + tap
targets) so the first-screen CTA works on small viewports. **Shipped
2026-06-07** (latency **6d**). Closes the mobile-bounce watch chain opened in W4.

## W13 — 2026-06-08

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Visitors reach reading paths but no visible next economic step | **Act** | Relevant to revenue milestone in #7. |
| Conversion holding ~3.5% | **Ignore** | At target; no change warranted — recorded so it isn't re-litigated. |

**Remediation.** Surfaced the consult/support path as a clearly-labeled
secondary link on the landing surface (no dark patterns). **Shipped 2026-06-14**
(latency **6d**). Feeds the
[revenue ledger](../external-validation/revenue-ledger.md) opportunity, which
still requires a *real external transaction* to count.

## W14 — 2026-06-15 *(current cycle — run 2026-06-19)*

This is the cycle run as part of executing issue
[#4](https://github.com/organvm-v-logos/.github/issues/4).

| Signal | Decision | Notes |
|:-------|:--------:|:------|
| Conversion holding ~3.5% post-experiment-cut; no regression after #5 was CUT | **Watch** | Confirms the June 5 decision to refocus on top-of-funnel; trigger: 3-week decline below 3.0%. |
| Top-of-funnel (new-visitor) volume is now the binding constraint, not conversion | **Act** | Per the [June 5 review](../../review.md), #5 was cut to refocus here; this is the first cycle to treat reach as the priority signal. |
| Returning-visitor rate flat-to-up | **Ignore** | Healthy; no action. Recorded to avoid re-litigation. |

**Remediation (open).** Open an owned top-of-funnel reach item: prioritize the
distribution surfaces that the cut of #5 freed capacity for. Target ship date
**2026-06-22** (next Monday), keeping the cycle within the 7-day SLA. Owner:
maintainer. This item will be marked **shipped** in the rollup once the change
is merged and live — not before.

**Cycle status:** signals classified, remediation opened and dated. The cycle
closes when the reach item ships or is explicitly deferred with a review date.

---

*ORGAN-V: Logos — Public Process. Pragma document: the honest account of
decisions taken on real signals.*
