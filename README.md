# TC Professor Outreach Skill

A reusable Codex skill for researching professors and drafting concise, evidence-grounded academic outreach emails for different applicants.

## What it does

- Builds a temporary applicant profile from information supplied in the current task.
- Verifies the professor's identity, research, and any explicit recruiting information using current public sources.
- Selects one research hook and maps up to two applicant proof points to it.
- Drafts a concise Chinese or English email, preserving exact project and publication status.
- Keeps source notes outside the email body and minimizes personal information.

The skill includes no prefilled applicant profile. Applicant information should be provided at runtime and is not saved unless requested.

## Install

Copy the `tc` directory into your Codex skills directory, for example:

```text
~/.codex/skills/tc/
```

Then invoke it in Codex with `$tc`.

## Example

```text
$tc Use the CV I attached to build my applicant profile. Research Professor X at University Y, verify current recruiting information, and draft a concise Chinese email for 2027 direct-PhD admission. Mention only my confirmed CV attachment.
```

## Included references and scripts

- `references/applicant_profile.md` — runtime profile and factuality rules
- `references/adaptation_contract.md` — rules for adapting one profile to multiple professors
- `references/short_email_pattern.md` — email structure and writing guidance
- `scripts/validate_outreach.py` — checks structured email artifacts and applicant claims
- `scripts/audit_privacy.py` — scans a skill directory for likely private data before sharing

Run the checks from this directory:

```bash
python -B scripts/audit_privacy.py .
python -B scripts/validate_outreach.py --help
```

## 中文简介

这是一个通用的 Codex 导师套磁技能：根据当前任务中提供的申请人资料，核验导师身份、研究方向和公开招生信息，选择一个有依据的研究切入点，并生成简洁、克制的中文或英文套磁邮件。技能目录不包含预置个人档案；申请人信息默认只在当前任务中使用，只有用户明确要求时才保存。

安装时将整个 `tc` 文件夹复制到 `~/.codex/skills/tc/`，之后在 Codex 中使用 `$tc` 调用。
