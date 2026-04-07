# Slots Animation Prompt Skill — 项目配置

## 项目概述

本项目基于 BMAD 框架，开发一套 **Slots 游戏动效 AI 提示词生成 Skill**。
用户上传静态图片，Skill 自动分析图像内容并生成适用于 AI 视频工具的动效提示词。

**目标工具：** Vidu Q2 + Seedance 2.0（双工具中文单语输出）

---

## 关键文件路径

| 文件 | 说明 |
|------|------|
| `slots-fx-prompt/SKILL.md` | **主 Skill 入口**（微文件架构，97行，三层渐进式加载） |
| `slots-fx-prompt/references/` | 步骤/规则/配置（按需加载到上下文） |
| `slots-fx-prompt/assets/` | 输出模板（不进上下文，仅路径引用） |
| `slots_animation_prompt_skill_v1_claude.md` | 旧版单文件（990行，归档保留） |
| `brainstorming/` | 历次头脑风暴设计记录 |

**安装路径：** `C:\Users\admin\.claude\skills\slots-fx-prompt\`（已安装为 Claude Code Skill）

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

1. **输入**：默认上传一张静态图片；意图 [D] 时上传两张（起始 + 结束）；加载页场景需简述主体
2. **首尾帧模式**：意图 [A/B/C] 上传一张图，意图 [D] 上传两张图（起始状态 + 结束状态）
3. **输出**：每次同时生成 Vidu Q2 + Seedance 2.0 两套，中文单语两套版本（Vidu Q2 + Seedance 2.0）
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
| 强度控制 | `motion amplitude: small/medium/large` | Slow/Gentle/Dynamic 等语言词 |
| 约束语 | 可选 | 必须显式写出 |
| 参考图引用 | `@Image1` / `@subject(...)` 标签 | @图片1 强制写入提示词开头（意图 [D] 双图时同时标注 @图片1 + @图片2） |

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
| v1 优化10 | Codex结构检查发现：MANDATORY EXECUTION RULES 未覆盖 Scene B/C，补充 3B-1、3B-2、3C-1 守门步骤 |
| v1 优化11 | 联网确认 Vidu Q2 & Seedance 2.0 均以中文提示词效果最佳，移除所有英文输出模板，改为纯中文单语输出 |
| v1 优化12 | 读取 Vidu 官方提示词指南，修复待机动效质量问题：①INTENSITY MAPPING 替换为官方中文动态词；②Template A2 新增 Vidu 专用首帧/中间帧/尾帧结构；③Template A Vidu 版改为连贯叙事；④Level 3 Idle 动态词升级为中等动态 |
| v1 优化13 | 读取 Seedance 2.0 官方提示词公式，修复@参考素材缺失问题：所有 Seedance 模板开头补充@图片1引用；全部 B/C 模板拆分为 Vidu Q2 / Seedance 2.0 独立版本 |
| v1 优化14 | 新增 TRIGGER CONDITIONS 章节：关键词触发（Vidu/Seedance/动效场景/游戏元素/意图表达）+ 图片上传触发，识别后自动进入 STEP 1 |
| v1 优化15 | 对照 Seedance 2.0 官方手册简洁原则，全部 Seedance 模板去除【】分段标签，改为连贯叙述格式，控制在 5–10 行 |
| v1 优化16 | 头脑风暴后新增 UI Layer 文字动效完整规则体系：①UI Layer Motion Rules（10种动效类型库、主体-文字联动时序、按图标类型推荐矩阵、硬性约束）；②INTENSITY MAPPING 新增 UI Layer 列（文字强度永远低主体一档）；③新增 STEP 3A-3b 素材类型识别节点；④新增 Template S（纯主体）/ Template T（纯文字）/ Template BG（纯背景）三个单层素材专属模板；⑤Template UI（交互按钮）记入待办 |
| v1 优化17 | 新增 STEP 4 方案预览步骤：用户选动效方向(A-F)+强度+预览形式，Skill 自动决定差异维度（9组状态映射），输出 2-3 个候选方案，用户确认后再生成完整提示词；MANDATORY EXECUTION RULES 补充第10条 |
| v1 优化18 | Codex Issue 批量处理（#4-#11）：①MANDATORY EXECUTION RULES 补充 3B-3b/3C-2b 守门步骤；②IMPORTANT RULES 明确 Vidu 三段结构仅适用 Scene A；③STEP 4-3 新增动效方向偏置映射表（A-F × 四维度）；④新增多主体主从规则（Primary Driver/Secondary Follower）；⑤Scene B/C 各自新增信息层级优先级表；⑥STEP 4 新增排除项输入及硬性约束规则；⑦新增批量全档模式 [ABC]；⑧素材/风格识别增加低置信度双候选确认分支 |
| v1 优化19 | 修复 STEP 4-5 确认范围说明：批量全档 [ABC] 模式跳过单方案预览，直接输出轻/中/强三档并询问确认 |
| v1 优化20 | Token 精简（-4%）：移除 Skill Goal 章节及双语步骤标签，压缩 COMPLIANCE/词汇表/FINAL OUTPUT FORMAT 章节 |
| v1 优化21 | Token 大幅精简（-185行）：移除步骤级重复警告、分隔线、STEP 4格式示例、SEEDANCE词汇表压缩至6行、IMPORTANT RULES 精简、模板注释移除；素材识别置信度 ≥90% 自动通过 |
| v1 优化22 | 删除所有输出模板开头平台触发前缀词（「娱乐游戏数字转轴符号」「娱乐游戏 Free Game」等短语），规避平台内容过滤 |
| v2 结构重构 | 微文件三层架构重构：SKILL.md 从 990 行压缩至 97 行；references/（10个子文件，按需加载）+ assets/（5个模板，不进上下文）；预计节省 ~55% 上下文消耗 |
| v2 优化1（Phase 1）| 基于 AI 任务拆解方法论：①MANDATORY EXECUTION RULES 补充完成标准列（12步均有可验收判据）；②step-4-preview.md 新增 4-6 生成后自动验证（9项检查清单，V1–V9，涵盖 Idle 循环/镜头运动/模糊表达/格式/合规，失败自动修正或标注回退层级）；③steps-1-2.md STEP 2D 补充素材类型识别守门（纯背景拦截，保留快速推断能力）|
| v2 优化2 | Scene B 新增 STEP 3B-3c 核心素材识别节点：AI 实时分析弹窗核心主题素材（动物/魔法阵/宝物/自然元素/人物），用户确认或纠正；多核心素材时用户选定主次；无核心素材时询问是否引入新素材（需上传图片）；STEP 4 动效方向推荐与核心素材强绑定 |

---

## 继续优化时的工作方式

1. **先检查 GitHub Issues**：`gh issue list -R b1906994806-beep/slots-FX-skill --state open`
   - 查看有无未处理的 `optimization-idea` 或 `bug` Issue
   - 优先处理高优先级 Issue，再进行新的优化
2. **读取主 Skill 文件**：`slots-fx-prompt/SKILL.md`（新架构）；旧版参考：`slots_animation_prompt_skill_v1_claude.md`
3. **描述具体问题**，Claude 定位需修改的段落后直接 Edit
4. **测试方式**：上传实际图片运行 Skill，观察输出质量
5. **版本记录**：每次优化后在本文件「已知优化历史」表格中追加记录
6. **关闭 Issue**：修复完成后执行 `gh issue close {id} -R b1906994806-beep/slots-FX-skill`
7. **收尾三件套（必做）**：每次优化结束前，必须同步以下三处，缺一不可：
   - `CLAUDE.md` 「已知优化历史」末尾追加本次版本记录
   - `README.md` 第 51 行附近「当前版本」标题 + 版本历史表追加同一条记录
   - `diff` 验证 Downloads 与 repo 克隆文件一致（`diff <(sed 's/\r//' Downloads/...) <(sed 's/\r//' /tmp/.../...)`）

---

## 沟通偏好

- 使用**中文**回答
- 提问方式：一问一答，逐步确认
- 输出风格：简洁直接，优先用表格或代码块呈现结构化内容
