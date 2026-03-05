# AGENTS.md — Codex Agent 工作指南

本文件定义 Codex Agent 在此仓库中的工作范围、维护规则和问题检测标准。

---

## 项目简介

`slots_animation_prompt_skill_v1_claude.md` 是核心文件。这是一个给 Claude 使用的 Skill 指令文件，用于指导 AI 生成 Slots 游戏动效提示词。

**不要把它当作代码文件处理。** 它的内容是结构化的自然语言指令。

---

## Codex 工作范围

### ✅ 允许的任务

| 任务类型 | 说明 |
|---------|------|
| 版本维护 | 根据 Issue 修改 Skill 文件内容，更新 CLAUDE.md 优化历史表格 |
| 问题检测 | 检查 Skill 文件的结构完整性、流程一致性、模板覆盖缺口 |
| 文档同步 | 确保 README.md 版本记录与 CLAUDE.md 优化历史保持一致 |
| Issue 处理 | 根据 Issue 标签执行对应修复流程 |

### ❌ 禁止的操作

- 不得修改 MANDATORY EXECUTION RULES 的强制约束逻辑
- 不得删除任何现有模板（只能新增或修改）
- 不得更改输出格式结构（Vidu / Seedance 双工具中文输出格式）
- 不得自行合并 PR，需等待用户确认

---

## Issue 标签与处理流程

### 标签定义

| 标签 | 触发条件 | 处理方式 |
|------|---------|---------|
| `optimization-idea` | 用户记录的优化想法，token 不足时暂存 | **仅记录，不主动修复**；等待用户在 Claude 会话中处理 |
| `output-quality` | 生成的提示词效果不符合预期 | 定位对应模板或规则，提出修改方案 |
| `ux-flow` | 流程步骤有歧义或缺口 | 检查 STEP 1–3 流程，修复问题步骤 |
| `tool-adaptation` | Vidu Q2 或 Seedance 2.0 有新特性/参数变更 | 更新对应工具的模板和词汇 |
| `compliance` | 合规词汇需要更新或调整 | 修改 COMPLIANCE / WORDING RULES 章节 |
| `new-style` | 需要新增美术风格类别 | 在 Style Detection 表和 STYLE MOTION PROFILES 中添加新行 |
| `template-gap` | 某场景缺少对应模板 | 新增模板，遵循现有模板结构 |
| `bug` | Skill 流程存在逻辑错误 | 定位错误位置，修复并说明原因 |

### optimization-idea 处理规则

`optimization-idea` 标签的 Issue 是用户在 Claude token 不足时的**跨会话记忆**，Codex 的职责是：

1. **帮助用户结构化记录**想法，确保信息完整（方向、背景、期望效果、优先级）
2. **不要自行修改** `slots_animation_prompt_skill_v1_claude.md`
3. **添加评论**总结该 Issue 与现有 Skill 的关联位置，方便 Claude 下次快速定位
4. Issue 由 Claude 在新会话中处理后，将状态标记为 `closed` 并注明 commit hash

---

## 版本命名规则

- 主版本格式：`v{major} 优化{n}`（例：v1 优化10）
- 每次修改后在 `CLAUDE.md` 的「已知优化历史」表格末尾追加一行
- commit message 格式：`fix: [标签] 简述修改内容` 或 `feat: [标签] 简述新增内容`

---

## 问题检测清单

Codex 定期检查以下项目，如发现问题自动创建 Issue：

### 结构完整性
- [ ] 所有场景（A/B/C）的首尾帧模式说明是否统一指向 STEP 1.2
- [ ] STYLE MOTION PROFILES 的风格数量是否与 Style Detection 表一致
- [ ] 所有 Seedance 模板开头是否包含 @图片1 引用（必选项）
- [ ] MANDATORY EXECUTION RULES 的步骤列表是否覆盖所有配置步骤

### 模板覆盖
- [ ] Template A2 的意图分支（A/B/C/D）是否与 STEP 1.2 的意图选项一致
- [ ] 所有模板是否同时存在 Vidu Q2 版和 Seedance 2.0 版

### 一致性
- [ ] README.md 版本表格是否与 CLAUDE.md 优化历史同步
- [ ] IMPORTANT RULES 末尾规则是否与 MANDATORY EXECUTION RULES 不矛盾

---

## 修改 Skill 文件的注意事项

1. **保持模板结构不变** — 只修改内容，不改变段落标题和层级
2. **工具版同步修改** — 修改任何模板时，Vidu Q2 版和 Seedance 2.0 版必须同时更新
3. **强度词汇一致** — 修改动效词汇时，检查 INTENSITY MAPPING 和 STYLE MOTION PROFILES 是否需要联动更新
4. **首尾帧意图同步** — 修改 STEP 1.2 时，同步检查 Template A2 的意图分支描述
