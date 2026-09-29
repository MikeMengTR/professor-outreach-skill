# Fixed Academic Outreach Letter Framework

Use this framework for every default Chinese academic outreach letter. The blocks and their order are fixed. Replace only the information slots with verified facts; do not rewrite the whole letter in a new structure.

The framework abstracts the original long-form self-recommendation format. It must not contain any particular applicant's name, profile, projects, or fixed personal claims.

## Before drafting

1. Build the applicant profile from supplied material and resolve conflicts.
2. Confirm the target role, cycle, language, attachment status, and signature preference.
3. Verify the professor's identity, current directions, one hook paper or active project, and any explicit recruiting information.
4. Select one primary proof and at most one complementary proof for the fit paragraph. Select up to three verified research/project items for the evidence block.
5. Resolve any framework slot that would otherwise require an unsupported or empty claim. Ask the user rather than inventing content.

## Fixed body order

Keep these blocks in this exact order. The role names describe paragraph positions; do not omit or merge a core block. Contact lines may be omitted only when not provided or not requested.

For an internal plan or structured JSON, assign the corresponding role name to every paragraph. Set JSON metadata `template_format` to `fixed-long`; this lets `scripts/validate_outreach.py` check block order and hook sentence count.

1. **Salutation — `salutation`**  
   `尊敬的[教授姓名]老师：`

2. **Courtesy — `courtesy`**  
   One courteous opening sentence. Keep it short and do not add praise.

3. **Identity and purpose — `identity`**  
   State the applicant's name, current affiliation/status, expected graduation or career stage when supplied, target cycle and role, and purpose for contacting this professor. Use the real application route only when verified; do not claim an award or eligibility that the profile does not confirm.

4. **Professor hook — `professor_hook`**  
   Exactly four sentences:
   - Sentence 1 names no more than three verified active research directions.
   - Sentence 2 names exactly one professor-side paper/project and says why it drew the applicant's attention.
   - Sentence 3 explains the problem plus one mechanism, design, or finding from that work.
   - Sentence 4 connects one or two sustained applicant interests to a future direction and the target role/cycle.

   Reusable sentence starts:

   ```text
   通过阅读您的个人主页与近期论文等信息，我了解到您围绕[研究方向]等方向开展研究。
   其中，[唯一 hook 论文/项目]引起了我的关注。
   您的工作[问题与核心机制/设计/发现]，使我进一步思考[申请人的具体研究问题]。
   我希望在[目标周期/身份]阶段继续探索[至多两个方向]，并尝试将[申请人兴趣]与您的相关研究结合。
   ```

   Keep the four sentence roles and order. Vary wording only when needed for grammatical fit or a different target role; do not add a second hook.

5. **Personal fit — `personal_fit`**  
   Start with a stage-appropriate version of this fixed pattern:

   ```text
   [本科/硕士/工作]期间，我围绕[目标方向所需的能力基础]开展了较系统的学习/研究/实践。
   ```

   Then state the primary applicant experience, actual role, concrete work, exact outcome/status, and one evidence-based bridge to the professor's direction. Add at most one complementary experience. This paragraph explains the applicant's fit; do not repeat the hook explanation.

6. **Basic-information lead-in — `basic_intro`**  
   Use a one-line transition, adapted only for the applicant's actual stage:

   ```text
   以下是我[本科/硕士/工作]期间的基本情况：
   ```

7. **Basic-information lines — `basic_academic`, `basic_courses`, `basic_language`, `basic_honors`, `basic_competitions`**  
   Keep five separate, unindented lines in this order:

   ```text
   学习/工作情况：[verified status, performance, or role]
   核心课程/专业能力：[relevant supplied courses or capabilities]
   语言能力：[verified language evidence, if supplied]
   荣誉与奖项：[verified relevant items]
   竞赛/资格：[verified relevant items]
   ```

   Keep all five lines, labels, and order stable. Use concise supplied facts. Do not derive scores or conversions. If a category is absent or private, ask whether it is unavailable or whether the user wants a factual non-disclosure wording on that line. Do not delete the line, guess a value, or leave a placeholder.

8. **Research heading — `research_heading`**  
   Keep a standalone line: `科研成果：` or, for a profile with project work but no formal research outputs, `科研与项目经历：`. Choose the label from verified profile facts, not stylistic preference.

9. **Research/project entries — `research_a`, `research_b`, `research_c`**  
   Place up to three separate entries under the heading, ordered by the applicant's source profile or explicit user preference. Keep each entry's topic/title, applicant role, methods/responsibilities, outcome, and exact status. Preserve all supplied fixed facts. Do not delete a confirmed entry only because it is less relevant to this professor; use the fit paragraph to prioritize relevance.

   Preserve the three item positions when the applicant has three or more confirmed items. If fewer are supplied, do not invent entries or repeat the same work: ask whether there are additional items or confirm that only the available items should be included. Keep the research heading and section in its fixed position; include only confirmed entries.

10. **Practical experience — `internship`**  
   Keep one separate paragraph in this position, beginning with the stage-appropriate label `实习经历：`, `工作经历：`, or `实践经历：`. State the actual organization/context, role, and relevant work only when supplied. If no such experience is supplied, ask whether the applicant has none to include; with confirmation, retain the paragraph and state that there is currently no relevant experience to add. Never silently omit the block.

11. **Closing — `closing`**  
    In this order, include only confirmed information:
    - confirmed attachment(s), if any;
    - one low-friction question about the target role/cycle or a short conversation;
    - one restrained commitment sentence that does not promise unsupported results or availability.

12. **Wishes — `wishes`**  
    One professional wishes sentence, for example `祝老师工作顺利、科研顺利！敬盼您的回复！`.

13. **Valediction and signature — `valediction`, `signature_name`, `signature_affiliation`, `signature_email`, `signature_phone`, `signature_date`**  
    Put the valediction and signature lines at the end, unindented. Include only name, affiliation, contact fields, and date supplied or requested. Do not invent contact details.

## Structural invariants

- The email body starts at the salutation. Do not put a subject, recipient metadata, citations, research notes, source URLs, internal fit labels, or analysis inside it.
- Keep all core blocks in the listed order. Do not merge, reorder, or drop blocks to meet a length target. Missing facts trigger a concise follow-up; after confirmation of absence or non-disclosure, keep the corresponding fixed line or paragraph with truthful wording.
- Keep exactly four hook sentences and one professor-side hook.
- Keep the basic-information categories in their five fixed positions.
- Preserve the source order of the research/project entries unless the user asks to reorder them.
- Preserve the original's restrained first-person voice. Avoid generic praise, inflated fit claims, and abstract-only summaries.
- No placeholders may remain in a send-ready email. Missing facts trigger a follow-up, not improvisation.
- The Chinese framework is the canonical structure. For English or another requested language, preserve the same block order and sentence functions in natural prose.
- Before delivery, compare the final body to all 24 role positions above. The only default omissions are unused research-item slots and unprovided signature contact/date lines.

## Output outside the email body

Return research notes and two or three subject options before or after the email as requested. Keep them clearly separated from the body. The email itself must contain only the fixed framework blocks.
