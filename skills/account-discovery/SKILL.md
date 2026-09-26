---
name: account-discovery
description: Turn a B2B segment brief into reproducible, tool-neutral account searches and an evidence-qualified shortlist, including domain normalization, subsidiary handling, exclusions, and coverage gaps.
compatibility: "Designed for Claude and ChatGPT."
---

# Account Discovery

Convert a segment definition into searches another person can rerun, then qualify only accounts supported by evidence. Use it for target organizations, not individual contacts, personal-data enrichment, or outreach.

## Required inputs

Collect the geography, organization type or industry, size measure and range, required or disqualifying attributes, time sensitivity, target count, available sources, and desired account unit: parent groups, operating subsidiaries, or both. Ask when a missing choice would materially change the universe, such as headquarters location versus operating presence. Otherwise use a marked assumption.

Treat the brief as a set of testable predicates. Separate:

- **Hard filters:** required for inclusion.
- **Exclusions:** sufficient to remove a candidate.
- **Preferences:** useful for ranking but not eligibility.
- **Unresolved terms:** labels such as “mid-market,” “technology company,” or “European” that need an operational definition.

Preserve the original brief alongside the operational definitions so the translation remains reviewable.

## Build tool-neutral search recipes

Inventory what each available source can query and what evidence it returns. Translate every predicate into the closest supported operation instead of assuming access to a particular commercial database. A useful recipe records:

| Brief predicate | Operational definition | Source and query/filter | Evidence returned | Limitation |
|---|---|---|---|---|
| Employee range | Latest credible company-wide count | Directory size filter, or web query plus company/about profile | Stated range and date | Bands may cross thresholds |

When a source lacks a direct filter, retrieve a broader set, then verify the missing predicate elsewhere. Keep exact queries, filter values, run date, result or pagination boundary, and deduplication rule. Never represent an unsupported filter as applied. Mark inaccessible sources and unavailable evidence rather than guessing.

## Resolve account identity

Use the registrable corporate domain as the primary account key when one is evidenced. Normalize scheme, `www`, path, query, fragment, case, and trailing dot. Preserve the observed domain and the normalization decision. Do not collapse distinct country or product domains merely because their names are similar.

Separate these relationships:

- **Same account:** aliases or redirects demonstrably resolve to one organization.
- **Subsidiary or brand:** separately operated entity or brand linked to a parent by evidence.
- **Parent group:** controlling organization supported by an ownership source.
- **Unresolved relationship:** plausible connection without adequate evidence.

Apply the user's unit of account. If both a subsidiary and parent qualify, retain the requested unit and cross-reference the other; do not silently deduplicate them. Record changes such as acquisitions or rebrands with effective dates when available.

## Qualify candidates

For every hard filter, attach a source, relevant fact, and observed or published date. Prefer organizational sources and authoritative registries for identity and ownership; use reputable secondary sources when primary evidence does not answer the predicate. Keep URLs or stable identifiers and short paraphrases.

Assign one status:

- **Qualified:** every hard filter has sufficient, non-conflicting evidence and no exclusion applies.
- **Review:** evidence is missing, stale, ambiguous, or materially conflicting.
- **Excluded:** a stated exclusion applies or a hard filter is disproved.

Conflicts stay visible. Explain which sources disagree, whether they measure different entities or dates, and what would resolve the conflict. Do not average incompatible figures. Never invent a company to fill a quota, and do not promote a preference into a hard rule.

## RevSwing workflow

When RevSwing is available, use **Companies → Discover companies** at `/companies` for company-first search. It supports explicit company filters, saved searches, selectable result columns, company profile review, page export, and adding selected companies to a company list. Use `/people/database` only after the account universe is defined when the task expands to finding people; its controls can exclude saved contacts and people already in campaigns.

RevSwing MCP has no tool for the external discovery search. `companies.list` is a read-only, bounded lookup of companies already saved in the workspace, with optional `q` and `limit`; use it to check existing records or identity collisions, not to claim market coverage. `contacts.list` and `lists.list` likewise read saved contacts and contact lists, and `lists.list` does not return company lists. Keep UI discovery filters and result boundaries in the search recipe so another operator can rerun them.

If later execution calls a RevSwing MCP tool classified as `write`, `send`, or `spend`, the first call must return a confirmation request. Show its impact and visible cost, obtain signed-in workspace approval, then replay the same tool with exactly the same arguments, the one-time confirmation token, and a fresh idempotency key. Changed arguments require a new confirmation.

## Deliverable

Return four sections:

1. **Search recipes:** predicate translation, exact searches or filters, source sequence, run date, and retrieval limits.
2. **Candidate accounts:** canonical name, normalized and observed domains, parent/subsidiary relationship, status, filter-by-filter evidence, confidence rationale, and next verification step where needed.
3. **Exclusions:** considered account, reason, decisive evidence, and date.
4. **Coverage gaps:** unsupported predicates, inaccessible or biased sources, result caps, stale evidence, geographic or language blind spots, and the likely effect on recall.

State counts at each stage so attrition is auditable. CRM changes, data purchases, and outreach require separate authorization.

## Synthetic worked example

**Synthetic data:** A brief asks for 50–200 employee cybersecurity vendors headquartered in Benelux, excluding consultancies, with healthcare experience preferred. Available sources are a general company directory and public websites.

Translate “Benelux” to headquarters in Belgium, Netherlands, or Luxembourg; treat employee count, headquarters, vendor status, and non-consultancy status as hard predicates, and healthcare experience as a ranking preference. Run the directory by geography, size band, and broad security category, recording the filters and export cap. Verify product versus consultancy status on each official site and record dated employee evidence. `shield-labs.example` is kept as a synthetic qualified candidate only if every hard predicate is evidenced. Its healthcare case study can raise rank but cannot rescue a failed hard filter. If `shield-benelux.example` is owned by `shield-group.example`, keep or collapse it according to the requested account unit and cite the ownership evidence. List candidates with ambiguous service mix under Review, and report that the directory's category taxonomy may miss security vendors filed under software.
