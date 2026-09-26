# RevSwing AI Skills

24 practical AI skills for using RevSwing with Claude, ChatGPT, Codex, and other agents that support the open Agent Skills format. Each skill combines a reusable revenue workflow with the real RevSwing screens and MCP tools that support it.

The library covers account research, prospecting, signals, positioning, outreach, sales conversations, campaign analysis, pipeline diagnostics, and data quality across RevSwing's Companies, People, Signals, Campaigns, Inbox, Tasks, Reports, and Integrations workspaces.

## Use with RevSwing

You can use every skill in either mode:

- **Connected mode:** connect the RevSwing remote MCP endpoint at `/mcp` through the agent's standard MCP connection flow, sign in to RevSwing, select the workspace, and let the skill use workspace-scoped tools.
- **Guided mode:** give the skill your exported or pasted context, then apply its output in the RevSwing screen named in the workflow.

RevSwing MCP uses Streamable HTTP and OAuth 2.1. Every tool call remains scoped to the authenticated workspace, granted scopes, and the member's resolved permissions. Connected reads such as `contacts.list`, `companies.list`, `campaign.sequence`, `inbox.thread`, and `analytics.campaign` run directly when the connection has the required access. Consequential tools use RevSwing's confirmation flow:

1. A `write`, `spend`, or `send` request returns a confirmation URL and impact summary.
2. A signed-in workspace member whose resolved permissions allow the requested action—an Admin or Member by default, or an eligible custom role—reviews the exact arguments and approves or rejects them.
3. After approval, the agent replays the same tool and arguments with the one-time confirmation token and a fresh idempotency key.
4. The operation counts as complete only after the replay succeeds.

This applies to `contact.create`, `contact.enrich`, `contact.unsubscribe`, `list.add_contact`, `campaign.enroll`, and `campaign.launch`. Approval never bypasses credential scopes, workspace tenancy, resolved role permissions, credits, sender readiness, suppression rules, sending limits, or campaign lifecycle checks.

### MCP tool catalog

The read-only catalog is `contacts.list`, `campaigns.list`, `campaign.get`, `campaign.sequence`, `campaign.validate`, `leads.search`, `lead.get`, `companies.list`, `lists.list`, `inbox.list`, `inbox.thread`, `analytics.campaign`, `analytics.workspace`, `tasks.list`, `domains.health`, `mailboxes.health`, `team.get`, `settings.get`, `webhooks.list`, and `memory.list`.

The consequential catalog is `contact.create`, `contact.enrich`, `contact.unsubscribe`, `list.add_contact`, `campaign.enroll`, and `campaign.launch`. MCP safety annotations describe each tool's actual side effects, but they do not replace RevSwing's server-side authorization, validation, and confirmation controls.

## Quick start

Clone the repository:

```bash
git clone https://github.com/RevSwing/ai-skills.git
```

Then choose the skill you need from `skills/`.

### Claude

Copy a skill folder into your project or personal Claude skills directory, or upload the folder through a supported Claude skill workflow. Keep the folder name and `SKILL.md` together.

Example project layout:

```text
.claude/
└── skills/
    └── account-research/
        └── SKILL.md
```

### ChatGPT and Codex

Add the selected skill folder through the supported Skills or plugin workflow. For a one-off task, attach or paste the relevant `SKILL.md` as task context and ask the model to use that skill.

Example request:

```text
Use the account-research skill to prepare an evidence-backed brief for this company. Separate facts, interpretations, hypotheses, and missing evidence.
```

## Skill library

### Strategy and positioning

| Skill | Purpose |
| --- | --- |
| [Audience Fit](skills/audience-fit/SKILL.md) | Turn product and customer evidence into testable account-fit rules, tiers, exclusions, and a validation pilot. |
| [Buying Committee](skills/buying-committee/SKILL.md) | Map evidence-backed roles, authority, responsibilities, and stakeholder gaps in a B2B purchase. |
| [Competitive Positioning](skills/competitive-positioning/SKILL.md) | Compare credible alternatives against buyer-specific criteria without inventing competitor claims. |
| [Outcome Offer](skills/outcome-offer/SKILL.md) | Convert verified capabilities and proof into a scoped, buyer-specific offer. |
| [Value Evidence Map](skills/value-evidence-map/SKILL.md) | Connect value claims to buyer outcomes, evidence strength, caveats, and usability decisions. |

### Research and prospecting

| Skill | Purpose |
| --- | --- |
| [Account Discovery](skills/account-discovery/SKILL.md) | Translate a segment brief into reproducible searches and an evidence-qualified account shortlist. |
| [Account Research](skills/account-research/SKILL.md) | Build a concise account brief with dated evidence, hypotheses, contrary signals, and research gaps. |
| [Buying Signal Review](skills/buying-signal-review/SKILL.md) | Assess whether a dated business event creates a credible reason for a conversation. |
| [Contact Role Mapping](skills/contact-role-mapping/SKILL.md) | Identify relevant people by role fit, current-employment evidence, and identity confidence. |
| [Market Source Scout](skills/market-source-scout/SKILL.md) | Compare current, lawful, accessible market data sources and design a coverage check. |
| [Problem Hypotheses](skills/problem-hypotheses/SKILL.md) | Turn account facts and interview evidence into ranked, falsifiable business-problem hypotheses. |
| [Prospect List Design](skills/prospect-list-design/SKILL.md) | Define or clean a reviewable prospect list with eligibility, normalization, deduplication, and suppression rules. |

### Outreach and messaging

| Skill | Purpose |
| --- | --- |
| [First Contact Email](skills/first-contact-email/SKILL.md) | Draft a focused first email from a supported premise, bounded offer, and feasible next step. |
| [Follow-up Email](skills/follow-up-email/SKILL.md) | Draft a useful follow-up after no response, or recommend stopping when another message is not justified. |
| [Next Step Design](skills/next-step-design/SKILL.md) | Choose the smallest credible action that creates value for both parties. |
| [Outreach Angle Lab](skills/outreach-angle-lab/SKILL.md) | Develop and compare distinct, evidence-grounded campaign premises. |
| [Outreach Copy Review](skills/outreach-copy-review/SKILL.md) | Review outreach for clarity, relevance, evidentiary support, and a proportionate ask. |
| [Professional Social Outreach](skills/professional-social-outreach/SKILL.md) | Draft connection and conversation messages suited to the actual relationship stage. |
| [Sequence Blueprint](skills/sequence-blueprint/SKILL.md) | Design a coordinated multichannel sequence with capacity controls, branches, and stop rules. |

### Conversations and operations

| Skill | Purpose |
| --- | --- |
| [Reply Triage](skills/reply-triage/SKILL.md) | Classify outreach replies and choose an appropriate response, handoff, or stop action. |
| [Sales Call Guide](skills/sales-call-guide/SKILL.md) | Prepare a branching introductory sales conversation grounded in known evidence. |
| [Campaign Measurement](skills/campaign-measurement/SKILL.md) | Analyze campaign data with explicit cohorts, denominators, quality controls, and bounded experiments. |
| [Pipeline Diagnostics](skills/pipeline-diagnostics/SKILL.md) | Diagnose pipeline inventory, cohort conversion, velocity, forecast limits, and data-quality risks. |
| [CRM Duplicate Review](skills/crm-duplicate-review/SKILL.md) | Identify likely duplicate records and prepare a conservative merge-review plan without changing CRM data. |

## Repository structure

```text
ai-skills/
├── README.md
└── skills/
    └── <skill-name>/
        └── SKILL.md
```

Every skill includes YAML frontmatter for discovery, task-specific instructions, uncertainty handling, a concrete deliverable, a RevSwing workflow, and a synthetic worked example.
