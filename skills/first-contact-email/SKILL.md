---
name: first-contact-email
description: Draft a first business email from a defined audience, an evidenced reason for contact, and a bounded offer. Use for one-to-one or reusable first-touch drafts; do not use it as authorization to send.
compatibility: "Designed for Claude and ChatGPT."
---

# First Contact Email

Create a credible first business email that gives the recipient one clear reason for the contact and one feasible way to respond. Treat relevance as a claim that must be supported, not as a license to invent familiarity or urgency. Drafting never authorizes sending, scheduling, enrolling recipients, or changing records.

## Inputs

Ask only for information whose absence prevents a sound draft:

- **Audience:** recipient, role, company or segment, and the role's likely relationship to the topic.
- **Premise evidence:** the observable fact that makes contact relevant, its source and traceability, and when it was observed. Distinguish direct evidence from user-supplied interpretation.
- **Offer:** the concrete help, resource, or conversation being proposed; who can receive it; delivery constraints; and claims that can be substantiated.
- **Sender context:** sender identity, company, and a truthful basis for offering the help.
- **Next-step bounds:** an action the sender can actually fulfill, such as replying with interest, reviewing a resource, or choosing from genuinely available meeting times.
- **Voice or constraints:** tone, locale, required wording, and facts or claims to avoid.

If identity, premise, or offer details are absent, produce the safe parts and list the missing inputs. Do not fill gaps with guessed facts. A placeholder is acceptable only when it names the missing fact and is clearly marked for completion before use.

## Decide what the email can say

Build a small evidence ledger before drafting. For each personalized statement, record the fact, source, and whether it is current enough. User-provided facts may be used with attribution in the evidence notes; they are not independently verified merely because the user supplied them.

Choose one premise that connects the evidence to a plausible responsibility or priority of the audience. Prefer a direct, specific fact. When only audience-level evidence exists, write at that level rather than implying knowledge about an individual. Describe an inferred implication as a possibility, not a fact. Exclude stale, ambiguous, contradicted, or unsourced details.

If sources conflict on the premise, do not select the more convenient version. State the conflict, omit the disputed personalization, and identify what would resolve it. When no supported reason for contact remains, provide a partial draft or drafting frame and mark the premise as a blocking input.

Fit the offer to the premise. It must be within the stated scope and within the sender's ability to deliver. Do not add guarantees, customer names, results, discounts, deadlines, or availability that were not provided. Reduce a broad offer to the smallest useful proposition the recipient can understand without a sales narrative.

Choose one next step with low ambiguity. It should match the offer and the recipient's likely effort. Do not present a calendar link, attachment, resource, or time slot unless it exists or is supplied. If availability is unknown, invite a reply rather than inventing times.

## Draft the message

Give the email a simple progression:

1. Open with the supported premise and why it connects to this audience.
2. State the bounded offer in concrete terms.
3. Ask for the single chosen next step.

Keep one reason for contact throughout. Remove secondary pain points, unrelated proof, biography, and competing calls to action. Use plain language and a respectful, specific tone. Avoid manufactured familiarity, praise that is not evidenced, pressure, and claims about what the recipient personally thinks or needs.

## Use with RevSwing

For a campaign message, draft in the campaign's Content Studio and review the actual sequence context first with `campaign.get` and `campaign.sequence`. Use RevSwing variables only when the value exists or has an explicit fallback. AI columns can create lead-specific inputs, but generated output remains a draft claim until its evidence is verified.

For a one-to-one task or conversation, use the shared composer in Tasks or Inbox. Ask AI can propose a message before a sending account is connected, but its suggestion must be reviewed and applied explicitly. A saved or generated draft is not a sent message, and RevSwing keeps Send unavailable until the required account and permissions are present.

Before any campaign activation, run `campaign.validate`. `campaign.launch` is a consequential send tool: it first returns a confirmation request, then requires human approval and an exact replay with a fresh idempotency key. Do not infer authorization to send from a request to draft or review copy.

## Deliverable

Return:

1. **Subject options:** several short alternatives reflecting the same supported premise, without unsupported urgency or clickbait.
2. **Concise draft:** a send-ready-looking draft with unresolved placeholders visibly marked. It remains a draft.
3. **Evidence notes:** map each personalized or material claim to its supplied source and observation date when available; label inferences and note excluded evidence.
4. **Missing inputs:** only facts needed to remove placeholders, resolve uncertainty, or make the proposed next step feasible. Write `None` when nothing material is missing.

Do not send the email or imply that it was sent.

## Synthetic worked example

**Synthetic inputs:** Audience: operations lead at Northstar Labs. Evidence: Northstar's careers page listed three warehouse coordinator openings, observed 2026-09-20. Offer: a no-cost workflow review covering handoffs between hiring and warehouse scheduling. Sender can deliver the review but has no confirmed meeting times.

**Subject options:** “Northstar's warehouse hiring” / “Hiring and scheduling handoffs” / “Workflow review for warehouse growth”

**Draft:** Hi [First name] — I noticed Northstar is advertising three warehouse coordinator roles. If those hires are increasing the number of scheduling handoffs your team manages, I can share a short review of where those handoffs commonly stall and two changes worth testing. Would it be useful if I sent the review here?

**Evidence notes:** The openings and count come from the synthetic careers-page observation dated 2026-09-20. Increased handoffs are explicitly conditional, not presented as known. No individual activity is claimed.

**Missing inputs:** Recipient name; sender name and company.
