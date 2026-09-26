---
name: crm-duplicate-review
description: Review CRM account or contact records for likely duplicates and produce a conservative, evidence-based merge plan without changing CRM data.
compatibility: "Designed for Claude and ChatGPT."
---

# CRM Duplicate Review

Identify records that may represent the same real entity, explain the evidence and uncertainty, and prepare a human-review plan. This is analysis only: do not merge, delete, overwrite, reparent, or otherwise mutate records. A merge recommendation is not authorization to execute it.

## Inputs and scope

Use the records in scope with their stable record IDs and entity type. Retain raw field values, source systems, creation and update times, ownership, relationships, activity references, and consent or suppression history when available. Record the matching scope, such as one workspace, region, business unit, or import batch.

Do not silently fill absent values. If stable IDs or entity types are missing, ask for them because a review plan cannot safely identify its subjects. For other missing evidence, proceed with an explicit limitation and mark affected candidates `insufficient evidence` or `needs verification`.

Keep accounts and contacts in separate comparisons. Also distinguish legal entities, locations, subsidiaries, and parent organizations when the data supports those distinctions.

## Review workflow

### 1. Create comparison values

Create reversible comparison values without changing the raw records. Depending on the field, trim whitespace, normalize case, standardize punctuation, parse domains, and standardize phone numbers only when the country context is known. Treat legal suffix removal, aliases, transliteration, and address standardization as comparison aids rather than canonical truth. Keep a field-level note of each transformation and any ambiguity.

### 2. Form candidate groups

Block and compare records using several relevant signals rather than broad resemblance alone. Strong account signals can include an exact authoritative registration identifier or multiple consistent attributes such as verified domain, address, and phone. Strong contact signals can include the same verified personal email, profile identifier, or phone together with compatible name and employer evidence.

A shared domain or similar organization name does not prove that accounts are identical. It may connect a parent, subsidiary, franchise, branch, or unrelated organization. Likewise, a shared or role mailbox such as `sales@` or `info@` is a contact route; it does not establish that two records describe one person.

### 3. Assign evidence-based confidence

Label each group `likely duplicate`, `possible duplicate`, `insufficient evidence`, or `confirmed separate` when decisive evidence establishes distinct entities. Explain the supporting and disconfirming signals and their source traceability. Confidence in identity is separate from confidence in choosing a survivor record. Prefer independent, specific, current signals over counts of weak similarities. Do not invent a universal score or claim certainty that the inputs do not support.

### 4. Review conflicts and stop conditions

Surface conflicts before proposing survivorship. Examples include different legal identifiers, incompatible locations, distinct people sharing a mailbox, parent-versus-subsidiary evidence, separate active customer relationships, and contradictory names or employers. Mark an explicit `no merge` when evidence indicates separate entities. Use `hold for verification` when a decisive conflict could plausibly be stale or erroneous, and name the evidence needed to resolve it.

### 5. Propose field survivorship

For reviewable candidates, propose a survivor record and a field-by-field plan based on authority, recency, completeness, and source traceability. Assess source-system identity, ownership, creation, activity, and relationship dependencies before choosing the structural survivor. When those facts are missing, report `survivor TBD` and the evidence needed; field-level recommendations can still be made without selecting a structural survivor. Do not use “newest wins” as a blanket rule. Preserve alternate values when they remain meaningful.

Treat these as protected: immutable record and external IDs; source and audit metadata; original creation times; consent, legal-basis, subscription, unsubscribe, suppression, bounce, and do-not-contact history; retention or deletion flags; and activity or relationship references. Never turn unknown or withdrawn consent into permission. Where consent states conflict, retain the full history and use the most restrictive effective state until an authorized reviewer resolves it. Describe any required activity or relationship re-linking for later execution, but do not perform it.

## RevSwing workflow

For RevSwing records, inspect **People** (`/people`) for contact identity, suppression state, campaign memberships, and recent activity; use **Companies** (`/companies`) for company identity and linked-contact context. Check **Inbox** (`/inbox`) and the campaign People and Activity views (`/campaigns/[id]`) when a proposed merge could affect conversation or campaign relationships. These surfaces help inventory dependencies; they do not authorize a merge.

With RevSwing MCP, `contacts.list` and `companies.list` provide bounded record lookup, `leads.search` and `lead.get` expose campaign memberships, and `inbox.list` and `inbox.thread` expose persisted conversation references. The implemented MCP catalog has no contact merge, delete, or generic update tool, so return a review plan rather than inventing an execution step. `contact.unsubscribe` is an account-wide suppression action, not a duplicate-resolution operation.

If the user separately requests any available consequential MCP action, it requires human confirmation followed by an exact replay of the same tool and arguments with the approval token; changed arguments require a new confirmation. This review never supplies that authorization.

## Deliverable

Return:

1. Scope, assumptions, normalization notes, and material data gaps.
2. Candidate groups containing group ID, record IDs, entity type, confidence, proposed disposition, supporting evidence with source, conflicts, and verification needs.
3. For each merge-review candidate, a field survivorship table with proposed value, source record, rationale, and protected-history treatment.
4. A separate no-merge/hold list with explicit reasons.
5. A concise review queue ordered by confidence and risk, plus a statement that no CRM mutation occurred.

## Synthetic example

Account records `A-17` (“Northstar Labs LLC”) and `A-44` (“Northstar Laboratories”) share a verified domain and the same registration ID; their phones differ. Mark them `likely duplicate`, retain the registration ID as protected, prefer neither phone automatically, and request phone verification. Contact records `C-8` (“Jordan Lee”) and `C-29` (“J. Lin”) only share `sales@northstar.example`. Mark them `insufficient evidence — no merge`: the role mailbox is a route, not proof of personal identity.
