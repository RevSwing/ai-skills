---
name: buying-committee
description: Map evidence-backed roles in a B2B purchase and tailor discovery and contact priorities for users, champions, approvers, procurement, and blockers.
compatibility: "Designed for Claude and ChatGPT."
---

# Buying Committee

Build a working map of who affects a B2B buying decision, what is known about their role, and what to validate next. Use it for opportunity discovery, account planning, deal reviews, or stakeholder preparation. Treat the map as a set of testable claims, not an org chart.

## Required inputs

Use the supplied contacts, meeting notes, emails, CRM fields, evaluation activity, decision process, commercial steps, and timing. Capture the purchase in scope and its current stage. Source and date consequential claims when available.

Ask for more information only when the purchase itself or the available evidence is too unclear to produce a useful map. Otherwise proceed, identify gaps, and mark assumptions. Do not invent reporting lines, access, budget, motives, or authority.

## Assign roles from behavior and authority

A person may hold multiple roles, and a role may have multiple people. Do not force every role to be filled. A job title is a clue about likely responsibilities; it is not evidence of authority in this decision.

- **User:** will operate, adopt, administer, or directly experience the proposed solution. Look for workflow ownership, hands-on evaluation, requirements, or adoption responsibility.
- **Champion:** actively advances the purchase inside the account and has enough credibility or access to influence it. Look for internal coordination, candid process guidance, introductions, advocacy, or work done between seller interactions. Enthusiasm alone is insufficient.
- **Approver:** can authorize the relevant commitment, budget, exception, or final decision. Look for an explicit signoff requirement, demonstrated budget control, or a named approval step. Seniority alone is insufficient.
- **Procurement:** owns or materially controls purchasing, commercial negotiation, or vendor onboarding and may coordinate required legal or security reviews. Look for explicit process ownership or purchasing gates. Do not treat every reviewer as procurement or assume procurement chooses the business solution.
- **Blocker:** can materially delay, prevent, or veto progress, with evidence of a specific gate, objection, competing priority, or withheld action affecting this purchase. Do not label someone a blocker merely because they ask hard questions, negotiate, lack enthusiasm, or have not replied.

For each assignment, record evidence and confidence as **confirmed**, **supported**, or **tentative**. Confirmed means the role or authority was credibly stated or demonstrated in the process. Supported means multiple observations fit without direct confirmation. Tentative means a plausible hypothesis with limited or indirect evidence. Preserve conflicts rather than averaging them away. Note evidence age when process or personnel may have changed.

## Build the map

1. Define the decision in scope. Separate this purchase from broader account influence.
2. Extract observable statements and actions before interpreting roles. Keep source facts distinct from inferences.
3. Assign only roles supported by those observations. If evidence is absent or contradictory, leave the role unknown or show competing hypotheses.
4. Identify what each person appears responsible for, what outcome or risk they have expressed, and their demonstrated influence on the next decision.
5. Turn material gaps into validation questions. Questions should be neutral, answerable, and tied to a decision: for example, “Who must approve an exception to the current budget?” Avoid leading questions such as “You are the final decision maker, right?”
6. Rank contact priorities from the current stage, unresolved risk, and ability to clarify or advance the next step. Do not rank by seniority alone. Give each priority a specific objective and evidence-based rationale.

## RevSwing workflow

When the user is working in RevSwing, use **People** (`/people`) and **Companies** (`/companies`) for known workspace identities and account context. Use **Inbox** (`/inbox`) for what stakeholders actually said, the campaign People and Activity views (`/campaigns/[id]`) for membership and engagement context, and **Tasks** (`/tasks`) for open follow-up work. These surfaces are evidence sources; a title, campaign membership, message event, or task assignment does not by itself establish buying authority.

With a connected RevSwing MCP client, `contacts.list` and `companies.list` support bounded identity lookups; `inbox.list` and `inbox.thread` retrieve persisted conversations; `leads.search` and `lead.get` retrieve campaign memberships; and `tasks.list` retrieves workspace tasks. Treat returned fields as workspace records with the same uncertainty rules as supplied CRM data. The role map itself requires no write, send, or spend action.

If the user separately requests a consequential follow-on, use only the exact available tool for that action. `contact.create`, `list.add_contact`, and `campaign.enroll` change workspace state; `contact.enrich` spends credits; `campaign.launch` sends; and `contact.unsubscribe` applies account-wide suppression and stops active campaign memberships. Each requires human confirmation, then an exact replay of the same tool and arguments with the approval token; changed arguments require a new confirmation. Never treat approval of the role map as approval of one of these actions.

## Deliverable

Produce four sections:

1. **Role map:** a table with person, evidence-backed role or roles, responsibilities in this decision, evidence and source, confidence, and current implication.
2. **Unknowns and conflicts:** unfilled roles, disputed authority, missing process steps, stale evidence, and assumptions that could change the plan.
3. **Validation questions:** grouped by the person best placed to answer, with the gap each question resolves.
4. **Contact priorities:** ordered contacts or stakeholder types, the objective for the next interaction, rationale, and any access dependency. If no named contact is justified, prioritize the role to identify rather than inventing a person.

Tailor discovery to responsibility: ask users about workflow and adoption, champions about internal alignment and process, approvers about outcomes and authorization criteria, procurement about gates and commercial requirements, and potential blockers about the concrete risk or constraint they own. Drafting questions or a contact plan does not authorize sending outreach, purchasing contact data, or changing CRM records.

## Synthetic example

Suppose Maya ran two product trials and documented team requirements; Luis introduced finance and shared the internal review sequence; Priya is called “VP” but has not participated; and Chen says all new vendors require his security review. Map Maya as a supported **user**, Luis as a supported **champion**, Chen as a confirmed security reviewer without forcing him into procurement, and leave **approver** unknown. Priya's title is not enough. First validate who owns budget approval and whether Chen can reject the vendor or only recommend remediation. Prioritize Luis for process clarification, then Chen for security criteria; contact Priya only after confirming her part in this purchase.
