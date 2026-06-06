# nature-comsol-simulation

`nature-comsol-simulation` 是一个面向 COMSOL Multiphysics 与机械工程有限元仿真论文的 Nature-style skill。它可以帮助你写作和审查 Results、Methods、figure plan、审稿风险、审稿回复、可复现性清单、验证策略、网格收敛报告和综述思路。

它适用于固体力学、结构动力学、接触/摩擦、热-结构耦合、流固耦合、生物力学、断裂与材料仿真等 COMSOL 或有限元论文。它不是 COMSOL 求解器，也不是工程认证工具；它的作用是把你已经提供的模型证据转化为更严谨、更像论文的输出。

## 设计思路

这个 skill 的核心判断是：仿真论文最常见的问题不是语言不够高级，而是 claim 超出了模型能支持的范围。比如：

- 只有一张应力云图，却声称证明了失效机制。
- 没有网格收敛，却把局部峰值应力写成关键发现。
- 没有实验或解析解验证，却声称模型已经证明真实结构更优。
- 边界条件和载荷来源不清楚，却把仿真结果写成普适结论。
- 接触、摩擦、热边界、材料非线性没有报告，却写出过强机制解释。

因此它采用三条主轴来路由任务：

| 主轴 | 作用 | 示例 |
|---|---|---|
| `simulation_domain` | 识别仿真物理域 | solid mechanics、structural dynamics、contact/friction、thermal-mechanical、FSI、biomechanics、fracture/materials |
| `model_claim` | 识别论文要表达的模型结论 | stress-strain、deformation、modal frequency、contact pressure、thermal stress、parametric sensitivity、validation、optimization |
| `artifact` | 识别需要生成的论文产物 | Results、Methods、figure plan、review-risk audit、response strategy、reproducibility checklist、literature-review plan |

这样做的好处是：以后即使扩展到电磁场、声学、MEMS、电池、CFD、多孔介质或岩土仿真，也只需要增加新的 fragment，而不用推翻整个架构。

## 它会强制检查什么

| 模块 | 检查原则 |
|---|---|
| claim 边界 | 不把云图差异、参数扫描趋势或数值相关性直接写成机制证明 |
| 模型透明度 | 几何、材料、边界条件、接触、网格、求解器、单位和输出必须可追踪 |
| verification / validation | 区分数值模型验证、解析/基准问题验证和实验验证 |
| 网格收敛 | 检查监测量、网格层级、单元阶数、局部加密、收敛阈值和 claim 相关性 |
| 边界条件 | 把载荷、约束、对称性、接触、热输入、初始条件视为 claim 的前提 |
| 求解器报告 | 报告 study type、非线性设置、时间步、耦合策略、收敛准则和不稳定情况 |
| 可复现性 | 追踪 COMSOL 版本、physics interface、参数表、`.mph`、脚本、导出数据和 solver log |
| 审稿风险 | 输出 missing inputs 和 risk flags，而不是把不确定性包装成漂亮但过强的句子 |

## 吸收的 GitHub 经验

这个 skill 不是凭空写 prompt，而是吸收了若干公开项目的结构思想：

| 项目 | 吸收的亮点 |
|---|---|
| [`MPh-py/MPh`](https://github.com/MPh-py/MPh) | COMSOL 模型应当被视为可脚本化、可检查、可追踪参数和导出的对象 |
| [`wjc9011/COMSOL_Multiphysics_MCP`](https://github.com/wjc9011/COMSOL_Multiphysics_MCP) | AI 辅助 COMSOL 需要明确 GUI/session/tool 边界，不能掩盖模型状态不确定性 |
| [`svd-ai-lab/sim-cli`](https://github.com/svd-ai-lab/sim-cli) | 求解器命令、日志、插件和输出应该成为一等证据 |
| [`KratosMultiphysics/Kratos`](https://github.com/KratosMultiphysics/Kratos) | 多物理场仿真需要模块化领域划分和显式假设 |
| [`sfepy/sfepy`](https://github.com/sfepy/sfepy) | 可读的问题定义有助于审稿人理解方程、材料、区域和边界条件 |
| [`precice/precice`](https://github.com/precice/precice) | 耦合仿真需要报告界面映射、耦合收敛和求解器分区 |
| [`OpenRadioss/OpenRadioss`](https://github.com/OpenRadioss/OpenRadioss) | 动力学事件仿真需要报告能量平衡、接触设置、时间步稳定性和失效模式 |
| [`OpenSees/OpenSees`](https://github.com/OpenSees/OpenSees) | 结构仿真论文要暴露模型校准、约束、加载协议和验证数据 |
| [`FEniCS/dolfinx`](https://github.com/FEniCS/dolfinx) | 可复现仿真需要清晰的问题定义和版本化计算产物 |

详细调研笔记见 [`references/prior-art-design-notes.md`](references/prior-art-design-notes.md)。

## 使用方法

安装时请复制整个目录，而不是只复制 `SKILL.md`：

```text
skills/nature-comsol-simulation/
skills/_shared/
```

然后直接用自然语言调用：

```text
Use nature-comsol-simulation to audit this COMSOL solid-mechanics Results section.
```

```text
帮我检查这个 COMSOL 热-结构耦合模型的 Methods，重点看网格收敛、边界条件和审稿风险。
```

```text
Reviewer says our contact-pressure simulation does not prove wear reduction.
Please draft a response strategy and list the extra evidence we need.
```

## 最好提供哪些输入

| 类别 | 建议提供 |
|---|---|
| 模型设置 | COMSOL 版本、模块/physics interface、study type、几何、维度、对称性假设 |
| 材料 | 材料模型、参数、单位、参数来源、线性/非线性、各向异性、黏弹性或塑性 |
| 边界条件 | 载荷、约束、接触对、摩擦系数、热输入、初始条件、耦合界面 |
| 网格 | 单元类型/阶数、网格层级、局部加密、监测量、收敛阈值、最终单元数 |
| 求解器 | stationary/time-dependent/eigenfrequency、非线性设置、容差、时间步、segregated/fully coupled |
| 验证 | 解析解、基准算例、实验测量、文献 benchmark、校准数据、误差指标 |
| 输出 | 图、表、导出数值、参数扫描、敏感性分析、失败或不稳定案例 |
| 论文需求 | 目标期刊、章节、claim、figure panel、审稿意见或希望生成的产物 |

## 示例

```text
Use nature-comsol-simulation.

任务：
1. 审查我们的 COMSOL 应力和位移图是否支持“新型植入物机械性能更优”的 claim。
2. 写一段 Nature-style Results。
3. 列出 missing inputs 和 reviewer-risk flags。

已知证据：
- Solid Mechanics, stationary study.
- 两个设计：baseline 和 porous lattice。
- 输出：von Mises stress 和 displacement contours。
- 网格收敛：做了三档网格，但只监测 displacement。
- 验证：压缩实验计划中，尚未完成。
```

合理输出应当是：可以生成可用的 Results 文本，但必须降级“设计更优”“失效风险更低”等强 claim，直到补充 stress convergence 和实验验证。
