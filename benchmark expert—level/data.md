### 1. MedXpertQA 数据集 (核心数据集)

- medxpertqa_text_input.jsonl (4.51MB, 2000条)

- 纯文本医学问答数据

- 包含：问题、选项、答案、医学任务类型、身体系统、问题类型

- 字段：id, question, options, label, medical_task, body_system, **question_type**

- medxpertqa_mm_input.jsonl (2.2MB)

- 多模态医学问答数据（文本+图像）

- 在文本版本基础上增加了images字段

- 包含医学图像，需要结合图像和文本进行推理

### 2. MedXpertQA 采样数据集 (测试用)

- medxpertqa_sampled_text_input.jsonl (0.44MB, 244条)

- 从完整MedXpertQA文本数据中采样的子集

- 用于快速测试和验证

- medxpertqa_sampled_mm_input.jsonl (0.22MB, 199条)

- 从完整MedXpertQA多模态数据中采样的子集

- 用于快速测试多模态功能

### 3. 其他医学问答数据集 (对比基准)

#### MedQA (1.15MB, 1273条)

- 美国医学执照考试(USMLE)风格的问题

- 结构简单：id, question, label

- 主要用于评估模型在标准医学考试上的表现

#### MedMCQA (2.48MB, 4183条)

- 印度医学入学考试(MCQ)风格的问题

- 包含：id, question, label, label_rationale, subject_name, topic_name

- 提供答案解释和学科分类信息

#### MMLU Medical (0.52MB, 1089条)

- 多任务语言理解(MMLU)的医学子集

- 结构：question, label, subject

- 涵盖多个医学学科，如解剖学、生理学等

## 主要区别总结

1. 模态类型：

- 纯文本：MedQA, MedMCQA, MMLU Medical, MedXpertQA文本版

- 多模态：MedXpertQA多模态版（文本+图像）

1. 数据规模：

- 完整版：MedXpertQA (2000条)，MedMCQA (4183条)

- 采样版：MedXpertQA采样版 (200-250条)

- 其他：MedQA (1273条)，MMLU Medical (1089条)

1. 问题复杂度：

- MedXpertQA：最复杂，包含详细的医学任务分类和身体系统信息

- MedMCQA：中等复杂度，包含学科和主题分类

- MedQA/MMLU：相对简单，主要是问题和答案

1. 应用场景：

- MedXpertQA：专门为医学多模态问答设计，支持图像理解

- 其他数据集：主要用于文本问答能力评估