# Revenue Ledger

Revenue-related events recorded toward Milestone 3 of
[#7](https://github.com/organvm-v-logos/.github/issues/7).
Acceptance criteria: see [README.md](README.md#3-revenue-related-event-need-1).

**Status: 0 / 1 qualifying event.**

A row qualifies only if it is a real economic transaction or committed pledge
from an **external party**, backed by a verifiable artifact (receipt, invoice,
payout notice, signed agreement, sponsorship confirmation). Internal transfers
and hypotheticals do not count.

> **Do not store secrets or full PII here.** Record amounts, dates, and a pointer
> to where the evidence lives (a receipt ID, an invoice number, a payout
> screenshot in a private location) — never card numbers, full names without
> consent, or access tokens.

| # | Date | Type | Amount (currency) | External source | Evidence pointer | Verified by |
|:-:|:-----|:-----|:------------------|:----------------|:-----------------|:------------|
| — | — | — | — | — | _No revenue event recorded yet._ | — |

<!-- TEMPLATE ROW:
| 1 | 2026-06-30 | Consultation | 150 USD | client (initials only) | Invoice #2026-014 (private finance folder) | @maintainer |
-->

## Eligible revenue channels (already part of the system)

- **Consulting** — paid bookings via the
  [Consult page](https://4444j99.github.io/portfolio/consult/).
- **Sponsorship** — GitHub Sponsors tier activation, or a direct sponsor agreement.
- **Tips / support** — one-off support payments.
- **Licensing / commission / grant** — a paid license, commissioned work, or a
  grant disbursement tied to this body of work.

## Recording procedure

1. Confirm the funds (or a firm, evidenced commitment) came from an external party.
2. Capture the evidence artifact in a **private** finance location; note only its
   identifier here.
3. Append a row above; update the counter in [README.md](README.md).
4. One qualifying row completes this milestone.
