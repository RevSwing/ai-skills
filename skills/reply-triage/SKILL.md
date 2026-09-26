---
name: reply-triage
description: Classify replies to business outreach, choose the appropriate response or handoff, and draft a reply when warranted while honoring opt-outs and uncertainty.
compatibility: "Designed for Claude and ChatGPT."
---

# Reply Triage

Turn an inbound outreach reply into an evidence-based classification and an operational next step. Keep two decisions separate: what the message means and what should happen because of it. Classification describes intent; action accounts for consent, ownership, timing, and available context. Drafting a response does not authorize sending it or changing a CRM.

## Gather the relevant record

Use the exact reply plus enough thread context to interpret references such as “that,” “later,” or “her.” Also use any supplied contact and account identities, sender identity, offer, ownership rules, prior consent or suppression status, and permitted next steps. Preserve message dates when timing matters.

Treat quoted history, signatures, automated notices, and the recipient's new words as distinct parts of the message. Do not classify text from the seller's earlier email as if the recipient wrote it. Ask for missing information only when it blocks a safe decision, such as whether “remove me” refers to outreach or an attached event list. Otherwise state a narrow assumption and proceed.

## Classify the reply

Assign a **primary intent** and, when needed, one or more **secondary intents**. Use these labels:

- **Positive:** expresses interest or accepts a relevant next step.
- **Referral:** identifies or offers to connect a more appropriate person.
- **Ambiguous:** meaning or desired action cannot be determined reliably from the record.
- **Objection:** raises a concern about fit, value, timing, authority, budget, or approach without asking to end contact.
- **Out of office:** an automated or explicit temporary-absence notice, possibly with a return date or alternate contact.
- **Wrong person:** says the recipient does not own, use, or decide on the topic. This is not a referral unless a specific alternative person or route is supplied.
- **Opt-out:** asks to stop outreach, be removed, unsubscribe, or otherwise withdraws permission.

Classify all material signals in a mixed reply. Explicit opt-out language overrides sales intent for the action even if the same reply is positive, supplies a referral, or asks a substantive question. Record those other signals as secondary context, but do not use them to continue selling. Do not infer an opt-out from a mere objection, wrong-person statement, or out-of-office notice. Conversely, do not soften “not interested, remove me” into an objection.

Support each label with a short quote or faithful paraphrase from the recipient-authored portion. Mark confidence as high, medium, or low. When evidence conflicts, explain the conflict and prefer the most recent explicit instruction. Do not invent sentiment or treat politeness as interest.

## Choose the action

Map classification to a proportionate next step:

- For positive replies, answer the question or advance only the accepted next step.
- For referrals, thank the recipient and route to the named person only within the user's authorization; do not imply an introduction occurred unless it did.
- For ambiguous replies, ask one focused clarifying question if a reply is safe and useful.
- For objections, address the stated concern using supplied facts, narrow the proposal, or hand off to the person who can answer. Do not manufacture proof.
- For out-of-office replies, honor an explicit return date and routing instruction. Avoid drafting an immediate sales reply to an automated notice unless the notice requires a practical response.
- For wrong-person replies, close the loop or ask for direction only when appropriate; do not pressure the recipient to perform prospecting.
- For opt-outs, suppress further sales follow-up. A minimal non-promotional acknowledgment may be drafted only if policy or the user calls for one.

Name the appropriate **owner** from supplied roles, such as account owner, sales representative, support, legal/privacy, or “unassigned.” Give a concrete next step and timing if the reply provides one. Never invent routing rules. Separate internal actions from recipient-facing text.

## RevSwing workflow

Use `/inbox` to review the full message timeline and campaign context before classifying. The Inbox supports All, Unread, Replies, Interested, and Not interested views, assignment, reply sentiment, replies, and unsubscribe; marking a disposition stops automated follow-ups for that lead, while unsubscribe additionally suppresses future email outreach. For LinkedIn threads, honor any awaiting-result or reconciliation warning and do not resend while the outcome is unknown. Use `/communications` when delivery history is needed.

For MCP-assisted triage, `inbox.list` can list threads by `unread`, `read`, `replied`, or `archived`, and `inbox.thread` returns one ordered conversation with its contact. The MCP does not provide reply sending, assignment, or disposition tools, so draft those actions or direct the user to `/inbox`. `contact.unsubscribe` is consequential: it applies account-wide email suppression and stops active campaign memberships. Call it only after the user approves the exact email and optional reason. The first call creates a confirmation request; after a signed-in member approves it, replay `contact.unsubscribe` with the exact same arguments and confirmation token. Never substitute a different email or reason; changed arguments require a new confirmation.

## Deliverable

Return:

1. **Classification:** primary intent, secondary intents, confidence, and evidence.
2. **Action:** recommended disposition, owner, next step, and timing.
3. **Draft:** a context-appropriate reply when useful, or “No draft” with the reason.
4. **Stop flags:** `sales_follow_up`, `other_outreach`, and `record_or_consent_action`, each stated explicitly with the evidence that controls it. Use “unknown—verify” where the record or policy is insufficient.

Keep the draft faithful to the thread, concise enough for the situation, and clear about what happens next. Do not claim a meeting, referral, removal, or transfer is complete unless the supplied record establishes it.

## Synthetic worked example

**Input:** “This looks relevant, but I am not the owner. Please contact Ren in Operations—and remove me from future sales emails.”

**Output:** Primary intent: opt-out (high); secondary: positive and referral. Evidence: the recipient says “remove me” and names Ren. Action: the account owner should record the opt-out; contacting Ren is a separate action that requires existing authorization. Draft: no sales reply; optionally acknowledge removal if policy calls for it. Stop flags: sales follow-up—stop; other outreach to this recipient—stop; record or consent action—required.
