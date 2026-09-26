---
name: follow-up-email
description: Draft evidence-grounded follow-up emails after no response, or recommend stopping, using the supplied conversation history, sequence limits, and consent signals.
compatibility: "Designed for Claude and ChatGPT."
---

# Follow-up Email

Turn a non-response into one of two useful outcomes: a follow-up draft that gives the recipient a fresh reason to engage, or a recommendation to stop with a concise rationale. Treat silence as an absence of evidence. It does not show interest, agreement, objection, or even that the earlier message was read.

## Required context

Use the information the user supplies:

- the complete relevant thread or a reliable summary, including dates and senders;
- the recipient's role and any facts already established about their situation;
- the offer, claim, resource, or question that the follow-up may legitimately introduce;
- sequence rules: messages already sent, maximum touches, allowed channels, timing limits, and any campaign stop conditions;
- consent signals, refusals, opt-outs, delivery failures, or requested recontact dates;
- the intended next step and the sender identity or voice, when those affect the draft.

Ask only for information whose absence prevents a sound send-or-stop decision. Otherwise proceed and label material assumptions. Do not invent opens, clicks, meetings, shared contacts, company events, needs, urgency, or previous engagement.

## Decide before drafting

Reconstruct the interaction in chronological order and separate four kinds of evidence: what the recipient explicitly said, what the sender said, verified context supplied by the user, and unknowns. Resolve apparent conflicts by favoring direct recipient statements and the most recent dated evidence. Flag a conflict that cannot be resolved instead of selecting the convenient interpretation.

Recommend stopping when any of these applies:

- the recipient opted out, refused the topic, asked not to be contacted, or otherwise withdrew permission;
- the sequence limit or another supplied stop condition has been reached;
- the requested recontact date has not arrived;
- repeated delivery failure makes the address or channel unusable;
- the only possible message would repeat the prior ask, manufacture familiarity, or imply engagement that is not in the record.

A refusal is not converted into an objection to overcome. If the recipient redirected the sender to another person, use that direction only as authorized and do not claim the new person knows the sender. If the evidence merely shows silence and the sequence still permits another touch, evaluate whether the message can add a real value delta.

## Find the value delta

The follow-up should earn its place by adding one relevant element that the prior message did not provide. Examples include a concise clarification, a directly useful resource the user supplied, a verified answer to an unresolved question, a narrower proposal, or an easier next step. Connect it to the existing thread without pretending it was requested or consumed.

Reject weak deltas such as “bumping this,” generic urgency, an unsupported compliment, or a restatement of the original pitch. When no defensible delta exists, recommend stopping rather than filling the sequence quota.

## Draft the message

Use the thread's established voice and level of formality. Make the connection to the earlier message accurate and brief. Lead with the new value or clarification, then offer a proportionate next step. A low-friction choice, a concrete question, or permission to close the loop may fit; choose based on the actual context rather than a stock pattern.

Avoid guilt, pressure, and surveillance language. Do not mention that the recipient is “busy,” “must have missed” the note, opened a message, visited a page, or showed interest unless the supplied evidence supports that exact claim and its use is appropriate. Do not use phrases that imply a relationship, prior conversation, or internal knowledge that the record does not establish.

Return either:

1. **Draft** — subject line when useful, message body, and a short note naming the new value introduced and any material assumption; or
2. **Stop recommendation** — do not include a sendable draft. State the decisive evidence, the applicable limit or consent signal, and whether a future follow-up is allowed under an explicit recipient request.

## Use with RevSwing

Start with the actual context. For campaign follow-ups, inspect `campaign.sequence` and the relevant membership with `leads.search` or `lead.get` before proposing the next step. For a reply-led follow-up, inspect the conversation with `inbox.list` and `inbox.thread`; do not invent prior messages or classify an unread thread from a subject line alone.

Draft in the campaign Content Studio, Inbox, or Tasks shared composer. Ask AI can generate a suggestion that preserves variables, but the user must review and apply it. Saving a draft does not send it. RevSwing has no MCP tool for sending an individual Inbox reply, so provide a reviewable draft and leave that send action in the product UI.

If the follow-up is a campaign step, run `campaign.validate` before launch. `campaign.launch` requires confirmation, human approval, and exact replay with a fresh idempotency key; report success only after execution returns a successful receipt.

## Synthetic worked example

**Input:** A seller sent one email about reducing manual renewal reporting. There was no reply. The sequence allows one more email. The user provides a two-step worksheet that estimates reporting effort, but has no evidence the recipient read the first email.

**Output:**

**Draft**

Subject: Renewal reporting worksheet

Hi Mira — following up with a worksheet that may be useful if renewal reporting is still manual. It breaks the estimate into data collection and report preparation, so you can assess the effort without a call. Would it be useful if I sent it over?

Best,
Jon

**Note:** The draft adds the supplied worksheet and asks permission to share it. It makes no claim that Mira saw the first email or has the stated problem.
