# Runtime Applicant Profile

Build this profile only from information supplied for the current task. Do not include a prefilled applicant profile in the public skill.

## Intake behavior

If the user supplies a CV, draft, or profile, extract the facts most relevant to the target email. Ask only about missing or conflicting details that could cause an inaccurate claim or change the requested opportunity.

If no background is supplied, request a compact bundle:

- preferred name, current status, and affiliation;
- target role and cycle;
- one to three relevant research/project experiences, including actual role, contribution, outcome, and exact status;
- research interests or constraints;
- confirmed attachments and signature preferences.

Do not require a full CV, GPA, rank, courses, awards, internship, phone, social contact, or demographic data. Include these only if supplied and useful for the target. Do not invent missing values or imply that an unsupplied experience does not exist.

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
7. Keep proof points in the user's supplied order unless the user asks to reorder them.

## Reuse and storage

Keep the normalized profile in working context when generating multiple letters. Do not copy professor-specific facts into the applicant profile.

Save a profile only when requested, under `profiles/` using a filename ending in `.local.json`; that path is ignored by the bundled `.gitignore`. Treat ignored files as sensitive and never add them to a public commit.
