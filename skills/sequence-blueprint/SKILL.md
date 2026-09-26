---
name: sequence-blueprint
description: Design a coordinated email, social, and call outreach sequence from audience evidence, operating capacity, channel constraints, and explicit stop rules; use for planning and experimentation, not sending or campaign activation.
compatibility: "Designed for Claude and ChatGPT."
---

# Sequence Blueprint

Create an executable outreach plan without executing outreach. It must not send messages, place calls, enroll contacts, alter a CRM, or imply that drafting authorizes those actions.

## Gather the planning inputs

Use supplied material and ask only when a missing fact prevents a sound plan. Otherwise proceed with clearly labeled assumptions.

- Define the goal, audience segment, buyer roles, and desired next step.
- Inventory observed problems or signals, approved claims, relevant proof, and source dates. Distinguish facts from hypotheses; do not turn weak evidence into personalization.
- Record channel eligibility and constraints: known preferences or consent, verified contact data, regional or company rules, social connection status, and channels unavailable to the team.
- Quantify capacity by channel: people, time, call coverage, research effort, reply handling, and concurrent conversations.
- Identify existing campaigns, recent touches, account owners, handoff rules, working hours, key dates, and measurement access.

If eligibility, policy, or contact data is unknown, mark the affected step `conditional` and state what must be verified before activation. Lack of a channel does not block designing a useful sequence around the available channels.

## Design from constraints

Start with the minimum coherent sequence that can test the intended angle within team capacity. Give every touch a job, such as establishing relevance, adding evidence, handling an objection, or making a low-friction close. Remove repetition.

Choose channels because they suit the audience, evidence, and operating model. A call can support a small, high-value segment with reliable numbers and enough capacity; social can add context when profiles are current and permitted; email can carry evidence when addresses and use are allowed. Do not claim a mix or timing pattern works universally.

Express cadence as reasoned intervals or event triggers. Tie delays to reply capacity, buyer work cycles, evidence shelf life, time zones, existing frequency, or observation needs. Where the basis is weak, label the interval as a test parameter.

Coordinate frequency at contact and account level. Check active sequences and owner activity before each touch. Define a context-appropriate contact budget or collision rule; with no defensible numeric cap, require owner review of recent and scheduled touches. Never use a new channel to evade a stop or opt-out.

## Build branches and controls

Represent the plan as states rather than an unconditional list. At minimum, specify:

- **Positive or curious response:** pause automation, assign a reply owner, and route to the agreed next step.
- **Objection or deferral:** stop the default path; answer only within available evidence, or schedule a dated follow-up when the contact requested one.
- **Referral:** stop messaging the original contact unless they invited continued contact; validate the new role and eligibility before a new plan.
- **No response:** continue only through the approved remaining steps, then close or cool down according to the plan.
- **Wrong person, hard bounce, invalid number, or channel restriction:** suppress the affected address or channel and investigate rather than substituting blindly.
- **Opt-out, do-not-contact request, or equivalent signal:** stop all covered outreach immediately, record the scope for later execution, and do not re-enter through another channel. Flag uncertainty about scope for policy review while applying the broad safe stop.

Name owners for sequence operations, replies, calls, data correction, and escalation. Include service expectations only when supplied or approved.

## Define the experiment

State the hypothesis, audience unit, eligibility rule, primary outcome, guardrails, observation window, and decision rule before launch. Change one material variable per comparison when attribution matters. Prefer outcomes connected to the goal, such as qualified replies or accepted meetings, while also tracking opt-outs, complaints, invalid contacts, and workload. Do not invent benchmarks or promise significance. If sample size is limited, frame the result as directional and record confounders such as list quality, sender, timing, or simultaneous campaigns.

## Use with RevSwing

When RevSwing is connected, use `campaigns.list` to locate the campaign, then `campaign.get` and `campaign.sequence` to inspect its lifecycle and persisted step order. Use `campaign.validate` before recommending activation; report every sender, sequence, and lead-readiness issue instead of treating a draft as launchable.

Build and edit the sequence in the campaign workspace and Content Studio. RevSwing campaign steps and variants use the shared composer, including variables, templates, snippets, signatures, attachments, and explicit saves. Use AI columns only for per-lead values that have a defined input, output, and fallback; generated values are not verified facts.

If contacts need to be added, `campaign.enroll` creates non-launched memberships. `campaign.launch` is a separate send action. Both require a signed-in workspace member whose resolved permissions allow the action—an Admin or Member by default, or an eligible custom role—to review the exact arguments, approve the confirmation request, and allow an exact replay with a fresh idempotency key. Never describe a campaign as enrolled or launched until that replay succeeds. Credential scopes, workspace tenancy, resolved role permissions, credits, suppression, sender, sequence, lifecycle, and sending-limit checks still apply after approval.

## Deliverable

Return: assumptions and evidence limits; audience and eligibility; channel rationale; a step table with state, trigger or delay, purpose, evidence, owner, and next branch; coordination and stop rules; capacity check; and an experiment card with success, guardrail, and revise/stop criteria. End with a separate activation checklist listing unresolved verifications and required execution authorization.

## Synthetic example

**Fictional scenario:** Northstar Analytics has 40 opted-in operations leads, one caller for two hours weekly, one dated case study, and a product launch in three weeks. Design email as the primary evidence channel, reserve calls for leads who engaged or match the highest-value tier, and use social only where profiles are current and company policy permits it. Treat a three-business-day email interval as an experiment chosen to keep replies within owner capacity. Any reply pauses the path; an opt-out suppresses all outreach; another team touch triggers owner review. Compare two opening angles on qualified replies, with opt-outs and reply backlog as guardrails, and label the small result directional.
