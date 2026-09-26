---
name: problem-hypotheses
description: Turn account facts and customer interview evidence into ranked, falsifiable business-problem hypotheses for discovery or outreach without treating signals, inferred causes, or product fit as proven pain.
compatibility: "Designed for Claude and ChatGPT."
---

# Problem Hypotheses

Use this skill when a user needs to reason from account research, customer interviews, call notes, or operational facts toward problems worth validating. The deliverable is an evidence map and a ranked set of hypotheses, not a diagnosis of the prospect.

## Required inputs

Work with the evidence provided and request more only when its absence makes the requested analysis unsound. Useful inputs are:

- Account facts, with source and date when available
- Direct statements from the account or comparable customers, preserving who said what and whether it is verbatim or paraphrased
- Observed behaviors or outcomes, including the relevant time period
- Product capabilities, prerequisites, and known limits
- The user's target role, business context, and purpose for the analysis

Keep account-specific evidence separate from evidence about other customers. Treat comparable-customer evidence as pattern support, not proof about the target. Mark unattributed, stale, ambiguous, or secondhand claims. Never fill an evidence gap with assumed industry behavior.

## Build an evidence chain

Normalize each useful input into one of four categories:

- **Symptom:** an observed condition, behavior, or reported friction, such as repeated manual reconciliation.
- **Cause:** an explanation for why the symptom occurs. A cause is a hypothesis unless directly established by suitable evidence.
- **Consequence:** an observed or plausible business effect. Keep measured effects distinct from projected effects.
- **Solution fit:** evidence that the user's offering could address the problem under the account's constraints. Fit does not prove the problem exists, and a problem does not prove fit.

Do not translate a technology choice, hiring event, growth signal, or generic persona pattern directly into pain. Use calibrated language: “the interviewee reported,” “the records show,” “may indicate,” or “unknown.” A prospect has a supported problem only when account-specific evidence establishes the relevant symptom or consequence; otherwise present a hypothesis to validate.

For each candidate problem, write a falsifiable statement in this form: **If [observable context], then [role or process] experiences [specific symptom], because [proposed cause], leading to [observable consequence].** Omit or mark unknown any link that lacks evidence. State what observation would disconfirm the hypothesis.

## Rank and select

Rank hypotheses using transparent, qualitative judgments rather than invented precision. Consider:

1. Strength and specificity of account evidence
2. Support from relevant comparable customers
3. Materiality of the stated or observable consequence
4. Amount of contrary evidence and number of unsupported links
5. Ability to validate the hypothesis with a clear question or observation

Explain close calls. A high product match may inform solution-fit notes but must not raise the evidence rank of the underlying problem. When hypotheses compete, preserve both until evidence distinguishes them. If the inputs support no responsible problem hypothesis, say so and return the most useful unknowns to investigate.

## RevSwing workflow

When RevSwing is connected, treat its surfaces as dated workspace evidence. **Companies** (`/companies`) and **People** (`/people`) provide account and contact context; **Inbox** (`/inbox`) provides stakeholder statements; **Signals** (`/signals`) provides monitored findings; campaign detail (`/campaigns/[id]`) provides lead and activity context; **Reports** (`/reports`) provides campaign and operational results; and **Tasks** (`/tasks`) provides recorded follow-up work. A signal, campaign state, reply, or task can establish an observation, but it does not establish the cause, business consequence, or product fit without further evidence.

In a connected RevSwing MCP client, use `companies.list` and `contacts.list` for bounded identity context, `inbox.list` and `inbox.thread` for persisted statements, `campaign.get`, `leads.search`, and `lead.get` for campaign context, `analytics.campaign` or `analytics.workspace` for persisted counts, and `tasks.list` for open or completed work. Record the tool result and observation date in the evidence chain. Do not convert workspace-wide totals into an account-specific problem.

This analysis requires no MCP mutation. If the user explicitly requests a later write, spend, or send action, the exact tool and arguments require human confirmation and then exact replay with the approval token; changed arguments require a new confirmation. Draft outreach remains a draft unless a separate send action is requested and approved.

## Deliverable

Return a compact evidence summary followed by a ranked list. For every hypothesis include:

- The falsifiable hypothesis and status: supported, provisional, weak, or contradicted
- Separate symptom, cause, consequence, and solution-fit fields
- Supporting evidence, tied to its source and whether it is target-specific or comparative
- Contrary evidence and material unknowns
- A concrete disconfirming condition
- One neutral validation question that asks about the current process before implying a problem
- A neutral outreach premise grounded only in verified context and framed as an invitation to compare notes

The outreach premise is draft language, not authorization to contact anyone. Avoid claiming pain, prescribing the product, manufacturing urgency, or implying that peer outcomes apply to the prospect. If verified context is too thin, recommend discovery or further research instead of producing personalized outreach.

## Synthetic worked example

**Fictional inputs:** Northstar's operations lead says monthly approvals require spreadsheet handoffs; two handoffs were late last quarter. The lead does not know why. Three existing customers reported delays caused by unclear ownership. The product can route approvals but requires a named owner.

**Rank 1 — provisional:** When monthly approvals cross spreadsheet handoffs, Northstar may experience late approvals; the cause is unknown, and the observed consequence is two late handoffs. Symptom support comes from Northstar; unclear ownership is only comparative cause evidence. Contrary evidence: none provided. Unknown: whether lateness affects a business outcome. Solution fit is conditional on a named owner. Disconfirm if the two delays were exceptional and the current process now completes on time. Validation question: “How do monthly approvals move between owners today, and where, if anywhere, do they tend to wait?” Neutral premise: “You mentioned spreadsheet handoffs in monthly approvals; I would be interested in comparing how the process works today and whether the recent delays were isolated.”
