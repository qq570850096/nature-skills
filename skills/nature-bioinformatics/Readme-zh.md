# nature-bioinformatics

面向 scRNA-seq、空间转录组和单细胞多组学论文发表的 Nature-style
bioinformatics skill。

`nature-bioinformatics` 不是一个自动跑完整分析的 pipeline，也不是简单的英文润色
prompt。它的目标是帮助作者把生物信息学结果组织成可发表、可审稿、可追踪的学术产物：
Results、Methods、figure plan、审稿风险检查、审稿回复策略和数据/代码可用性清单。

它最关心的问题不是“这句话能不能写得更漂亮”，而是：

- 这个 claim 的证据是什么？
- 证据来自哪个 sample、cohort、figure、statistic 或 validation？
- 这个结论能写到什么强度？
- 哪些地方会被生信审稿人追问？
- 哪些信息不能由 AI 补，需要作者确认？

---

## 项目定位

`nature-bioinformatics` 服务的是论文发表阶段的生信工作流。

适合：

- 单细胞/空间组学论文 Results 写作
- scRNA-seq / spatial transcriptomics Methods 补全
- 多 panel 生信图表逻辑规划
- 审稿前 reviewer-risk audit
- 审稿意见回复策略
- GEO / SRA / ENA / 代码仓库 / figure source data 清单检查
- 中文实验笔记转 Nature-style 英文表达

不适合：

- 从零执行完整 scRNA-seq 分析
- 代替作者编造 marker gene、统计结果、样本量、软件版本或 accession
- 把预测性分析包装成已验证机制
- 替代湿实验、生信统计或临床验证

---

## 为什么需要这个 skill

很多生信论文被质疑，不是因为英语不够流利，而是因为 claim 比证据走得更远。

常见问题包括：

- 用 UMAP 可视化支撑过强结论
- 把 ligand-receptor prediction 写成真实细胞通讯
- 把 pseudotime 写成真实时间顺序或谱系分化
- 把 spatial proximity 写成细胞功能互作
- 用 cell number 代替 donor/sample-level biological replication
- 只给 marker heatmap，却没有说明细胞注释依据
- Methods 中缺少 QC、normalization、integration、统计模型、数据库版本
- 数据可用性里没有 accession、processed matrix、metadata 或代码 release

这个 skill 的设计目标，就是把这些高风险判断放进工作流里，而不是等审稿人指出来。

---

## 设计来源与前人经验

`nature-bioinformatics` 是在 `nature-skills` 原有 router-style 架构上，吸收多个公开
医学/生信/科学 agent skill 项目的设计亮点后形成的。它不是复制这些项目的内容，而是借鉴
它们的工程组织方式和质量控制思想。

| 项目 | 吸收的亮点 | 在本 skill 中的落地 |
|---|---|---|
| [`K-Dense-AI/scientific-agent-skills`](https://github.com/K-Dense-AI/scientific-agent-skills) | 大规模科学 skill 的目录治理和横向分类 | 保留可扩展任务轴，未来可继续加入 bulk RNA-seq、ATAC-seq、variant、proteomics 等方向 |
| [`FreedomIntelligence/OpenClaw-Medical-Skills`](https://github.com/FreedomIntelligence/OpenClaw-Medical-Skills) | 医学、生信、药物发现、临床任务的广覆盖 | 首版聚焦 scRNA/spatial，但设计时预留医学 AI 与多组学扩展空间 |
| [`ClawBio/ClawBio`](https://github.com/ClawBio/ClawBio) | specification-first、可复现、环境与校验意识 | 强制保留 software、version、database release、accession、code/data traceability 等字段 |
| [`GPTomics/bioSkills`](https://github.com/GPTomics/bioSkills) | 按生信任务和数据类型拆 skill | 用 `data_modality` 和 `analysis_claim` 作为核心路由轴，而不是只按论文 section 拆分 |
| [`aipoch/medical-research-skills`](https://github.com/aipoch/medical-research-skills) | 医学研究 skill 的 audit / veto gate 思路 | 引入 reviewer-risk flags、missing-input flags 和 fatal/major/minor 风险分级 |

换句话说，这个 skill 的定位是：用 `nature-skills` 的 Nature-style 写作与发表框架，承接
前人项目在科学 skill 目录治理、生信任务拆分、可复现契约和质量审核上的经验。

---

## 核心能力

| 能力 | 说明 |
|---|---|
| Claim-evidence mapping | 把每个结论拆成主张、证据等级、支持材料和边界 |
| Results drafting | 写作或重构 scRNA/spatial Results，避免过度机制化 |
| Methods auditing | 检查 QC、normalization、integration、annotation、statistics、software/version 是否完整 |
| Figure planning | 把 UMAP、heatmap、spatial map、DEG、trajectory、communication 等组织成证据链 |
| Reviewer-risk audit | 从生信审稿人角度标记 fatal / major / minor risk |
| Response strategy | 把细胞注释、批次效应、统计、细胞通讯等质疑转成回复策略 |
| Data availability | 检查 raw data、processed data、metadata、figure source data、code 和 accession |
| Chinese author mode | 接受中文笔记，输出英文正文并保留中文核对项 |

---

## 设计架构

这个 skill 采用 `nature-skills` 项目里的 router-style 架构：

```text
用户请求
  -> SKILL.md 判断是否触发
  -> manifest.yaml 识别任务轴
  -> always_load 加载核心原则
  -> static/fragments 加载当前任务片段
  -> references 按需加载深层检查表
  -> 输出可直接使用的文本、计划或清单
```

### 三个任务轴

`manifest.yaml` 中定义了三个主要轴：

| 轴 | 作用 | 当前支持 |
|---|---|---|
| `data_modality` | 判断数据类型 | `scrna-seq`, `spatial-transcriptomics`, `single-cell-multiomics` |
| `analysis_claim` | 判断分析主张 | `cell-annotation`, `differential-expression`, `trajectory-pseudotime`, `cell-cell-communication`, `spatial-niche`, `integration-batch-effect`, `biomarker-signature` |
| `artifact` | 判断输出产物 | `results`, `methods`, `figure-plan`, `review-risk-audit`, `response-strategy`, `data-availability-checklist` |

这种设计让 skill 不必一次加载所有资料。比如用户只问“审稿人质疑细胞注释”，就只需要加载
cell annotation 和 response strategy 相关片段；如果用户问空间转录组图表，则加载 spatial
和 figure plan 相关片段。

---

## 生信写作原则

### 1. 先分清证据等级

| 等级 | 含义 | 推荐表达 |
|---|---|---|
| Observation | 分析中观察到的模式 | observed, detected, enriched, associated |
| Inference | 计算方法推断出的关系 | suggests, indicates, is consistent with |
| Mechanism | 有直接或正交证据支持的机制 | demonstrates, supports a mechanism in which |
| Clinical implication | 和诊断、预后、治疗或分层相关 | may inform, warrants validation, is associated with |

### 2. 不把预测写成事实

- ligand-receptor analysis 是 interaction hypothesis，不是 confirmed communication。
- pseudotime 是 inferred ordering，不是 chronological time。
- spatial proximity 是空间接近，不是 physical interaction。
- DEG/pathway enrichment 是表达或通路层面的关联，不是机制证明。
- biomarker/signature 是 candidate，除非有独立验证和严格建模。

### 3. 不隐藏缺失信息

如果作者没有提供 sample size、donor number、statistical test、multiple-testing correction、
software version、database release、accession 或 validation，skill 会把它们列成 missing
inputs，而不是帮作者补一个看起来合理的值。

---

## 安装和使用

### Codex 插件安装

如果通过本仓库的 Codex plugin 使用，`nature-bioinformatics` 已经包含在插件镜像中：

```text
plugins/nature-skills/skills/nature-bioinformatics/
```

安装整个插件后，使用下面这类请求即可触发：

```text
帮我写 scRNA-seq Results。
```

```text
Audit this spatial transcriptomics figure for reviewer risk.
```

```text
审稿人质疑我们的细胞注释不可靠，帮我制定回复策略。
```

### 手动安装

如果手动安装 local skills，请复制：

```text
skills/_shared/
skills/nature-bioinformatics/
```

`_shared` 目录必须一起复制，因为该 skill 会加载共享的 reader workflow、paper-type taxonomy、
ethics 和 terminology ledger。

---

## 推荐输入格式

你可以直接给自然语言请求，也可以按下面模板给更完整的信息：

```text
任务：帮我写 / 审核 / 回复 / 规划
数据类型：scRNA-seq / spatial transcriptomics / single-cell multiomics
研究对象：物种、组织、疾病、处理条件
样本信息：donor/sample 数、组别、批次、细胞数或 spot 数
核心结论：你想表达的主张
证据：figure、统计结果、marker、DEG、pathway、验证实验
方法：软件、版本、QC、normalization、integration、统计检验
边界：哪些只是预测，哪些已经验证
目标产物：Results / Methods / figure plan / 审稿回复 / 风险审查 / 数据可用性
```

如果信息不完整也可以使用。skill 会先输出缺失项和风险，而不是停止。

---

## 输出格式

默认输出包含：

```text
Detected scope
- data_modality:
- analysis_claim:
- artifact:

Terminology ledger
| Canonical term | First-use definition | Variants seen | Decision |

Claim-evidence map
| Claim | Evidence tier | Support supplied | Missing input or boundary |

[Requested artifact]

Reviewer-risk flags

Missing inputs / placeholders

中文核对
```

短任务会压缩表格，但不会省略风险和缺失信息。

---

## 使用示例

### 示例 1：写 scRNA-seq Results

输入：

```text
帮我写 scRNA-seq Results。
我们在疾病组巨噬细胞中发现 IL1B、TNF、CXCL8 上调，所以想写它们驱动炎症进展。
目前有 UMAP、marker heatmap、疾病组 vs 对照组的 DEG 表。
```

skill 会：

- 识别为 `scrna-seq + differential-expression + results`
- 标记“驱动炎症进展”为过强因果表达
- 要求 donor/sample 数、统计方法、多重检验和验证证据
- 建议更稳妥表达，例如：

```text
Disease-associated macrophages showed increased expression of inflammatory
genes, including IL1B, TNF and CXCL8, consistent with an activated inflammatory
state.
```

### 示例 2：审稿人质疑细胞注释

输入：

```text
Reviewer says cluster 7 is not convincingly annotated as exhausted T cells.
Help me plan the response.
```

skill 会：

- 识别为 `scrna-seq + cell-annotation + response-strategy`
- 建议补充 marker evidence、reference atlas mapping、label-transfer confidence
- 如果证据不足，建议把 definitive label 改为 candidate state
- 不会编造 marker gene 或声称已经新增分析

### 示例 3：空间转录组 figure plan

输入：

```text
我要做一个 spatial transcriptomics figure，核心结论是肿瘤边缘存在免疫抑制 niche。
现在有组织切片图、空间 cluster、免疫细胞 marker 和 ligand-receptor 分析。
```

skill 会建议 panel 逻辑：

1. 组织区域和样本概览
2. spatial cluster 或 tissue region 定义
3. 免疫细胞状态空间分布
4. 跨 sample/section 的 niche enrichment 量化
5. ligand-receptor prediction 作为 hypothesis
6. 验证或限制说明

同时会提醒：ligand-receptor 预测不能写成 confirmed communication。

### 示例 4：Methods 检查

输入：

```text
帮我检查单细胞 Methods 是否完整。
我们用了 Seurat 做过滤、整合、聚类和注释，但 Methods 现在写得很短。
```

skill 会检查：

- Seurat 版本
- reference genome/build
- QC thresholds
- doublet / ambient RNA 处理
- normalization 和 integration 方法
- clustering resolution
- marker 或 reference atlas
- DEG test 和 multiple-testing correction
- accession、代码和 figure source data

### 示例 5：数据可用性清单

输入：

```text
帮我整理单细胞论文的数据可用性。
我们有 raw FASTQ、processed matrix、cell annotation、figure source data 和分析代码。
```

skill 会输出：

- raw data repository 需求，例如 SRA / ENA / DDBJ / controlled access
- processed matrix 和 metadata 存放建议
- cell annotation、embedding、spatial coordinates 的文件要求
- figure source data 要求
- code repository、release、environment 和 licence 清单
- 缺失 accession 或 DOI 时的占位说明

---

## 文件结构

```text
skills/nature-bioinformatics/
├── SKILL.md
├── manifest.yaml
├── README.md
├── Readme-zh.md
├── agents/
│   └── openai.yaml
├── static/
│   ├── core/
│   │   ├── output-format.md
│   │   ├── stance.md
│   │   └── workflow.md
│   └── fragments/
│       ├── analysis_claim/
│       ├── artifact/
│       └── data_modality/
├── references/
│   ├── claim-risk-checklist.md
│   ├── figure-archetypes.md
│   ├── methods-reporting-checklist.md
│   ├── prior-art-design-notes.md
│   ├── repository-accession-guide.md
│   └── reviewer-risk-rubric.md
└── evals/
    └── evals.json
```

---

## 验证

当前 skill 包含基础 eval case，覆盖：

- scRNA-seq Results claim 降级
- 细胞注释审稿回复
- 空间转录组 figure claim audit
- Methods reporting audit
- 生信论文 pre-submission risk audit

这些 eval 的目标不是检查唯一答案，而是检查 skill 是否遵守关键边界：

- 不编造 marker、accession、软件版本或统计结果
- 不把预测写成验证事实
- 能暴露 sample、batch、statistics、validation 等缺口
- 能区分 observation、inference、mechanism 和 clinical implication

---

## Roadmap

当前版本聚焦 scRNA-seq / spatial transcriptomics / single-cell multiomics。后续可以扩展：

- bulk RNA-seq
- ATAC-seq / multiome
- WGS / WES / variant calling
- proteomics / metabolomics
- microbiome
- survival modelling and clinical cohorts
- reproducible execution scripts for selected analysis checks

---

## 一句话总结

`nature-bioinformatics` 的核心不是“让生信论文更会说话”，而是让每一个生信 claim
都能被证据、方法、数据和审稿风险追踪到。
