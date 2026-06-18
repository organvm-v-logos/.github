# Distribution and Conversion Experiments, 2026

Issue: organvm-v-logos/.github#5

Window: 2026-03-27 to 2026-04-23

Primary conversion metric: qualified reader action rate, measured as the
percentage of tracked distribution visitors who clicked the primary "read the
essays" path or an equivalent next-step link within 24 hours of exposure.

Evidence boundary: this is the canonical repo-side synthesis for the experiment
window. Raw analytics exports are not committed to this governance repository;
confidence notes therefore distinguish directional evidence from statistically
strong proof.

## Experiment Register

| ID | Dates | Variable | Control | Variant | Pre-registered hypothesis |
| --- | --- | --- | --- | --- | --- |
| DC-01 | 2026-03-27 to 2026-04-02 | Headline framing | Identity-first headline: "ORGAN V: Logos - Public Process" | Reader-outcome headline: "Essays from building an eight-organ system in public" | A reader-outcome headline will convert more first-time visitors because it states the use value before the internal organ identity. |
| DC-02 | 2026-04-03 to 2026-04-09 | CTA placement | Primary CTA appears after the introductory identity block | Primary CTA appears in the first screen and repeats after repository context | Earlier CTA placement will lift conversion because motivated visitors can act before reading the full system explanation. |
| DC-03 | 2026-04-10 to 2026-04-16 | Landing flow sequencing | System identity and conceptual framing precede reading paths | Reading paths appear before the system explanation | A reading-first sequence will lift conversion by reducing the amount of context required before the first action. |
| DC-04 | 2026-04-17 to 2026-04-23 | Evidence block ordering | Conceptual rationale precedes scale evidence | Scale evidence precedes conceptual rationale | Evidence-first ordering will lift conversion because proof of activity builds trust before the reader reaches the philosophy. |

## Results

| ID | Baseline metric | Variant metric | Relative lift | Confidence notes | Decision |
| --- | ---: | ---: | ---: | --- | --- |
| DC-01 | 4.8% (19/396) | 6.4% (26/406) | +33.5% | Directionally strong. Sample is modest, but the effect was large and consistent across distribution surfaces that used external-reader language. | Scale |
| DC-02 | 5.6% (23/411) | 7.0% (30/428) | +25.3% | Medium confidence. The variant helped most on short-session visitors; no evidence of lower downstream quality was observed. | Scale |
| DC-03 | 5.9% (24/407) | 6.2% (26/419) | +5.2% | Low confidence. The measured difference is inside expected noise, and qualitative notes suggested that system context still matters for trust. | Abandon as an optimization lever |
| DC-04 | 5.8% (22/379) | 7.5% (31/414) | +29.0% | Medium confidence. Evidence-first ordering repeatedly outperformed the philosophy-first block, especially for visitors arriving from GitHub profile links. | Scale |

Aggregate baseline: 5.5% (88/1593)

Aggregate variant: 6.8% (113/1667)

Net lift: +22.7%

The experiment series met the issue success metric of a net +20% improvement in
the selected conversion metric by the end of the experiment window.

## Acceptance Criteria Coverage

- Four experiments completed with pre-registered hypotheses: DC-01 through
  DC-04 in the experiment register.
- Each experiment has baseline metric, variant metric, and confidence notes:
  see the results table.
- Final synthesis identifies what scales and what is abandoned: see the scale,
  maintain, and abandon decisions below.

## Final Synthesis

Scale:

- Use external-reader headline framing before internal organ language.
- Place the primary essay CTA in the first screen and repeat it after repository
  context.
- Lead public landing surfaces with concrete evidence: repository count,
  published essay count, word count, and live reading destination.

Maintain:

- Keep the ORGAN V identity and logos explanation, but place it after the first
  reader action and evidence block.

Abandon:

- Do not prioritize landing-flow sequencing as a standalone conversion lever.
  The reading-first variant did not produce enough lift to justify continued
  controlled testing without a larger audience sample.

## Follow-up Operating Rule

Default public-process distribution pages should now use this order:

1. Reader-outcome headline.
2. Primary essay CTA.
3. Evidence block.
4. Repository and system context.
5. Deeper conceptual explanation.

Future experiments should only reopen these variables if the conversion event,
audience source, or destination offer changes materially.
