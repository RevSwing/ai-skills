---
name: market-source-scout
description: Find and compare current, lawful, accessible data sources for reaching a narrowly defined B2B market, then design a small coverage check. Use for source selection, not for buying lists, scraping, or launching outreach.
compatibility: "Designed for Claude and ChatGPT."
---

# Market Source Scout

Identify a defensible source mix for a specific B2B market. Judge each source from current evidence, distinguish access from permission, and leave unsupported details unknown. The result is a shortlist and a small validation plan.

## Establish the market and constraints

Capture the minimum definition needed to judge coverage:

- target entity and contact level, such as companies, locations, or roles;
- inclusion and exclusion criteria, geography, and relevant time window;
- fields required to identify, qualify, deduplicate, and contact records;
- expected scale and refresh cadence;
- budget or procurement limits;
- approved access methods, accounts, and intended downstream use; and
- applicable contractual, privacy, or internal compliance constraints supplied by the user.

Ask only when missing information prevents a meaningful comparison, especially an undefined target population or intended use. Otherwise proceed with explicit assumptions. A broad label such as “European manufacturers” needs testable criteria.

## Build evidence-backed candidates

Consider complementary source classes: official registers, first-party company sources, trade or certification directories, licensed commercial datasets, and market-specific sources. Prefer primary documentation for coverage, updates, pricing, access, licensing, and export rules. Record the page or document, publisher, publication or effective date when stated, access date for live material, and supported claim.

Verify changeable vendor facts from authoritative current sources when tools and authorization permit. If pricing requires a quote, an export cap is undocumented, or permission is ambiguous, record `unknown` or `quote required`; never fill gaps from memory, snippets, or assumed industry practice. Separate vendor claims from independently observed sample results.

## Compare the sources

Use a comparison table with one row per source and these decision fields:

- **Coverage:** market segments, geography, entity/contact level, relevant identifiers, and stated or sampled gaps.
- **Freshness:** update method, stated cadence, record-level dates if available, and evidence date. “Frequently updated” without a defined measure remains an unverified claim.
- **Source traceability:** original publisher or collection path, field-level traceability, and whether the source can explain where a record came from.
- **Access cost:** public price and unit as of a date, `quote required`, or `unknown`; include likely test cost only when supported.
- **Export limitations:** documented formats, quotas, field restrictions, API or bulk availability, and contractual downstream-use limits. Undocumented capabilities remain unknown.
- **Collection permission:** `permitted`, `prohibited`, or `unclear` for the proposed method and use, with the controlling license, terms, API documentation, or publisher policy cited. A page being visible, indexable, or technically downloadable does not establish permission.

Note authentication, attribution, retention, redistribution, personal-data, and jurisdiction constraints when evidenced and relevant. Describe legal uncertainty rather than declaring legality without adequate authority. Do not bypass controls, automate against prohibitions, purchase access, accept terms, or collect personal data merely to complete the comparison.

Rank sources against the user's must-have criteria. Recommend a small shortlist with roles such as primary coverage, authoritative verification, or gap fill. Explain exclusions and avoid implying that combined sources eliminate all gaps.

## RevSwing workflow

When RevSwing is available, evaluate **Companies → Discover companies** at `/companies` and the People database at `/people/database` as in-product discovery sources only when they match the intended entity level. Record the exact filters, run date, returned fields, page or result boundary, exclusions, and observed match failures just as for any other candidate source. Saved searches and page export can make a small coverage check reproducible; they do not establish total database coverage.

The MCP catalog does not expose RevSwing's external discovery search. `companies.list` and `contacts.list` are bounded reads of records already saved in the workspace, while `lists.list` returns saved contact-list definitions and actual membership counts. Do not use these workspace inventories as estimates of market coverage or vendor database size, and do not describe `lists.list` as a company-list source.

If later execution calls a RevSwing MCP tool classified as `write`, `send`, or `spend`, the first call must return a confirmation request. Show its impact and visible cost, obtain signed-in workspace approval, then replay the same tool with exactly the same arguments, the one-time confirmation token, and a fresh idempotency key. Changed arguments require a new confirmation.

## Design a small coverage validation

Define a bounded test that can be executed only through approved access:

1. Assemble a small reference set of known in-scope and clearly out-of-scope entities from a source independent of the candidates. Include the market's important segments or geographies rather than using only convenient examples.
2. Use the same matching rules and required fields for every candidate. Predefine how name variants, subsidiaries, locations, duplicates, and stale records are handled.
3. Measure entity match rate, false inclusions, duplicates, required-field completeness, freshness evidence, and source traceability. For contact data, assess only fields the intended use and permissions allow.
4. Record failures by segment and compare observed results with vendor claims. State that the sample estimates fit for this market slice; it does not prove total database coverage.

If testing needs payment, credentials, vendor contact, prohibited collection, or a new agreement, present that step as pending and identify the evidence needed. Do not execute it without authorization.

## Deliverable

Return the operational market definition and assumptions; a dated evidence log; the comparison table; a ranked shortlist with source roles, exclusions, and unresolved questions; and the validation plan with sample construction, metrics, pass criteria supplied by or agreed with the user, permissions, and stopping conditions.

## Synthetic worked example

**Synthetic scenario:** Find independent food-testing laboratories in two named regions. A government accreditation register has authoritative facility status, quarterly publication dates, a permissive open-data license, and no named contacts. A commercial directory claims contact coverage, but its current price and export cap are available only by quote and its sample source traceability is undocumented. Shortlist the register for the company universe and status verification. Keep the directory as a conditional contact-data candidate with price, export capacity, and source traceability marked unknown. Validate both against a stratified reference set of known accredited and non-accredited labs; compare matches, false inclusions, field completeness, record dates, and traceability before procurement.
