<div align="center">

# SteeraMed-Toxicity: From Rare Toxicity Signals to Clinical Review
# SteeraMed-Toxicity：从罕见毒性信号到临床复核

**Long-Tail Pharmacovigilance: The Semaglutide–NAION Case and a Pilot Benchmark for Language Models**
**长尾药物警戒：司美格鲁肽–NAION 案例与语言模型试点基准**

**A module of the [SteeraMed](https://steeramed.com) framework**
**[SteeraMed](https://steeramed.com) 框架的模块**

[![DeepoMe](https://img.shields.io/badge/Organization-DeepoMe-blue)](https://steeramed.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Paper](https://img.shields.io/badge/Preprint-forthcoming-orange)]()

</div>

---

[English](#english) | [中文](#中文)

---

<a name="english"></a>

## Can language models rank the harms nobody listed?

Semaglutide became a safety concern after clinicians saw three patients with
sudden vision loss in one week — all taking the drug. The case exposes three
gaps in drug safety: a **representation gap** (individual vulnerability is
poorly captured), a **prediction gap** (short-lived, rare harms are hard to
forecast), and an **inference gap** (mixed evidence is not consistently turned
into testable clinical questions).

The paper proposes **long-tail pharmacovigilance** — a research program that
makes the tail (rare, unanticipated, or individual-specific harms) the primary
target of safety evaluation — and RARE-Bench, its first benchmark: can language
models rank uncommon, unexpected drug harms and flag signals for clinical
review? The longer-term
goal is to learn whether these rankings can help trial teams choose what to
monitor.

### Key findings (pilot, 60 drugs)

- **The long tail is where models matter**: the model beat every frequency-based
  baseline on long-tail label recall (3.8–4.3% versus 0–0.5%) — global
  frequency retrieved none, and no rarity-seeking reweighting did better
- **Honest baseline, split verdict**: a similar-drug label-transfer baseline
  retrieved far more of the tail (2.9%); the model's edge was **unresolved
  overall** (+0.013, 95% CI −0.018 to +0.039) but differed by neighborhood
  (+0.034 without same-class neighbors, −0.026 with; interaction p = 0.038) —
  **complements rather than rivals**
- **Generic prior dominates the head**: under target-only input, random genes
  scored the same as real targets overall (0.64 versus 0.61) — real targets
  carry a small, measurable signal **only on low-prevalence terms** (+0.010 to
  +0.014, both CIs above zero), and the model's edge appears class-level
  rather than drug-specific.
- **Free ranking missed the eye; directed questioning needs controls**: free
  ranking never mentioned the eye for semaglutide or tirzepatide. Eye-directed
  questioning returned eye terms for the case drugs and for two
  negative-control drugs alike; only the specific term NAION, named by one
  model, stood out. A directed sweep is informative only against the same
  question asked of control drugs.
- **Gold standards can disagree**: a gene-level probe found the best
  nomination method **reverses** when the validation frame changes from
  curated annotations to co-targeting — what counts as "related" is a framing
  choice

## Boundaries

This pilot shows that rare, unexpected adverse-effect ranking **can be
measured**. It does **not** show that a model could have predicted the
semaglutide–NAION signal, that paired molecular profiles improve prediction,
or that using the benchmark improves Phase II trial success. Those questions
require held-out tests on clinical decisions, followed by prospective
evaluation.

## Repository status

> **Status.** This repository currently provides the project overview and key
> findings. The frozen protocol with change and errata logs, sampling lists,
> raw model-output records, scoring and enrichment code, and reproduction
> scripts will be released here in stages: Stage 1 — with the preprint's
> public release (frozen protocol and sampling lists); Stage 2 — after
> community feedback (raw outputs, code, and reproduction scripts).
> Until release, materials are available from the author on reasonable request.

## Citation

```bibtex
@article{xiong2026toxicity,
  title={Long-Tail Pharmacovigilance: The Semaglutide--NAION Case and a Pilot
         Benchmark for Language Models},
  author={Xiong, Jianghui},
  journal={Preprints},
  year={2026},
  note={Preprint forthcoming. Code and frozen artifacts:
        https://github.com/DeepoMe/SteeraMed-Toxicity}
}
```

## Links

- **[SteeraMed](https://steeramed.com)** — the broader framework
- **[SteeraMed-RootMap](https://github.com/DeepoMe/SteeraMed-RootMap)** — companion dependency-map repository
- **[SteeraMed-MorbiMap](https://github.com/DeepoMe/SteeraMed-MorbiMap)** — companion candidate-ranking repository
- **[SteeraMed-bench](https://github.com/DeepoMe/SteeraMed-bench)** — companion benchmark repository
- **[DeepoMe](https://steeramed.com)** — the organization behind this work

## License

MIT (code) / CC BY 4.0 (data and documentation)

## Contact

Jianghui Xiong — [jianghui@deepome.com](mailto:jianghui@deepome.com)

---

<a name="中文"></a>

## 语言模型能排出"没人写进说明书"的 harms 吗？

司美格鲁肽成为安全关切，源于一周内三位突发视力丧失患者——都在用该药。
这一案例暴露药物安全的三个缺口：**表征缺口**（个体易感性刻画不足）、
**预测缺口**（罕见短程 harm 难以预测）、**推断缺口**（混杂证据未被一致
转化为可检验的临床问题）。

论文提出**长尾药物警戒**——让尾部（罕见、意外、个体特异的 harm）成为安全性评价首要目标的研究纲领——
并给出其第一个基准 RARE-Bench：语言模型能否对不常见、意外的药物
harm 排序，并为临床复核标记信号？

### 核心发现（试点，60 药）

- **长尾是模型的用武之地**：长尾标签召回 3.8–4.3% 对频率基线 0–0.5%——全局频率检索为零，稀有加权也无效
- **诚实的基线，分裂的判决**：同类药标签迁移基线长尾召回 2.9%；模型总体优势**未分辨**（+0.013，95% CI −0.018～+0.039）但按邻居结构分裂（无同类 +0.034/有同类 −0.026；交互 p = 0.038）——**互补而非竞争**
- **头部被通用先验主导**：仅靶点输入下，随机基因与真实靶点总分相同（0.64 对 0.61）——**真实靶点仅在低流行词上有微弱可测信号**（+0.010 至 +0.014，置信区间均不含 0），优势更像类别层面而非药物特异机制
- **自由排序漏掉眼部；定向询问须对照解读**：自由排序从不提及司美格鲁肽/替尔泊肽的眼部风险；定向眼部提问对病例药与两个负对照药同样返回眼词——只有 NAION 这个具体术语（单一模型命名）是突出的。定向扫描只有对照同一问题问对照药才有信息量
- **金标准会互相反对**：基因层探针发现，验证框架从策展注释换为共靶向时，最优提名方法**反转**——"相关"的定义本身是一种框架选择

## 边界

本试点证明罕见意外不良反应排序**可测量**。不能证明模型可预测司美格鲁肽-NAION
信号、配对分子谱可改进预测、或使用本基准可提高 II 期试验成功率——这些问题
需要对临床决策的留出检验与前瞻评估。

## 仓库状态

> **状态**：本仓库目前提供项目概述与主要发现。冻结协议（含变更与勘误日志）、抽样列表、原始模型输出、评分与富集代码及复现脚本将分阶段在此发布：阶段 1——预印本公开发布时（冻结协议与抽样列表）；阶段 2——社区反馈后（原始输出、代码与复现脚本）。发布前可向作者合理索取。

## 许可

MIT（代码）/ CC BY 4.0（数据与文档）

## 联系方式

熊江辉 — [jianghui@deepome.com](mailto:jianghui@deepome.com)

[DeepoMe](https://steeramed.com) · [SteeraMed](https://steeramed.com)
