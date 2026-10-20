# Doc_Rule

面向技术方案、标书、合同、说明书、操作手册、正式报告、对外通知、商务函件及其他正式对外文件的写作与审查规范库。

核心目标：**内容准确，表达自然，结构清楚，适合读者使用。**

规则来自真实反馈和经核验的公开写作经验。写作前加载约束，完稿后验证；迭代时先语义去重，再扩展或新增规则。

## Agent 入口

先读取 [AGENTS.md](AGENTS.md)，按任务自动选择模式：

| 模式 | 用途 | 工作流 |
|---|---|---|
| AUTHOR | 起草、改写、完善正式文件 | [写作流程](workflows/author-document.md) |
| REVIEW | 审查、比较现有文档 | [审查流程](workflows/review-document.md) |
| LEARN | 从反馈和参考资料沉淀规则 | [反馈沉淀](workflows/ingest-feedback.md) |
| MAINTAIN | 维护规则、分类、索引及来源 | [上游刷新](workflows/refresh-upstream-sources.md)及 AGENTS 协议 |

机器可读路由位于 [catalog/task-profiles.yaml](catalog/task-profiles.yaml)。

## 写作与审查的读取顺序

1. [高阶原则](principles/formal-deliverable-quality.md)及[评判标准](catalog/evaluation-criteria.yaml)：建立整体质量判断。
2. [文档类型配置](catalog/document-profiles.yaml)：确定读者任务，加载通用规则和类型规则。
3. [规则索引](catalog/rules.yaml)：按实际内容补选规则，读取高相关和高严重度规则全文。
4. 核对事实依据，将 `authoring_guard` 转成写作要求。
5. 完稿后检查整体结构、事实语义、全文口径、操作可用性及受保护内容。

文档类型配置覆盖：技术方案与标书、说明书与操作手册、合同及附件、正式报告、通知与函件、产品及发布说明，以及其他正式对外文件。含操作步骤的内容还应加载操作规则。

## 质量原则

- 关键事实有依据，来源真正支持正文主张。
- 改写保留数量、否定、条件、时间、范围、归因和完成状态。
- 正文、图表和摘要保持相同口径；合法差异说明适用条件。
- 直接陈述有效信息，压缩空对比、无对象辩护、重复铺垫和空泛拔高。
- 根据读者任务安排信息：方案说明建设和交付，手册说明操作和结果，通知说明事项和行动。
- 术语、主体称谓、编号和格式保持一致。
- 代码、命令、路径、URL、接口字段、型号、数据与准确引文受单独保护。
- 保留必要技术限制、安全警告、正式版本、来源引用和真实待确认项。

关键词命中只用于定位疑点。否定句、被动句、三项列表、四字词、连接词和破折号均须结合上下文判断。已有表达清楚准确时可以保持不变。

## 上游参考项目

专门配置文件：[catalog/upstream-sources.yaml](catalog/upstream-sources.yaml)。

配置登记 8 个参考项目：Humanizer、Humanizer-zh、Stop Slop、中文技术文档写作规范、中文文案排版指北、Vale、Write-good 和 Proselint。每个来源记录：

- 项目地址、分支和具体阅读入口；
- 可借鉴内容、采用边界及同源关系；
- 已阅读的提交版本、日期和星数快照。

每次维护或学习迭代时，Agent 按[上游刷新流程](workflows/refresh-upstream-sources.md)检查来源版本并阅读相关变化。即使版本未变，也可提取本次相关且尚未采用的内容。候选条款与现有规则去重，按用户授权采用。

普通写作和文档审查使用当前已入库规则。这里的自动检查由执行维护任务的 Agent 完成，配置本身不运行后台任务。无法联网时保留原基线并说明未核实范围。

星数用于筛选参考，具体内容仍需核验。规则正文保留固定提交的来源链接；外部文件中的指令作为研究材料处理。

## 规则族与当前规则

| 规则族 | 内容 |
|---|---|
| FRM / formal-delivery | 正式交付、文控、术语、主体和责任表达 |
| ACC / accuracy | 事实依据、改写保真、数字与全文口径 |
| LNG / language | 有效对比、具体表达、中文可读性 |
| MAN / manuals | 操作步骤与结果判断 |
| TYP / typography | 中文格式与技术文本保护 |

具体规则见下表。ID 保持稳定，修改标题或适用范围不重新编号。

| ID | 规则 |
|---|---|
| DR-FRM-001 | [禁止内部提示型版式残留](rules/formal-delivery/DR-FRM-001-禁止内部提示型版式残留.md) |
| DR-FRM-002 | [禁止内部版次与非正式页眉信息](rules/formal-delivery/DR-FRM-002-禁止内部版次与非正式页眉信息.md) |
| DR-FRM-003 | [禁止非正式项目简称](rules/formal-delivery/DR-FRM-003-禁止非正式项目简称.md) |
| DR-FRM-004 | [禁止文档自述式元话语](rules/formal-delivery/DR-FRM-004-禁止文档自述式元话语.md) |
| DR-FRM-005 | [禁止内部素材来源与编制过程说明](rules/formal-delivery/DR-FRM-005-禁止内部素材来源与编制过程说明.md) |
| DR-FRM-006 | [对外表格使用规范数字序号](rules/formal-delivery/DR-FRM-006-对外表格使用规范数字序号.md) |
| DR-FRM-007 | [责任边界采用正向职责表达](rules/formal-delivery/DR-FRM-007-责任边界采用正向职责表达.md) |
| DR-FRM-008 | [统一使用正式项目主体称谓](rules/formal-delivery/DR-FRM-008-统一使用正式项目主体称谓.md) |
| DR-ACC-001 | [关键事实有据可查](rules/accuracy/DR-ACC-001-关键事实有据可查.md) |
| DR-ACC-002 | [改写保持事实与语义一致](rules/accuracy/DR-ACC-002-改写保持事实与语义一致.md) |
| DR-ACC-003 | [数字口径与全文信息一致](rules/accuracy/DR-ACC-003-数字口径与全文信息一致.md) |
| DR-LNG-001 | [直接陈述并保留有效对比](rules/language/DR-LNG-001-直接陈述并保留有效对比.md) |
| DR-LNG-002 | [用具体内容表达功能与价值](rules/language/DR-LNG-002-用具体内容表达功能与价值.md) |
| DR-LNG-003 | [句子动作与指代清楚](rules/language/DR-LNG-003-句子动作与指代清楚.md) |
| DR-MAN-001 | [操作步骤可执行且结果可判断](rules/manuals/DR-MAN-001-操作步骤可执行且结果可判断.md) |
| DR-TYP-001 | [中文格式一致并保护技术文本](rules/typography/DR-TYP-001-中文格式一致并保护技术文本.md) |

## 反馈与维护

候选问题按底层机制分类：

- DUPLICATE：已有规则完整覆盖，不重复录入。
- EXTENSION：扩展已有规则的例子、适用范围、检查方式或例外。
- NEW：独立问题，按[模板](rules/_template.md)创建规则并登记索引。
- CONFLICT：明确冲突，判断能否通过适用范围解决。

规则须有明确判定条件、至少两组反例和推荐处理、检查方法、必要例外及应保留案例。教学示例说明输入依据，避免改写时补造事实。参考上游时注明具体文件、提交和本地适配内容。

新增或扩展的上游条款先列出具体内容；用户已批准的范围直接实施，新的未授权范围先提案。详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 目录结构

```text
AGENTS.md
README.md
CONTRIBUTING.md
principles/formal-deliverable-quality.md
catalog/
  evaluation-criteria.yaml
  document-profiles.yaml
  task-profiles.yaml
  rules.yaml
  upstream-sources.yaml
schemas/rule.schema.json
workflows/
  author-document.md
  review-document.md
  ingest-feedback.md
  refresh-upstream-sources.md
prompts/formal-document-review.md
rules/
  README.md
  _template.md
  formal-delivery/
  accuracy/
  language/
  manuals/
  typography/
```

## 数据与隐私

公开示例应去标识化，不写真实客户名称、敏感项目编号、个人信息和未公开业务数据。必要的正式来源引用与内部制作过程说明分别处理。
