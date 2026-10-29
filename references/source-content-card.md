# Source-content card contract

Load when saving or reusing a source, or handing research to another author. This file owns the card fields and reading-scope vocabulary; other skills should reference it rather than maintain another schema.

A card preserves what a source actually says and how it can be used. A URL list is a discovery aid, not a content library. Use one stable source ID per underlying work, connect distinct versions explicitly, and link captures and notes without copying originals already saved elsewhere. Related records may point to the same card.

## Required fields

Use Markdown, JSON, or existing ledger fields with equivalent meaning. Write `unknown` or `not applicable` where appropriate; empty fields must not imply a completed check.

| Field | Record |
|---|---|
| Identity | Stable source ID; exact title; author/publisher; underlying URL, DOI, or repository identity; kind such as textbook, lecture, paper, official tutorial, product documentation, code, experiment, blog, interview, or record. |
| Dates and version | Publication/event/update dates as applicable, retrieval date, and edition/term/release/commit. Separate an observed date from a guessed one. |
| Independence and relationships | Underlying study or implementation identity; derivative/duplicate records; earlier/later versions; retracted or corrected status when known. Shared data, authorship, or methods can limit independence even across different URLs. |
| Saved evidence | Existing original/capture path, notes path, acquisition provider, and precise page/heading/table/line/code locator. Hash an artifact when exact capture identity matters. |
| Reading scope | Vocabulary below, the exact sections inspected, who inspected them, and any access/extraction failure. |
| Substantive content | The question addressed; definitions/argument/mechanism; method or actual implementation; results with units, baseline, and conditions when relevant; examples that help reproduce the reasoning. |
| Claim support | Which research question or claim the content directly supports, what it only reports, what is inference, and what it cannot establish. |
| Limits and disagreement | Source's limitations, additional audit qualifications, competing findings, and unresolved issues. Keep the source's own caution separate from the researcher's inference. |
| Verification and corrections | Claim-level verdict, original locator the parent checked, inspection date, latest evidenced correction and affected outputs. Distinguish reported wording from independently corroborated effects. |
| Reuse | Intended teaching/analysis use, related content cards, and the next precise gap if more evidence is needed. Proposed use is not instructor approval. |

For large works, keep bounded section cards under a shared identity. Do not label an entire book, website, or repository fully read when only selected sections were inspected.

## Reading scope

| Value | Meaning |
|---|---|
| `full-body` | The complete substantive body of this bounded work was read; name any excluded supplementary material. |
| `selected-sections` | Named passages/chapters/files were read; conclusions are limited to those sections. |
| `abstract-only` | Abstract or equivalent overview only. Method/results details remain unverified unless present there, and are attributed accordingly. |
| `catalog-or-discovery` | Title, TOC, schedule, search hit, metadata, or link only. Useful for discovery; not proof of content or coverage. |
| `failed-access` | Required content was not obtained. Record the error and any separately accessible portion. |
| `unknown` | Prior record does not establish what was read. Treat as a lead until the needed original passage is checked. |

Reading scope and claim verdict are separate. A selected section can establish a specific definition; a fully read paper can still have weak causal evidence. A previously checked passage can be reused without claiming it was newly inspected.

## Complete hypothetical example

Everything in this example, including source, numbers, quotes, and paths, is fictional. It illustrates the contract and must never be cited as research.

```markdown
# S-queue-v2 — Queue Separation in a Document Review Service

- Kind: first-party engineering experiment and implementation note.
- Author/publisher: Example Systems Engineering.
- URL: https://example.org/engineering/queue-separation-v2
- Dates: published 2026-04-10; experiment 2026-03; captured 2026-04-12.
- Version: article v2; implementation release review-service-2.4.
- Relationships: supersedes S-queue-v1. The release note and mirrored blog
  describe the same experiment and do not count as additional studies.
- Saved original: raw/queue-separation-v2.md.
- Notes: notes/queue-separation.md.
- Acquisition: saved web capture; provider recorded in search_manifest.md.
- Reading scope: selected-sections. Worker read Design, Method, Results and
  Limits. Parent read Method, Table 2 and the Results correction on 2026-04-12.
  Appendix capacity sweep was not read.

## Question and substantive content

Question Q2: Does separating short and long jobs improve tail latency under
the same resource budget?

Mechanism: one FIFO queue lets long jobs delay short jobs. The revised service
classifies jobs by estimated length and sends them to separate worker pools.
This reduces waiting behind long jobs, but a poor classifier can strand
capacity in one pool.

Method: replay of 600 synthetic document jobs. Table 2 compares one shared
pool of 8 workers with two pools of 8 workers each. The replay inputs and
hardware type match; total worker count does not.

Reported result: p95 end-to-end latency changes from 20 s to 12 s. The
measurement includes queue wait and processing, excluding client upload.
This is a 40% reported reduction for these two configurations, not proof of
an architecture benefit at equal capacity.

Original locator: Method, paragraphs 2–3; Table 2; Limits, paragraph 1.
Short decisive excerpt from Table 2: "Worker count: shared 8; split 16."

## Support, limits and disagreement

- Q2/C2 verdict: partial. The source supports an observed latency difference;
  it does not answer the equal-budget question.
- Evidence type: the publisher reports its own replay; the saved table
  directly supports the worker counts, not independent production effects.
- Source limitation: synthetic workload and estimated job lengths.
- Audit qualification: capacity and queue organization changed together.
- Open: equal-capacity comparison, classifier errors, full cost per accepted
  job, and sustained production behavior.

## Verification and correction

Parent checked the saved original Method and Table 2 on 2026-04-12.
C2 earlier wording: "Queue separation cuts latency 40% at equal capacity."
Corrected wording: "The publisher reports a 40% p95 reduction while doubling
workers; this does not isolate queue separation."
Propagation: report.md comparison table, notes/queue-separation.md and the
Q2 claim row corrected. Older v1 notes retained and marked superseded.

## Reuse

Use: explain head-of-line blocking and confounded comparisons.
Do not use: claim lower cost, equal-capacity superiority, or production SLOs.
Next gap: find an equal-capacity replay or run one under separate authority.
```

## Counting and maintenance

When reporting coverage, keep source identities, versions, captures, cards, read scopes, claims, and independent studies distinct. Several workers reading one original may improve checking but do not multiply the evidence base. Save new qualifications as linked corrections and update dependent wording; preserve the original artifact and earlier version for provenance.
