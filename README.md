# Ai-team — 数字团队管理 Skill

一个用于 [CodeBuddy Code](https://cnb.cool/codebuddy/codebuddy-code) 的 skill，通过管理员 **Claw** 协调一组专业员工 Agent，帮你派单、追踪任务、管理数字团队。

## 功能

| 子命令 | 说明 |
|--------|------|
| `dispatch <任务描述>` | 分析任务，匹配岗位，派单给合适的员工 Agent |
| `status` | 查看当前团队状态 |

## 使用方式

```
/ai-team dispatch 帮我修复登录页的 bug
/ai-team dispatch 写一个用户注册的单元测试
/ai-team status
```

## 派单逻辑

- **同步任务**（秒级完成）：直接在对话中执行
- **异步任务**（编码、安装等耗时操作）：后台启动 Agent，完成后自动汇报结果

## 支持岗位

- 程序员 — 编码、调试、重构
- 产品 — 需求分析、竞品调研、PRD 输出
- UI/UX — 交互方案、体验走查
- 测试 — 测试用例、Bug 挖掘、回归验证

## 安装

将本仓库的文件放入 CodeBuddy skills 目录：

```
~/.codebuddy/skills/ai-team/
```

## 文件结构

```
ai-team/
├── SKILL.md      # skill 入口，子命令路由
├── dispatch.md   # 派单流程定义
└── README.md     # 本文件
```
