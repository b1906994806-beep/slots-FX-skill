# Slots Animation Prompt Skill — 项目配置

## 项目概述

本项目基于 BMAD 框架，开发一套 **Slots 游戏动效 AI 提示词生成 Skill**。
用户上传静态图片，Skill 自动分析图像内容并生成适用于 AI 视频工具的动效提示词。

**目标工具：** Vidu Q2 + Seedance 2.0（双工具中文输出）

---

## 关键文件路径

| 文件 | 说明 |
|------|------|
| `C:\Users\admin\Downloads\slots_animation_prompt_skill_v1_claude.md` | **主 Skill 文件**（当前最新版本，优先读取此文件） |
| `C:\Users\admin\Downloads\lobby_icon_animation_skill_v3_claude.md` | 参考基线：Lobby 大厅图标动效 Skill（已验证） |
| `C:\_bmad-output\brainstorming\brainstorming-session-2026-03-04.md` | 完整设计文档（头脑风暴成果，包含所有设计决策） |

> 读取路径：`C:\Users\admin\Claude code test\bmad-workspace\_bmad-output\brainstorming\brainstorming-session-2026-03-04.md`

---

## Skill 覆盖场景

```
A. 图标动效（Reel Symbols）
   └── 低级 / 高级 / Wild / Scatter / Bonus × 待机 / 落定 / 中奖 / 期待抖动

B. Free Game 弹窗 & 转场
   └── 触发弹窗入场 / 待机 / 转场进入 / 结算弹窗入场 / 待机 / 转场退出

C. 加载页开场动画
   └── 单次播放 / 循环播放
```

---

## 核心设计决策（勿随意更改）

1. **输入**：用户只上传一张静态图片，无需额外描述（加载页场景需简述主体）
2. **首尾帧模式**：所有场景统一上传一张图 → Skill 询问首帧或尾帧
3. **输出**：每次同时生成 Vidu Q2 + Seedance 2.0 两套，纯中文输出，共两个版本
4. **强度体系**：三级强度映射（一级=Small/Subtle，二级=Medium/Moderate，三级=Large/Dynamic）
5. **主体动作规则**：必须按「主体专项动作规则库」逐部位描述，禁止使用模糊表达
6. **合规过滤**：所有输出前必须过滤禁用词，使用中性替换词
7. **约束段落**：
   - Seedance 输出末尾必须附加显式约束语
   - Vidu 输出末尾必须标注 motion amplitude 参数

---

## 两个工具的提示词差异

| 维度 | Vidu Q2 | Seedance 2.0 |
|------|---------|-------------|
| 结构 | 主体+动作+场景+风格+构图 | 主体+动作+镜头+场景+风格+约束 |
| 字数 | 灵活 | 控制在 30–200 词 |
| 强度控制 | 小幅动态/中等动态/大动态（官方中文触发词） | Slow/Gentle/Dynamic 等语言词 |
| 约束语 | 可选 | 必须显式写出 |
| 参考图引用 | `@Image1` / `@subject(...)` 标签 | **`@图片1` 必选项**，提示词开头必须标注 |

---

## 已知优化历史

| 版本 | 优化内容 |
|------|---------|
| v1 初版 | 完整框架，覆盖三场景，双工具双语输出 |
| v1 优化1 | 主体动作规则细化（逐部位描述，禁止模糊表达） |
| v1 优化2 | 图层识别深化（动物/角色/道具各自子层拆解） |
| v1 优化3 | 新增 Template A2（图标首尾帧专用双语模板） |
| v1 优化4 | 所有模板补充中文版（全部双语化） |
| v1 优化5 | 首尾帧模式统一为「上传一张图 → 询问首/尾」 |
| v1 优化6 | 首尾帧流程重设计：意图优先4选项（让它动/还原/回到原位/从A到B），首尾帧为默认模式，删除各模板重复说明 |
| v1 优化7 | Seedance 全模板加语境锚定句（应对LLM全文过滤），新增叙事版模板（Template A）及专属词汇库 |
| v1 优化8 | 新增风格识别层（S1–S9，Slots专属9种美术风格）及 STYLE MOTION PROFILES 章节，风格词汇自动融入提示词 |
| v1 优化9 | 新增 MANDATORY EXECUTION RULES，修复 AI 跳过配置步骤的根本原因：禁止自动填充、各步骤加🛑守门标记、澄清"自动分析"仅指图像内容 |

---

## 继续优化时的工作方式

1. **先读取主 Skill 文件**：`slots_animation_prompt_skill_v1_claude.md`
2. **描述具体问题**，Claude 定位需修改的段落后直接 Edit
3. **测试方式**：上传实际图片运行 Skill，观察输出质量
4. **版本记录**：每次优化后在本文件「已知优化历史」表格中追加记录

---

## 沟通偏好

- 使用**中文**回答
- 提问方式：一问一答，逐步确认
- 输出风格：简洁直接，优先用表格或代码块呈现结构化内容
