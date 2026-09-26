---
name: value-evidence-map
description: Inventory and deduplicate value claims from company materials, connect them to buyer outcomes and traceable evidence, and identify claims usable with explicit caveats.
compatibility: "Designed for Claude and ChatGPT."
---

# Value Evidence Map

Build an auditable map of what a company says its offering does, why a buyer might care, and what evidence supports each claim. Use this for messaging, enablement, positioning, or diligence when the user supplies company materials or a source inventory. The result is an analysis artifact; creating it does not authorize publishing copy, contacting buyers, or changing a source system.

## Inputs

Use the materials provided: product pages, decks, case studies, research, customer quotations, internal notes, or structured exports. For each source, capture a stable locator, title, date if known, source type, and whether it is company-authored, customer-attributed, or independently produced. Preserve exact page, slide, section, timestamp, or record identifiers when available.

Also identify the intended buyer, use case, market, and date sensitivity. If these are missing, proceed with clearly marked assumptions unless their absence prevents a sound interpretation. Treat inaccessible or partial sources as unavailable evidence rather than filling gaps from memory.

## Build the map

1. **Register sources.** Assign each source a short ID. Record source traceability and access limitations. Retain a short excerpt when permitted or an accurate paraphrase when quoting would be inappropriate. Do not promote an unattributed internal assertion into customer or independent proof.
2. **Atomize and classify claims.** Split compound statements into claims that can be evaluated separately. Classify each item as:
   - **Feature:** a capability, property, process, or availability statement.
   - **Outcome:** a change in the buyer's work or business condition.
   - **Proof:** an observation, result, testimonial, benchmark, certification, or other support for a feature or outcome.
   A sentence may contain multiple types; create separate linked records instead of assigning one blended label.
3. **Deduplicate by meaning.** Group variants only when they assert materially the same proposition. Create a neutral canonical claim and retain every wording variant and source ID. Keep claims separate when they differ in buyer, scope, metric, baseline, timeframe, conditions, or certainty. Similar vocabulary alone is not enough to merge them.
4. **Connect value logic.** Where supported, link `feature → mechanism → buyer outcome → proof`. Label links as **stated** when a source makes the connection and **inferred** when the reasoning is plausible but unstated. Write the missing assumption on every inferred link. Never turn correlation, a testimonial, or a single example into a general causal conclusion.
5. **Assess support.** Rate evidence for the precise canonical claim:
   - **Direct:** evidence measures or explicitly verifies that claim for a defined context.
   - **Indirect:** evidence supports a related mechanism, proxy, or narrower case.
   - **Absent:** no supplied evidence supports it.
   - **Conflicting:** supplied sources materially disagree.
   Record population, sample, baseline, timeframe, method, and source independence when known. Describe gaps rather than inventing a score or benchmark.
6. **Screen elevated language.** Flag superlatives, exclusivity, guarantees, and broad comparisons such as “best,” “leading,” “fastest,” “only,” “always,” or “#1.” A defensible comparison needs a named comparator set, measure, scope, time period, and supporting source. Preserve the original wording for traceability, but exclude or narrow unsupported elevated language.
7. **Decide usability.** Mark each canonical claim **usable**, **usable with caveat**, or **hold**. A caveat must state the actual boundary, such as “observed in one customer case over six months,” not merely “results may vary.” Use `hold` for unresolved contradictions, absent support for a material factual assertion, or wording that exceeds the evidence.

## RevSwing workflow

When RevSwing is a source, register each product surface or MCP result separately with its observation date and workspace scope. Campaign detail (`/campaigns/[id]`) can document configured sequence, readiness, lead state, and activity; **Reports** (`/reports`) can document persisted campaign and operational results; **Inbox** (`/inbox`) can document attributed customer statements; and **People** (`/people`) and **Companies** (`/companies`) can define the relevant contact and account context. UI labels and configuration establish features or settings, while realized outcome claims require observed results and the applicable cohort, timeframe, and denominator.

In a connected RevSwing MCP client, `campaign.get`, `campaign.sequence`, and `campaign.validate` supply campaign configuration and readiness evidence; `analytics.campaign` and `analytics.workspace` supply persisted counts; `leads.search` and `lead.get` supply lead-state evidence; and `inbox.list` and `inbox.thread` supply attributed conversation evidence. Keep tool outputs scoped to the returned workspace, campaign, contact, and observation time. A validation result establishes readiness issues, not campaign performance; a count establishes quantity, not causation.

Building the evidence map requires no write, spend, or send. If the user separately requests a consequential MCP action, human confirmation must cover the exact tool and arguments, followed by an exact replay with the approval token; changed arguments require a new confirmation. Do not treat a usable claim as permission to publish it or launch a campaign.

## Deliverable

Return:

- A source register with source ID, locator, date, type, attribution, and limitations.
- An evidence map with claim ID, canonical claim, type, variants, source IDs, target buyer/outcome, mechanism, link basis, evidence rating, evidence details, conflicts or gaps, superlative flag, and usability decision.
- A shortlist containing only usable or caveated claims. For each, provide approved scope, required caveat, strongest source IDs, and contexts where it should not be used.
- A short gap list ordered by which missing evidence most affects usability. Add focused follow-up questions only when an answer would change a decision.

Make source IDs and claim IDs stable within the deliverable. Separate source statements from analyst inference throughout.

## Synthetic example

Fictional sources S1 and S2 say “launch sequences in minutes” and “go live faster”; S3 reports that one five-person team reduced setup from two hours to 25 minutes in a four-week pilot. Map the first two as variants only if both refer to sequence setup. Canonicalize the outcome as “may reduce sequence setup time for small teams,” link it to S1–S3, and rate the evidence direct but narrow. Shortlist it as usable with the caveat “observed in one five-person-team pilot over four weeks.” Hold “the fastest platform” because the materials provide no comparator set or market-wide measurement.
