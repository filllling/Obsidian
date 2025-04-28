将它们大致分为三类：
- **纯 Encoder 模型**（例如 BERT），又称自编码 (auto-encoding) Transformer 模型；
- **纯 Decoder 模型**（例如 GPT），又称自回归 (auto-regressive) Transformer 模型；
- **Encoder-Decoder 模型**（例如 BART、T5），又称 Seq2Seq (sequence-to-sequence) Transformer 模型。

## Transformer 的结构

标准的 Transformer 模型主要由两个模块构成：
- **Encoder（左边）：** 负责理解输入文本，为每个输入构造对应的语义表示（语义特征）；
- **Decoder（右边）：** 负责生成输出，使用 Encoder 输出的语义表示结合其他输入来生成目标序列。
- **Encoder-Decoder 模型**或 **Seq2Seq 模型：** 适用于需要基于输入的生成式任务，例如翻译、摘要。

![[transformers.svg]]

**在 Encoder 中，由于翻译一个词语需要依赖于上下文，因此注意力层可以访问句子中的所有词语；而 Decoder 是顺序地进行解码，在生成每个词语时，注意力层只能访问前面已经生成的单词**


### Encoder 分支

纯 Encoder 模型只使用 Transformer 模型中的 Encoder 模块，也被称为自编码 (auto-encoding) 模型。在每个阶段，注意力层都可以访问到原始输入句子中的所有词语，即具有“双向 (Bi-directional)”注意力。

纯 Encoder 模型通常通过破坏给定的句子（例如随机遮盖其中的词语），然后让模型进行重构来进行预训练，最适合处理那些需要理解整个句子语义的任务，例如句子分类、命名实体识别（词语分类）、抽取式问答。

**BERT**
 1. **遮盖语言建模**
 2. **NSP** (下句预测)
 


### Decoder 分支

纯 Decoder 模型只使用 Transformer 模型中的 Decoder 模块。在每个阶段，对于给定的词语，注意力层只能访问句子中位于它之前的词语，即只能**迭代地基于已经生成的词语来逐个预测后面的词语**，因此也被称为自回归 (auto-regressive) 模型。

纯 Decoder 模型的预训练通常围绕着预测句子中下一个单词展开。纯 Decoder 模型适合处理那些**只涉及文本生成**的任务。