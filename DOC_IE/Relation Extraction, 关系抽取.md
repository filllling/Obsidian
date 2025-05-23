
### ✅ **任务目标**

从文档中预测**实体之间的属性或关系类**

## 🧩 任务定义（文档级关系抽取 DocRE）

### 给定：

- 文档 D：由多个句子组成；
    
- 实体集合$V = \{e_i\}_{i=1}^​$：文档中提到的所有实体；
    
- 每个实体 $e_i$​：包含一个或多个**实体提及（Entity Mentions）**，即 $e_i = \{m_j\}_{j=1}^M$。
    

### 目标：

- 对任意实体对 $(e_s, e_o)$，其中 $s \neq o$，预测它们之间的**关系类型**；
    
- **多标签分类任务**：一个实体对可能存在多个关系。

## 📑 核心概念解释

|概念|含义|
|---|---|
|**实体（Entity）**|指具有特定语义的文本单位，如人物、地点、组织、时间、数字等|
|**实体提及（Entity Mention）**|在文本中出现的指代某个实体的短语。例如：“NYC” 和 “the big apple” 都指“New York City”|
|**句内关系（Intra-sentence Relation）**|实体对在**同一句话中**的关系，特征称为**局部特征（local features）**|
|**跨句关系（Inter-sentence Relation）**|实体对出现在**不同句子中**，关系需结合上下文推理，特征称为**全局特征（global features）**|


## 🧠 举例说明

> 文本：**“乔布斯创立了苹果公司。他于2001年推出了iPod。”**

- 实体：乔布斯、苹果公司、iPod、2001年
    
- 实体提及：“他” → 乔布斯（共指）
    
- 跨句关系（Inter-sentence）：乔布斯 与 iPod 的“推出”关系