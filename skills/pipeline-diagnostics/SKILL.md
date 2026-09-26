---
name: pipeline-diagnostics
description: Diagnose stage bottlenecks and opportunity-data risks from supplied pipeline snapshots or history; use when current inventory, cohort conversion, stage velocity, or forecast limits must be kept analytically distinct.
compatibility: "Designed for Claude and ChatGPT."
---

# Pipeline Diagnostics

Analyze supplied opportunity data to locate plausible constraints and decide what owners should inspect or change. Treat the result as a diagnostic, not proof that a stage, person, or process caused an outcome.

## Establish the analysis contract

Identify the decision, as-of date, reporting period, and available data shape. Useful fields are a stable opportunity ID, owner, amount and currency, current stage, stage definitions and order, created date, stage entry and exit timestamps, close date, expected close date, and terminal outcome. Ask only for a missing item that makes the requested calculation unsound; otherwise proceed with a labeled assumption.

Define the record grain before counting. Distinguish one current row per opportunity, repeated export rows, legitimate time-stamped snapshots, and stage-event history. Collapse exact duplicates using stable IDs and relevant timestamps, but do not collapse separate opportunities merely because account, name, or amount matches. Report duplicate rules and before/after counts.

Create a stage map from supplied definitions. Do not assume labels such as “qualified,” “commit,” or “closed” have standard meanings. Mark ambiguous, unmapped, skipped, regressed, and reopened stages. Treat closed-won and closed-lost as terminal outcomes unless the history explicitly records a reopen; exclude terminal records from active pipeline inventory while retaining them for eligible cohort outcomes.

Preserve original currencies. Do not sum amounts across currencies. Report counts and values by currency, or convert only with a user-supplied exchange-rate policy, rate date, and source; show both original and converted values. Keep count-based and amount-weighted results separate so a few large deals cannot silently dominate the diagnosis.

## Keep four analytical views separate

### Snapshot pipeline

Describe active inventory at the as-of date by stage, owner, age, expected close period, count, and value. This is a stock measure: it does not establish conversion, throughput, or time spent in prior stages. Flag stale expected close dates, terminal records left in active stages, missing owners, and amount or currency coverage. Disclose the age convention, such as elapsed calendar days versus business days, timezone, and treatment of partial days. Treat a generic record `updated` timestamp as modification metadata unless its meaning establishes substantive deal activity.

### Cohort conversion

Define entry once: for example, opportunities created in July or first entering discovery in Q3. For each ordered milestone, calculate `unique cohort opportunities that reached the milestone / eligible unique cohort opportunities`. State whether conversion is opportunity-count or amount-weighted, whether reaching a later stage implies earlier milestones, and how skips, regressions, reopenings, and immature cohorts are handled. Never use the current stage distribution as a conversion funnel.

### Velocity

Use stage-event timestamps to calculate elapsed time from entry to exit. Show coverage and use robust summaries such as median and quartiles when supported. Keep completed durations separate from right-censored open durations; an open opportunity's age is not a completed cycle time. Missing or contradictory timestamps remain unknown. Snapshot-only data can support current age, not historical stage velocity.

### Forecast

Forecast only for an explicit close window and as-of date. Separate a seller-entered forecast category from a calculation. If probabilities are supplied and their meaning is known, show weighted pipeline as `amount × probability` by opportunity and currency; describe it as a model output, not promised revenue. Historical win-rate or velocity scenarios require comparable mature cohorts and documented definitions. Otherwise provide transparent scenarios or state that the data cannot support a forecast. Never invent stage probabilities, exchange rates, close dates, or precision.

## Diagnose and act

For each possible bottleneck, show the observed pattern, exact calculation, coverage, competing explanations, and evidence that would discriminate among them. A large snapshot stage may reflect inflow, long dwell, seasonality, or stale records. A conversion drop may reflect qualification rules or cohort mix. Assign actions to functional owners, not blame: for example, RevOps resolves stage mapping and duplicates; sales managers review aged records and exit criteria; deal owners correct specific next steps or dates. Drafting recommendations does not authorize CRM edits.

## RevSwing workflow

RevSwing's `/reports` route provides campaign and lead funnels, activity, issues, per-campaign performance, and exportable lead results. `/campaigns/{campaignId}` provides campaign overview, people, sequence, launch readiness, and activity; `/tasks` provides the operational follow-up queue. These surfaces describe outreach operations. They are not a generic CRM opportunity pipeline and must not be relabeled as opportunity stages, bookings, revenue, or forecast categories.

With MCP, use `campaigns.list` and `campaign.get` for campaign identity and state, `analytics.campaign` for persisted campaign lead-state and activity counts, `leads.search` and `lead.get` for membership-level checks, `tasks.list` for current work inventory, and `analytics.workspace` for current workspace totals. The available MCP has no opportunity-stage history, opportunity amount, currency, probability, or close-date tool. For an opportunity diagnosis, use the supplied snapshot or an authorized export and mark RevSwing-only sections unsupported. Keep all diagnostic MCP work read-only. If a separate request introduces a consequential MCP action, require confirmation on the final arguments and then replay the exact same tool and arguments with the confirmation token; changed arguments require a new confirmation.

## Deliverable

Return: scope and assumptions; data-quality ledger with affected counts; stage map; separate snapshot, cohort conversion, velocity, and forecast sections (mark unsupported sections); transparent numerator/denominator calculations; ranked bottleneck hypotheses; owner/action/evidence-needed table; and forecast limitations. Include record and amount coverage, currency treatment, cohort maturity, and an as-of date.

## Synthetic worked example

*Synthetic data:* A July-created cohort has 10 unique opportunities after one exact duplicate is removed. Eight reached discovery, four reached proposal, and two closed won by the 30 September as-of date: reach rates are 8/10 = 80%, 4/10 = 40%, and 2/10 = 20%. Separately, the 30 September snapshot has seven active opportunities in proposal. History covers only five exited proposal spells; their median completed dwell is 26 days, while two current proposal ages are censored. The proposal stage is a bottleneck hypothesis because cohort progression drops and active inventory is concentrated there, but the limited duration coverage and unknown inflow prevent a causal conclusion. RevOps should restore missing event history; the sales manager should inspect proposal exit criteria and the seven aged records. No revenue forecast is supportable without a close window, currencies, amounts, and a documented probability or historical model.
