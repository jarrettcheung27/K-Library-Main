# Intro
*An **AI agent** is an autonomous software system that perceives its environment, interprets user-defined goals, and executes a sequence of actions—often structured as a workflow—to achieve those goals. It employs reasoning and decision-making capabilities to select appropriate tools and strategies, dynamically adjusting its actions based on feedback and environmental changes until the desired outcome is accomplished.*
Using tools.
## Agent Working Principal 
First, It will try understand the user's purpose using LLM, and extract some key information, select some proper tools. Second, it will execute the selected tools, input those key informations, and obtian a result from those tools. Finally, it construct an answer or take an action according to that result.

![[Pasted image 20251214160730.png|800]]


## ==Prerequisites for Learning Agent==
- Knowledge of machine learning frameworks like TensorFlow or PyTorch.
- Understanding of natural language processing (NLP) techniques.
- Experience with API integration and web development.
- Basic knowledge of data structures and algorithms.
- Langchain

# AI agent 产品
## Mauns
能够执行的操作基本都是基于Web前端的
初步来看，可交互性比较差，可能是我还不是很会用。
生成的内容基本还是基于为文本的，比如是传递信息类的文本网页，不过网页大部分也是文本吧，只是超文本罢了，基本的需求还是能够满足的。
但是网页的质量还是挺可观的，无论是网页的配色还是风格排版，UI设计的能力不比一般的专业人员差。
生成软件的Bug不知道多不多。
目前的使用费用还是比较贵的，比如一个初级的套餐需要40 dollors, 有大概8000积分，每做一个PPT大概需要500积分（大概3dollors 做一个ppt）
生成的速度还是比慢，比如生成一个20页的PPT大概需要20分钟，可能服务器的算力还是比较有限。
可以使用Knowlege来对交互方式进行规范，比如在每个重要节点再次确认一下要求，这个设置

### 能力边界
- 生成PPT
- 可以生成一个网站，用于指导与学习知识。
- 可以生成一个网站，DNA存储系统UI界面。
- 制作动画。
- 能不能叫他直接生成论文理论分析的曲线？

### 局限性
IDE只有一个VS code, 是不是就没办法操作其他的软件了，只局限在纯软件。
### 母公司是哪个？
蝴蝶效应，还没有上市。

### Konwledge 设置思路
- 完成一个每一个模块，就交付检查，测试。如果觉得合理，并且测试通过后，再进行下一个模块。
## Visual Studio Code Copilot
使用过程很流畅，而且基本上没有什么Bugs, 能够自己配置环境，编译，运行。
但是某些依赖的程序还是需要自己手动在浏览器上面下载。
所以人的作用就是想想怎么创造出一些产品的需求，然后准确地描述给AI，让它实现。

### 使用评价
- 2025/03
>还是需要序理解整个开发的流程和步骤是什么，去指导AI一步步地推进，否者AI就一直在迭代，生成代码Debug中不断地循环。
>你不知道它到那一步了，可能整个下午一点进度都没有。
- 2026/01


## Moltbot
### Questions
这几天很火的的Clawdbot（moltbot）是真的比传统的AI agent有很大的突破，还是说主要是营销手段？
>都有

之前的 agnet 不执行真实任务，运行在用户本地的主要瓶颈是什么？moltbot的核心突破点主要是哪里？
>1. 主要是安全问题，LLM没有获得足够的权限，而且存在幻觉等问题，有可能会出现不可逆的操作。所以之前的Agent, 比如像manus，主要是在云端的虚拟机内运行，操作。
>2. 主要突破点就是部分放权，不保证没有风险。

AI 能够直接接管网站和应用吗？怎么过人机检测这一关？

### 本地运行的配置要求
一般在16GB 内存的电脑上就能跑，最好在Linux 或者 Macos上部署，比较稳定。
好像主要是针对mac 优化，可能在WSL上运行有比较多的问题。
### 本地运行Agent的主流架构
云端大模型负责思考  
本地 agent 负责执行，所以只需要比较小参数的模型就行

### Moltbot 的核心设计
LLM（决策）  
↓  
Tool Router（明确可调用能力集合）  
↓  
本地执行模块（有限权限）
## 怎么用来商业化？
目前manus还不支持中文，所以对于没有掌握英文的人来说，还是有障碍。可以利用自己的英语能力和专业能力去提供服务。

# Frameworks to Creat Agents
- Smolagents
- LangGraph
- AutoFen

# Harness Engineering
# 相关技术
### MCP(Model Context Protocol)
### Human in the Loop
Let the agent ask for confirmation in each step of the workflow.
