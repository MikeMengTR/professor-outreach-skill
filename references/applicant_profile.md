# Runtime Applicant Profile

Build this profile from information supplied for the current task. The public skill must not contain a prefilled applicant profile.

## Intake behavior

If the user supplies a CV or draft, extract the available fields first and ask only for blocking gaps. If no background is supplied, request the minimum useful bundle in one compact prompt:

- preferred name and current status/affiliation;
- target opportunity and intake/cycle;
- two to four relevant experiences or results, including exact status;
- research interests or target directions;
- confirmed attachments;
- desired language, length, and tone;
- optional signature contact details.

Do not require GPA, rank, phone, social contact, demographic data, or a full CV. These are optional and should be included only when relevant and user-approved.

## Normalized fields

Use this structure internally. A saved profile may use the same JSON shape:

```json
{
  "name": "[required only for a final send-ready email]",
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
      "status": "[in preparation, submitted, under review, accepted, published, completed, or other exact state]",
      "source": "[chat, CV section, supplied document, or URL]"
    }
  ],
  "attachments_confirmed": ["[exact filename or attachment type]"],
  "contact": {
    "email": "[optional]",
    "phone_or_social": "[optional]"
  },
  "constraints": ["[facts, wording, or claims that must not change]"],
  "output_preferences": {
    "tone": "[concise, formal, warm, or user-specified]",
    "contact_in_signature": "[none, email, or email plus phone/social]"
  }
}
```

Placeholders illustrate the schema only. Never pass a placeholder into the final email.

## Fact control

For each claim, retain its source and exact state. Use these rules:

1. A current explicit user correction overrides an older supplied file.
2. A source document overrides an assistant inference.
3. Submitted, under review, accepted, and published are distinct states.
4. Participation, leadership, and first-author status are distinct roles.
5. If two sources conflict, report the conflict and ask which is current.
6. Do not derive rank, GPA conversions, authorship, venue status, dates, or attachment presence.

## Reuse and storage

Keep the normalized profile in working context when generating several letters in one task. Do not copy target-professor facts into the applicant profile.

Save a profile only at the user's request. Use a filename ending in `.local.json` under `profiles/`; both are ignored by the bundled `.gitignore`. Tell the user that ignored files remain sensitive local data and should not be attached to issues, commits, or public prompts.
