# 论文科学写作skill

面向 Codex 的六个独立论文写作技能，覆盖研究问题与缺口、核心思想与贡献、标题、摘要、引言和全文逻辑审查。依据《科学写作与报告 论文写作图片文字整理》中已有的写作要求制作，将课堂原则转为可执行的工作流程、输出要求和检查标准。

支持中文与英文论文。各技能可单独调用，也可按论文写作顺序组合使用。当前材料只列纲要而未展开的方法、实验、图表、审稿回复等内容，不另行作为完整技能提供。

## 技能说明

| 技能目录 | 名称 | 功能 |
| --- | --- | --- |
| [refine-research-problem-gap](refine-research-problem-gap/SKILL.md) | 研究问题与缺口分析 | 明确研究对象、条件、困难与可检验目标，区分 Challenge 和 Gap，核实已有方法的适用边界。 |
| [formulate-paper-idea-contributions](formulate-paper-idea-contributions/SKILL.md) | 核心思想与学术贡献 | 用一句话说明核心思想，区分工作量、技术动作与学术增量，建立缺口—思想—价值—证据对应关系。 |
| [write-academic-paper-title](write-academic-paper-title/SKILL.md) | 论文标题 | 生成和比较标题，执行字数及句式约束，检查实时性、鲁棒性等标题承诺的证据。 |
| [write-academic-paper-abstract](write-academic-paper-abstract/SKILL.md) | 论文摘要 | 压缩完整研究逻辑，保留关键结果，核验数字、单位和范围，检查中英文信息一致性。 |
| [write-academic-paper-introduction](write-academic-paper-introduction/SKILL.md) | 论文引言 | 从背景收敛到问题，通过文献建立缺口，说明设计动机与贡献，组织段落递进关系。 |
| [audit-paper-logic-consistency](audit-paper-logic-consistency/SKILL.md) | 全文逻辑与一致性审查 | 检查问题、方法、主张、证据的跨章节一致性，区分确定性错误、待核实问题与可选优化。 |

每个目录含 `SKILL.md` 和 `agents/openai.yaml`。前者定义触发条件、流程和交付标准；后者提供技能名称、简要说明及默认调用提示。六个技能均为文字工作流程，不需要额外 Python 包、API 密钥或配套脚本。

## 在 Codex 中安装

将需要的技能目录放到 Codex 能发现的技能目录中，保留目录结构，不要只复制 `SKILL.md`，也不要把六个技能合并为一个文件。常见安装位置为个人的 `~/.agents/skills/`，或项目的 `.agents/skills/`；具体以所用 Codex 客户端的技能发现规则为准。

例如将 `write-academic-paper-abstract` 整个目录复制为：

```text
~/.agents/skills/write-academic-paper-abstract/SKILL.md
~/.agents/skills/write-academic-paper-abstract/agents/openai.yaml
```

Windows 中 `~` 表示当前用户目录。复制后在新会话中检查技能列表。ChatGPT 中已安装的个人技能与本地 Codex 目录属于不同安装入口，本仓库提供可移植的技能文件。

## 使用方法

在支持技能调用的 Codex 对话中，用 `$技能名` 明确调用，并提供当前论文材料。客户端若显示技能选择器，也可以从中选择对应技能。

### 研究问题与缺口

```text
请使用 $refine-research-problem-gap，根据论文初稿和提供的相关文献，凝练一个可验证的研究问题，分析现有方法的适用边界，并列出待核实的缺口论断。
```

### 核心思想与贡献

```text
请使用 $formulate-paper-idea-contributions，根据研究问题、方法和结果，给出一句核心思想，再提炼有证据支持的学术贡献。不要把框架、算法、实验机械拆成三条贡献。
```

### 标题

```text
请使用 $write-academic-paper-title，根据当前稿件生成3个中文论文标题，每个不超过20个字，推荐一个。不要使用正文没有验证的性能承诺。
```

### 摘要

```text
请使用 $write-academic-paper-abstract，将摘要凝练至450字以内，保留主要方法及最重要的结果，并检查英文摘要与中文版在数值、对象和结论强度上是否一致。
```

### 引言

```text
请使用 $write-academic-paper-introduction，根据提供的稿件和文献改写引言，突出具体问题、研究缺口及其与方法设计的对应关系。无法核实的文献或事实请标注。
```

### 全文审查

```text
请使用 $audit-paper-logic-consistency，从头到尾检查当前论文，按优先级列出位置、问题依据、影响和具体修改建议，区分确定性错误与需要作者核实的问题。
```

## 建议提供的材料

- 问题与缺口：研究设想、场景条件、现有方法以及最接近的相关文献。
- 核心思想与贡献：明确的问题和缺口、方法设计、主要结果及验证证据。
- 标题：全文或至少研究问题、方法与主要结果，以及长度、语言、句式要求。
- 摘要：当前正文、摘要、样本口径、关键结果和期刊要求。
- 引言：当前正文、相关文献、核心思想与贡献，以及引用格式要求。
- 全文审查：当前完整稿件、补充材料和作者已确认的数据口径；只有部分材料时，只审查已提供部分。

## 组合顺序与边界

建议顺序：研究问题与缺口 → 核心思想与贡献 → 引言 → 摘要 → 标题 → 全文一致性审查。实际写作中可反复迭代；修改研究结果后，应重新核对摘要、贡献和标题。

所有技能以当前材料为依据，不编造文献、数值、实验和创新性，不将关联升级为因果。证据不足时标为待核实或待验证。仅请求文字时直接输出文字；请求修改 Word 等文件时，使用当前环境适用的文档工具保留格式并验证。技能能辅助写作和审查，不能代替原始数据核验或保证论文录用。

## 官方说明

本地技能发现路径和调用方式参见 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。当前官方个人目录为 `~/.agents/skills/`，项目目录为 `.agents/skills/`。
