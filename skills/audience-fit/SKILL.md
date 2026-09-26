---
name: audience-fit
description: Convert product capabilities and customer evidence into testable B2B account-fit rules, tiers, exclusions, qualification questions, and a pilot; use for defining or revising an ICP, not for ranking current buying intent.
compatibility: "Designed for Claude and ChatGPT."
---

# Audience Fit

Turn evidence about what the product can deliver into an account-selection hypothesis that can be tested. Treat fit as the account's durable ability to receive value and be served successfully. Keep current intent signals—such as recent engagement, active research, or an open opportunity—in a separate field or analysis. High intent does not repair poor fit, and low observed intent does not make a well-matched account a poor fit.

## Required inputs

Use whatever is available from these categories:

- Product capabilities, prerequisites, limitations, delivery model, and disqualifying constraints.
- Customer or prospect evidence with source, date, account attributes, use case, adoption, outcome, and relevant failures or churn.
- Commercial constraints such as supported regions, minimum viable contract, service capacity, or required integrations.
- The decision the rules will support: prospecting, qualification, territory design, or a limited pilot.

Ask only for a missing fact that would materially change the result, such as an unknown product prerequisite. Otherwise proceed with clearly labeled assumptions and list the evidence needed to resolve them. Never infer market size, prevalence, or causal relationships from a small customer set.

## Build the fit model

First, translate capabilities into conditions for value. Distinguish required conditions from favorable characteristics. A required condition must have a direct product or delivery reason; a favorable characteristic should have supporting customer evidence. Record counterexamples as carefully as successes.

Define every proposed segment rule as a measurable filter:

| Field | Contents |
|---|---|
| Criterion | Observable account or workflow attribute |
| Test | Field, operator, and value or a reproducible manual check |
| Role | Required gate, supporting signal, or exclusion |
| Rationale | Capability or outcome that makes it relevant |
| Evidence | Source observations, including counterevidence |
| Confidence | High, medium, or low, with a reason |

Prefer attributes that can be verified consistently. Do not substitute easy-to-source proxies for the actual condition without stating the proxy risk. Mark unavailable values as unknown; do not silently convert unknowns to failures.

Create tiers from explicit rule combinations rather than arbitrary point totals. For example, Tier 1 can require every product prerequisite plus two evidence-backed supporting signals, while Tier 2 meets prerequisites but has unresolved or weaker supporting evidence. If weighted scoring is requested, show the reasoning and sensitivity to plausible weight changes; do not present weights as objective unless outcome data validates them.

Maintain exclusions separately. A hard exclusion is a known incompatibility, legal or delivery constraint, or repeated evidence of inability to realize value. A temporary exclusion is a condition that can change, such as an unsupported integration on a published roadmap. A lack of information belongs in an “unknown” queue for qualification.

Assess confidence by evidence quality, relevance, recency, consistency, and independence—not merely sample count. With a thin or biased sample, label the model provisional, narrow claims to the observed contexts, surface selection bias, and retain competing hypotheses. Do not turn the current customer profile into a presumed total market.

## Qualification and pilot

For each unknown or weak rule, provide one concise qualification question, what evidence would answer it, and how each answer changes tier or exclusion status. Questions should test operational facts, such as workflow volume or integration ownership, rather than invite generic agreement.

Design a bounded pilot that samples the proposed top tier, at least one adjacent tier, and meaningful exclusions or borderline cases when ethical and practical. Specify sample selection, baseline, success and failure measures, observation period if known, and decision rules for expanding, revising, or rejecting each hypothesis. Useful measures can include qualified-opportunity rate, activation, time to value, retention proxy, delivery effort, and disqualification reason, chosen to match the available funnel. Do not invent benchmark targets; derive thresholds from the user's baseline or label them as decisions still to set.

## RevSwing workflow

When RevSwing is available, use **Companies → Discover companies** at `/companies` to translate fit rules into supported company filters such as headquarters, employee count, industry, revenue, type, technologies, funding, hiring, and business attributes. Keep the product's Company news, Buying intent, and Executive changes filters in the separate intent overlay. Use `/people/database?companyId=<company-id>` to inspect potential roles at a selected company and `/people` to review saved contacts, email status, source, list membership, and suppression state.

The read-only MCP tools `companies.list` and `contacts.list` accept only `q` and bounded `limit` arguments; `lists.list` returns contact-list definitions and membership counts. They read saved workspace records. They do not run Discover companies, expose the full market, or calculate fit, so report result limits and do not infer coverage from them.

If later execution calls a RevSwing MCP tool classified as `write`, `send`, or `spend`, the first call must return a confirmation request. Show its impact and visible cost, obtain signed-in workspace approval, then replay the same tool with exactly the same arguments, the one-time confirmation token, and a fresh idempotency key. Changed arguments require a new confirmation.

The deliverable should contain: scope and assumptions; evidence summary and gaps; measurable filters; rule-based tiers; exclusions and unknowns; qualification questions; a separate intent overlay; and the pilot plan. Drafting the model does not authorize outreach, data purchasing, campaign launch, or CRM changes.

## Synthetic example

*Synthetic illustration:* A scheduling product requires a supported calendar and provides value when teams coordinate many external meetings. Three successful customers all use Google Workspace, but only two have high meeting volume; one failed customer also uses Google Workspace and lacked an operations owner. Make “supported calendar” a required gate, “documented external-meeting volume” a low-confidence supporting signal, and “no owner for rollout” a provisional exclusion to test. Keep “visited pricing this week” as intent only. Ask who owns rollout and how meeting volume is measured, then pilot across high-volume accounts and near-boundary accounts before tightening the rules.
