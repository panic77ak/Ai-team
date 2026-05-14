# Dispatch — 派单流程

用户触发：`/ai-team dispatch <任务描述>`

任务描述：`$ARGUMENTS`

## 执行步骤

### Step 1：分析任务
分析任务描述，判断：
- 任务类型（编码/测试/分析/设计/其他）
- 匹配的岗位（当前可用：程序员、产品、UI/UX、测试）
- 执行模式：
  - **同步**：简单查询、秒级完成 → 直接执行
  - **异步**：编码、安装、耗时操作 → 后台 Agent

### Step 2：确认项目目录
询问或推断任务对应的项目目录：
- 如果用户在任务描述中提到了项目名/路径，直接使用
- 如果不明确，询问："这个任务对应哪个项目目录？"

### Step 3：派单

**同步任务**：直接在当前对话中完成，无需派出员工。

**异步任务**：使用 Agent 工具，参数如下：
```
subagent_type: general-purpose
run_in_background: true
description: <岗位名>执行<任务名>
prompt: |
  你是数字团队的程序员员工。
  
  任务：<具体任务描述>
  项目目录：<项目路径>
  验收标准：<完成判断依据>
  
  工作前请先：
  1. 读取 C:\Users\onechang\.codebuddy\agents\programmer\AGENT.md 了解你的工作规范
  2. 读取 C:\Users\onechang\.codebuddy\memories\ 中与任务相关的历史经验
  
  完成后：
  1. 通过 SendMessage（type: message, recipient: main）汇报结果
  2. 执行经验沉淀决策（见 AGENT.md 中的决策树）
```

### Step 4：回复老板
派出后立即回复：
```
已派单 ✅

员工：程序员
任务：<任务描述>
项目：<项目目录>
模式：后台异步执行

完成后会自动汇报结果。
```

### Step 5：收到汇报后转达
当收到员工 SendMessage 后，整理结果转达给老板，格式简洁，结论前置。
