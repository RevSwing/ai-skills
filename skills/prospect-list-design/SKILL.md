---
name: prospect-list-design
description: Design a reviewable B2B prospect-list specification or clean supplied prospect records for import, including eligibility, normalization, deduplication, source traceability, suppression, and exception handling.
compatibility: "Designed for Claude and ChatGPT."
---

# Prospect List Design

Turn supplied requirements or records into an auditable prospect-list package. Work only with the material the user provides or sources they explicitly authorize. Producing a specification or file does not authorize enrichment purchases, outreach, or changes to a CRM or suppression system.

## Establish the list contract

Before classifying records, translate the request into a short contract:

- Define the unit of analysis: account, contact, or an account-contact pair. State whether subsidiaries, branches, franchises, and multiple contacts per account count separately.
- Separate **required eligibility** from preferences used for ranking. Express every required rule as a test with `pass`, `fail`, or `unknown`, including geography, company type, segment, role, seniority, and any date boundary.
- Define the minimum accepted record. Typical account fields are name and a stable account key such as normalized domain; typical contact fields are full name, account link, and one permitted contact route. Adapt these to the user's import target.
- Identify suppression rules, including opt-outs, do-not-contact flags, bounced or invalid addresses, excluded accounts, and any jurisdiction or consent restriction supplied by the user. A known suppression signal is never erased by a cleaner source.
- Record an `as_of` date and the destination's field names, formats, allowed values, and required identifiers. If destination requirements are unavailable, produce a proposed schema and mark it for confirmation.

Ask only when an ambiguity would materially change inclusion or merging. Otherwise proceed with a plainly labeled assumption.

## Preserve evidence while normalizing

Retain each original record or a source-record identifier. Never overwrite raw values. For every normalized or chosen value, retain its source, observed date when available, and transformation or selection note.

Normalize whitespace, casing where case is not meaningful, phone numbers to a declared convention when the country is known, and domains to lowercase hostnames without protocol, path, query, or a leading `www.`. Preserve the original email; normalize a comparison copy conservatively. Do not infer an email, country, employer, legal entity, or consent status from a pattern alone.

When sources disagree, choose a value only if the contract provides a priority rule or one source is demonstrably more authoritative and current. Otherwise keep the conflict and route the record to review. Distinguish supplied facts, deterministic transformations, and inferences.

## Resolve entities conservatively

Deduplicate accounts before contacts. Auto-merge accounts only when a strong shared identifier establishes the same entity at the list contract's unit of analysis, such as the same source-system account ID or a verified canonical domain exclusive to that entity. A shared domain can serve distinct subsidiaries, franchises, or tenants; it does not establish identity by itself. A similar name, shared parent, redirect, generic email domain, or matching address is supporting evidence, not sufficient by itself. Keep aliases and all contributing source IDs after a merge.

Within a resolved account, auto-merge contacts only when a stable person-specific contact ID establishes identity, or an exact normalized personal mailbox has corroborating identity evidence and no conflicts. A role mailbox, shared inbox, or reassigned address identifies a contact route rather than necessarily one person. Matching names, titles, phone fragments, or social profiles should create a possible-duplicate group for review. Do not merge contacts across accounts solely because names match. If merging would discard a suppression flag, conflicting employer, or distinct contact route, retain the records and escalate.

## Classify and deliver

Evaluate required rules after normalization and entity resolution:

- **Accepted:** all required tests pass, minimum fields are present, and no applicable suppression exists.
- **Rejected:** at least one required test fails or an applicable suppression is confirmed. Keep the record with a specific reason; never drop it silently.
- **Review needed:** a required test is unknown, evidence conflicts, identity is ambiguous, or the proposed import cannot safely represent the record.

## RevSwing workflow

When RevSwing is available, use `/people` to review saved contacts by email status, source, contactable or suppressed state, and contact-list membership; it also supports CSV import, export, enrichment, and adding selected contacts to a static list. Use `/companies` for saved-company identity, company lists, linked people, and email coverage. Use `/people/database` for company-first discovery or a reviewed company CSV import. Keep contact lists and company lists distinct.

For a read-only MCP inventory, use `contacts.list`, `companies.list`, and `lists.list`; each is bounded, and `lists.list` returns contact lists only. Consequential options are `contact.create`, duplicate-safe `list.add_contact` for one existing contact and contact list, `contact.enrich` for selected `email`, `phone`, `linkedin`, or `company` fields, and `contact.unsubscribe` to apply account-wide email suppression and stop current campaign memberships. Do not call any of them merely because the list specification is complete.

Every RevSwing MCP tool classified as `write`, `send`, or `spend` requires confirmation. The first call returns the impact and, for `contact.enrich`, the visible maximum credit cost. Obtain signed-in workspace approval, then replay the same tool with exactly the same arguments, the one-time confirmation token, and a fresh idempotency key. Changed arguments require a new confirmation. Preserve the returned tool receipt in the list audit package.

Return a reviewable package containing:

1. The list contract and marked assumptions.
2. Accepted, rejected, and review-needed records with stable row IDs, reason codes, and human-readable notes.
3. A duplicate-resolution log showing source IDs, chosen survivor IDs, evidence, and whether the decision was automatic or pending.
4. Coverage notes: counts by outcome, missing-field rates, unresolved conflicts, source/date coverage, and any segment that may be systematically absent. Do not claim the supplied data represents the full market.
5. An import-ready schema with field name, type/format, required status, allowed values, source mapping, and example. Include source traceability and suppression fields when the destination supports them; otherwise provide a companion audit file. Do not perform the import unless separately authorized.

## Synthetic example

Two supplied rows list `Northstar Labs` at `https://www.northstar.example/about` and `Northstar` at `northstar.example`. Their canonical domains match, so they may be one account; both source IDs and names remain in the merge log. A contact appears once as `A. Chen` and once as `Alex Chen`, with different emails. Name similarity does not justify merging, so both enter a possible-duplicate review group. One row carries `do_not_contact=true`; that row is rejected with a suppression reason even if the other source lacks the flag. The package reports one resolved account, the unresolved contact identity, and the exact fields required before import.
