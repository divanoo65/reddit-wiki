---
title: Chinchilla 规模化定律
type: concept
tags:
  - AI
  - LLM
  - ScalingLaws
  - MachineLearning
summary: Chinchilla 规模化定律是由 DeepMind 提出的关于大语言模型训练参数量与数据量之间最优比例的经验法则，指出在计算预算有限的情况下，模型参数量与训练数据量应按比例同等增加。
sources:
  - raw/notebooklm-analysis/llm-weekly-discussion.md
created: 2024-05-22
updated: 2024-05-22
layer: L1
confidence: high
reasoning: 直接从NotebookLM思维导图中提取的概念。
---

# Chinchilla 规模化定律

### 概念定义

Chinchilla 规模化定律（Chinchilla Scaling Laws）是由 DeepMind 在 2022 年发表的论文《Training Compute-Optimal Large Language Models》中提出的核心理论。该定律的核心观点在于，对于给定的计算预算（Compute Budget），存在一个最优的模型参数量与训练数据量（Token 数）的比例。研究发现，此前许多模型（如 GPT-3）在训练时并未达到计算最优，即模型参数量过大而训练数据量不足。Chinchilla 定律建议，为了获得最佳性能，模型参数量与训练 Token 数应该按比例同步增加，即每增加一倍的参数量，就应增加一倍的训练数据量。这一发现打破了“模型越大越好”的盲目追求，强调了数据规模在模型训练中的决定性作用。

### 技术细节

在 Chinchilla 框架下，模型性能的提升不再仅仅依赖于单纯增加参数规模，而是通过精确的计算资源分配来实现。其核心技术细节包括：
1. **计算最优性（Compute-Optimality）：** 通过对不同规模的模型进行大量实验，拟合出损失函数（Loss）与计算量、参数量、数据量之间的幂律关系。
2. **比例平衡：** 实验表明，对于计算最优模型，参数量与 Token 数的比例大致为 1:20，即每个参数对应约 20 个 Token 的训练数据。
3. **当前挑战：** 随着模型规模进入 GPT-4 及以上量级，研究界开始质疑该定律的普适性。当前观点认为，在超大规模模型中，单纯的 Token 数量增长已不足以维持性能提升，数据质量（Data Quality）和合成数据（Synthetic Data）的引入变得比单纯的规模扩张更为关键。

### 应用场景

1. **模型训练规划：** 在预训练阶段，开发者利用该定律估算所需的计算资源（如 GPU 小时数）和数据集规模，以确保在有限预算下达到最优模型性能。
2. **架构设计与优化：** 帮助研究人员确定模型架构的宽度与深度，避免因参数分配不当导致的计算资源浪费。
3. **推理时扩展研究：** 随着 [[推理时计算]] 的兴起，研究者正在探索是否可以将 Chinchilla 的逻辑从“训练时扩展”迁移到“推理时扩展”，例如通过增加 [[思考代币]] 的数量来提升模型在推理阶段的性能，这被视为对传统规模化定律的现代演进。

### 相关链接

- [[规模化定律]]
- [[合成数据]]
- [[推理时计算]]
- [[r/MachineLearning — 每周讨论：大语言模型规模化定律]]