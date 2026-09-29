---
name: tc
description: Research professors and draft evidence-grounded academic outreach letters for applicants to graduate study, research, internships, visiting positions, or postdoctoral roles. Preserve the fixed letter framework and adapt only applicant- and professor-specific facts.
---

# TC Professor Outreach

Research the target professor, then draft the email by filling the fixed framework in `references/fixed_outreach_template.md`. The framework is the default for every applicant. Do not replace it with a free-form or one-screen email unless the user explicitly requests another format.

## Privacy and factuality

- Use applicant facts only from the current conversation or user-provided files. Never search for the applicant or include applicant details in web queries.
- Do not store applicant data in this skill. Save a profile only when requested, under an ignored local path.
- Preserve exact roles, dates, outcomes, metrics, and publication/project states. Never upgrade submitted work to under review, accepted, or published.
- Mention only confirmed attachments and contact details. Do not infer eligibility, recruiting, quota, funding, or availability.
- Keep research citations and internal fit labels outside the email body.

## Build the runtime profile

Read `references/applicant_profile.md` when facts are incomplete, spread across files, or reused across targets. Extract the applicant's identity/status, target role and cycle, verified study/work facts, three strongest research or project items when available, practical experience, research interests, constraints, confirmed attachments, and signature preferences.

Ask for missing facts that would otherwise leave a required framework slot empty or force an unsupported claim. Do not fill gaps with placeholders, generic achievements, or invented statements. If a section is genuinely inapplicable, confirm that with the user and retain the fixed position with concise, factual wording; do not omit it unless the user explicitly changes the framework.

## Research the professor

Use current public sources for professor-specific and time-sensitive claims.

1. Resolve identity using name plus institution, department, lab, homepage, or publication topics.
2. Prefer official university and lab pages for title, affiliation, contact, research direction, and explicit recruiting information.
3. Prefer publisher, DOI, proceedings, arXiv, project, or official code pages for research claims. Read an abstract or paper before describing a mechanism.
4. Select exactly one professor-side paper or active project as the hook.
5. Distinguish explicit recruiting evidence from inference. If none is public, say so in research notes and ask about plans without claiming an opening.

Keep evidence links and notes outside the email body.

## Map fit without changing the framework

Read `references/adaptation_contract.md` for letters to multiple professors. Select one primary and, where useful, one complementary applicant proof point for the professor-specific fit paragraph. Use the fixed research-experience section to present the applicant's confirmed items in the prescribed order.

Classify fit internally as `direct`, `adjacent`, or `exploratory`. For adjacent or exploratory fit, state the difference in research setting, name the transferable capability, and connect it to a concrete target-side question. Never alter the letter structure to hide a weak fit.

## Draft with the fixed framework

Read `references/fixed_outreach_template.md` before drafting. Treat its ordered blocks, paragraph roles, hook sentence count, required headings, and closing sequence as invariants:

- Keep every block in order. Do not merge, reorder, or remove a block to shorten the letter.
- Preserve each paragraph's sentence function and fixed opening where specified. Replace only the bracketed meaning slots with verified, target-specific facts.
- Use exactly one professor hook and exactly four sentences in the professor-hook paragraph.
- Include the confirmed applicant proof points and exact status labels in their designated paragraphs.
- Keep subject options and research notes outside the email body. The body starts at the salutation and contains no URLs, citations, analysis, or placeholders.
- Do not impose a one-screen or character limit. Complete the framework first; shorten wording inside its slots only when meaning and factual coverage remain intact.
- Follow a user-requested alternative format only when the user explicitly asks to change the fixed framework.

Use the requested language. For English or another language, preserve the same block order and sentence functions in natural language rather than translating Chinese wording literally.

## Deliver

Unless the user asks for only the email, return:

1. a compact identity and recruiting note with source links;
2. the selected hook and evidence level;
3. the fit label and selected applicant proof points;
4. two or three subject options;
5. the complete fixed-framework email body.

Before delivery, check every body block against the ordered role list in the reference; revise any draft that merged, omitted, or reordered a block. For a structured JSON artifact, set `metadata.template_format` to `fixed-long` and assign the framework `role` to each paragraph before running `scripts/validate_outreach.py`. Keep the private applicant profile outside the public skill directory.

Before publishing or sharing this skill directory, run:

```bash
python -B scripts/audit_privacy.py .
```

Do not publish while the audit reports findings.
