---
name: tc
description: Research professors and draft concise, evidence-grounded academic outreach emails for graduate study, research, internships, visiting positions, and postdoctoral roles. Use for 套磁信、导师联系邮件、保研/直博/硕博/RA/实习/访问学生/博士后邮件. Default to a concise Chinese or English email; use the long fixed framework only when explicitly requested.
---

# TC Professor Outreach

Create a concise professor outreach email from user-provided applicant facts and current target evidence. Keep real applicant details out of the public skill files.

## Privacy and factuality

- Use applicant facts only from the current conversation or user-provided files. Never search for the applicant or include applicant details in web queries.
- Do not store applicant data in this skill. Save a profile only when requested, under an ignored local path.
- Preserve exact roles, dates, outcomes, metrics, and publication/project states. Never upgrade submitted work to under review, accepted, or published.
- Mention only confirmed attachments and contact details. Do not infer eligibility, recruiting, quota, funding, or availability.
- Keep research citations and internal fit labels outside the email body.

## Build the runtime profile

Read `references/applicant_profile.md` when facts are incomplete, spread across files, or reused across targets. Extract identity/status, target role and cycle, two to four verified proof points, research interests, constraints, confirmed attachments, and signature preferences.

Ask only about missing facts that could make the email inaccurate or materially change its purpose. Do not require a full CV, GPA, rank, awards, internships, phone, or a long project list. Never invent missing information.

## Research the professor

Use current public sources for professor-specific and time-sensitive claims.

1. Resolve identity using name plus institution, department, lab, homepage, or publication topics.
2. Prefer official university and lab pages for title, affiliation, contact, research direction, and explicit recruiting information.
3. Prefer publisher, DOI, proceedings, arXiv, project, or official code pages for research claims. Read an abstract or paper before describing a mechanism.
4. Select exactly one professor-side paper or active project as the hook.
5. Distinguish explicit recruiting evidence from inference. If none is public, say so in research notes and ask about plans without claiming an opening.

Keep evidence links and notes outside the email body.

## Map fit

Read `references/adaptation_contract.md` when adapting letters across professors. Select one primary and at most one complementary applicant proof point for the email. Classify fit internally as `direct`, `adjacent`, or `exploratory`.

For adjacent or exploratory fit, state the difference in research setting, identify the transferable capability, and connect it to a concrete target-side question. Do not manufacture overlap or inflate the applicant's experience.

## Draft the email

Read `references/short_email_pattern.md`. The default is a concise, one-screen email with:

- one verified professor hook;
- one or two relevant applicant proof points;
- one honest, evidence-based fit bridge;
- only confirmed attachments;
- one low-friction ask.

For Chinese, normally target 350–650 Chinese characters excluding the signature. For English, normally target 180–300 words excluding the signature. Follow an explicit user length or tone request when supplied.

Use a natural order that serves the case: salutation and purpose, applicant identity and evidence, professor direction and hook, fit bridge, attachment and ask, closing and signature. Do not force unrelated CV sections into the email. Preserve exact publication and project states. Mention detailed courses, awards, methods, internships, or additional projects only when directly relevant.

The long format in `references/fixed_outreach_template.md` is optional. Use it only when the user explicitly asks for a long-form self-recommendation letter, a full CV-style letter, or that fixed framework. If requested, follow it exactly and ask about any missing required fields before drafting.

## Deliver and check

Unless the user asks for only the email, return:

1. a compact identity and recruiting note with source links;
2. the selected hook and evidence level;
3. the fit label and selected applicant proof points;
4. two or three subject options;
5. the concise email body.

Keep citations, source URLs, research notes, fit labels, and placeholders outside the email body. Before delivery, verify names, target cycle, roles, hook title and claims, applicant facts, status labels, attachment, and signature against their sources.

For a structured JSON artifact, use `scripts/validate_outreach.py`; add `metadata.template_format: fixed-long` and paragraph roles only when using the optional long framework. Keep the private applicant profile outside the public skill directory.

Before publishing or sharing this skill directory, run:

```bash
python -B scripts/audit_privacy.py .
```

Do not publish while the audit reports findings.
