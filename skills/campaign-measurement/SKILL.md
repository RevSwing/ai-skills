---
name: campaign-measurement
description: Analyze supplied B2B campaign data with explicit cohorts, denominators, data-quality controls, segment comparisons, and a bounded experiment; use for decision support rather than external benchmark claims.
compatibility: "Designed for Claude and ChatGPT."
---

# Campaign Measurement

Turn campaign records into reproducible evidence for a decision such as whether to continue a message, investigate a segment, or run a controlled test. Use only supplied data. Do not invent benchmarks, causal effects, or missing outcomes.

## Establish the measurement contract

Start with the decision and define:

- **Unit of analysis:** message, recipient, account, conversation, or opportunity. Match it to the decision; do not mix message-level exposure with person-level outcomes without an aggregation rule.
- **Exposure:** what qualified an entity for the cohort, including campaign or variant and eligible send dates.
- **Outcome:** the event being counted, its attribution rule, and whether it is unique per unit. Separate any reply from positive reply, qualified conversation, opportunity, and revenue.
- **Cohort window:** inclusion dates for exposure and the observation period allowed for outcomes. Report an as-of date and identify immature records that have not received the full window.
- **Population and exclusions:** audience, suppressions, test records, bounces, and user-requested filters.

Ask for a missing definition only when different choices would materially change the decision. Otherwise use a marked assumption and show how it affects interpretation.

## Build an auditable analysis table

Preserve raw counts, then normalize without silently discarding records. Use stable identifiers for campaign, variant, recipient, account, message, and outcome. Define duplicate rules before calculation: collapse exact duplicate events; preserve legitimate repeated sends at message level; count multiple replies from one recipient once for a unique-recipient metric. Report the rule and counts before and after.

Classify delivery explicitly. A sent denominator includes attempted sends; a delivered denominator excludes confirmed failures. Keep missing status unknown. Never label `replies / sent` as a delivered reply rate. Show both denominators when the distinction matters.

Treat opens and clicks as diagnostic. State whether machine activity, privacy prefetch, security scanners, or repeats were filtered. Without bot classification, label rates as potentially inflated and avoid using them as primary success criteria. Separate automated replies, including out-of-office notices, from human replies; show an all-recorded-replies metric only with an explicit label. Prefer downstream human outcomes. Report negative human replies and opt-outs separately as adverse-outcome guardrails rather than blending them into positive engagement.

Handle missing outcomes by distinguishing **no observed outcome**, **outcome field unavailable**, and **not yet mature**. Do not convert unavailable or immature observations into zero. Provide coverage counts for every metric.

## Calculate reproducible metrics

For every metric, give its numerator, denominator, formula, cohort dates, outcome window, unit, exclusions, and value. Examples include:

- delivery rate among known final statuses = confirmed delivered messages / attempted sends with known final delivery status; also report confirmed delivered / all attempted sends and unknown-status coverage;
- unique reply rate on delivered = recipients with at least one attributed reply / unique recipients with at least one confirmed delivery;
- positive reply rate = recipients with at least one positive attributed reply / the explicitly chosen eligible population;
- opportunity conversion = eligible accounts with an attributed opportunity / eligible accounts with mature outcome coverage.

If the source cannot support a requested denominator or attribution rule, calculate a clearly named proxy only when useful and state what it cannot establish. Keep counts beside percentages.

## Compare segments without overstating evidence

Apply identical definitions and maturity windows across segments. Show counts, rates, absolute difference, and relative lift only when the baseline is nonzero. Include coverage and delivery composition. Treat tiny samples as directional and show sensitivity to one additional outcome when it could change the decision.

Separate association from causation. List plausible confounders such as send date, list source, company size, geography, sender, deliverability, prior engagement, or unequal follow-up. If assignment was not randomized, describe segment differences as observational. Do not “control” for a factor that the data does not contain.

## Propose a bounded experiment

Convert the main uncertainty into one testable hypothesis. Specify eligibility, randomization unit, control and treatment with one intended difference, primary outcome, guardrails, attribution window, data-quality checks, and review rule. Use the user's baseline and practical threshold. If absent, label the minimum worthwhile effect unresolved; do not substitute a benchmark. Randomize at account level when contacts can influence one another. Recommend a pilot when volume is too low for a decisive comparison.

## RevSwing workflow

When RevSwing is available, use `/reports` to review date-filtered lead activity, cumulative lead funnels, latest recorded outcomes, delivery issues, campaign step facts, and A/B assignment reconciliation. The Campaign Performance panel counts leads once in lead-level metrics, exposes evidence IDs, and excludes identified bot or scanner activity from engagement rates; repeated events and retries can still appear in step activity. Use `/campaigns/{campaignId}` for campaign context and `/communications?campaignId={campaignId}` for delivery attempts and outcomes.

For MCP-assisted reads, use the exact tools `campaigns.list` to resolve a campaign, `campaign.get` for metadata, and `analytics.campaign` for persisted lead-state and activity counts. `campaign.sequence`, `leads.search`, and `lead.get` can clarify sequence and membership context. These reads do not replace the cohort, maturity, denominator, or attribution checks above, and they do not expose an arbitrary experiment export or prove causality. Do not invoke `campaign.enroll` or `campaign.launch` while measuring. If the user separately authorizes a consequential MCP action, first request confirmation with its final arguments; after signed-in approval, replay the exact same tool and arguments with the confirmation token. Any argument change requires a new confirmation.

## Deliverable

Return: decision and scope; data-quality ledger; metric specification table; reproducible calculations with counts; segment comparison; limitations and confounders; decision supported now; and one bounded experiment. Drafting an analysis does not authorize launching the experiment, changing campaign settings, or modifying records.

## Synthetic worked example

*Synthetic data:* Variant A attempted 120 sends and confirmed 108 delivered; Variant B attempted 100 and confirmed 80 delivered. After removing exact duplicate reply events, A has 6 unique repliers and B has 6, all mature for a 14-day window. On sent, rates are 6/120 = 5.0% and 6/100 = 6.0%. On confirmed delivered recipients, they are 6/108 = 5.6% and 6/80 = 7.5%. B is directionally higher, but the delivery imbalance and small number of replies make a creative conclusion weak. Test the variants with account-level random assignment, the same audience and send schedule, unique positive reply as the primary outcome, delivery rate as a guardrail, and a 14-day observation window; set the worthwhile effect and review size from the user's economics before launch.
