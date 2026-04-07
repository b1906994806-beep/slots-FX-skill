# Slots FX Skill

AI 视频工具提示词生成 Skill，用于 Slots 游戏动效素材制作。

## 项目目标

用户上传静态图片，Skill 自动分析图像内容并生成适用于 AI 视频工具的动效提示词。

**输出工具：** Vidu Q2 + Seedance 2.0（双工具中文单语输出）

---

## 文件结构

```
slots-FX-skill/
├── slots-fx-prompt/
│   ├── SKILL.md                                # 主 Skill 入口（微文件架构）
│   ├── references/                             # 步骤/规则/配置（按需加载）
│   └── assets/                                 # 输出模板（路径引用，不进上下文）
├── slots_animation_prompt_skill_v1_claude.md   # 旧版单文件（归档保留）
├── CLAUDE.md                                   # 项目配置与优化历史
├── AGENTS.md                                   # Codex Agent 工作指南
└── brainstorming/
    ├── brainstorming-session-2026-03-04.md     # 初版设计头脑风暴
    ├── brainstorming-session-2026-03-05.md     # v1 优化头脑风暴
    └── brainstorming-session-2026-03-06.md     # v1 优化16 头脑风暴（UI Layer + 单层素材模板）
```

---

## Skill 覆盖场景

| 场景 | 说明 |
|------|------|
| A. 图标动效（Reel Symbols）| 低级 / 高级 / Wild / Scatter / Bonus × 待机 / 落定 / 中奖 / 期待抖动 |
| B. Free Game 弹窗 & 转场 | 触发弹窗 / 结算弹窗 / 转场进入 / 转场退出 |
| C. 加载页开场动画 | 单次播放 / 循环播放 |

---

## 核心设计原则

1. **流程强制确认** — 所有配置步骤必须逐步确认，禁止跳步或自动填充
2. **首尾帧意图优先** — 用户先选动效意图，再指导上传图片
3. **素材类型识别** — 上传图片后先判断素材类型（完整图标/纯主体/纯文字/纯背景），路由至对应模板
4. **双工具中文单语** — Vidu Q2 与 Seedance 2.0 各输出一套中文提示词
5. **风格感知动效** — 识别 S1–S9 美术风格，融入对应运动词汇
6. **语境锚定合规** — Seedance 版开头加 @图片1 引用，应对 LLM 全文过滤

---

## 当前版本

**v2 结构重构** (2026-03-12)

| 版本 | 优化内容 |
|------|---------|
| v1 初版 | 完整框架，覆盖三场景，双工具双语输出 |
| v1 优化1 | 主体动作规则细化（逐部位描述）|
| v1 优化2 | 图层识别深化（动物/角色/道具各自子层拆解）|
| v1 优化3 | 新增 Template A2（首尾帧专用双语模板）|
| v1 优化4 | 所有模板补充中文版（全部双语化）|
| v1 优化5 | 首尾帧模式统一为「上传一张图 → 询问首/尾」|
| v1 优化6 | 首尾帧流程重设计：意图优先4选项，首尾帧为默认模式 |
| v1 优化7 | Seedance 语境锚定句，叙事版模板，专属词汇库 |
| v1 优化8 | 风格识别层 S1–S9，STYLE MOTION PROFILES 章节 |
| v1 优化9 | MANDATORY EXECUTION RULES，修复流程跳步根本原因 |
| v1 优化10 | MANDATORY EXECUTION RULES 补充 Scene B/C 守门步骤 |
| v1 优化11 | 移除英文输出模板，改为纯中文单语输出 |
| v1 优化12 | Vidu 首尾帧结构 + 官方中文动态词 + Level 3 Idle 升级中等动态 |
| v1 优化13 | Seedance 全模板补充 @图片1 引用，B/C 模板拆分独立版本 |
| v1 优化14 | 新增 TRIGGER CONDITIONS 自动触发章节 |
| v1 优化15 | Seedance 全模板简洁化，去除【】标签，连贯叙述格式 |
| v1 优化16 | 新增 UI Layer 文字动效规则体系；INTENSITY MAPPING 扩展 UI Layer 列；新增 STEP 3A-3b 素材类型识别节点；新增 Template S / T / BG 单层素材专属模板 |
| v1 优化17 | 新增 STEP 4 方案预览：动效方向+强度+预览形式选择，Skill 自动决定差异维度，输出 2-3 个候选方案，用户确认后生成完整提示词 |
| v1 优化18 | Codex Issue 批量处理（#4-#11）：MANDATORY EXECUTION RULES 补充 3B-3b/3C-2b 守门步骤；Vidu 三段结构明确仅适用 Scene A；STEP 4-3 新增动效方向偏置映射表；新增多主体主从规则；Scene B/C 新增信息层级优先级表；STEP 4 新增排除项输入；新增批量全档模式 [ABC]；素材/风格识别增加低置信度双候选确认分支 |
| v1 优化19 | 修复 STEP 4-5 确认范围说明：批量全档 [ABC] 模式跳过单方案预览，直接输出轻/中/强三档并询问确认 |
| v1 优化20 | Token 精简（-4%）：移除 Skill Goal 章节及双语步骤标签，压缩 COMPLIANCE/词汇表/FINAL OUTPUT FORMAT 章节 |
| v1 优化21 | Token 大幅精简（-185行）：移除步骤级重复警告、分隔线、STEP 4格式示例、SEEDANCE词汇表压缩至6行、IMPORTANT RULES 精简、模板注释移除；素材识别置信度 ≥90% 自动通过 |
| v1 优化22 | 删除所有输出模板开头平台触发前缀词（「娱乐游戏数字转轴符号」「娱乐游戏 Free Game」等短语），规避平台内容过滤 |
| v2 结构重构 | 微文件三层架构重构：主入口切换为 `slots-fx-prompt/SKILL.md`；`references/` 按需加载步骤与规则；`assets/` 存放模板并通过路径引用；旧版单文件保留为归档参考 |
| v2 优化1（Phase 1）| MANDATORY EXECUTION RULES 补充完成标准列；step-4-preview.md 新增 4-6 生成后验证（9项检查清单）；STEP 2D 补充纯背景拦截守门节点 |
| v2 优化2 | Scene B 新增 STEP 3B-3c 核心素材识别节点：AI 实时分析弹窗核心主题素材（动物/魔法阵/宝物/自然元素/人物），用户确认或纠正；多核心素材时用户选定主次；无核心素材时询问是否引入新素材（需上传图片）；STEP 4 动效方向推荐与核心素材强绑定 |
