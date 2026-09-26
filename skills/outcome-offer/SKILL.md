---
name: outcome-offer
description: Turn verified product capabilities and proof into a buyer-specific B2B offer with explicit outcomes, evidence needs, scope conditions, and role-based variants.
compatibility: "Designed for Claude and ChatGPT."
---

# Outcome Offer

Create a credible offer that shows how a product can change a buyer's operation and what outcome that change may support. Use this when capabilities and some proof already exist, but they have not yet been assembled into an offer for a particular account, segment, or buying group. Do not use aspiration, customer anecdotes, or general market claims as if they prove a result.

## Gather the decision inputs

Use the supplied material and its source traceability. Seek these inputs:

- buyer segment, current workflow or problem, decision roles, and priority;
- verified capabilities, including relevant limits or dependencies;
- proof such as measured customer results, evaluation data, references, or demonstrations;
- commercial scope: included work, exclusions, implementation responsibilities, timing, pricing structure, and success criteria;
- constraints such as environment, volume, geography, security, data access, or adoption requirements.

Ask only when a missing fact prevents a sound offer, such as an unidentified buyer or no usable capability evidence. Otherwise proceed with explicit assumptions and list the evidence still needed. Drafting an offer does not authorize outreach, quoting a binding price, changing CRM data, or promising contractual terms.

## Build the value chain

For each material claim, trace:

`verified capability → mechanism → operational change → measurable indicator → buyer outcome`

Keep each link specific. A capability is what the product demonstrably does. The mechanism explains how it affects the work. The operational change states who does what differently. The indicator is observable, such as time per review or accepted error rate. The outcome is the business effect the buyer values.

Mark the status of every result statement:

- **Verified result:** directly supported by identified evidence. State the population, conditions, period, and source when available.
- **Target:** a result the parties could agree to pursue and measure. Present it as a target, never as an expected fact.
- **Hypothesis:** a plausible effect that still needs discovery or a pilot. State what would validate it.

Do not convert a capability into a guaranteed outcome. Do not extrapolate one customer's percentage, imply causation from correlation, or calculate ROI without buyer-specific inputs. If the user requests a guarantee unsupported by evidence, preserve the commercial intent by offering a measurable target, pilot, or conditional scenario instead.

## Shape the offer

Choose a scope that gives the buyer a meaningful result while keeping dependencies visible. Define:

1. **Buyer and change:** the role or team, current friction, proposed workflow change, and intended outcome.
2. **Offer:** included product, services, onboarding, and concrete deliverables.
3. **Proof:** evidence supporting each important capability or result, plus gaps and the least burdensome way to close them.
4. **Success plan:** baseline, indicator, measurement method, target or decision threshold, owner, and review point. Avoid invented universal timelines.
5. **Conditions:** buyer inputs, adoption assumptions, integrations, volume bands, exclusions, and circumstances that would invalidate the claim.
6. **Next decision:** a proportionate action such as a scoped validation, technical review, commercial review, or purchase decision.

When evidence conflicts, retain both findings, compare their populations and conditions, and narrow the claim to the supported overlap. If that cannot be done, label the result unresolved and make verification part of the offer.

## Adapt for decision roles

Keep one factual core and change emphasis rather than facts:

- **Economic buyer:** business priority, cost or risk mechanism, scenario assumptions, decision threshold, and ownership.
- **Functional leader:** workflow change, team impact, adoption, operational indicators, and rollout conditions.
- **Technical or security evaluator:** capability boundaries, architecture or data requirements, validation method, and failure conditions.
- **Champion or end user:** daily friction removed, required behavior change, early proof point, and internal narrative.
- **Procurement or legal:** scope units, dependencies, exclusions, evidence behind claims, and terms that require formal agreement.

## Use with RevSwing

Use RevSwing as the working evidence surface when it is connected. Read `contacts.list`, `companies.list`, and `campaigns.list` to identify the buyer, account, and active campaign context. Use `inbox.thread` for stated needs or objections and `analytics.campaign` only for measured campaign activity; do not turn outreach metrics into product-outcome proof.

Store the approved offer language in the relevant campaign Content Studio draft, task, or Inbox draft. Ask AI can help adapt the same factual core for a role or channel, but review its claims, variables, and conditions before applying it. AI columns may populate per-lead context only when their source and fallback are clear.

This skill produces and places a reviewable offer. It does not authorize contact creation, enrichment, enrollment, or launch. RevSwing tools in the `write`, `spend`, or `send` classes require a separate confirmation request, human approval, and exact replay.

## Deliverable

Return a concise offer brief containing: buyer context; a one-sentence offer; the value-chain claims with status and source; included scope and deliverables; proof available and proof required; success measures; assumptions, dependencies, and exclusions; role-specific variants; and the recommended next decision. Separate known facts, user-provided assumptions, and open questions.

## Synthetic worked example

**Synthetic inputs:** A support software vendor has verified that its routing feature classifies incoming tickets and sends them to configured queues. One pilot report shows median triage time fell from 12 to 7 minutes for 4,000 English-language tickets over six weeks. The prospect uses three languages and has not supplied a baseline.

**Offer:** “For the support operations team, configure and validate automated routing on English tickets to reduce manual triage work, then decide whether multilingual expansion is justified.” The 12-to-7-minute result is verified only for the named pilot conditions. A reduction for this buyer is a target pending its baseline. Phase one includes workflow mapping, English routing configuration, and a four-week measurement plan; multilingual routing is excluded until accuracy is validated. The operations leader variant emphasizes queue time and staffing, while the technical variant emphasizes language coverage, integration, and an agreed accuracy threshold.
