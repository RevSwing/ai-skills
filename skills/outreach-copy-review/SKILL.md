---
name: outreach-copy-review
description: Audit and revise a business outreach draft for clarity, recipient relevance, evidentiary support, and a proportionate ask while preserving its intended meaning and factual claims.
compatibility: "Designed for Claude and ChatGPT."
---

# Outreach Copy Review

Review the words the recipient will actually receive. Diagnose specific passages and their likely interpretation; do not assign a performance, quality, persuasion, or deliverability score. The outcome is a clearer draft with traceable edits, visible uncertainty, and a credible next step. Do not promise or predict response-rate gains.

## Inputs

Use the draft plus whatever context is available:

- recipient role, organization, and situation;
- sender's intended meaning and desired next step;
- source or status of personalization, proof, product claims, and results;
- channel, relationship stage, constraints, and any required wording.

Proceed when some context is missing. Mark assumptions and place consequential missing facts in the unresolved-facts section. Ask a question first only when the draft is absent or when two plausible interpretations would produce materially different messages and the intended one cannot be inferred.

## Review the draft

First identify the draft's current proposition: why this recipient, what problem or opportunity is named, what the sender claims, and what action is requested. Separate those elements from stylistic wording so the revision does not silently change the offer, audience, commercial terms, or level of commitment.

Audit the text in four dimensions:

1. **Clarity:** Locate vague references, dense sentences, jargon, buried purpose, conflicting statements, and unclear actors or timing. State what a recipient could misunderstand.
2. **Relevance:** Connect each recipient-specific statement to supplied evidence. Distinguish observed facts from role-based hypotheses and generic relevance. Remove personalization that does not help explain why the outreach matters, and soften inferred needs into appropriately tentative language.
3. **Evidence:** Inventory factual claims, named customer or partner references, comparisons, quantified outcomes, superlatives, and implied guarantees. Preserve supported claims accurately. Do not invent proof, upgrade a hypothesis into a fact, or change a number to make it sound stronger. Flag missing source traceability, scope, date, comparability, or permission. If a claim cannot be supported, recommend verification, qualification, or removal and show the safe revision.
4. **Ask quality:** Assess whether the requested action is clear, specific, proportionate to the relationship, and deliverable by the sender. Reduce unnecessary recipient effort, expose hidden prerequisites, and make the response path easy. Do not manufacture urgency or treat silence as interest.

Prefer the smallest edit that fixes a material problem. Preserve useful specificity and the sender's recognizable voice. Explain meaningful tradeoffs: for example, qualifying an uncertain claim improves credibility but reduces apparent certainty; shortening context improves scanability but may remove rationale a less familiar recipient needs. Do not apply universal word-count, tone, or formatting rules.

## Use with RevSwing

Review copy in its real context. Use `campaign.sequence` for a campaign step and `inbox.thread` for a conversation reply so the revision does not repeat, contradict, or overstate earlier messages. Use `lead.get`, `contacts.list`, or `companies.list` only for fields they actually return; missing details remain unresolved rather than becoming personalization.

Apply approved revisions in the campaign Content Studio, Inbox, or Tasks shared composer. Ask AI suggestions and AI-column values are drafts that require review. Preserve valid RevSwing variables and confirm that every variable has a value or fallback before the copy is ready.

For campaign copy, run `campaign.validate` after saving the sequence. This skill does not send. `campaign.launch` requires a separate confirmation request, human approval of the exact lead IDs and campaign, and an exact replay with a fresh idempotency key.

## Deliverable

Return these sections:

### Prioritized edits

List material edits in priority order. For each, quote or identify the affected passage, explain the recipient-facing issue, and state the change. Prioritize misleading or unsupported content, then unclear relevance or ask, then readability. Do not pad the list with cosmetic rewrites.

### Revised draft

Provide a ready-to-review version. Retain required language and supported factual claims. Use brackets only for information that must be supplied before use, such as `[verified result and source]`; do not disguise invented copy as a placeholder. Drafting does not authorize sending the message or starting a campaign.

### Unresolved facts

List facts that require verification, their source if known, and the consequence of leaving each unresolved. State `None` when the revision needs no additional verification.

### Tradeoffs

Briefly record choices that meaningfully affect specificity, tone, evidence strength, or recipient effort. State `None material` when applicable. Describe expected communication effects qualitatively without claiming performance gains.

## Synthetic example

**Draft:** “Saw Acme is scaling fast. Our platform guarantees 40% more pipeline. Can you spare 45 minutes tomorrow?”

**Context:** Acme posted three sales openings. The sender has no source for the 40% figure and has had no prior contact.

**Prioritized edits:** Replace “scaling fast” with the observed hiring signal and avoid inferring company-wide growth. Remove the unsupported guarantee. Replace the abrupt 45-minute request with a smaller, specific invitation tied to the hiring context.

**Revised draft:** “I noticed Acme is hiring for three sales roles. Teams adding reps sometimes revisit how new pipeline is created and followed up. Would a brief exchange about that workflow be useful for your team?”

**Unresolved facts:** Whether the recipient owns this workflow; the product's verified capabilities; any approved customer evidence relevant to growing sales teams.

**Tradeoffs:** Removing the number makes the message less dramatic but avoids presenting unverified proof. The smaller ask tests relevance before requesting meeting time.
