---
name: tc
description: Research, draft, revise, and quality-check concise, evidence-grounded professor outreach emails for any applicant. Use for 套磁信、导师联系邮件、保研/直博/硕士/博士/RA/实习/访问学生/博士后申请邮件, short Chinese or English academic cold emails, adapting one applicant profile to different professors, or revising an existing outreach draft. Build each letter only from user-supplied applicant facts and current professor evidence; never rely on a bundled personal preset.
---

# TC Professor Outreach

Create a concise professor outreach email from a runtime applicant profile and verified target evidence. Keep the public skill free of real applicant data.

## Protect applicant privacy

1. Treat applicant files, contact details, identifiers, academic records, and unpublished work as private runtime inputs.
2. Never search the web for the applicant or place applicant details in search queries unless the user explicitly asks.
3. Do not save applicant data inside this skill. Work from the current conversation or a user-provided file. Create a local profile or output file only when requested, and place it under an ignored path such as `profiles/` or `outputs/`.
4. Include only information needed for the email. Omit identity numbers, home addresses, birth dates, private account credentials, and unrelated personal details. Phone or social contact is optional.
5. Do not repeat contact details in research notes. Put confirmed contact details only in the requested email signature or artifact.
6. Never infer, complete, or "improve" a missing applicant fact. Mark it missing and ask only when it blocks an accurate draft.

## Build the runtime applicant profile

Read `references/applicant_profile.md` whenever applicant facts are incomplete, spread across files, or intended for reuse across professors.

Accept facts from chat, a CV, a draft, or another user-provided document. Normalize them into a temporary profile with:

- identity and current academic/professional status;
- target opportunity, intake/cycle, and output language;
- two to four verified proof points with the applicant's role, methods, outcome, and exact status;
- research interests and constraints;
- confirmed attachments and optional contact fields.

Use this source priority: explicit current instruction, supplied source document, earlier statement in the same task, then missing. When sources conflict, surface the conflict instead of choosing silently.

Ask a compact follow-up only if a missing value risks identifying the wrong professor, fabricating applicant evidence, misstating the target, or claiming an attachment that is not confirmed. Otherwise draft with the strongest verified subset.

## Research the professor

Use current public sources for professor-specific and time-sensitive claims.

1. Resolve identity using name plus institution, department, lab, homepage, or publication topics.
2. Prefer official university and lab pages for title, affiliation, contact, directions, and explicit recruiting information.
3. Prefer publisher pages, DOI records, arXiv, or project pages for papers. Read at least the abstract before describing a mechanism.
4. Search recent work first, then select exactly one hook paper or one active research direction.
5. Separate explicit recruiting evidence from inference. Never infer openings, quotas, funding, or eligibility from publication activity.

Keep source links and evidence notes outside the email body.

## Map evidence to the target

Read `references/adaptation_contract.md` before producing multiple letters or adapting an earlier letter to a new professor.

Select:

- one primary applicant proof point closest to the target;
- at most one secondary proof point that adds a distinct capability;
- one honest fit bridge labeled internally as `direct`, `adjacent`, or `exploratory`.

For adjacent or exploratory fit, state the difference in research setting, identify the transferable method or capability, and connect it to a concrete target-side question. Do not manufacture overlap or use claims such as "highly aligned" without evidence.

## Draft the email

Read `references/short_email_pattern.md` before drafting or revising.

Default to a one-screen email with:

- one verified professor hook;
- no more than two applicant proof points;
- one evidence-based fit bridge;
- only confirmed attachments;
- one low-friction ask.

For Chinese, normally target 350-650 Chinese characters excluding the signature. For English, normally target 180-300 words excluding the signature. Follow an explicit user length or tone request over these defaults.

Preserve exact publication and project states such as in preparation, submitted, under review, accepted, or published. Keep detailed biography, course lists, awards, and methods in the CV unless directly relevant.

## Deliver

Return, unless the user requests only the email:

1. a compact identity and recruiting note with source links;
2. the selected hook, evidence level, and fit label;
3. two or three subject options;
4. the final email body.

Use the requested language. Do not place citations, source markers, analysis, or placeholders inside the email body.

Create a DOCX only when requested or when revising an existing Word artifact. For DOCX, use restrained A4 business-email formatting and render every page for visual QA before delivery.

## Validate

Before delivery, check names, target cycle, role, paper title, applicant claims, status labels, attachments, contact details, and current date against their sources.

For a structured JSON or DOCX artifact, run:

```bash
python -B scripts/validate_outreach.py <artifact> --profile <profile.local.json>
```

The profile is optional when the user did not request a saved profile. Run `python -B scripts/validate_outreach.py --help` for the generic JSON contract.

Before publishing or sharing this skill directory, run:

```bash
python -B scripts/audit_privacy.py .
```

Add known private terms with repeated `--deny-term` arguments when auditing a previously personalized copy. Do not publish while the audit reports findings.
