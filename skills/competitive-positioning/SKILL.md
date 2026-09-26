---
name: competitive-positioning
description: Compare buying alternatives against buyer-specific criteria and produce evidence-backed differentiation for sales strategy or messaging.
compatibility: "Designed for Claude and ChatGPT."
---

# Competitive Positioning

Build a comparison that helps a specific buyer understand tradeoffs among credible ways to solve their problem. Treat the status quo and an in-house approach as alternatives alongside named vendors. Do not turn missing evidence into a claim.

## Required inputs

Use what the user provides and ask only when a missing fact would materially change the comparison. Useful inputs are:

- buyer segment, use case, current process, and desired outcome;
- decision participants and their success, risk, cost, and adoption criteria;
- alternatives under consideration, including “do nothing for now” and “build or operate internally”;
- dated sources such as product documentation, proposals, security materials, contracts, buyer interviews, evaluations, and verified deployment results;
- constraints such as deadline, integrations, governance, resources, and budget treatment.

If buyer criteria are absent, derive provisional criteria from supplied buyer evidence and label them as hypotheses. If no evidence supports a buyer-specific comparison, provide a discovery plan rather than generic competitive claims.

## Workflow

### Frame the decision

State the buyer, decision, use case, time horizon, and alternatives. Define the status quo concretely: current tools, manual work, delay, or accepted problem. Define the in-house option by the work it would require, without assuming it is inferior. Add or remove alternatives only when evidence shows the buyer considers them credible.

Translate buyer evidence into criteria. For each criterion, record whose criterion it is, why it matters, whether it is a requirement or preference, and the evidence date. Preserve disagreements between stakeholders instead of averaging them away. Do not invent weights; use stated priorities or label a provisional ranking.

### Build an evidence ledger

For every material comparison, retain:

- claim or observation;
- alternative and criterion;
- source, source type, and publication or observation date;
- scope, such as plan, region, deployment model, or buyer environment;
- confidence and any contradiction or missing detail.

Prefer current primary material and direct buyer evidence. A vendor statement can establish what that vendor says it offers, but not an unobserved outcome. Flag stale sources and date mismatches. When sources conflict, show the conflict and state what would resolve it. Never infer competitor limitations from silence, and never estimate competitor prices. Record price as “not verified” unless supported by dated, applicable evidence.

### Compare and position

Evaluate each alternative only against the same buyer criteria. Use `Supported`, `Partially supported`, `Not supported`, `Unclear`, or another plainly defined scale. Each substantive cell should point to evidence or state what is unknown. Distinguish product capability from implementation effort, operating responsibility, and realized outcome.

Identify differentiation only where the evidence shows a relevant contrast. A defensible positioning statement has this form:

> For [buyer/use case], [offering] is well suited when [criterion] matters because [supported capability or operating model], evidenced by [dated source]. Compared with [alternative], the relevant difference is [substantiated contrast]. [Uncertainty or condition].

Avoid claims such as “only,” “best,” “faster,” or “cheaper” unless the evidence directly supports the scope and comparison. Do not convert a missing feature, undisclosed price, or old document into a current disadvantage.

## RevSwing workflow

When the decision concerns a RevSwing campaign or workspace, use **Inbox** (`/inbox`) for buyer-stated criteria, campaign detail (`/campaigns/[id]`) for the configured sequence, lead states, readiness, and activity, and **Reports** (`/reports`) for persisted campaign and operational results. **People** (`/people`) and **Companies** (`/companies`) can anchor the buyer and account context. These surfaces can support claims about the buyer's current RevSwing setup or observed results; they do not establish competitor capabilities or outcomes.

With RevSwing MCP, `campaign.get` retrieves campaign metadata, `campaign.sequence` retrieves the persisted ordered sequence, `campaign.validate` returns concrete readiness issues, `leads.search` and `lead.get` retrieve lead state, and `analytics.campaign` retrieves authoritative campaign counts. `contacts.list`, `companies.list`, `inbox.list`, and `inbox.thread` can supply buyer context and statements. Cite the specific tool result and observation date; do not generalize one workspace result into a market comparison.

Competitive analysis needs no consequential MCP action. If the user separately requests `campaign.enroll` or `campaign.launch`, require human confirmation and then exact replay of the same tool and arguments with the approval token; changed arguments require a new confirmation. Enrollment does not launch, and approval of positioning language does not authorize either action.

## Deliverable

Return:

1. **Decision frame** — buyer, use case, time horizon, alternatives, criteria, and stated or provisional priorities.
2. **Comparison matrix** — rows are buyer criteria; columns include the offered solution, named competitors, status quo, and in-house. Each cell gives the assessment, a short reason, evidence date/source, and confidence.
3. **Substantiated positioning statements** — a small set of buyer-relevant claims, each tied to evidence and conditions.
4. **Uncertainty register** — stale, missing, conflicting, or scope-limited evidence; impact on the conclusion; and the next verification step.
5. **Discovery questions** — prioritized questions that could change the decision, addressed to the relevant buyer role. Include questions about the cost and risk of the current state, internal build capacity and ongoing ownership, must-have criteria, switching effort, and how price will be evaluated.

Keep facts, buyer statements, and analyst inferences visibly distinct. Give a conditional recommendation only if evidence supports one; otherwise state which alternatives remain viable and why.

## Synthetic worked example

*Fictional example:* A regional manufacturer is comparing AcmeFlow with RivalOne, spreadsheets, and an internal workflow. Its operations lead requires an audit trail by Q1; IT requires single sign-on. A dated AcmeFlow security guide supports single sign-on, while RivalOne’s supplied materials do not address it. The matrix marks AcmeFlow `Supported`, spreadsheets `Not supported` for the stated audit requirement based on the buyer’s documented process, and RivalOne `Unclear` rather than unsupported. The positioning says AcmeFlow fits the documented access-control requirement, subject to plan and implementation confirmation. Discovery asks IT to verify the required identity provider and asks operations how spreadsheet exceptions are currently audited.
