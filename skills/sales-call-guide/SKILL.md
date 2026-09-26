---
name: sales-call-guide
description: Create an evidence-grounded, branching conversation guide for an introductory B2B sales call, including discovery, buyer-led objection handling, notes, and proportionate next steps; use for call preparation or facilitation, not for placing calls.
compatibility: "Designed for Claude and ChatGPT."
---

# Sales Call Guide

Build a guide a seller can use during an introductory conversation without turning it into a rigid script. Help the seller learn whether a relevant problem exists, respond to what the buyer says, and end with a proportionate outcome. Do not place a call, contact anyone, update records, or claim the conversation occurred.

## Inputs

Use what the user provides about:

- the buyer's role, responsibilities, and likely influence in the decision;
- the account and trigger for the conversation;
- direct buyer statements, prior exchanges, and known priorities;
- the seller's offering, supported capabilities, limitations, and approved proof;
- call objective, planned participants, time available, and permitted next steps.

Ask only for a fact whose absence would make the guide misleading, such as what the product does. Otherwise use marked assumptions and editable placeholders. Separate direct buyer evidence from seller interpretation, CRM labels, and hypotheses. Give recent, direct buyer statements the most weight. Never invent an objection, problem, urgency, competitor, customer example, result, or social proof.

## Shape the conversation

Start with a compact **Evidence and assumptions** block. Identify the known reason for the call, the buyer role, the most relevant verified context, and any assumptions the seller must validate.

Then produce these sections:

1. **Opener**: Thank the buyer, state the evidence-based reason for the conversation, confirm the proposed focus, and allow redirection. Do not imply a hypothesis is true.
2. **Core discovery**: Provide a small ordered set of open questions. Begin with the current situation and desired outcome, then explore process, impact, prior attempts, stakeholders, and decision approach where relevant. Add optional follow-ups for answer categories such as “priority confirmed,” “different priority,” or “no active problem.”
3. **Role-tailored questions**: Adapt emphasis to evidence about the person. An operational user may clarify workflow; a functional leader may discuss outcomes and ownership; a technical evaluator may focus on requirements, dependencies, and risk; a commercial participant may address process and constraints. Do not infer authority from title. Clarify the person's evaluation role when unknown.
4. **Conversation branches**: Write branches as `If the buyer says/indicates X → seller response → next question or action`. Include only branches supported by known context or neutral possibilities. Useful branches include confirmed relevance, a different priority, unclear impact, satisfied status quo, another stakeholder needed, a factual question the seller cannot yet answer, and explicit disinterest.
5. **Objection responses**: Include only objections the buyer expressed. Acknowledge without arguing, check understanding when useful, give a concise verified response, and offer a low-pressure choice. If none are evidenced, write “Observed objections: none supplied” plus a response pattern rather than predictions.
6. **Notes fields**: Provide blank fields for exact buyer language, current process, desired outcome, impact, constraints, stakeholders and roles, decision path, unanswered questions, seller follow-ups, consent or contact preferences, and evidence source. Keep facts, interpretations, and open questions distinct.
7. **Next-step options**: Offer two or three choices scaled to the conversation: no action, requested information, a focused follow-up, or another relevant person. State prerequisites and owners. Do not presume a meeting, trial, proposal, timeline, or data access. Include wording to confirm the buyer's choice.

## RevSwing workflow

Use `/tasks` to prepare from an assigned call task, due date, campaign, contact or company details, linked signal, and saved activity. Use `/campaigns/{campaignId}` for the originating campaign and `/inbox` for the actual conversation history. `/communications` contains calling setup and communication history; call details and outcome recording remain user-operated product actions.

MCP can supply bounded context through `tasks.list`, `contacts.list`, `companies.list`, `campaign.get`, `lead.get`, `inbox.list`, and `inbox.thread` when their identifiers and permissions are available. There is no MCP tool for placing a call, recording an outcome, creating a follow-up task, or booking a meeting. Do not imply that preparing the guide performed any of those actions. All listed tools are reads. If the user later requests a consequential MCP action, obtain confirmation for the final tool arguments and replay the exact same tool and arguments with the confirmation token after signed-in approval; any change requires a new confirmation.

## Branch and boundary rules

- Treat “no,” “not interested,” “do not contact me,” or equivalent language as a decision. Acknowledge it, record the preference, and end without a new pitch or workaround. If scope is ambiguous, ask a narrow preference question only when necessary.
- When the buyer corrects the premise, update the path immediately and explore the corrected priority only with permission.
- When evidence conflicts, surface the conflict in the guide and use a neutral verification question. Do not choose the interpretation most favorable to the seller.
- When a product, security, legal, pricing, or implementation answer is unknown, say so and capture an owner and follow-up; do not improvise.
- Keep seller talk tracks concise and conversational. Questions are options, not a checklist that must all be asked.

## Synthetic worked example

**Synthetic inputs:** Maya leads support operations and wrote, “We lose track of escalations between teams.” The product can record handoff ownership; no performance results or decision role are known.

**Opener:** “You mentioned that escalations can lose visibility between teams. Would it be useful to understand where that happens today, or is there another issue you would rather focus on?”

**Branch:** If Maya describes a recurring handoff gap → ask who owns it and what happens when missed. If it is no longer a priority → ask whether she wants to end or receive any requested overview. If she asks for measured results → say none were supplied, clarify the relevant measure, and capture a follow-up owner.

**Possible next step:** With Maya's agreement, send a verified capability summary; otherwise record no further action.
