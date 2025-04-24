## 🧠 一、什么是 TF-IDF？

**TF-IDF（Term Frequency - Inverse Document Frequency）** 是一种评估**一个词语对一个文档的重要性**的方法，尤其适用于文本挖掘和信息检索领域。

它由两部分组成：
- **TF（词频）**：衡量词语在文档中出现的频率。
- **IDF（逆文档频率）**：衡量词语在所有文档中具有多大的“区分力”。

---

### ✅ TF（Term Frequency）：

表示词在当前文档中出现的频率。
$$
TF(t,d)== \frac{f_{t,d}}{\sum_{k} f_{k,d}}​​
$$
其中：
- $f_{t,d}$词 $t$在文档 $d$中的出现次数
- 分母是文档中所有词的总数（也可以不归一化 )

---

### ✅ IDF（Inverse Document Frequency）：

反映词在**整个语料库**有多“稀有”，越稀有的重要性越高。
IDF(t)=log⁡(N1+nt)IDF(t) = \log \left( \frac{N}{1 + n_t} \right)IDF(t)=log(1+nt​N​)

其中：
- $N$：总文档数
- $n_t$​：包含词 $t$的文档数（加 1 避免除以 0）

---

### ✅ TF-IDF 计算公式：

$TF-IDF(t,d)=TF(t,d)×IDF(t)$

通俗理解：  
👉 一个词在当前文档中出现得多（TF 高）  
👉 同时在其他文档中出现得少（IDF 高）  
👉 那它在这个文档中就是**有区分力的关键词**