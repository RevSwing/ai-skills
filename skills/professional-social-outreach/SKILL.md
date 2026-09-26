---
name: professional-social-outreach
description: Draft evidence-grounded professional social connection requests and conversation messages suited to the relationship stage, platform constraints, and recipient responses; do not use it to automate engagement or sending.
compatibility: "Designed for Claude and ChatGPT."
---

# Professional Social Outreach

Draft a credible connection or conversation message for the current relationship stage. Use only context supplied by the user or verified in a public source. Drafting does not authorize sending, connecting, following, reacting, commenting, scraping profiles, or automating engagement.

## Gather the usable context

Use the information available about:

- **People and relationship:** identities, roles, organization, how they actually know of each other, and the last direct interaction.
- **Evidence:** relevant facts, sources, observation dates, and whether each fact was user-supplied or publicly verified.
- **Intent:** connection, question, resource, continued discussion, or a next step the sender can fulfill.
- **Platform constraints:** channel, message type, supplied character limit, sequence rules, and consent or contact restrictions.
- **History and voice:** prior messages, exact replies, referrals, requested follow-up dates, refusals, touches already made, formality, and locale.

Ask only for missing facts that block a sound draft. Otherwise mark assumptions. Never invent profile details, engagement, shared groups, mutual connections, events attended, interests, problems, or familiarity. A public fact may support relevance, but it does not prove a personal need. If evidence conflicts, prefer a direct recipient statement and the most recent dated primary source; disclose unresolved conflicts and omit the disputed claim.

## Match the message to the stage

Choose one stage from the evidence:

1. **No established relationship:** Give a truthful point of relevance and make a modest request. Do not put a full pitch in an invitation or imply prior contact.
2. **Connected, no conversation:** Explain briefly why the sender is writing. Offer one grounded idea, question, or resource. Acceptance is not interest.
3. **Active conversation:** Respond to what the recipient said, answer questions first, and propose a proportionate next step.
4. **Warm introduction or known relationship:** Name the real introduction or interaction accurately. Mention a referrer only as authorized; do not imply endorsement or recipient interest.
5. **Dormant conversation:** Reopen only with a genuine new reason or at a requested time. Do not assume old context still applies.

Honor supplied platform limits. If a limit or feature is unknown, say so and provide a concise draft plus a shorter fallback. Do not advise tactics that evade platform controls or simulate organic behavior.

## Build the conversation path

Keep each draft focused on one supported reason and one feasible next step. Avoid generic praise, exaggerated admiration, pressure, false urgency, and calling a public post “insightful” unless the draft names a concrete, verified idea.

Provide response branches only for plausible recipient signals:

- **Interested or asks a question:** answer directly, then offer the smallest useful next step.
- **Asks for information:** offer only material that exists and the sender can provide.
- **Refers another person:** follow the stated boundary; do not imply the new person expects contact.
- **Not now:** acknowledge the timing and use a future date only if the recipient provides one.
- **Declines or asks to stop:** acknowledge briefly and stop; do not rebut or switch channels.
- **No response:** silence is not interest. Follow up only when rules allow it and there is meaningful new value.

Stop when there is an opt-out or refusal, a platform or sequence limit is reached, a requested recontact date has not arrived, the account or channel is unusable, or no supported and useful next message remains. Do not produce a sendable follow-up after a decisive stop signal.

## RevSwing workflow

Use `/integrations/linkedin` to review the connected LinkedIn identity and extension state, `/settings/sending-limits` for configured LinkedIn limits, `/tasks/linkedin` for due manual social steps, `/inbox` for synchronized conversation history, and `/communications` for saved action status and delivery evidence. If an action is marked outcome unknown or reconciliation required, preserve that state and do not draft or recommend a resend. `/campaigns/{campaignId}` shows the sequence context when the message belongs to a campaign.

MCP can read relevant context with `inbox.list`, `inbox.thread`, `tasks.list`, `campaign.get`, `campaign.sequence`, `campaign.validate`, `leads.search`, and `lead.get`. It has no LinkedIn send, connect, follow, react, comment, or retry tool. Keep the output as a draft and direct execution to the verified RevSwing screens only when the user has authorized it. `campaign.enroll` and `campaign.launch` are consequential and are not part of drafting social copy. If separately requested, call with final arguments to obtain confirmation, wait for signed-in approval, then replay the exact same tool and arguments with the confirmation token; changed arguments require a new confirmation.

## Deliverable

Return:

1. **Stage and evidence notes:** relationship stage, facts and source traceability, uncertainties, and excluded claims.
2. **Primary draft:** labeled by message type and visibly marked if a placeholder remains.
3. **Short fallback:** only when a platform limit is unknown or compression may be needed.
4. **Response branches:** concise drafts for the likely signals relevant to this situation.
5. **Stop condition:** the exact signal or limit after which outreach should end.

Do not send or schedule any message.

## Synthetic worked example

**Synthetic inputs:** Lena wants to connect with Omar, an operations director. His company announced a new distribution center on 2026-09-12. They have no prior relationship. The platform limit is unknown. Lena can share a warehouse handoff checklist.

**Stage and evidence:** No established relationship. The distribution-center announcement is public company context; Omar's personal priorities are unknown.

**Connection draft:** Hi Omar — I saw your company's announcement about the new distribution center. I work on warehouse handoffs and would value connecting. No assumption that this sits with you.

**Short fallback:** Hi Omar — your company's new distribution center caught my attention. I work on warehouse handoffs and would value connecting.

**Branches:** If interested: “Thanks, Omar. I have a short handoff checklist I can share here if useful.” If he says it is outside his role: “Thanks for clarifying. I won't keep pursuing it with you.”

**Stop condition:** Stop if Omar declines, asks not to be contacted, or does not respond and no permitted follow-up with new value is supplied.
