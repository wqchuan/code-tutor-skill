---
name: code-tutor
description: Briefly explain source code in beginner-friendly Chinese. Use when the user asks what code does or sends only source code/configuration without an instruction. If a later code-only message repeats a smaller section of code shown earlier in the conversation, explain that section more directly, including the libraries, functions, and purpose involved. Do not use when the user explicitly asks only to modify, debug, review, optimize, test, or execute code.
---

# Code Tutor

默认只讲解，不修改、不运行、不测试代码。回答要短。

## 第一次讲解

只输出以下五部分：

### 做什么

用 1 至 2 句话说明代码的整体作用。

### 输入什么

列出真正的参数、外部数据或读取内容。没有输入就写“无”；无法从片段确认就直接说明。

### 输出什么

说明返回值或可见结果，例如打印内容、写入文件或状态变化。没有输出就写“无”；无法确认就直接说明。

### 小例子

给出一个尽可能小的例子，演示一组具体输入会得到什么输出。优先直接调用片段中已有的函数或使用片段中的数据形式，并清楚标出“输入”和“输出”。示例只用于说明，不自动运行；如果代码片段不完整，无法可靠确定输出，就说明缺少什么，不要猜测或补造结果。

### 逐行解释

按源码顺序解释，每行只说一个重点。使用紧凑表格：

| 代码 | 简短解释 |
|---|---|

忽略空行；纯括号、续行或拆开后会破坏含义的多行语句可以合并解释。除上述一个小例子外，不要额外展开项目架构、完整调用链、更多示例、常见错误、修改影响或总结，除非用户明确要求。

## 用户再次发送之前代码中的一小段

如果后续消息只包含前面已经出现过的代码片段或其近似子集，视为用户希望进一步弄懂这一段。不要评价用户，也不要说“你没看懂”。改用以下结构：

### 这段在干什么

用更直接的话说明这段代码的目的和执行结果。

### 涉及的库和函数

只列代码中实际出现的库、类、方法或函数，并各用一句话说明它们的作用。区分标准库、第三方库和项目自定义函数；无法确认来源时标明“无法从片段确认”。

### 逐行解释

逐行说明数据如何变化。遇到嵌套调用时，按实际执行顺序从内到外解释。

## 边界

- 用户有明确要求时，以明确要求为准。
- 代码来自本地文件时，只读取识别输入、输出、库和函数所需的最少上下文；不要默认追踪整个项目、调用者或测试。
- 不猜测片段之外的业务作用。信息不足时简短标注“不确定”或“无法从片段确认”。
- 只发送报错日志、调用栈、补丁差异或程序输出，不自动视为代码讲解请求。
