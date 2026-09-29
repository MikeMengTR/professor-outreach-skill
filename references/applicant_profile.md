# Runtime Applicant Profile

Build this profile only from information supplied for the current task. Do not include a prefilled applicant profile in the public skill.

## Intake behavior

If the user supplies a CV, draft, or profile, extract all relevant framework fields first. Ask only about missing or ambiguous facts that would otherwise leave a fixed section unsupported or empty.

If no background is supplied, request this bundle in one compact prompt:

- preferred name and current education/work status and affiliation;
- target role and cycle;
- up to three research or project experiences, with exact role, contribution, outcome, and status;
- practical, internship, or work experience, or confirmation that there is none to include;
- available academic/work record, relevant courses or capabilities, language evidence, honors, and competition/qualification facts;
- research interests and target constraints;
- confirmed attachments, desired language, and signature preferences.

Do not require GPA, rank, phone, social contact, demographic data, or a full CV. These facts are optional. Keep the five basic-information lines in the fixed template. If a category is private, absent, or inapplicable, ask whether the user confirms there is nothing to include or prefers a factual non-disclosure wording on that line. Ask whether there is practical experience to include; when the user confirms there is none, keep the practical-experience paragraph and say so briefly. Do not invent a value or print a placeholder.

## Normalized fields

Use this structure internally. Save it only when the user requests a reusable profile.

```json
{
  "name": "[required for a send-ready email]",
  "preferred_name": "[optional]",
  "affiliation": "[current institution, department, lab, or employer]",
  "current_status": "[degree, year, position, or career stage]",
  "target": {
    "cycle": "[year, term, or flexible]",
    "role": "[PhD, direct-PhD, master's, RA, internship, visiting, postdoc, or other]",
    "language": "[Chinese or English]"
  },
  "research_interests": ["[interest]"],
  "basic_information": {
    "academic_or_work_record": "[verified facts or user-approved omission]",
    "courses_or_professional_capabilities": "[verified facts or user-approved omission]",
    "language": "[verified facts or user-approved omission]",
    "honors": "[verified facts or user-approved omission]",
    "competitions_or_qualifications": "[verified facts or user-approved omission]"
  },
  "proof_points": [
    {
      "id": "proof-1",
      "topic": "[work or achievement]",
      "role": "[applicant's actual role]",
      "methods": ["[verified method or capability]"],
      "outcome": "[verified result]",
      "status": "[exact state: in preparation, submitted, under review, accepted, published, completed, or other]",
      "source": "[chat, CV section, supplied document, or URL]"
    }
  ],
  "practical_experience": ["[verified internship, work, or practical experience]"],
  "attachments_confirmed": ["[exact filename or attachment type]"],
  "contact": {
    "email": "[optional]",
    "phone_or_social": "[optional]"
  },
  "constraints": ["[facts, wording, or disclosures that must not change]"]
}
```

Bracketed values document the schema only. Never pass them to an email.

## Fact control

For each claim, retain its source and exact status:

1. A current explicit user correction overrides an older supplied file.
2. A source document overrides an assistant inference.
3. Submitted, under review, accepted, and published are distinct states.
4. Participation, leadership, and first-author status are distinct roles.
5. If sources conflict, surface the conflict and ask which is current.
6. Do not derive rank, GPA conversions, authorship, venue status, dates, awards, or attachment presence.
7. Keep research/project entries in the user's supplied order unless the user asks to reorder them.

## Reuse and storage

Keep the normalized profile in working context when generating multiple letters. Do not copy professor-specific facts into the applicant profile.

Save a profile only when requested, under `profiles/` using a filename ending in `.local.json`; that path is ignored by the bundled `.gitignore`. Treat ignored files as sensitive and never add them to a public commit.
