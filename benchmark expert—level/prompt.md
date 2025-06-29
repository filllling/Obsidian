## 🧩 代码结构与核心功能总结

### ✅ 类名：`PromptTemplates`

用于根据所用数据集和模型类型，自动生成不同类型的提示词模板，适配 Zero-Shot AO / CoT 和 Few-Shot 场景。

---

## 🎯 主要功能说明

### 1️⃣ 系统角色定义（System Role）

| 类型                         | 默认值                                                  | 数据集特化                                                      | 模型特化 |
| -------------------------- | ---------------------------------------------------- | ---------------------------------------------------------- | ---- |
| `zero_shot_system_role`    | "You are a helpful assistant."                       | 医学类数据集：设为 `"You are a helpful medical assistant."`         |      |
| `zero_shot_ao_system_role` | "Please answer only."                                | 若模型名包含 `"qvq"`，设为 `"You are a helpful medical assistant."` |      |
| `few_shot_system_role`     | "Follow the given examples and answer the question." | 固定                                                         |      |

---

### 2️⃣ Trigger 句定义（Answer Trigger）

用于指导模型输出答案的固定句式（通常出现在 `A:` 后）。

#### 💡 Zero-Shot AO Trigger：

- 普通数据集：  
    `"Among A through D, the answer is"`
    
- `medxpertqa` 类数据集：  
    `"Among {start} through {end}, the answer is"`
    

#### 💡 Zero-Shot CoT Trigger：

- 默认：  
    `"Therefore, among A through D, the answer is"`
    
- `medxpertqa`：  
    `"Therefore, among {start} through {end}, the answer is"`
    
- DeepSeek Reasoner 模型：  
    加入 `"Put your final answer within \boxed{}."` 前缀
    
- QVQ 模型：  
    CoT Trigger 替换为 `"Let's think step by step."`
    

---

### 3️⃣ Prompt 模板定义（最终构造）

|Prompt 名称|模板内容|
|---|---|
|`zero_shot_ao_prompt`|`Q: {question}\nA: {trigger}`|
|`zero_shot_cot_prompt`|`Q: {question}\nA: Let's think step by step.`（触发 CoT 模式）|
|`few_shot_prompt`|`Q: {question}\nA:`（用于 few-shot 模板组装）|
|`few_shot_trigger`|`The answer is`（用于 few-shot 示例中指示最终答案）|

---

## 🧠 总结表格：按模式整理

|模式|Prompt 模板|特点说明|
|---|---|---|
|Zero-Shot AO|`Q: {{question}}\nA: {{trigger}}`|简短回答；用于快速选项预测|
|Zero-Shot CoT|`Q: {{question}}\nA: Let's think step by step.`|启动推理链；再加 `trigger` 输出最终选项|
|Few-Shot|多个 `Q: ... A: ... The answer is ...` 示例拼接|适用于引导模型模仿推理风格，训练阶段/分析用|