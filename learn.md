# Learn — Skill 自我迭代流程

用户触发：`/ai-team learn <问题描述或建议>`

或由管理员 Claw 在收到员工"流程建议"汇报后自动触发。

输入：`$ARGUMENTS`

---

## 执行步骤

### Step 1：读取现有流程

读取以下文件，了解当前 skill 状态：
- `dispatch.md` — 当前派单流程
- `SKILL.md` — 当前子命令路由

### Step 2：分析问题

判断输入属于哪类：

| 类型 | 处理方式 |
|------|----------|
| 派单流程有缺陷 | 修改 dispatch.md |
| 岗位匹配不准 | 修改 dispatch.md 的 Step 1 判断逻辑 |
| 缺少新子命令 | 修改 SKILL.md，新增子命令 + 对应 .md 文件 |
| Agent prompt 不够清晰 | 修改 dispatch.md 中的 prompt 模板 |

### Step 3：生成变更 diff 预览

以如下格式展示给用户确认：

```
--- 当前版本
+++ 建议修改

文件：dispatch.md / SKILL.md
位置：<具体章节>

- <删除的内容>
+ <新增的内容>

变更原因：<为什么要改>
```

### Step 4：等待用户确认

- 用户确认 → 执行 Step 5
- 用户拒绝/修改意见 → 根据反馈调整 diff，重回 Step 3

### Step 5：写回文件

按确认的 diff 修改对应文件，然后：
1. 追加变更记录到 `CHANGELOG.md`（如不存在则创建）
2. 格式：`## YYYY-MM-DD\n- <变更描述>`
3. 回复用户：`流程已更新，下次会话生效。`

### Step 6：推送到 GitHub（可选）

询问用户是否需要将更新推送到 GitHub 仓库，确认后执行 git commit + push。
