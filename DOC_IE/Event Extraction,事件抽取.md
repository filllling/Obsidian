任务的目标是从给定文档中识别并抽取以下组成部分：

- **事件提及（Event Mention）**：指的是用于表述事件的短语或句子；
    
- **事件触发词（Event Trigger）**：通常是一个动词，用来标识事件的发生；
    
- **事件类型（Event Type）**：表示由数据集预定义的事件类别，例如“冲突-攻击（Conflict-Attack）”；
    
- **参数提及（Argument Mention）**：由与事件相关的实体组成，提供事件的更多细节信息，如“谁、什么、何时、何地以及如何发生”；
    
- **参数角色（Argument Role）**：表示实体在事件中所扮演的角色或类型；
    
- **事件记录（Event Record）**：是事件表中的一个条目，包含多个带有参数角色的参数。

例子：

> 输入：乔布斯于2001年发布了iPod。  
> 输出：
- 事件类型：产品发布
    
- 触发词：发布
    
- 参数：乔布斯（主体），iPod（客体），2001年（时间）