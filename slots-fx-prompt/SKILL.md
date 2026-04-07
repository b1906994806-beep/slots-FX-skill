---
name: slots-fx-prompt
description: >
  Slots 游戏动效 AI 提示词生成器。用户上传静态图片，自动分析图像内容，
  生成适用于 Vidu Q2 和/或 Seedance 2.0 的动效提示词。
  触发关键词：Vidu、Seedance、动效提示词、图标动效、待机动效、中奖动效、
  落定动效、弹窗动效、加载页动效、转场动效、Slots 图标、Reel Symbol、
  Wild 图标、Scatter 图标、Bonus 图标、Free Game 弹窗、让它动起来、做动效、生成提示词。
  用户上传图片且消息含"动效/提示词/让它动/Vidu/Seedance/图标/游戏"时也触发。
allowed-tools: Read
version: 1.0.0
---

# Slots 动效提示词生成器

## 触发条件

**关键词触发**（含以下任意一词即触发）：
Vidu / Seedance / Vidu Q2 / Seedance 2.0 / 动效提示词 / 图标动效 / 待机动效 /
中奖动效 / 落定动效 / 弹窗动效 / 加载页动效 / 转场动效 / Slots 图标 /
Reel Symbol / Wild 图标 / Scatter 图标 / Bonus 图标 / Free Game 弹窗 /
让它动起来 / 让这个动起来 / 做动效 / 生成动效 / 生成提示词（需结合游戏/图标语境）

**图片上传触发**：用户上传图片，且消息含：
动效 / 提示词 / 让它动 / 做动效 / Vidu / Seedance / 图标 / 游戏

**触发后**：直接进入 STEP 1，输出工具选择问题。
若触发词模糊（无游戏/图标语境），先确认："你是要生成 Slots 游戏动效提示词吗？"

---

## 强制执行规则

🛑 **以下所有步骤均由用户明确确认后，才可生成提示词：**

| # | 步骤 | 说明 | 完成标准 |
|---|------|------|---------|
| 1 | STEP 1.1 | 目标工具选定 | `tool` 已确认为 Vidu Q2 / Seedance 2.0 / Both 之一 |
| 2 | STEP 1.2 | 生成模式 + 意图（首尾帧时）确认 | `mode` 已确认；首尾帧模式下 `intent` 已确认为 A/B/C/D 之一 |
| 3 | STEP 2 | 场景类型选定 | `scene` 已唯一确定为 A/B/C/D 之一，无歧义 |
| 4 | STEP 3A-1 | 图标类型（Scene A） | `icon_level`（Level1/2/3）已确认 |
| 5 | STEP 3A-2 | 动效状态（Scene A） | `motion_state` 已确认为该图标类型允许的状态之一 |
| 6 | STEP 3A-3b | 素材类型识别（置信度≥90%自动通过） | `material_type` 已确认；纯背景素材已拦截并提示重新上传 |
| 7 | STEP 3B-1 | 弹窗/转场阶段（Scene B） | `motion_state`（阶段1–6）已确认 |
| 8 | STEP 3B-2 | 转场方案（阶段[3]或[6]时，Scene B） | 转场方案（独立/通用）已确认；非转场阶段此步跳过 |
| 9 | STEP 3B-3b | 素材类型识别（Scene B） | `material_type` 已确认；纯背景已拦截 |
| 10 | STEP 3B-3c | 核心素材识别（Scene B，完整弹窗素材时） | `core_asset` 已由用户确认（含类型、姿态、主次关系）；无核心素材时已询问是否引入新素材并获得答复 |
| 11 | STEP 3C-1 | 播放模式（Scene C） | `playback_mode`（单次/循环）已确认 |
| 12 | STEP 3C-2b | 素材类型识别（Scene C） | `material_type` 已确认；纯背景已拦截 |
| 13 | STEP 4 | 方案预览已输出，用户已选定方案 | 用户已选定唯一方案编号；选定前禁止进入生成阶段 |

⚠️ 用户消息含部分信息时，仍需逐步确认所有未明确步骤，禁止自动填充。
✅ STEP 1.3 为可选步骤：用户选 [S] Spine 时读取 spine-constraints.md 并全流程应用约束；跳过则无落地约束。
✅ 图片上传可在任意时间点，但分析仅在所有配置步骤确认后开始。
✅ STEP 3A-3b 确认素材类型 → 经过 STEP 4 预览 → 再路由至对应模板生成。
✅ Scene A 中检测到纯背景素材：立即提示改选 Scene B/C 或重新上传，不得继续生成。
✅ STEP 4 默认规则：动效方向必选；强度默认中；预览形式默认半结构；可选补充自动推断。

---

## 执行步骤索引

执行时按需读取对应文件：

- **STEP 1–2**（工具/模式/场景）→ 读取 `{baseDir}/references/steps-1-2.md`
- **Spine 约束**（STEP 1.3 选 [S] 时）→ 读取 `{baseDir}/references/spine-constraints.md`
- **STEP 3A**（图标流程）→ 读取 `{baseDir}/references/steps-3a-icon.md`
- **STEP 3B**（弹窗流程）→ 读取 `{baseDir}/references/steps-3b-popup.md`
- **STEP 3C**（加载页流程）→ 读取 `{baseDir}/references/steps-3c-loading.md`
- **STEP 4**（方案预览）→ 读取 `{baseDir}/references/step-4-preview.md`
- **动效规则**（图标各级规则 + 主体动作规则库）→ 读取 `{baseDir}/references/motion-rules.md`
- **UI 层文字动效规则** → 读取 `{baseDir}/references/ui-layer-rules.md`
- **弹窗/转场/加载页规则** → 读取 `{baseDir}/references/popup-loading-rules.md`
- **风格档案 + 强度映射** → 读取 `{baseDir}/references/style-profiles.md`
- **合规词过滤** → 读取 `{baseDir}/references/compliance.md`
- **输出模板** → 路径引用 `{baseDir}/assets/` 对应模板文件

---

## 输出格式规范

每次生成，按已选工具输出对应版本：

```
【Vidu Q2 版本】提示词：
（末尾标注运动幅度参数）

【Seedance 2.0 版本】提示词：
（末尾必须包含显式约束语）
```

**通用规则：**
- 所有提示词输出语言：**中文**
- Vidu Q2：连贯口语叙述，不用【】标签；动态词用官方词（小幅/中等/大动态）；核心氛围词重复 2 次以上
- Seedance 2.0：必须以 `@图片1的[核心特征]，` 开头；连贯叙述，5–10 行；意图[D]同时标注 `@图片1` 和 `@图片2`
- 生成前执行风格识别（S1–S9），风格词汇自然融入
- 输出前执行合规词过滤
- Idle 态必须注明无缝循环；禁止镜头运动（转场除外）
- 主体动作禁止模糊描述，必须按主体专项规则指定部位、动作、因果链
- 首尾帧模式必须依次描述：起始状态 → 动作弧线 → 结束状态，匹配意图[A/B/C/D]
