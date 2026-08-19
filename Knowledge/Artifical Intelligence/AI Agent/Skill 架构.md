# AI Agent Skill 架构介绍

## Skill 和 instruction 的区别什么？
Skill 和 instruction 都是用于指导 AI 代理执行特定任务的工具，但它们在结构和用途上有所不同。
- Skill：Skill 是一种结构化的指令集，通常包含元数据（如名称、描述和触发条件）以及详细的执行步骤。Skill 更加模块化，适用于需要重复使用或共享的任务。Skill 通常以独立文件的形式存在，便于管理和维护。
- Instruction：Instruction 通常是更为简洁的文本指令，直接告诉 AI 代理该做什么。Instruction 更加灵活，适用于临时或一次性的任务。Instruction 通常嵌入在对话或任务描述中，而不是作为独立的文件存在。



# Skill.md 模板
Skill 模板的主要内容包括以下几个部分：
- Skill 的元数据（name, description, triggers）：
  - name: Skill 的唯一标识符，通常为小写字母和短横线组成的字符串。
  - description: 对 Skill 功能的简要描述，帮助用户理解该 Skill 的用途。
  - triggers: 触发该 Skill 的关键词或短语列表，用户输入这些关键词时会激活该 Skill。
- Skill 的标题
- 使用场景说明
- 前置条件
- 执行步骤
```md
---  
name: password-reset  
description: Reset user password with security verification  
triggers:  
 - "reset password"  
 - "forgot password"  
 - "can't login"  
---  
  
# Password Reset Skill  
  
## When to use  
Use this skill when the user needs to reset their password.  
  
## Prerequisites  
- User must provide email or username  
- User must pass security verification  
  
## Execution steps  
1. Verify user identity  
2. Send reset link to registered email  
3. Confirm password change
```