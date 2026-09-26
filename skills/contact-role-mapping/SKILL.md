---
name: contact-role-mapping
description: Identify and prioritize relevant people at target business accounts from supplied or publicly accessible evidence, documenting role fit, current-employment confidence, identity ambiguity, and verification gaps. Use for research and contact planning, not for finding private contact details, outreach, or paid enrichment.
compatibility: "Designed for Claude and ChatGPT."
---

# Contact Role Mapping

Create a defensible shortlist of people whose current responsibilities plausibly connect them to the user's stated business problem. Treat a contact as a person-to-role-to-account claim that needs evidence, rather than as a name attached to a senior title.

## Inputs

Use what the user provides and ask only when a missing item prevents sound prioritization:

- target accounts or a rule for selecting them;
- offering, problem, or decision the contacts should be relevant to;
- preferred geographies, business units, functions, or seniority, if any;
- available sources and the research cutoff date;
- exclusions, such as existing relationships, competitors, or roles that must not be included.

If the buying context is vague, state a narrow working assumption and keep role recommendations provisional. Do not assume access to a platform, subscription, login, or paid data. Work from supplied material or sources the current environment can lawfully access.

## Map roles before people

Translate the business problem into a small role map for each account. Separate roles where the evidence supports the distinction:

- **likely owner:** accountable for the affected function or outcome;
- **practitioner or evaluator:** understands the workflow and may assess a solution;
- **approver or sponsor:** may control budget, policy, or executive priority;
- **influencer or blocker:** shapes security, procurement, legal, technical, or adoption requirements.

Prioritize functional relevance, scope, and account fit. Seniority alone does not establish relevance. Explain why each role matters in terms of the stated problem, and label a role hypothesis when account-specific responsibility is not confirmed.

## Establish identity and current employment

For every named person, record dated evidence that connects the same person to the target account and role. Prefer direct, recent sources such as an employer leadership page, an official biography, a recent company announcement, or the person's current professional profile. Useful secondary evidence can include reputable event biographies and trade coverage. Search snippets, undated directories, scraped profiles, and old biographies are leads rather than confirmation.

Compare source publication or update dates with the research cutoff. A current-looking title on one page can still be stale. When sources conflict, preserve both claims, name their dates, and lower confidence; do not silently choose the more convenient version. Distinguish:

- **confirmed:** recent, credible evidence directly supports identity, company, and role;
- **probable:** evidence is credible but indirect, old, or missing one element;
- **unverified:** only weak, undated, or conflicting evidence is available.

Guard against namesakes. Use only professional discriminators such as function, employer history, location when explicitly published for work, or linked company pages. Do not infer age, gender, ethnicity, health, family status, personality, or other personal traits. Do not invent or pattern-guess email addresses, phone numbers, social handles, or contactability.

## Rank and document the shortlist

Rank people within each account using evidenced role relevance first, then current-employment confidence, then useful coverage across distinct buying roles. Avoid padding the list with weak matches. If no person clears a reasonable evidence threshold, return the target role as an open seat and specify what must be verified.

## RevSwing workflow

When RevSwing is in scope, use the **People Database** (`/people/database`) to search by explicit role, seniority, location, and company criteria. Keep discovery results as candidates until current employment and account relevance are verified. Use **People** (`/people`) for existing workspace contacts and their campaign membership and recent activity, and **Companies** (`/companies`) for the linked account record. The People Database can add selected candidates to contacts or a campaign and can request enrichment, but research and ranking alone do not authorize any of those actions.

In a connected RevSwing MCP client, `contacts.list` supports bounded lookup of existing contacts, `companies.list` supports name or domain lookup, and `lists.list` shows existing contact lists and membership counts. These tools do not replace People Database discovery or public-source verification. Do not claim that RevSwing MCP found a new person when the person came from another source.

For an explicitly requested follow-on, `contact.create`, `list.add_contact`, and `campaign.enroll` change workspace state, while `contact.enrich` spends credits. Each requires human confirmation and an exact replay of the same tool and arguments with the approval token; changed arguments require a new confirmation. `campaign.launch` is a separate send action and must never be inferred from permission to research, save, enrich, or enroll contacts.

For each shortlisted contact, provide:

| Field | Content |
|---|---|
| Account and person | Published professional identity, or “open seat” if no identity is supportable |
| Current title and role type | Observed title plus owner, evaluator, approver, or influencer hypothesis |
| Relevance | Short account-specific rationale tied to the stated problem |
| Evidence | Source title or publisher, direct link or supplied reference, publication/update date, and access date |
| Confidence | Confirmed, probable, or unverified, with the reason |
| Identity uncertainty | Namesake risk, title conflict, business-unit ambiguity, or “none observed” |
| Missing verification | The exact evidence needed before the contact is treated as current and relevant |

End with coverage gaps by account and a compact verification queue ordered by which checks could change prioritization most. Keep the deliverable as research. Do not imply that creating it authorizes outreach, CRM updates, data purchases, or enrichment.

## Synthetic example

**Fictional scenario:** Northstar Robotics wants contacts at fictional Arbor Freight for warehouse-safety software. An Arbor Freight announcement dated 2026-02-14 names Priya N. as “VP, Distribution Operations,” while a 2023 conference page calls her a regional director.

Shortlist Priya as a likely operational owner because the recent employer source connects her to distribution operations. Mark current employment **probable** if the announcement describes a project but does not explicitly say she still holds the role at the research cutoff. Cite both dated sources, note the title change as resolved in favor of the newer official evidence but not independently confirmed, and request a current leadership page or current professional profile. Do not create an email address or claim she owns safety procurement without evidence.
