# 论文科学写作 Codex Skills

按论文写作功能组织的 **13个独立Codex技能**。在原有6个技能基础上，根据本次《论文科学写作.docx》的41张嵌入图片新增7个技能，覆盖相关工作、研究方法、实验设计、结果讨论、图表表达、结论、语言与段落结构，并扩展投稿前自检。

支持中英文、算法、实证、理论及定性研究。将课件中的原则改写为触发条件、执行流程、输出要求及完成检查；各技能可以单独使用，无需依赖其他技能文件夹。

## 功能分类

| 技能目录 | 名称 | 功能 | 本次更新 |
| --- | --- | --- | --- |
| [refine-research-problem-gap](refine-research-problem-gap/SKILL.md) | 研究问题与缺口 | 收敛具体问题，区分Challenge与Gap，核实已有方法边界 | 既有技能，补充自检要求 |
| [formulate-paper-idea-contributions](formulate-paper-idea-contributions/SKILL.md) | 核心思想与贡献 | 解释核心思想，建立缺口、学术增量与证据对应 | 既有技能，补充自检要求 |
| [write-academic-paper-title](write-academic-paper-title/SKILL.md) | 论文标题 | 生成准确、具体、可检索并满足字数要求的题名 | 既有技能，补充自检要求 |
| [write-academic-paper-abstract](write-academic-paper-abstract/SKILL.md) | 论文摘要 | 压缩研究逻辑与关键结果，检查中英文信息一致 | 既有技能，补充自检要求 |
| [write-academic-paper-introduction](write-academic-paper-introduction/SKILL.md) | 论文引言 | 建立研究动机、缺口和方案之间的论证 | 既有技能，补充自检要求 |
| [write-academic-related-work](write-academic-related-work/SKILL.md) | 相关工作与研究定位 | 按研究路线组织相关工作并比较最接近研究，准确定位本文的学术增量 | 本次新增 |
| [write-academic-research-method](write-academic-research-method/SKILL.md) | 研究方法与公式阐释 | 解释方法设计动机、框架信息流与公式含义，检查实现细节和复现信息 | 本次新增 |
| [design-academic-experiments](design-academic-experiments/SKILL.md) | 实验设计与证据链 | 把学术主张转为研究问题，设计公平基线、消融与可靠性验证证据 | 本次新增 |
| [write-academic-results-discussion](write-academic-results-discussion/SKILL.md) | 结果分析与讨论 | 围绕关键观察解释结果、连接学术主张，并明确外推范围与失败条件 | 本次新增 |
| [present-academic-figures-tables](present-academic-figures-tables/SKILL.md) | 图表选择与表达审查 | 按研究问题选择图表，核对统计含义、图注、坐标单位和排版可读性 | 本次新增 |
| [write-academic-paper-conclusion](write-academic-paper-conclusion/SKILL.md) | 论文结论与局限 | 凝练问题、核心思想和主要发现，明确结论适用范围与研究局限 | 本次新增 |
| [polish-academic-language-structure](polish-academic-language-structure/SKILL.md) | 学术语言与段落结构 | 压缩冗余、理顺段落和术语，同时保留论文事实、条件与证据强度 | 本次新增 |
| [audit-paper-logic-consistency](audit-paper-logic-consistency/SKILL.md) | 全文逻辑与一致性审查 | 四轮修改、跨章核对、审稿意见诊断和投稿前自检 | 既有技能，扩展检查清单 |

## 文件结构

```text
论文科学写作skill/
├── README.md
├── SOURCE_MAP.md
├── write-academic-related-work/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/source-guidance.md
├── present-academic-figures-tables/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/chart-semantics.md
└── …其余独立技能目录
```

`SKILL.md`中的YAML定义技能名称和触发条件；正文规定流程与交付。`agents/openai.yaml`提供显示名称、简介及默认提示。`references/`保存详细规则、模板或检查表，并从技能正文直接链接。复制整个技能目录即可，不要只复制SKILL.md，也不要将13个技能合并为一个文件。

## 安装到Codex

将需要的独立技能目录复制到当前Codex客户端支持的技能发现位置。常见位置为个人的`~/.agents/skills/`或项目的`.agents/skills/`；若客户端使用`~/.codex/skills/`，使用该位置。自定义环境以客户端当前说明为准。

以下示例克隆仓库并全部安装到个人目录；如果已存在同名技能，先检查本地修改并选择性复制，避免覆盖。

```bash
git clone https://github.com/wangzhuo199344/paper-scientific-writing-skills.git
mkdir -p ~/.agents/skills
cp -R paper-scientific-writing-skills/论文科学写作skill/*/ ~/.agents/skills/
```

Windows PowerShell示例：

```powershell
git clone https://github.com/wangzhuo199344/paper-scientific-writing-skills.git
$skillsPath = Join-Path $env:USERPROFILE '.agents/skills'
New-Item -ItemType Directory -Force -Path $skillsPath | Out-Null
Get-ChildItem './paper-scientific-writing-skills/论文科学写作skill' -Directory |
    Where-Object { Test-Path (Join-Path $_.FullName 'SKILL.md') } |
    Copy-Item -Destination $skillsPath -Recurse
```

复制后在新会话中检查技能是否显示，用`$技能名`明确调用。本仓库提供可移植的文件；GitHub上传不等于自动安装到每个本地Codex客户端或ChatGPT个人技能列表。

## 调用示例

### 研究问题

```text
请使用 $refine-research-problem-gap，根据稿件及提供文献凝练研究问题，区分Challenge和Gap，并列待核实项。
```

### 核心思想

```text
请使用 $formulate-paper-idea-contributions，给出一句核心思想，再提炼有证据支持的贡献。
```

### 标题

```text
请使用 $write-academic-paper-title，生成3个不超过20字的中文标题并推荐一个。
```

### 摘要

```text
请使用 $write-academic-paper-abstract，凝练摘要至450字以内，检查中英文对象、数值和结论强度一致。
```

### 引言

```text
请使用 $write-academic-paper-introduction，根据稿件和实际文献重写引言，明确问题、缺口及设计依据。
```

### 相关工作与研究定位

```text
请使用 $write-academic-related-work，依据当前稿件与已提供文献重写相关工作，并明确最接近工作与本文的差异。
```

### 研究方法与公式阐释

```text
请使用 $write-academic-research-method，重组方法章节，说明每项设计的动机、公式含义与实际实现。
```

### 实验设计与证据链

```text
请使用 $design-academic-experiments，为本文各项主张设计研究问题、基线、消融与验证方案，并标明已完成与待开展项目。
```

### 结果分析与讨论

```text
请使用 $write-academic-results-discussion，根据图表和实验记录改写结果讨论，区分观察、解释与可支持的结论。
```

### 图表选择与表达审查

```text
请使用 $present-academic-figures-tables，检查本文图表是否支持明确研究问题，并修正图注、统计含义与可读性。
```

### 论文结论与局限

```text
请使用 $write-academic-paper-conclusion，根据当前论文撰写结论，保留主要发现与边界，避免照搬摘要。
```

### 学术语言与段落结构

```text
请使用 $polish-academic-language-structure，凝练这段论文文字，理顺逻辑和术语，保留数值、条件与结论强度。
```

### 全文审查

```text
请使用 $audit-paper-logic-consistency，按研究主线、结构、证据、语言四轮审查，并按优先级列出位置、依据、影响和修改建议。
```

## 组合使用与材料准备

按任务选择：问题与缺口 → 核心思想与贡献 → 相关工作与引言 → 方法 → 实验设计 → 结果讨论与图表 → 结论 → 摘要与标题 → 全文审查。语言和段落修改在科学逻辑及证据链稳定后开展；不要求一次调用全部技能。

| 任务 | 建议提供材料 |
| --- | --- |
| 问题、相关工作、引言 | 当前稿件或研究设想、最接近文献、已有方法和场景条件 |
| 方法 | 问题定义、实际实现、公式、符号、参数、框架及必要代码说明 |
| 实验设计 | 核心主张、已完成实验、数据划分、基线、调参和评价协议 |
| 结果、图表、结论 | 实际图表或数据、关键结果、条件、重复单位及失败情况 |
| 语言与全文审查 | 当前稿件、修改范围、权威数据口径、目标模板及长度要求 |

材料不完整时只审已提供部分，未知事实标为待核实。需要实际检索文献、作图、修改Word或复算时，应使用当前环境适用的检索、绘图、文档或计算工具；这些技能本身是文字工作流程，没有额外Python依赖、API密钥或自动实验程序。

## 来源与边界

本次Word内没有可提取正文，其41张图片已按出现顺序逐张读取。图片序号、课件页码和功能对应见 [SOURCE_MAP.md](SOURCE_MAP.md)。既有6个技能保留原有材料的来源说明；本次新增规则另行标注，不把新文档没有的前半部分当作重新提取内容。

遵守当前事实，不编造文献、数值、创新性、实验或统计显著性，不将关联升级为因果。课件示例用于理解写作结构，示例数字不能成为用户研究结果。图表使用真实数据及精确工具；投稿格式依实际期刊或会议模板核对。技能可以辅助写作和检查，不能代替原始数据核验或保证录用。
