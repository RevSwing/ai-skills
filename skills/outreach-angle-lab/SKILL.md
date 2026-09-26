---
name: outreach-angle-lab
description: Develop and compare genuinely distinct, evidence-grounded outreach campaign premises for a defined B2B audience and offer. Use when choosing what business case a campaign should test, before writing message variants or launching outreach.
compatibility: "Designed for Claude and ChatGPT."
---

# Outreach Angle Lab

Turn an audience-and-offer brief into campaign premises that make different business arguments. An angle is a testable reason the audience might consider the offer; it is not a subject line, tone choice, or synonym swap. Do not send, launch, buy data, or update systems unless separately authorized.

## Establish the brief

Collect or infer:

- audience: role, account type, relevant operating context, exclusions;
- offer: capability, mechanism, limits, and intended next step;
- evidence: customer results, product facts, research, account signals, objections, and source/date where available;
- campaign constraints: market, channel, consent limits, capacity, and claims needing approval;
- decision: what the campaign should teach and which outcome can be observed.

Ask only for a missing audience or offer when its absence makes useful premises impossible. Otherwise use explicit assumptions. Keep an evidence ledger with `supported`, `inferred`, `unknown`, and `conflicted` claims. Treat plausible interpretations as hypotheses. Preserve source disagreements and state what would resolve them.

## Build distinct premises

Draft three to five premises when the available evidence supports that many; return fewer rather than padding the set. Each premise must differ on all four dimensions below:

1. **Business rationale:** the economic or operational reason to act, such as avoiding a cost, capturing an opportunity, reducing exposure, or enabling a change.
2. **Relevant signal:** an observable condition that makes this rationale more likely for the audience. State its source and recency, or mark it as a targeting field that still needs validation.
3. **Proof requirement:** the evidence needed to make the premise credible. Distinguish proof already supplied from proof required before external use.
4. **Test:** a falsifiable comparison that can show whether the premise deserves further investment.

Explain the audience-to-offer bridge: why the audience influences the issue, how the offer could affect it, and what must be true for that mechanism to work. Include counterevidence or a disqualifier. Reject premises that change wording, tone, examples, or call to action while retaining the same rationale and signal.

Do not turn weak signals into asserted pain or intent. Signals such as hiring, funding, technology use, or leadership changes justify a hypothesis only when linked to the rationale. Never invent customer proof, statistics, urgency, or response benchmarks.

## Design interpretable tests

For each premise, specify:

- hypothesis and eligible audience slice;
- the premise variable being tested;
- elements held constant where feasible, such as offer, sender, channel, audience rule, and next step;
- observable primary measure and relevant guardrail;
- a decision rule based on the user's baseline, feasible sample, or a predefined directional criterion;
- what result would weaken the premise and what follow-up evidence would distinguish likely causes.

Without baseline or sample information, propose measurement and mark the stopping threshold unresolved. Do not supply generic sample sizes, durations, or success rates. Flag tests confounded by different audiences, offers, or delivery conditions.

## Use with RevSwing

Use `campaigns.list`, `campaign.get`, and `campaign.sequence` to establish the current campaign and control message. Use `analytics.campaign` for measured lead and activity counts, and use Signals findings only as dated evidence or targeting hypotheses. Keep website visits, external events, and custom AI research findings distinct from confirmed buying intent.

Build angle variants in the campaign Content Studio. Hold the audience rule, sender, channel, cadence, and next step constant where the test calls for it. Use AI columns for documented per-lead inputs or generated variables, then review the outputs and fallbacks before they enter copy. Run `campaign.validate` after authoring changes.

The lab ends with a reviewable test design. Enrollment through `campaign.enroll` and sending through `campaign.launch` are separate consequential actions. Each requires its own confirmation, signed-in human approval, exact replay, and successful receipt.

## Deliverable

Return:

1. **Brief and evidence ledger** — audience, offer, assumptions, supported facts, conflicts, and important gaps.
2. **Angle briefs** — for each: premise statement; business rationale; signal and source traceability; audience-to-offer bridge; supplied proof; proof still required; counterevidence/disqualifier; test design; claim cautions.
3. **Distinctness check** — a compact comparison across rationale, signal, proof requirement, and test. Merge or replace any pair that is substantially the same.
4. **Recommendation** — rank angles using evidence strength, audience relevance, mechanism credibility, distinctness, testability, and claim risk. Label each `ready to test`, `validate first`, or `hold`. Explain the tradeoff and name the next evidence that could change the ranking.

Use numeric scores only when the user supplied meaningful weights. A strong recommendation may be to validate evidence before campaigning.

## Synthetic worked example

**Synthetic inputs:** finance leaders at multi-site clinics; an invoice-routing product; supplied product documentation confirms routing by location, but no customer outcomes are provided.

**Angle A — exception-control:** premise that decentralized invoice intake makes exception ownership hard to see. Signal: clinics adding locations, if verified. Proof required: evidence that the product exposes exception ownership and credible customer outcome evidence before claiming improvement. Test: compare this premise with a different rationale among similarly sized, expansion-stage clinics while holding offer and next step constant; measure qualified positive replies, with misrouted-role replies as a guardrail.

**Angle B — close-readiness:** premise that finance teams need earlier visibility into invoices outstanding near close. Signal: stated multi-entity close responsibility, not expansion alone. Proof required: workflow evidence for status visibility plus validated outcome proof. Test: target the same role and account band using this rationale; a weak result alongside frequent “already visible” objections would weaken it.

These are distinct because they concern different operating consequences, depend on different signals and proof, and can fail for different reasons. With no outcome proof or baseline, recommend validating the mechanism and proof before setting a launch threshold.
