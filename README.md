# Ai-team — 数字团队管理 Skill

一套基于 Markdown 的 AI 团队调度方案，通过管理员 **Claw** 协调一组专业员工 Agent，帮你派单、追踪任务、管理数字团队。

适用于任何支持自定义 slash command / skill 的 AI 编程工具，如 Claude、Cursor、CodeBuddy、Continue 等。

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

将本仓库文件放入你所用工具对应的 skill/command 目录，例如：

| 工具 | 目录 |
|------|------|
| CodeBuddy Code | `~/.codebuddy/skills/ai-team/` |
| Cursor | `.cursor/rules/` 或自定义 slash command 目录 |
| Continue | `.continue/prompts/` |

其他工具参考各自文档，将 `.md` 文件注册为自定义命令即可。

## 文件结构

```
ai-team/
├── SKILL.md      # skill 入口，子命令路由
├── dispatch.md   # 派单流程定义
└── README.md     # 本文件
```
