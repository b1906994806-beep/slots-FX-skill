---
stepsCompleted: [1, 2, 3, 4]
workflow_completed: true
inputDocuments: []
session_topic: 'Slots 图标动效提示词中文字/标题元素（UI Layer）缺乏动作描述和光效规则'
session_goals: '为图标提示词补充文字动效 & 光效的生成逻辑，可直接落地到 Skill 模板'
selected_approach: 'ai-recommended'
techniques_used: ['SCAMPER Method', 'Morphological Analysis', 'First Principles Thinking']
ideas_generated: 22
context_file: 'C:/Users/admin/Downloads/slots_animation_prompt_skill_v1_claude.md'
---

# Brainstorming Session Results

**Facilitator:** Admin
**Date:** 2026-03-06

## Session Overview

**Topic:** Slots 图标动效提示词中文字/标题元素（UI Layer）缺乏动作描述和光效规则
**Goals:** 为图标提示词补充文字动效 & 光效的生成逻辑，可直接落地到 Skill 模板

## Technique Selection

**Approach:** AI-Recommended Techniques
**Phase 1:** SCAMPER Method — 系统拆解现有规则的扩展切入点
**Phase 2:** Morphological Analysis — 文字动效 × 光效 × 动效状态 完整矩阵
**Phase 3:** First Principles Thinking — 从根本推导文字动效原则

---

## Idea Organization and Prioritization

### 主题一：文字动效类型库（10种核心动效）

行业验证的标准文字动效类型，可直接写入 Skill 的 MOTION RULES BY SCENE > UI Layer 章节。

| # | 动效类型 | 核心描述 | 适配符号 |
|---|---------|---------|---------|
| 1 | 弹出回弹（Pop/Bounce） | 缩小→放大至120%→回弹至100%，0.3–0.5s | BONUS / FREE SPINS |
| 2 | 金色扫光（Gold Shine） | 高光条从左至右扫过，周期2–3s，静止底字 | JACKPOT / GRAND / MEGA |
| 3 | 呼吸发光（Glow Pulse） | 外发光缓慢增强→减弱，周期2s，无位移 | WILD / 普通功能符号 |
| 4 | 闪烁高亮（Flicker） | 亮度随机闪烁或描边闪动，配合星光点闪 | SCATTER |
| 5 | 粒子火花（Spark/Burst） | 金色火花/星星/能量粒子从文字边缘爆开 | SUPER / MEGA / BONUS |
| 6 | 金币掉落（Coin Rain） | 文字周围不时掉落金币/钻石，点缀型 | JACKPOT |
| 7 | 轻微浮动（Gentle Float） | 整体上下浮动约2px，周期2–4s | 卡通风格符号 |
| 8 | 形变（Squash & Stretch） | 轻微压扁再恢复，弹性感，幅度极小 | 卡通/动物/冒险主题 |
| 9 | 能量环绕（Energy Orbit） | 光环/能量圈/电流围绕文字旋转 | MAGIC WILD / POWER BONUS |
| 10 | 渐变流动（Gradient Flow） | 文字内部颜色渐变缓慢流动（彩虹/金属） | 高端JACKPOT/稀有符号 |

**行业标准组合公式（5层叠加结构）：**
- 第1层：文字渐变 + 描边
- 第2层：外发光呼吸
- 第3层：扫光或闪光
- 第4层：粒子（星星/金币/能量）
- 第5层：轻微位移或浮动

> 核心极简公式（顶级Slots三要素）：金属渐变 + 扫光 + 轻微呼吸发光

---

### 主题二：主体-文字联动规则（结构性新增）

当前Skill最大缺口——主体动效与文字动效的因果时序关系。

**联动时序默认规则：**
主体动作先触发 → 文字动效随后跟随（约0.1–0.2s延迟）

**例外：文字领先于主体（仅Scatter期待抖动）：**
文字先闪烁预告 → 主体随后开始抖动

**因果链改编（从主体规则平移到文字层）：**

| 主体层（现有规则） | 文字层（改编后） |
|---|---|
| 头部前冲 → 下颌跟随张开 | 文字外框扩张 → 描边光晕跟随爆开 |
| 眼睛由紧缩→爆发发光 | 文字亮度由暗→峰值 |
| 耳朵向外炸开 | 文字字母间距向外撑开 |
| 尾巴甩动（延迟跟随） | 粒子从文字尾端延迟飞出 |

---

### 主题三：图标类型 × 动效状态 × 文字动效 完整矩阵

**落定（Land）定义修正：** 非物理下落，而是符号停稳时的短促能量爆发强调（0.3–0.5s），告知玩家注意。

#### Wild 图标

| 状态 | 主体强度 | 文字动效 | 联动时序 |
|---|---|---|---|
| Idle | 中等动态 | 呼吸发光 + 微扫光（2–3s周期） | 与主体浮动同步 |
| Land | 中等动态 | 描边短促闪光 + 轻微弹跳回弹（小爆发0.3–0.5s） | 主体能量闪后同步 |
| Win | 大动态 | 弹出回弹 + 粒子火花 + 扫光 | 主体爆发→文字弹出→粒子扩散 |

#### Scatter 图标

| 状态 | 主体强度 | 文字动效 | 联动时序 |
|---|---|---|---|
| Idle | 中等动态 | 呼吸发光 + 星光点闪（神秘感） | 与主体同步 |
| Land | 中等动态 | 描边短促闪光 + 小爆发 | 主体能量闪后同步 |
| Win | 大动态 | 弹出回弹 + 能量环绕 + 粒子爆发 | 主体爆发→文字弹出→环绕扩散 |
| Anticipation | — | 文字先闪烁（预告）→ 主体才开始抖动 | 文字领先主体（反转时序） |

#### Bonus 图标

| 状态 | 主体强度 | 文字动效 | 联动时序 |
|---|---|---|---|
| Idle | 中等动态 | 呼吸发光 + 偶发星光粒子 | 与主体同步 |
| Land | 中等动态 | 描边短促闪光 + 小爆发 | 主体能量闪后同步 |
| Win | 大动态 | 弹出回弹 + 金色粒子火花 + 扫光 | 主体爆发→文字弹出→粒子散开 |

#### Low-tier / High-tier 图标（仅Win状态）

| 图标类型 | 主体强度 | 文字动效 | 联动时序 |
|---|---|---|---|
| Low-tier | 小幅动态 | 轻微扫光（单次，不循环） | 主体光晕亮起时文字同步扫光 |
| High-tier | 中等动态 | 扫光 + 轻微弹出回弹 | 主体能量环扩散时文字弹出 |

---

### 主题四：UI Layer 设计原则与硬性约束

**四条底层原则（First Principles推导）：**

| 原则 | 结论 |
|---|---|
| 信息优先 | 文字任何时候必须可读，动效不能破坏字形 |
| 强度从属 | 文字动效强度永远低于主体一档，主角是图像不是文字 |
| 节奏错开 | 各效果层错开触发，避免同时抢占注意力 |
| 语义一致 | 动效类型呼应符号含义（SCATTER用神秘感，BONUS用爆发感）|

**UI Layer Hard Restrictions（文字动效硬性约束）：**
- 文字缩放幅度不超过 110–120%
- 各效果层（呼吸/扫光/粒子）必须错开触发节奏，禁止同时循环
- 循环周期不低于 2 秒
- 文字动效强度比主体低一档（主体大动态→文字中等动态；主体中等动态→文字小幅动态）
- 禁止文字遮挡主体核心部位
- 文字内容（字形、字色）保持可读，不因动效失真

**INTENSITY MAPPING 新增 UI Layer 列：**

| Level | 状态 | 主体 Vidu 词 | 文字层 Vidu 词 | 文字层 Seedance |
|---|---|---|---|---|
| Level 1 | Win | 小幅动态 | — | 无文字动效 |
| Level 2 | Win | 中等动态 | 小幅动态 | Subtle sweep |
| Level 3 | Win | 大动态 | 中等动态 | Moderate / Energetic |
| Level 3 | Idle | 中等动态 | 小幅动态 | Gentle / Continuous |
| Level 3 | Land | 中等动态 | 小幅动态 | Subtle burst |
| Scatter | Anticipation | — | 小幅动态（先行闪烁）| Subtle anticipatory flicker |

---

### 主题五：流程结构升级（结构性漏洞修复）

**漏洞1：素材类型识别缺失**

当前STEP 3A-3上传图片后，Skill假设所有素材都是"完整图标（主体+文字）"。实际素材类型可能有三种。

**修复方案：** 在 STEP 3A-3 上传之后、3A-4 视觉识别之前，增加素材类型判断节点：

```
上传图片后 →
  ├─ 完整图标（主体 + 文字）→ 现有流程（主体动效 + 文字联动）
  ├─ 纯文字素材（Title Only）→ Template T 流程
  └─ 纯主体素材（Subject Only）→ 现有流程（跳过 UI Layer）
```

**漏洞2：纯文字素材无独立生成路径**

用户场景：上传纯文字PNG + 说"给这个文字设计待机动效"，当前Skill完全无法处理。

**修复方案：新增 Template T（Text-Only 专属模板）**

现有模板无法复用的三个原因：
1. Seedance开头`@图片1的[主体核心特征]`——纯文字无"主体"
2. 动效描述绑定"主体专项动作规则因果链"——纯文字无身体部位
3. 约束语"保持主体外形一致"——应替换为"保持字形清晰可读"

**Template T 草案结构：**

Vidu Q2：
```
娱乐游戏数字转轴文字标题动效，固定镜头。
[字体/颜色/描边/发光初始状态描述]
[文字动效描述：按UI Layer规则选配动效类型，描述光效层次与节奏]
文字清晰可读，字形无变形，[小幅动态 / 中等动态]
```

Seedance 2.0：
```
@图片1的[文字核心特征：字体/颜色/描边]，娱乐游戏数字转轴文字标题动效，固定镜头，[风格质感]。
[连贯描述文字动效过程：光效层次、粒子效果、节奏感，控制在3–4句。]
保持字形清晰可读，字色一致，无失真。[Subtle/Gentle] motion, seamless loop.
```

---

## 单层素材模板体系（新增）

用户上传的素材可能是拆分后的单个图层，当前Skill只能处理完整图标。本次新增以下模板体系：

| 模板 | 素材类型 | 挂载场景 | 核心动效逻辑 | 本次状态 |
|---|---|---|---|---|
| 现有流程 | 完整图标（主体+文字） | Scene A | 主体专项规则 + 文字联动 | ✅ 已有 |
| **Template S** | 纯主体（Subject Only） | Scene A | 现有主体规则，约束语去掉文字相关 | 📋 本次新增 |
| **Template T** | 纯文字（Text Only） | Scene A | UI Layer 文字动效规则 | 📋 本次新增 |
| **Template BG** | 纯背景（Background Only） | Scene B / Scene C | 大气粒子/光效流动/环境循环 | 📋 本次新增 |
| **Template UI** | 交互按钮（Spin/Start等） | 待定 Scene D | 按下→反馈→弹起，点击动效专属规则 | 🔲 待办，后续版本 |

**素材类型识别节点（新增于 STEP 3A-3 之后）：**

```
上传图片后 →
  ├─ 完整图标（主体 + 文字）→ 现有流程
  ├─ 纯主体（Subject Only）→ Template S
  ├─ 纯文字（Text Only）→ Template T
  ├─ 纯背景（Background Only）→ Template BG（Scene B/C子路径）
  └─ 交互UI按钮 → 🔲 待办
```

### Template S 草案（纯主体）

Vidu Q2：
```
娱乐游戏数字转轴符号主体动效，固定镜头。
[按主体专项动作规则，明确X带动Y，Y延迟跟随Z的因果链逐部位描述]
固定镜头，保持主体外形纹理色彩一致，无变形。[小幅动态 / 中等动态 / 大动态]
```

Seedance 2.0：
```
@图片1的[主体核心特征一句话描述]，娱乐游戏数字转轴符号主体动效，固定镜头，[风格质感]。
[连贯描述主体动效：按主体专项规则描述核心部位动作及带动关系，控制在3–5句。]
保持主体外形、纹理、色彩一致，无变形。[Subtle/Moderate/Dynamic] motion, smooth pacing.
```

### Template BG 草案（纯背景）

> 主要用于 Scene B（弹窗）和 Scene C（加载页）的背景层素材。

Vidu Q2：
```
娱乐游戏[弹窗背景 / 加载页背景]动效，固定镜头，[小幅动态 / 中等动态]。
[连贯叙述：大气粒子漂浮 / 光效流动 / 环境色彩渐变 / 背景光晕脉冲]
无明显重启点，无缝循环，背景元素保持稳定不突变。
```

Seedance 2.0：
```
@图片1的[背景核心视觉特征]，娱乐游戏[弹窗背景 / 加载页背景]动效，固定镜头，[风格质感]，轻柔大气。
[连贯描述背景动效：粒子漂浮节奏 + 光效脉冲周期 + 色彩氛围变化，控制在3–4句。]
背景元素保持稳定，无突变，seamless loop, [Gentle/Ambient] motion.
```

---

## Action Plan（落地优先级）

### P1 — 立即落地（直接影响现有输出质量）

1. **补充 UI Layer Hard Restrictions** → 写入 Skill 的 MOTION RULES BY SCENE 章节
2. **补充主体-文字联动时序规则** → 写入各模板的动效描述段落说明
3. **完整矩阵写入提示词规则** → 在 MOTION RULES BY SCENE 新增"UI Layer Motion Rules"小节，按图标类型列出推荐文字动效

### P2 — 中期补全（完善规则体系）

4. **文字动效类型库（10种）** → 写入 MOTION RULES BY SCENE > UI Layer 作为可选词汇库
5. **INTENSITY MAPPING 增加 UI Layer 列** → 扩展现有表格

### P3 — 结构升级（单层素材模板体系）

6. **STEP 3A-3 后增加素材类型判断节点** → 修改 STEP 3A 流程说明，新增五路分支
7. **新增 Template T（纯文字）** → Vidu + Seedance 各一个
8. **新增 Template S（纯主体）** → Vidu + Seedance 各一个
9. **新增 Template BG（纯背景）** → Vidu + Seedance 各一个，Scene B/C 子路径

### 🔲 待办（后续版本）

10. **新增 Template UI（交互按钮点击动效）** → 需同时新增 Scene D 入口 + 点击动效专属规则体系

---

## Session Summary

**本次头脑风暴核心发现：**
- 文字动效不是"锦上添花"，而是 Skill 当前的结构性缺口
- 最重要的不是补充10种动效类型，而是建立"主体-文字联动时序"这条规则主线
- 发现了更深层的流程漏洞：Skill 无法处理单层素材，需要建立完整的单层素材模板体系（S / T / BG）
- 行业核心极简公式：金属渐变 + 扫光 + 呼吸发光，克制胜过复杂

**创意突破点：**
- 主体专项动作因果链（X带动Y延迟跟随Z）可以直接改编到文字层
- 文字强度永远低主体一档——可直接系统化写入 INTENSITY MAPPING
- Scatter Anticipation 的"文字先行"是唯一合理的反转时序场景
- 交互按钮（Spin/Start）点击动效是全新场景类型，记入待办
