---
name: next-step-design
description: Choose and phrase a credible, low-friction next action for a specific B2B outreach or sales conversation, based on relationship stage, mutual value, and delivery readiness.
compatibility: "Designed for Claude and ChatGPT."
---

# Next Step Design

Choose the smallest credible action that helps both parties learn, decide, or make progress. Calibrate it to the actual exchange, demonstrated engagement, and the seller's present ability to deliver.

## Establish the decision context

Extract or request only context that changes the choice:

- the relevant conversation in sequence, with speakers and dates when available;
- explicit recipient signals: questions, refusals, priorities, commitments, referrals, or requested timing;
- relationship stage and what has already been exchanged or completed;
- the unresolved decision or task on each side;
- resources, people, analyses, demonstrations, or commercial actions that actually exist;
- delivery constraints: ownership, access, preparation, approvals, and dependencies;
- channel, consent, and any contact or sequence limits.

Separate direct statements from seller interpretation and unknowns. Prefer the recipient's latest explicit statement when records conflict. Silence does not establish interest. Ask only when missing context prevents a responsible choice; otherwise mark assumptions.

## Calibrate the commitment

Infer stage from behavior, not a CRM label alone:

- **Unengaged or lightly engaged:** favor an answerable question, permission to send an existing relevant item, or an easy decline.
- **Problem exploration:** propose a focused exchange that resolves a named uncertainty, such as answering two questions or comparing the current workflow.
- **Solution evaluation:** propose review of a real artifact, demonstration against agreed criteria, technical validation, or access to an appropriate specialist.
- **Decision coordination:** propose a scoped decision meeting, stakeholder alignment, pilot decision, or commercial review only when prerequisites are known.
- **Active customer or partner:** use the shared plan, responsibilities, and existing cadence.

These are guides rather than an automatic ladder. Honor a recipient's higher-commitment request when the seller can deliver it and its purpose is clear.

## Generate and compare candidates

Create two to four viable requests. For each, state:

1. **Action:** what each party would do.
2. **Recipient effort:** time, preparation, coordination, access, or perceived risk. Describe it from known facts; do not invent precise durations.
3. **Recipient value:** the question answered, work reduced, risk clarified, or decision advanced.
4. **Seller value:** the uncertainty resolved or decision advanced.
5. **Readiness:** what exists and what must be prepared before offering it.
6. **Fit and risk:** why it matches the observed stage, plus any assumption or likely friction.

Discard candidates that mainly extract time or information, repeat an unanswered request without added value, depend on an invented asset, or promise unavailable access, analysis, pricing, a pilot, or an introduction. Do not disguise a meeting request as a free assessment or hide a call requirement behind a resource offer. State whether an existing item can be delivered asynchronously and on what known terms.

Select for mutual value, recipient burden, stage fit, and delivery certainty. Prefer a smaller step when readiness is weak and a larger one when purpose and prerequisites are established. If none creates credible mutual value, recommend no request yet and identify what the seller must prepare.

## Phrase the request

Tie the action to the recipient's stated context without overstating agreement. Name the purpose, participation, and choice. Keep optionality genuine; when useful, provide an asynchronous path or an easy decline. Avoid false scarcity, artificial deadlines, guilt, surveillance signals, and assumed consensus.

Drafting does not authorize sending, calendar booking, CRM changes, introductions, or creation of promised deliverables.

## RevSwing workflow

Ground the choice in the actual RevSwing record: `/inbox` holds the ordered conversation and campaign context, `/tasks` holds owners, due dates, linked people or companies, campaign and signal context, and task activity, and `/campaigns/{campaignId}` shows the campaign's people, sequence, readiness, and activity. Use `/communications` only to verify communication status or delivery history; an unknown or reconciliation-required outcome is a stop condition, not a reason to resend.

For MCP reads, use `inbox.list` and `inbox.thread` for conversation evidence, `tasks.list` for current task inventory, `campaign.get` and `campaign.sequence` for campaign context, and `lead.get` for one campaign membership. The MCP has no tool to send a reply, create or edit a task, book a meeting, or update a next step. Keep the selected action as wording and a fulfillment checklist unless the user separately authorizes a supported action. Any consequential MCP tool must first return a confirmation request for its final arguments; after signed-in approval, replay the exact same tool and arguments with the confirmation token. Changed arguments require a new confirmation.

## Deliverable

Return:

- a brief evidence and stage assessment, with assumptions and conflicts;
- a candidate table or compact list covering action, recipient effort, recipient value, seller value, readiness, and fit/risk;
- the selected next step and why it wins;
- exact wording suitable for the current channel and voice;
- a fulfillment checklist naming the owner, inputs, asset or agenda, approvals, delivery method, and dependencies;
- a fallback or stop condition if the recipient declines, does not respond, or a prerequisite cannot be met.

## Synthetic worked example

**Synthetic input:** During a first reply, a finance operations lead says duplicate invoice review is manual and asks whether the product supports their ERP. The seller has a verified compatibility matrix but no buyer-specific analysis or approved pilot.

**Candidates:** (1) send the compatibility excerpt after confirming ERP version: low effort and directly useful; verify it is current. (2) request a discovery call: higher effort and broader than the question. (3) offer a pilot: potentially valuable but not deliverable because scope and approval are absent.

**Selected wording:** “Yes, we have a compatibility matrix for that ERP. Which version are you running? I can send the relevant excerpt here so you can check the supported connection and limits.”

**Prepare:** confirm matrix version and source, identify the correct excerpt and limitations, name the person responsible for the answer, and be ready to send it in the same channel. If the version is unsupported or unknown, say so and propose a technical check rather than implying compatibility.
