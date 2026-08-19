# 部署环境
- 可以试试云电脑部署（但是费用比较高贵 300块/月）
- 买24G/512GB 部署本地LLM模型
- 买24G/512GB 部署云端LLM模型（30/mon，但是性能不算很顶顶尖）, 平时可以作为个人电脑使用。
- 买16G/256GB 部署云端LLM模型。
# 使用场景
- 完成一些信息收集和调研（平时也没有很多需要调研的地方呀）
- 写毕业论文
	- 补充文献确实可以自我校验
- 将工作流中的一些（基于文本处理的）分支，外包给Agent。
- 将过往的一些工作流喂给AI, 实现自动化（看看什么格式比较合适）
- 当作一个个人助理，安排日程？（这个可以做到，感觉与macos的生态兼容性还是比较好的）
- 可以让它自己写 SKill 或者找 MCP 来提高工作流的效率，所以会越用越智能。
- 可以正常创建 Excel 表格，而且布局还很智能。

# 性能

# 安装流程
## 安装前准备（确保顺利运行）

### **确认系统版本与硬件**
    
- macOS Sequoia 15.7.3（支持最新 Homebrew、Node.js、Docker 等）
	
- Apple Silicon（M系列）可直接安装和运行多数工具
        
### **安装 Xcode Command Line Tools（如果未装过）**  
打开终端运行：

xcode-select --install

等待安装完毕。
    
### **安装 Node.js（推荐 Node 18+）**  
OpenClaw 依赖 Node.js 18 以上环境。你可以用 Homebrew 安装：

brew install node@18

确保 `node -v` 输出的是 18 以上版本。
    
### **获取 AI 模型 API Key**
- OpenClaw 本身是 agent 框架，它需要后端 LLM（如 OpenAI / Claude / Mixflow / AskCodi 等）来推理。
	
#### 1. **使用国内中转平台调用模型：**（连接不太成功）
baseURL: 'https://api.laozhang.ai/v1'
api-key：'sk-vYpyqCw0TH3LDtndB499E68a45Fd4a8fB93d35259462A66a'
model: 'gemini-2.5-pro'
"api": "openai-compatible",
**接入配置方法：**
``` node.js
// 安装：npm install openai
import OpenAI from 'openai';

// 初始化客户端
const client = new OpenAI({
  apiKey: process.env.LAOZHANG_API_KEY || '您的API密钥',
  baseURL: 'https://api.laozhang.ai/v1'
});

// 流式输出示例（实时响应）
async function streamChat() {
  const stream = await client.chat.completions.create({
    model: 'gemini-2.5-pro',
    messages: [
      { role: 'system', content: '你是一个有帮助的AI助手' },
      { role: 'user', content: '请写一个简单的React组件' }
    ],
    stream: true,  // 启用流式输出
    temperature: 0.7
  });

  // 逐字输出
  for await (const chunk of stream) {
    process.stdout.write(chunk.choices[0]?.delta?.content || '');
  }
}

// 并发调用多个模型
async function compareModels(prompt) {
  const models = ['gpt-4.1', 'claude-sonnet-4-20250514', 'gemini-2.5-pro'];

  const promises = models.map(model =>
    client.chat.completions.create({
      model,
      messages: [{ role: 'user', content: prompt }],
      max_tokens: 100
    })
  );

  const results = await Promise.all(promises);
  results.forEach((result, index) => {
    console.log(`\n${models[index]}:\n${result.choices[0].message.content}`);
  });
}

// 运行示例
streamChat().catch(console.error);
```

#### 2. ==使用M4 部署本地模型 ollama==
不知道性能怎么样

#### 3. 使用minimax 按月订阅
[配置方法](https://platform.minimaxi.com/docs/coding-plan/openclaw)

### VPN 安装教程
[安装教程](https://user2.bby012.com/#/knowledge)

需要开启tun才能实现全局代理（终端也走代理）(需要以管理员身份运行)

## 全自动安装（推荐初学者）
*需要先连接VPN，确保全部资源可以访问。*

OpenClaw 官方提供一键安装脚本，能自动安装依赖及初始化配置：

`curl -fsSL https://openclaw.ai/install.sh | bash`

## 启动 OpenClaw
`openclaw tui` 进入UI 界面，看看 agent 能否正常回消息。
按照指导配置LLM模型及channel
## 通过 Telegram 与 agent 对话
**注册手机号：**
国家：+1 号码：2177647181 
**接码地址**  
https://api2.hwzh.xyz/AbX9bcUR2Z3453/abde2078-ca68-4788-ae10-1a2257aa4d0c/GetHTML 
原两步验证(密码)：112233

1. 找 BotFather — 在 Telegram 搜索 @BotFather，发 /newbot 创建机器人，获取     
 token                                                                          
 2. 配置 OpenClaw — 在 ~/.openclaw/openclaw.json 里添加 botToken                
 3. 启动 Gateway + 配对 — 运行 openclaw gateway
 4. 运行 openclaw pairing list telegram，会显示类似这样的输出：                 
```
     telegram:                                           
     - code: ABC123XYZ                                  
       from: 123456789                                   
       updatedAt: 2026-02-25T15:10:00Z 
```

**Telegram bot API：**
Use this token to access the HTTP API:
`8766901681:AAE5p2mswL4xgToltaHqOTvmMXXgfH8ytCw`

# 拓展工具
## Brave Serach
增强Agent 的搜索能力
API Key:  `507a1fc039dca7cd037d91e4a5f34c3b1b3fe4db55311847373b0f3af07fc8de`
