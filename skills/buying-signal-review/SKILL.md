---
name: buying-signal-review
description: Assess dated business events as possible reasons for a relevant prospect conversation, while distinguishing evidence of change from evidence of purchase intent.
compatibility: "Designed for Claude and ChatGPT."
---

# Buying Signal Review

Evaluate whether a business event creates a timely, evidence-backed reason to start or reassess a prospect conversation. Treat the event as context for a hypothesis, never as proof that the account wants to buy.

## Required inputs

Use what the user provides and ask only when a missing item prevents a sound assessment:

- target account and, when known, the relevant team or role;
- the event claim, event date, discovery or publication date, and source links or excerpts;
- the seller's offering and the problem it can credibly address;
- any known account history, active opportunity, suppression rule, or prior outreach;
- the review date and any user-defined freshness window.

Keep source traceability attached to each claim. If an event date is unavailable, do not substitute the article date without labeling it as a proxy. When the offering or target role is missing, assess evidence quality but mark commercial relevance unresolved.

## Review the event

Normalize the event before scoring its usefulness. Separate:

- **event date:** when the change occurred or was officially announced;
- **source date:** when each source published or updated its account;
- **observed fact:** what the evidence directly supports;
- **inference:** a plausible operational consequence or conversation angle.

Check freshness against the event's likely decision cycle and the user's context. A leadership appointment, regulatory deadline, facility opening, funding round, hiring pattern, or technology change can age at different rates. Avoid a universal cutoff. State why the event is still actionable now, already stale, or awaiting a dated milestone.

Test causal relevance as a chain: **event → plausible business consequence → problem the offering addresses → person likely to care**. Each link must be supported or explicitly marked as an assumption. Mere industry similarity, company growth, or a keyword match is not enough. Do not convert layoffs, crises, legal disputes, or personal events into urgency without a respectful, directly relevant business basis.

Corroborate material claims. Prefer a dated primary source such as a company filing, official announcement, job listing, or executive statement. Use an independent source when it adds confirmation or context. Multiple pages that repeat one press release count as one evidence lineage, not independent corroboration. Record contradictions, source incentives, date mismatches, and unavailable evidence. Never invent missing facts.

## Decide the disposition

Choose one outcome based on the evidence available:

- **Use now:** the event is dated, sufficiently current, corroborated for its importance, and causally relevant enough for a modest conversation hypothesis.
- **Monitor:** the event is credible but timing, consequence, ownership, or applicability remains unresolved; define what evidence would change the decision.
- **Do not use:** the event is stale, contradicted, too weakly connected, materially unverified, sensitive without a legitimate basis, or already superseded.

Confidence describes the assessment's evidence quality, not likelihood to purchase. Existing account engagement, stated priorities, budget, evaluation activity, or a direct request may strengthen a separate intent assessment, but must not be inferred from the event alone.

## RevSwing workflow

When RevSwing is available, review detected events at `/signals`. The Signals view separates findings from Agents and supports Website visitors, Social activity, AI signals, and External signals; inspect the finding details, dates, status, and displayed evidence before applying this skill. A saved company's drawer at `/companies` also shows Company signal activity. Keep monitored events separate from saved-contact engagement and from any claim of purchase intent.

The current RevSwing MCP catalog has no signal read, agent creation, or monitoring tool. Do not claim to retrieve or configure signals through MCP. Read-only `companies.list` can resolve a saved company, while `inbox.list` and `inbox.thread` can inspect persisted conversation context when the user includes it in scope; conversation activity is a separate intent input, not corroboration of the underlying event.

Routing a signal to a campaign or launching outreach is outside review. If a separately authorized RevSwing MCP action is classified as `write`, `send`, or `spend`, the first call must return a confirmation request. Show its impact and visible cost, obtain signed-in workspace approval, then replay the same tool with exactly the same arguments, the one-time confirmation token, and a fresh idempotency key. Changed arguments require a new confirmation.

## Deliverable: signal cards

Produce one card per distinct event, followed by a brief cross-card priority order when reviewing several events. Each card includes:

1. **Event and account** — a neutral one-sentence claim.
2. **Dates and freshness** — event date, source dates, review date, age, and context-specific freshness judgment.
3. **Evidence** — sources, direct facts, source traceability, independence, contradictions, and confidence.
4. **Causal relevance** — the event-to-consequence-to-offering-to-role chain, with assumptions labeled.
5. **What remains unknown** — facts that could reverse or materially change the assessment.
6. **Disposition** — use now, monitor, or do not use, with a concise reason.
7. **Recommended next step** — the least presumptive useful action, such as verify a milestone, research ownership, or draft a conversation opener for user review. Do not send outreach, purchase data, or modify records unless separately authorized.
8. **Expiry or reassessment condition** — a specific date, milestone, contradiction, or evidence trigger. If no defensible date exists, use a condition rather than inventing one.

## Synthetic worked example

**Synthetic event:** Northstar Labs announced on 3 March that it will open a second support center in June; an 8 March local permit record confirms the site. Reviewed 20 March for a workforce scheduling product.

**Assessment:** The dated announcement and independent permit record support the expansion, but neither shows a software evaluation. The plausible chain is new site → more scheduling complexity → potential relevance to support operations; current tooling and the owning leader remain unknown. **Disposition: monitor.** Next, identify the operations owner and verify hiring or launch timing. Reassess when hiring begins or by 15 May; expire the angle if the opening is canceled or delayed without a new date.
