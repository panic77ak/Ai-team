---
name: ai-team
description: 数字团队管理系统。用于派单、查看团队状态、管理员工、自我迭代。子命令：dispatch（派单）、status（团队状态）、learn（流程迭代）。
---

# AI Team 管理系统

数字团队管理 skill。通过管理员 Claw 协调一组专业员工 Agent 完成工作。

## 使用方式

```
/ai-team dispatch <任务描述>    — 派一个任务给合适的员工
/ai-team status                — 查看当前团队状态
/ai-team learn <问题或建议>    — 改进 skill 自身的派单流程
```

## 执行逻辑

根据用户输入的子命令，加载对应的 skill 文件：

- `dispatch` → 执行 @dispatch.md 的派单流程
- `status` → 激活管理员 Claw 汇报当前团队状态
- `learn` → 执行 @learn.md 的 skill 自我迭代流程

**用户输入**：`$ARGUMENTS`

请分析上面的参数，识别子命令（dispatch / status / learn），然后按对应流程执行。

如果没有子命令或参数不清晰，列出可用命令并询问用户。
