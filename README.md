# 套磁 Skill

**TC** 是一个面向 Codex 的通用导师套磁技能。它根据申请人提供的经历和目标导师的公开资料，核验导师研究与招生信息，梳理双方研究之间的联系，并起草简洁、具体、克制的中文或英文套磁邮件。

本项目适用于保研、直博、硕士、博士、科研助理（RA）、实习、访问学生及博士后等申请场景。

## 功能

- **整理申请人资料：** 从当前对话或用户提供的简历、草稿中提取与目标相关的经历，保留准确分工、结果和状态。
- **核验导师信息：** 根据姓名、学校、院系、实验室或主页确认导师身份，优先参考学校、实验室、论文等公开来源。
- **核实招生情况：** 区分明确公开的招生信息与推测；没有可靠信息时如实说明。
- **建立研究匹配：** 选择一个导师研究 hook，结合一至两项申请人经历，说明直接或可迁移的联系。
- **撰写简洁邮件：** 默认采用一屏左右的短邮件，保留重点经历、具体研究理解和一个低负担询问，不堆叠简历内容。
- **保护申请人信息：** 不依赖内置个人档案，不会为了搜索导师而搜索申请人的个人信息；未经确认，不声称已附上材料。

## 使用方法

在 Codex 中通过 **`$tc`** 调用。提供导师姓名及所属学校、院系、实验室或主页；如果附有简历或经历说明，TC 会优先从中提取相关信息。

示例：

```text
$tc 请根据我附上的简历整理申请人经历。请核验某大学某院系张老师的研究方向和公开招生信息，结合我的相关项目，起草一封申请2027级直博的中文套磁邮件。随信仅确认附上个人简历。
```

如果缺少的信息会影响导师身份、申请目标或邮件事实准确性，TC 会先询问必要问题；其他情况下会依据已确认的信息起草，不补造经历。

## 效果示例

以下内容为**完全虚构的简洁邮件示例**。申请人、院校、导师、论文和项目均非真实信息；论文题目为虚构内容，不对应具体期刊或真实个人。

### 示例邮件

尊敬的X老师：

感谢您在百忙之中阅读来信。我是示例大学自动化专业本科生甲，预计2027年毕业，希望申请您团队2027级直博。

我以项目负责人身份完成了一项微电网多能源预测研究，负责数据整理、模型实现和实验分析；相关论文已投稿。该经历让我持续关注预测信息如何服务后续能源决策。

了解到您围绕多智能体协同控制和智能电网能源管理开展研究后，我关注到您团队的《Cooperative Planning for Distributed Energy Systems》。该工作将协同决策机制用于动态能源管理。我的研究目前聚焦负荷预测，尚未涉及多主体控制；但时序建模和实验分析经验可作为我进一步探索预测与协同决策衔接问题的基础。

冒昧请教您是否考虑招收2027级直博生，或是否方便进一步交流研究匹配与申请安排？随信附上个人简历，敬请您审阅。

祝工作顺利！

示例申请人  
示例大学自动化专业

示例仅用于呈现默认短邮件风格。实际内容会依据用户确认的经历和导师公开资料生成；未确认的论文状态、附件或招生信息不会写入邮件。

## 可选长篇框架

如果用户明确要求长篇自荐信、完整履历式邮件或指定固定长框架，TC 才会启用 [固定长篇框架](references/fixed_outreach_template.md)。它要求更多基本信息；资料不足时会先询问，不会擅自填充或删掉相关段落。

## 安装

将本仓库内容放入 Codex 的技能目录，并保留 `SKILL.md`、`agents`、`references` 和 `scripts` 的相对位置。

常见目录示例：

```text
macOS / Linux: ~/.codex/skills/tc/
Windows:       %USERPROFILE%\.codex\skills\tc\
```

重启或刷新 Codex 后，在对话中输入 **`$tc`** 调用。

## 隐私与事实边界

- 仓库中不包含预置申请人档案。申请人资料默认只在当前任务中使用；只有用户明确要求时才保存。
- 只使用撰写邮件所需的个人信息；不会要求无关的身份证号、家庭住址、出生日期或账号凭证。
- 未经用户确认，不把“已投稿”写成“审稿中”“已录用”或“已发表”，也不声称存在未确认的附件、推荐关系、招生名额或申请资格。
- 导师研究与招生信息可能变化。涉及导师身份、当前研究和招生安排时，应依据当时可用的公开来源核验，并将来源说明放在邮件正文之外。
- 默认短邮件；只有用户明确要求时，才改用长篇固定框架。

## 项目结构

```text
SKILL.md                              技能主流程与质量要求
agents/openai.yaml                    Codex 技能选择器名称与简介
references/applicant_profile.md       申请人资料整理与事实核对
references/adaptation_contract.md     跨导师复用时的事实与适配规则
references/short_email_pattern.md     默认短邮件结构与写作规范
references/fixed_outreach_template.md 用户明确要求时使用的长篇框架
scripts/validate_outreach.py          结构化邮件及事实约束校验
scripts/audit_privacy.py              发布前隐私检查
```

## 本地检查

在仓库根目录运行：

```bash
python -B scripts/audit_privacy.py .
python -B scripts/validate_outreach.py --help
```

## 许可证

当前仓库尚未指定开源许可证。仓库公开并不自动授予他人复制、修改或再发布的许可。

## English summary

TC is a general-purpose Codex skill for researching professors and drafting concise, evidence-grounded academic outreach emails. It defaults to a short email with one professor-side hook, one or two relevant applicant proofs, an honest fit bridge, and a low-friction ask. A longer fixed framework is available when explicitly requested.
