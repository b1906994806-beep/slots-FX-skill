# Slots Game Animation Prompt Generator — Skill v1

## TRIGGER CONDITIONS

当用户的消息满足以下任意一条，**立即自动启动本 Skill**，从 STEP 1 开始执行，无需用户额外说明：

### 🔑 关键词触发（含以下词汇之一即触发）

| 类型 | 触发关键词 |
|------|-----------|
| 工具指向 | `Vidu`、`Seedance`、`Vidu Q2`、`Seedance 2.0` |
| 动效场景 | `动效提示词`、`图标动效`、`待机动效`、`中奖动效`、`落定动效`、`弹窗动效`、`加载页动效`、`转场动效` |
| 游戏元素 | `Slots 图标`、`Reel Symbol`、`Wild 图标`、`Scatter 图标`、`Bonus 图标`、`Free Game 弹窗` |
| 意图表达 | `让它动起来`、`让这个动起来`、`做动效`、`生成动效`、`生成提示词`（需结合游戏/图标语境） |

### 🖼️ 图片上传触发

用户上传图片，且消息中包含以下任意词：
`动效` / `提示词` / `让它动` / `做动效` / `Vidu` / `Seedance` / `图标` / `游戏`

### ⚠️ 触发后行为

1. 识别到触发条件后，**直接进入 STEP 1**，输出工具选择问题
2. 若用户消息中已包含部分配置信息（如"Scatter 图标的中奖动效"），**仍需逐步确认所有未明确的步骤**，不得自动填充
3. 若触发词模糊（如仅说"做个动效"而无游戏/图标语境），先回复一句确认："你是要生成 Slots 游戏动效提示词吗？"

---

## MANDATORY EXECUTION RULES

🛑 **NEVER generate prompts until ALL of the following are explicitly confirmed by the user:**

1. **STEP 1.1** — Target tool selected (or default [C] confirmed)
2. **STEP 1.2** — Generation mode selected AND intent [A/B/C/D] confirmed if First-Last Frame
3. **STEP 2** — Scene type selected
4. **STEP 3A-1** — Icon type selected (if Scene A)
5. **STEP 3A-2** — Animation state selected (if Scene A)
6. **STEP 3A-3b** — Asset type detected and confirmed (Complete Icon / Subject Only / Text Only / Background Only)
7. **STEP 3B-1** — Popup/Transition stage selected (if Scene B)
8. **STEP 3B-2** — Transition design selected if stage [3] or [6] (if Scene B)
9. **STEP 3B-3b** — Asset type detected and confirmed (Complete Popup / Background Only) (if Scene B)
10. **STEP 3C-1** — Playback mode selected (if Scene C)
11. **STEP 3C-2b** — Asset type detected and confirmed (Complete Loading Page / Background Only) (if Scene C)
12. **STEP 4** — 方案预览已输出，用户已选定方案（或确认在某方案基础上微调）

⚠️ **If the user's message already contains partial information** (e.g. mentions "待机动效" or "图标"), acknowledge it, then **still ask for all unconfirmed steps** before generating. Do NOT auto-fill missing selections.

✅ **Image upload** may happen at any point — but analysis only begins after all configuration steps are confirmed.

✅ **单层素材路由顺序：** STEP 3A-3b 确认素材类型后 → 仍需经过 STEP 4 方案预览 → 再路由至对应模板（Template S / T / BG）生成完整提示词。完整图标同理。

✅ **Background Only 异常分支（Scene A）：** 若在 Scene A 流程中检测到纯背景素材，立即提示用户：「纯背景素材不适用于图标动效场景，请改选 Scene B（弹窗）或 Scene C（加载页），或重新上传包含主体的图片。」不得继续生成提示词。

✅ **STEP 4 默认规则：** 动效方向为唯一必选项；强度默认中；预览形式默认半结构；可选补充缺失时自动推断，不追问。

---

## STEP 1: Global Configuration

🛑 **必须逐步确认，不得跳过。用户未明确回答前禁止进入下一步。**

### 1.1 Target Tool
> 请选择目标工具：
- **[A]** Vidu Q2
- **[B]** Seedance 2.0
- **[C]** 两者都输出（同时输出两套）

**默认：[C] 两者都输出**

### 1.2 Generation Mode
> 请选择生成模式：
- **[1]** 首尾帧模式 — **默认** — 指定动效的起点或终点状态
- **[2]** 全能参考模式 — **高级** — 上传一张参考图，AI 全程参考

If **[1]** First-Last Frame Mode selected:
> 你的动效意图是什么？
- **[A] 让它动起来** — 从这张图出发，向前演绎动效
- **[B] 还原这一刻** — 动效以这张图作为结束状态
- **[C] 回到原位** — 运动后回到与上传图相同的状态（循环）
- **[D] 从A到B** — 我有起始和结束两个状态

- **[A] [B] [C]** — 上传 **1 张**图片
- **[D]** — 上传 **2 张**：先发起始状态图，再发结束状态图

---

## STEP 2: Scene Selection

🛑 **STEP 1 全部确认后方可进入此步骤。**

> 请选择场景类型：
- **[A]** 图标动效（Reel Symbols）
- **[B]** Free Game 弹窗 & 转场
- **[C]** 加载页开场动画

---

## STEP 3A: Icon Animation Flow

🛑 **STEP 2 确认场景 [A] 后方可进入。3A-1 → 3A-2 → 3A-3 必须按顺序逐步确认，不得跳步。**

### 3A-1 Select Icon Type

> 请选择图标类型：

| 选项 | 类型 | 动效强度 |
|------|------|--------|
| [1] | 低级图标 Low-tier Symbol | 一级 Level 1 |
| [2] | 高级图标 High-tier Symbol | 二级 Level 2 |
| [3] | Wild 图标 | 三级 Level 3 |
| [4] | Scatter 图标 | 三级 Level 3 |
| [5] | Bonus 图标 | 三级 Level 3 |

### 3A-2 Select Animation State

| 图标类型 | 可选状态 |
|---------|---------|
| 低级图标 | 中奖动效 Win |
| 高级图标 | 中奖动效 Win |
| Wild | 待机 Idle / 落定 Land / 中奖 Win |
| Scatter | 待机 Idle / 落定 Land / 中奖 Win / 期待抖动 Anticipation |
| Bonus | 待机 Idle / 落定 Land / 中奖 Win |

### 3A-3 Upload Image

> 请上传图标图片，AI 自动分析视觉结构。

**首尾帧模式下：** 上传说明已在 STEP 1.2 中确认，按意图 [A/B/C/D] 上传对应数量图片。

### 3A-3b Asset Type Detection（素材类型识别）

🛑 **图片上传后，必须先判断素材类型，再进入视觉识别。禁止跳过此步骤。**

AI 自动识别上传图片属于以下哪种类型，并告知用户确认：

| 类型 | 识别特征 | 后续流程 |
|------|---------|---------|
| **完整图标**（主体 + 文字） | 画面同时包含主体图像和标题文字 | 继续 3A-4 → 生成完整提示词（主体 + 文字联动） |
| **纯主体**（Subject Only） | 只有动物/角色/道具等主体，无文字无背景 | 跳转 Template S 流程 |
| **纯文字**（Text Only） | 只有标题文字（如 WILD / BONUS），无主体 | 跳转 Template T 流程 |
| **纯背景**（Background Only） | 只有背景光效/粒子/环境元素，无主体无文字 | **Scene A 下：报错，提示用户改选 Scene B/C 或重新上传**；Scene B/C 下：跳转 Template BG 流程 |

> **完全无法确定时**，询问用户：「请问你上传的图片是完整图标、纯主体、纯文字，还是纯背景素材？」
>
> **低置信度时（有倾向但不确定）**，输出双候选确认：「我更倾向识别为 **[类型A]**（理由：[特征依据]），其次可能是 **[类型B]**。请确认或选择。」— 用户确认后继续，无需重新上传。

### 3A-4 Automatic Visual Recognition

**Style Detection** — Identify the visual art style (choose closest match):

| # | 风格 | 识别特征 |
|---|------|---------|
| S1 | 3D卡通 | 3D渲染，夸张比例，饱和色彩，卡通描边 |
| S2 | 3D写实史诗 | 高精度3D，电影级打光，宏大叙事感 |
| S3 | 2D精绘插画 | 手绘笔触质感，丰富色彩层次，叙事性构图 |
| S4 | 动漫/Anime | 日式角色风格，大眼睛，速度线，闪光效果 |
| S5 | 霓虹发光 | 暗色背景，霓虹光晕，电光粒子，高饱和发光 |
| S6 | 奢华金属 | 金色/大理石质感，低调配色，高端奢华氛围 |
| S7 | 暗黑哥特 | 暗色调，戏剧性阴影，哥特纹样，诡异氛围 |
| S8 | Q版萌系 | 超变形比例，糖果色，圆润造型，极度可爱 |
| S9 | 印度宝莱坞 | 繁复曼陀罗/花纹，宝石色彩，神祇图腾，节庆华丽感 |

将识别到的风格代号（S1–S9）带入后续提示词生成，参照 STYLE MOTION PROFILES 章节。

> **低置信度时（两种风格相近，无法确定唯一）**，输出双候选确认：「风格更接近 **[SX] [风格名]**（理由：[视觉特征依据]），其次可能是 **[SY] [风格名]**。请确认或选择。」— 用户确认后，以选定风格进入后续步骤；若用户无偏好，默认选择置信度更高的那项继续。

**Subject Detection** — Identify the primary subject (choose closest match):
- Character / Animal / Dice / Cards / Sports equipment / Weapon / Gem / Coin / Mechanical device / Title-focused

**Auto Layer Decomposition:**

Primary layer — Main subject. Further decompose based on subject type:

- **Animal subject sub-layers:**
  - Facial: eyes (color / glow state) / mouth-jaw (open/closed / fangs visible) / ears (position) / nose / whiskers / fur texture
  - Body: neck / shoulders / chest / visible limbs / tail
  - Surface detail: stripe patterns / scales / feathers — must be noted for consistency preservation

- **Character subject sub-layers:**
  - Facial: expression / eyes / mouth
  - Body: upper body stance / arms / weapon or prop held
  - Surface detail: clothing / hair / accessories

- **Prop subject sub-layers (Gem / Coin / Dice / Cards):**
  - Shape: geometry, facets, edges
  - Surface: material finish (gold / crystal / metallic)
  - Orientation: current facing angle

Secondary layer — Atmosphere support:
- Coins / gems / particles / light aura / energy rings / smoke / lightning / water ripple

UI layer — Interface elements:
- Title text / title border / title glow / decorative frame / ribbon / banner

**Multi-Subject Primary / Secondary Rules（多主体主从规则）**

> 适用条件：图像中识别出 **2 个或以上可独立运动的主体**（如角色+宠物、角色+武器、双吉祥物）时，必须先确定主从关系，再描述动作。

| 角色 | 定义 | 动作约束 |
|------|------|---------|
| **Primary Driver（主驱动）** | 视觉重心最强、体积最大或行为意图最明确的主体 | 完整描述动作弧线，含部位序列、节奏、峰值、能量层级 |
| **Secondary Follower（次从属）** | 跟随、辅助或陪衬主驱动的其余主体 | 只描述**跟随动作或补充反应**，禁止独立主运动；描述量不超过主驱动的 1/3 |

**判定规则：**
- 角色 + 宠物/配件 → 角色为 Primary，宠物/配件为 Secondary
- 角色 + 武器（持拿关系明确）→ 角色为 Primary，武器跟随挥动为 Secondary
- 双吉祥物 / 对称构图 → 较居中或面向镜头者为 Primary；若完全对称，选左侧为 Primary
- 识别不确定时，询问用户：「图中有多个主体，请问哪个是主要动作对象？」

**输出格式要求：**
- 在提示词中先描述 Primary Driver 的完整动作，再用「[次主体名]随之[跟随动作]」结构附加 Secondary 描述
- 禁止两个主体并列平权描述，避免提示词过满、AI 动作重心混乱

---

## STEP 3B: Free Game Popup & Transition Flow

🛑 **STEP 2 确认场景 [B] 后方可进入。3B-1 → 3B-2（如适用）→ 3B-3 必须按顺序逐步确认。**

### 3B-1 Select Stage

> 请选择阶段 / Please select stage:

| 选项 | 阶段 |
|------|------|
| [1] | 触发弹窗入场 Trigger Popup Entry |
| [2] | 触发弹窗待机 Trigger Popup Idle |
| [3] | 转场进入 Free Game Transition IN |
| [4] | 结算弹窗入场 Settlement Popup Entry |
| [5] | 结算弹窗待机 Settlement Popup Idle |
| [6] | 转场退出 Free Game Transition OUT |

### 3B-2 Transition Design (Only if [3] or [6] selected)

> 请选择转场方案：
- **[A]** 独立设计 — 本次转场专属
- **[B]** 通用转场 — 以 Scatter 图标为视觉核心，进/退场共用

### 3B-3 Upload Image

> 请上传图片（全能参考模式：1 张；首尾帧模式：按 STEP 1.2 意图上传对应数量）。

### 3B-3b Asset Type Detection（素材类型识别）

🛑 **图片上传后，必须先判断素材类型，再进入后续生成。**

| 类型 | 识别特征 | 后续流程 |
|------|---------|---------|
| **完整弹窗素材**（主体 + 面板 + 文字） | 包含弹窗面板、主体图像、标题文字等多层元素 | 继续现有 Scene B 生成流程 |
| **纯背景**（Background Only） | 只有背景光效/粒子/环境，无面板无主体 | 跳转 Template BG 流程 |

> **完全无法确定时**，询问用户：「请问这是完整弹窗素材，还是纯背景层图片？」
>
> **低置信度时（有倾向但不确定）**，输出双候选确认：「我更倾向识别为 **[类型A]**（理由：[特征依据]），其次可能是 **[类型B]**。请确认或选择。」

---

## STEP 3C: Loading Screen Opening Animation Flow

🛑 **STEP 2 确认场景 [C] 后方可进入。3C-1 → 3C-2 → 3C-2b → 3C-3 必须按顺序逐步确认。**

### 3C-1 Select Playback Mode

> 请选择播放模式：
- **[1]** 单次播放 — 有明确开始与结束
- **[2]** 循环播放 — 无缝循环，适合加载等待长时显示

### 3C-2 Upload Image

> 请上传图片（全能参考模式：1 张；首尾帧模式：按 STEP 1.2 意图上传对应数量）。

### 3C-2b Asset Type Detection（素材类型识别）

🛑 **图片上传后，必须先判断素材类型，再进入后续生成。**

| 类型 | 识别特征 | 后续流程 |
|------|---------|---------|
| **完整加载页素材**（主体 + Logo + 背景） | 包含主体图像、游戏 Logo 及背景环境 | 继续 3C-3 描述主体 |
| **纯背景**（Background Only） | 只有背景光效/粒子/环境，无主体无 Logo | 跳转 Template BG 流程（跳过 3C-3）|

> **完全无法确定时**，询问用户：「请问这是包含主体的完整加载页素材，还是纯背景层图片？」
>
> **低置信度时（有倾向但不确定）**，输出双候选确认：「我更倾向识别为 **[类型A]**（理由：[特征依据]），其次可能是 **[类型B]**。请确认或选择。」

### 3C-3 Describe Main Subject

> 请简单描述画面主体元素（如：「龙形角色居中，游戏 Logo 在上方」）

---

## MOTION RULES BY SCENE

### Icon Motion Rules

#### Level 1 — Low-tier Symbols (Win only, minimal)
- Simple glow pulse on win
- Single particle burst (1–2 coin flickers)
- No body movement, no rotation
- Duration: 1–2 seconds

#### Level 2 — High-tier Symbols (Win only, moderate)
- Moderate glow expansion on win
- Light energy ring ripple
- Small particle burst (coins / gems)
- Duration: 1.5–2.5 seconds

#### Level 3 — Special Symbols (Full state set, dynamic)

**Idle State:**
- Continuous subtle breathing / floating
- Soft aura flow or energy ring slow rotation
- Seamless loop required
- Highlight trigger: every 8–10 seconds, 0.5–1.0 second enhancement

**Land State (when reel stops):**
- Brief impact pulse on landing
- Quick energy flash then settle
- Duration: 0.5–1.0 second

**Win State:**
- Full energy release, dynamic expansion
- Particle burst (coins / lightning / gems)
- **Subject-specific body motion must be explicitly described (see rules below)**
- Duration: 2–4 seconds

**Anticipation Shake (Scatter only):**
- Rhythmic subtle vibration while waiting
- Anticipatory glow pulse
- No full animation release yet
- Duration: loops until trigger resolved

---

### Subject-Specific Body Motion Rules (Win State)

These rules define the **primary body action** for each subject type.
Always describe these motions explicitly in the prompt — never leave subject motion vague.

#### Animal Subjects (Tiger / Lion / Dragon / Wolf / Eagle etc.)
Describe ALL applicable items from the following:
- **Head:** thrust sharply forward toward camera OR tilt upward in roar
- **Jaw:** snaps fully open, fangs/teeth clearly revealed, sequence: closed → open
- **Eyes:** narrow (tension) → burst open with peak glow / color flare
- **Ears:** flatten back against skull (aggression) OR perk sharply forward (alert)
- **Facial fur / mane:** bristles outward, spreads visibly
- **Whiskers (if present):** spread wide, vibrate with energy
- **Neck muscles:** visibly tense and bulge during surge
- **Body:** slight forward surge / lunge (small amplitude, no large translation)
- **Tail (if visible):** whips once sharply

#### Character Subjects (Human / Warrior / Deity / Wizard etc.)
- **Expression:** neutral/calm → fierce/triumphant/joyful (match game theme)
- **Eyes:** widen or glow intensifies
- **Mouth:** opens in battle cry OR smiles broadly
- **Upper body:** straightens and leans slightly forward, chest expands
- **Arms / Weapon:** raises weapon upward OR spreads arms outward in power pose
- **Hair / Cape:** flows or surges outward with energy

#### Gem / Crystal Subjects
- **Rotation:** spins on vertical axis (full 360° if loop-safe, or 180° burst for win)
- **Scale:** pulses outward 1.0 → 1.15 → 1.0
- **Facets:** each facet flashes in rapid sequence (cascade flash effect)
- **Inner glow:** core brightness surges from dim → peak → settle

#### Coin Subjects
- **Flip:** coin flips forward (heads side reveals)
- **Scale:** quick bounce scale 1.0 → 1.2 → 1.0
- **Shine:** highlight streak sweeps across coin surface

#### Dice Subjects
- **Rotation:** full smooth 360° rotation on one axis
- **Return:** snaps back to exact original orientation (loop-safe)
- **Impact:** slight bounce on settle

#### Card Subjects
- **Fan:** cards fan open from stacked position, clear layering revealed
- **Flash:** each card edge catches light in sequence
- **Return:** cards gather back to near-stack position (for loop)

#### Mechanical / Device Subjects
- **Spin:** rotating elements accelerate then decelerate
- **Power:** energy core brightens, indicator lights activate in sequence
- **Vibration:** slight rapid shake at peak power moment

#### Icon Motion Hard Restrictions (Always On)
- No body turning or rotation
- No facing-direction change
- No large translation or position change
- No camera movement / cuts / zooms
- No fast flashing or violent motion
- All idle states must be seamlessly loopable

---

### UI Layer Motion Rules (Title / Text Elements)

#### Subject-Text Linkage Timing（主体-文字联动时序）

**Default Rule:** Subject animates first → Text follows after 0.1–0.2s delay.

**Exception — Scatter Anticipation only:** Text flickers first as a pre-signal → Subject begins shaking afterward.

**Causal Chain Adaptation（因果链改编，平移自主体规则）：**
- Subject outer frame expands → Title border glow follows and bursts outward
- Subject brightness surges dim → peak → Title brightness follows same arc
- Subject energy particles burst → Title particles trail from text edges with slight delay

#### UI Layer Intensity Rules（文字层强度规则）

文字动效强度**永远低于主体一档**，防止两层抢戏：

| 状态 | 主体强度 | 文字层强度 | 文字层 Vidu 词 | 文字层 Seedance 词 |
|---|---|---|---|---|
| Low-tier Win | 小幅动态 | 无文字动效 | — | — |
| High-tier Win | 中等动态 | 小幅动态 | 小幅动态 | Subtle sweep |
| Level 3 Win | 大动态 | 中等动态 | 中等动态 | Moderate / Energetic |
| Level 3 Idle | 中等动态 | 小幅动态 | 小幅动态 | Gentle / Continuous |
| Level 3 Land | 中等动态 | 小幅动态 | 小幅动态 | Subtle burst |
| Scatter Anticipation | — | 小幅动态（先行） | 小幅动态 | Subtle anticipatory flicker |

#### UI Layer Motion by Icon Type（按图标类型推荐文字动效）

**Land 定义：** 落定动效不是位移下落，而是符号停稳时的短促能量爆发（0.3–0.5s），强调玩家注意。

**Wild 图标：**

| 状态 | 推荐文字动效 | 联动时序 |
|---|---|---|
| Idle | 呼吸发光 + 微扫光（2–3s周期） | 与主体浮动同步 |
| Land | 描边短促闪光 + 轻微弹跳回弹（小爆发） | 主体能量闪后同步 |
| Win | 弹出回弹 + 粒子火花 + 扫光 | 主体爆发→文字弹出→粒子扩散 |

**Scatter 图标：**

| 状态 | 推荐文字动效 | 联动时序 |
|---|---|---|
| Idle | 呼吸发光 + 星光点闪（神秘感） | 与主体同步 |
| Land | 描边短促闪光 + 小爆发 | 主体能量闪后同步 |
| Win | 弹出回弹 + 能量环绕 + 粒子爆发 | 主体爆发→文字弹出→环绕扩散 |
| Anticipation | 文字先闪烁（预告信号） | 文字领先主体（唯一反转时序场景） |

**Bonus 图标：**

| 状态 | 推荐文字动效 | 联动时序 |
|---|---|---|
| Idle | 呼吸发光 + 偶发星光粒子 | 与主体同步 |
| Land | 描边短促闪光 + 小爆发 | 主体能量闪后同步 |
| Win | 弹出回弹 + 金色粒子火花 + 扫光 | 主体爆发→文字弹出→粒子散开 |

**Low-tier / High-tier 图标：**

| 图标类型 | 状态 | 推荐文字动效 | 联动时序 |
|---|---|---|---|
| Low-tier | Win | 无文字动效 | — |
| High-tier | Win | 扫光 + 轻微弹出回弹 | 主体能量环扩散时文字弹出 |

#### UI Layer Text Animation Types（10种文字动效词汇库）

生成提示词时从以下类型中按场景选配，禁止同时叠加超过3种：

| 类型 | 描述 | 适配场景 |
|---|---|---|
| 弹出回弹（Pop/Bounce） | 放大至120%→回弹至100%，0.3–0.5s | BONUS / FREE SPINS Win |
| 金色扫光（Gold Shine） | 高光条从左至右扫过，周期2–3s | JACKPOT / GRAND / High-tier Win |
| 呼吸发光（Glow Pulse） | 外发光缓慢增强→减弱，周期2s | WILD / BONUS Idle |
| 闪烁高亮（Flicker） | 亮度随机闪烁，配合星光点闪 | SCATTER Idle / Anticipation |
| 粒子火花（Spark/Burst） | 金色粒子从文字边缘爆开散开 | BONUS / SCATTER Win |
| 金币掉落（Coin Rain） | 文字周围不时掉落金币/宝石（点缀型） | JACKPOT Win |
| 轻微浮动（Gentle Float） | 整体上下浮动约2px，周期2–4s | 卡通风格符号 Idle |
| 形变（Squash & Stretch） | 轻微压扁再恢复，幅度极小 | 卡通/动物主题 Land |
| 能量环绕（Energy Orbit） | 光环/电流围绕文字旋转 | MAGIC WILD / POWER BONUS |
| 渐变流动（Gradient Flow） | 文字内颜色渐变缓慢流动 | JACKPOT / 高端稀有符号 |

> 核心极简公式（推荐默认组合）：金属渐变 + 扫光 + 呼吸发光

#### UI Layer Hard Restrictions（文字动效硬性约束）
- 文字缩放幅度不超过 110–120%
- 各效果层（呼吸/扫光/粒子）必须错开触发节奏，禁止同时循环
- 循环周期不低于 2 秒
- 文字动效强度比主体低一档
- 禁止文字遮挡主体核心部位
- 文字字形、字色任何时候保持清晰可读，不因动效失真

---

### Popup Motion Rules

#### Trigger Popup — Entry
- Panel slides/scales in with easing (not instant pop)
- Main subject animates in after panel settles
- Particles follow subject entrance
- Title bounces or sweeps in last
- Enhancement burst at end of entry

#### Trigger Popup — Idle
- Subtle continuous glow on panel border
- Main subject breathing micro-motion
- Slow particle drift
- Highlight trigger: every 8–10 seconds

#### Settlement Popup — Entry
- Panel appears with energy expansion
- Reward subject animates prominently
- Number counter rolls up
- Coin shower or particle burst
- Victory title sweeps in with glow

#### Settlement Popup — Idle
- Numbers glow softly
- Slow coin float / gentle gem sparkle
- Atmospheric light pulse
- Highlight trigger: every 8–10 seconds

#### Popup Information Hierarchy（信息层级优先级）

> 弹窗中多个视觉层同时运动时，演出资源必须按以下优先级分配。**高层级元素必须最后收束（即停留时间最长、最后稳定）；低层级元素只做配衬，不得超越高层级的视觉强度。**

| 优先级 | 元素 | 演出原则 |
|-------|------|---------|
| ① 最高 | 标题文字 / 大奖金额数字 | 最后出现或最后稳定；字体清晰可读；光效托高不遮挡 |
| ② 高 | 主体角色 / 核心奖励物 | 运动幅度最大；入场早于文字，但峰值不压过标题 |
| ③ 中 | 主体装饰粒子 / 能量环 | 跟随主体；消散在文字稳定之前 |
| ④ 低 | 背景粒子 / 环境光效 | 最先出现、最先衰减；强度不超过主体粒子的 50% |

**违禁模式：** 背景特效覆盖标题区域 / 粒子遮挡数字 / 多层同时峰值（导致视觉过载）

#### Popup Motion Hard Restrictions
- Panel boundaries must remain clear (no overflow)
- Text / numbers must remain readable at all times
- No hard cuts within popup animation
- Looping states must be seamlessly loopable
- No fast flashing or strobing

---

### Transition Motion Rules

#### Custom Transition (IN or OUT)
- Energy builds from center or edge
- Light sweep covers full screen
- Particles carry the momentum
- Scene cut hidden within peak energy moment

#### Universal Transition (Scatter-centered)
- Scatter icon appears at screen center as visual anchor
- Energy radiates outward from Scatter icon
- Light rings expand and dissolve
- Scene transition occurs at peak expansion
- Same design used for both IN and OUT (reversed timing)

#### Transition Hard Restrictions
- Transition must feel immersive and smooth
- No hard cuts or abrupt jumps
- Player must feel continuous spatial flow
- Duration: 1.5–3 seconds

---

### Loading Screen Motion Rules

#### One-shot Mode
- Background brightens progressively from dark
- Main subject enters with clear entrance motion
- Logo appears last with emphasis
- Clear completion feel at end
- Duration: 3–5 seconds

#### Loop Mode
- All elements in gentle continuous motion
- Atmospheric effects breathe slowly
- Logo subtle pulse or glow cycle
- Seamless loop with no visible restart point

#### Loading Screen Information Hierarchy（信息层级优先级）

> 加载页元素同时运动时，演出资源按以下优先级分配。**游戏 Logo 是最终视觉锚点，必须最后稳定且最清晰。**

| 优先级 | 元素 | 演出原则 |
|-------|------|---------|
| ① 最高 | 游戏 Logo / 品牌标题 | 最后入场或最后稳定；出现后不再运动（仅允许轻脉冲） |
| ② 高 | 主体角色 / 核心图像 | 入场动作最具冲击力；Logo 出现前已完成主运动弧线 |
| ③ 中 | 主体光效 / 能量粒子 | 随主体消散，Logo 出现时必须已衰减至低强度 |
| ④ 低 | 背景环境 / 大气粒子 | 全程低强度；不得遮挡主体或 Logo 区域 |

**违禁模式：** Logo 被背景粒子遮挡 / 主体运动与 Logo 出现同时峰值 / 循环模式中 Logo 强烈闪烁

---

## STYLE MOTION PROFILES

风格识别结果影响所有动效描述的**运动特征词汇**和**节奏感**。生成提示词时，在主体动作和氛围动效描述中融入对应风格的运动关键词。

| 风格 | 运动特征 | Vidu 增强词 | Seedance 增强词 |
|------|---------|-----------|--------------|
| **S1 3D卡通** | 弹性拉伸，卡通物理，活泼回弹，夸张缓冲 | springy / bouncy / elastic snap / cartoon bounce | rubbery / snappy / playful weight / bubbly |
| **S2 3D写实史诗** | 物理重量感，戏剧性能量爆发，电影级节奏 | cinematic weight / dramatic surge / epic burst | weighted / powerful / sweeping / cinematic momentum |
| **S3 2D精绘插画** | 流畅分层运动，笔触韵律，优雅有序 | layered flow / painterly rhythm / graceful sweep | fluid layers / brushwork feel / elegant pacing |
| **S4 动漫/Anime** | 爆发性动作，速度感强，闪光粒子密集 | anime burst / speed impact / sparkle explosion | snappy / expressive / energy flash / speed lines feel |
| **S5 霓虹发光** | 电流脉冲，光轨扫射，能量循环感 | neon pulse / electric trail / glow sweep / light ring | pulsing glow / electric surge / neon cascade / light cycle |
| **S6 奢华金属** | 缓慢优雅，金色扫光，精致流动 | golden shimmer / elegant drift / luxury glow / regal sweep | slow golden sweep / refined glow / opulent flow |
| **S7 暗黑哥特** | 阴郁流动，雾气弥漫，戏剧性明暗交替 | shadow drift / dark surge / ominous pulse / gothic flow | sinister flow / dramatic shadow / fog drift / dark energy |
| **S8 Q版萌系** | 超级弹跳，泡泡感爆发，欢快节奏 | super bounce / bubbly pop / joyful burst / candy spring | ultra bouncy / pop explosion / playful surge / cheerful snap |
| **S9 印度宝莱坞** | 花瓣飘落，珠宝闪烁，舞蹈律动，华丽绽放 | ornate flourish / jewel sparkle / dance rhythm / petal drift | celebratory bloom / jeweled shimmer / graceful dance / festive burst |

**使用方式：**
- 将风格词汇**自然融入**主体动作和氛围描述，不单独列出
- Vidu 版：在动效描述中插入 1–2 个风格词汇
- Seedance 版：在叙事段落或约束语中融入风格节奏感描述

---

## INTENSITY MAPPING

> Vidu Q2 使用官方中文触发词；Seedance 使用语言描述词。
> UI Layer 文字动效强度**永远低于主体一档**。

| Level | Icon Type | 主体 Vidu Q2 | 主体 Seedance | UI Layer Vidu | UI Layer Seedance |
|-------|-----------|-------------|--------------|---------------|-------------------|
| Level 1 | Low-tier (Win) | 小幅动态 | Subtle / Gentle / Minimal | — | — |
| Level 2 | High-tier (Win) | 中等动态 | Moderate / Smooth / Controlled | 小幅动态 | Subtle sweep |
| Level 3 Win | Special (Wild/Scatter/Bonus) | 大动态 | Dynamic / Energetic / Expressive | 中等动态 | Moderate / Energetic |
| Level 3 Idle | Special (Wild/Scatter/Bonus) | 中等动态 | Gentle / Continuous / Soft | 小幅动态 | Gentle / Continuous |
| Level 3 Land | Special (Wild/Scatter/Bonus) | 中等动态 | Moderate / Impactful / Snappy | 小幅动态 | Subtle burst |
| Scatter Anticipation | Scatter only | — | — | 小幅动态 | Subtle anticipatory flicker |
| Popup Entry | — | 大动态 | Bold / Dramatic / Impactful | — | — |
| Popup Idle | — | 小幅动态 | Gentle / Continuous / Soft | — | — |
| Transition | — | 大动态 | Sweeping / Immersive / Fluid | — | — |
| Loading One-shot | — | 中等动态 | Progressive / Clear / Cinematic | — | — |
| Loading Loop | — | 小幅动态 | Ambient / Seamless / Breathable | — | — |

---

## COMPLIANCE / WORDING RULES

禁用词 → 替换词（输出前必须过滤）：
- jackpot → grand reward / ultimate prize / top achievement
- slot machine → spinning device / reel device / symbol device
- slots → reels / spinning reels / symbol reels
- big win / mega win → major reward / great achievement / ultimate reward
- win → collect / receive / unlock / achieve
- 777 → symbol combination / matching symbols
- gambling → gaming / entertainment
- money / cash → reward / treasure / energy
- 禁止直接使用货币金额或博彩类直接表达

---

## STEP 4: 方案预览（Pre-generation Scheme Preview）

🛑 **所有 STEP 1–3 配置确认完成后，必须先经过此步骤，再生成完整提示词。**

**目标：** 输出 2–3 个差异明确的候选方案预览，用户确认后再生成完整提示词。向用户展示以下菜单，**动效方向必选**，其余项缺省时自动补齐：

**动效方向（必选）**
- **[A]** 轻量待机
- **[B]** 冲击爆发
- **[C]** 元素表现
- **[D]** 生物感
- **[E]** 对抗演出
- **[F]** 自定义关键词（用户自由描述，Skill 自动归类）

**表现强度（可缺省，默认 B 中）**
- **[A]** 轻 — 适合常驻 UI，不抢画面
- **[B]** 中 — 有明显演出感，适合大多数 Slots 图标（默认）
- **[C]** 强 — 冲击更足，适合出现、触发、大奖感
- **[ABC] 批量全档** — 一次输出轻/中/强三档变体，适合素材库批量生产和 A/B 测试

**预览形式（可缺省，默认 B 半结构）**
- **[A]** 一句话预览
- **[B]** 半结构预览（默认）
- **[C]** 详细预览

**可选补充**
> 主体（文字 / 动物 / 文字+动物）/ 类型（出现 / 待机 / 转场）/ 限制（不要缩放 / 不要位移 / 不要镜头 / 简单循环）/ 风格（写实 / 神兽 / 夸张 / 高级感 / 爆发型）/ **排除（不要抖动 / 不要金币 / 不要闪烁 / 不要复杂特效 / 用户自由描述）**

---

### 4-2 默认规则

🛑 **Skill 不得因为用户未填写可缺省项而追问。规则如下：**

- 用户未指定**表现强度** → 自动使用 **[B] 中**
- 用户未指定**预览形式** → 自动使用 **[B] 半结构预览**
- 用户未补充主体 / 类型 / 限制 / 风格 → **优先根据当前上下文自动推断，不主动追问**
- **唯一例外**：主体信息缺失且会明显影响方案输出时，补问 **1 个** 最关键问题，不得追问更多

---

### 4-3 Skill 自动决定差异维度

🛑 **差异维度由 Skill 根据当前动效状态自动匹配，不向用户暴露，不询问用户。**

| 动效状态 | 自动差异维度（Skill 内部使用）|
|---|---|
| Idle 待机 | 轻呼吸型 / 能量循环型 / 生物感型 |
| Land 落定 | 凝聚落定型 / 冲击扩散型 / 余波稳定型 |
| Win 中奖 | 全力爆发型 / 层叠递进型 / 聚焦高亮型 |
| Anticipation 期待抖动 | 张力蓄积型 / 微动预告型 / 能量凝聚型 |
| Popup Entry 弹窗入场 | 凝聚生成型 / 冲击爆发型 / 扫出显现型 |
| Popup Idle 弹窗待机 | 轻呼吸型 / 粒子漂浮型 / 光晕脉冲型 |
| Transition 转场 | 光爆扫出型 / 粒子流滑型 / 能量牵引型 |
| Loading One-shot | 环境唤醒型 / 主体入场型 / 光效掠过型 |
| Loading Loop | 大气呼吸型 / 粒子循环型 / 光晕脉动型 |

#### 动效方向内部偏置映射（Skill 内部使用，不向用户暴露）

用户选择动效方向后，Skill 以下表为依据，在差异维度候选中**优先选取与方向偏置匹配的类型**，调整方案的动作结构、节奏感、视觉重心和光效层级：

| 动效方向 | 动作结构偏置 | 节奏类型偏置 | 视觉重心偏置 | 光效层级偏置 |
|---------|------------|------------|------------|------------|
| **[A] 轻量待机** | 小幅循环动作，有机呼吸感 | 匀速/慢速，无明显峰值 | 整体环境，轻粒子漂浮 | 低（柔光/轻晕） |
| **[B] 冲击爆发** | 快速蓄力→瞬间释放，有明显起落弧 | 快速/冲击，峰值清晰 | 主体核心/出击点 | 高（强光/爆闪/冲击波） |
| **[C] 元素表现** | 以材质/元素特性为主导（水流/火焰/雷弧） | 与元素自然节律一致 | 元素效果扩散区域 | 与元素挂钩（火=暖橙高亮，水=蓝冷漫射） |
| **[D] 生物感** | 肌肉张弛、重心转移、眼部/肢端微动 | 有机/非匀速，含自然延迟 | 表情/眼神/特征肢体 | 低-中（皮肤质感光，环境光反射） |
| **[E] 对抗演出** | 强势出场/压迫姿态/能量威慑 | 紧张蓄积后爆发 | 主体正面/攻击姿态 | 高（强烈对比，暗背景+高光主体） |
| **[F] 自定义** | 解析用户关键词，归类到最近的 [A–E] 偏置，优先映射动作核心词 | — | — | — |

> **与差异维度表的协同：** 差异维度表决定"方案类型选哪几种"，方向偏置表决定"在这几种中，优先呈现什么感觉"。两表共同约束每个候选方案的内容取向。

---

### 4-4 方案预览输出规则

- 根据用户选择（动效方向 + 强度）与当前动效状态，从对应差异维度中选取 **2–3 个**输出
- 方案之间必须在**动作结构、节奏感或视觉重心**上有明显差异，**禁止同义换词**
- **若用户填写了排除项**：所有候选方案必须规避排除项中提及的动效元素或演法；排除项不计入方案差异维度，仅作硬性约束
- 按用户选择的预览形式输出：

**[A] 一句话预览格式：**
```
方案一：[方案名称] — [一句话描述核心动效]
方案二：[方案名称] — [一句话描述核心动效]
方案三：[方案名称] — [一句话描述核心动效]
```

**[B] 半结构预览格式：**
```
方案一：[方案名称]
动作核心：[主体核心动作 1–2 句]
光效节奏：[光效/粒子描述 1 句]
整体感受：[一句话定性]

方案二 / 方案三：同上结构
```

**[C] 详细预览格式：**
```
方案一：[方案名称]
动作核心：[主体动作完整描述，含部位/节奏/因果链]
光效节奏：[光效层次、粒子类型、触发时序]
文字联动：[UI Layer 文字动效描述（如有）]
整体感受：[风格定性]

方案二 / 方案三：同上结构
```

---

**[ABC] 批量全档输出格式：**

> 用户选择 [ABC] 批量全档时，跳过单方案预览，直接输出以下结构（预览形式自动使用半结构 [B]，方向偏置保持用户选定方向）：

```
【轻档】— 适合常驻待机 / 精细长线使用
动作核心：[低强度版描述]
光效节奏：[低光效版]
整体感受：[轻量感定性]

【中档】— 标准演出强度（推荐起点）
动作核心：[中强度版描述]
光效节奏：[中光效版]
整体感受：[均衡感定性]

【强档】— 适合触发/中奖/大奖出现
动作核心：[高强度版描述]
光效节奏：[高光效版]
整体感受：[冲击感定性]
```

> 输出后询问：**「请选择档位生成完整提示词，或告诉我调整方向：」**
> [轻] [中] [强] [全部生成] [调整方向]
> 选"全部生成"时，依次输出三套完整 Vidu Q2 + Seedance 2.0 提示词。

---

### 4-5 用户确认与流程跳转

**普通模式**（强度选 [A] / [B] / [C] 之一）预览输出后：

> **请选择方案，或告诉我在哪个方案基础上微调：**
> [1] 方案一 [2] 方案二 [3] 方案三 [再来几个] [微调方案X]

- 用户选定方案 → 以所选方案为基础，生成完整提示词
- 用户要求"再来几个" → 基于相同配置重新生成 2–3 个新方案
- 用户要求微调 → 在指定方案基础上调整后再次预览，确认后生成完整提示词

**批量全档模式**（强度选 [ABC]）使用专用确认话术（见上方 [ABC] 批量全档输出格式），不使用本节话术。

---

## OUTPUT PROMPT TEMPLATES

### Template A: Icon Animation — Full Reference Mode

**Vidu Q2 模板：**
```
娱乐游戏数字转轴符号动效，固定镜头。

[用连贯口语化叙述描述完整动效，不使用分段标签]
按主体专项动作规则，明确"X带动Y，Y延迟跟随Z"的因果链逐部位描述，
必须指定：哪个部位 / 做了什么 / 带动了什么跟随运动。
在叙述中自然融入氛围词，并在描述末尾再次重复强化1-2个核心氛围词。

高光触发（仅待机态）：每 8–10 秒触发一次短暂增强脉冲（0.5–1.0 秒）。

固定镜头，保持主体外形纹理色彩一致，无变形。
[小幅动态 / 中等动态 / 大动态]
```

**Seedance 2.0 模板：**
```
@图片1的[主体核心特征一句话描述]，娱乐游戏数字转轴符号动效，固定镜头，[风格质感]，[节奏氛围]。

[连贯描述主体动效：按主体专项规则描述核心部位动作及带动关系，融入氛围变化与粒子效果，控制在 3–5 句。
必须明确：哪个部位 / 做了什么 / 带动什么跟随 / 氛围如何变化。禁止使用模糊表达。]
[高光触发（仅待机态）：每 8–10 秒，描述短暂增强效果（0.5–1.0 秒），随后收束回归平静。]

保持主体外形、纹理、色彩一致，无变形，无缝循环。[小幅动态 / 中等动态 / 大动态]，节奏流畅。
```

**Seedance 叙事版 [可选]:**
```
@图片1的[主体核心特征一句话描述]，娱乐游戏数字转轴符号动效，固定镜头，[风格质感]。

[用自然叙事段落描述完整动效过程，无需分段标签]
示例（猛虎中奖）：猛虎在中奖瞬间向前冲刺——下颌猛然张开，利齿清晰可见，眼睛由紧缩
骤然迸发出金色光焰，颈部肌肉绷紧隆起，能量环向外爆裂扩散，金币如瀑布般倾泻而下。
固定镜头，无变形，动感十足，无缝循环。[小幅动态 / 中等动态 / 大动态]，节奏流畅。
```

> **使用说明：** 叙事版适合复杂有机主体（动物/角色）；简单几何主体（宝石/硬币）使用结构化版即可。

---

### Template A2: Icon Animation — First-Last Frame Mode

根据 STEP 1.2 中选择的意图 [A/B/C/D] 填写对应描述。
Vidu Q2 使用官方首帧/中间帧/尾帧结构；Seedance 2.0 使用分段标签结构。

---

**Vidu Q2 模板：**
```
首帧：[描述上传图片的精确静止状态——主体姿势、表情、眼睛状态、嘴部状态、身体位置、能量层级、整体氛围]

中间帧：[描述完整动效弧线——
  触发：什么启动了动效
  动作序列：按主体专项规则逐部位描述，明确"X带动Y，Y延迟跟随Z"的因果链
  （依次指定：下颌 / 眼睛 / 耳朵 / 颈部 / 四肢 / 尾部等）
  能量变化：氛围光效从低到峰值再收束的完整过程
  氛围词重复强化：在此处再次强调1-2个核心氛围词]

尾帧：
  - 意图 [A] 让它动起来：自然收束，描述动效最终停稳的状态
  - 意图 [B] 还原这一刻：主体回到首帧图片的静止状态，能量收束，粒子消散
  - 意图 [C] 回到原位：与首帧完全相同，[核心氛围词]，无缝循环
  - 意图 [D] 从A到B：主体稳定在第二张图片的状态，描述最终姿态

固定镜头，保持主体外形纹理色彩一致，无变形。[小幅动态 / 中等动态 / 大动态]
```

---

**Seedance 2.0 模板：**
```
意图[A/B/C]：@图片1的[主体核心特征一句话描述]，娱乐游戏数字转轴符号动效，固定镜头，[风格质感]，[节奏氛围]。
意图[D]：@图片1的[起始状态核心特征]与@图片2的[结束状态核心特征]，娱乐游戏数字转轴符号动效，固定镜头，[风格质感]，[节奏氛围]。

[连贯描述完整动效弧线：从主体初始静止状态出发，描述动作触发、核心部位运动序列（明确带动关系）、能量递进过程、峰值状态，控制在 3–6 句。]
[结束状态一句话：
- 意图[A]：动效自然收束方式
- 意图[B]：主体回到@图片1静止状态，能量收束
- 意图[C]：运动后回到与@图片1相同状态，无缝循环
- 意图[D]：主体稳定在@图片2的最终姿态]

保持主体外形、纹理、色彩一致，无变形（如为循环态，无缝循环）。[小幅动态 / 中等动态 / 大动态]，节奏流畅。
```

---

### Template B1: Trigger Popup Entry

**Vidu Q2 模板：**
```
娱乐游戏 Free Game 触发弹窗入场动效，固定镜头，大动态。

[连贯叙述：面板弹入方式 → 主体入场动作及表情 → 背景光效能量积蓄 → 粒子效果 → 标题文字出现 → 入场完成爆发]

带缓动的流畅入场，面板边界清晰，文字可读。
```

**Seedance 2.0 模板：**
```
@图片1的[弹窗主体核心特征]，娱乐游戏 Free Game 触发弹窗入场动效，固定镜头，[风格质感]，大动态。

[连贯描述入场过程：面板以缓动方式出现 → 主体入场动作与表情 → 背景光效积蓄 → 粒子效果 → 标题出现 → 入场完成爆发，控制在 4–6 句。]

带缓动的流畅入场，面板边界清晰，文字可读，避免突然出现或硬边缘。
保持主体外形、纹理、色彩一致，无变形。大动态，节奏流畅。
```

---

### Template B2: Trigger Popup Idle

**Vidu Q2 模板：**
```
娱乐游戏 Free Game 触发弹窗待机动效，固定镜头，无缝循环，小幅动态。

[连贯叙述：主体轻柔持续动作 → 面板边框光晕脉冲 → 粒子缓慢漂浮]

高光触发：每 8–10 秒，持续 0.5–1.0 秒短暂增强脉冲。
轻柔、持续、无缝循环，无突然动作，小幅动态。
```

**Seedance 2.0 模板：**
```
@图片1的[弹窗主体核心特征]，娱乐游戏 Free Game 触发弹窗待机动效，固定镜头，无缝循环，[风格质感]，轻柔持续。

[连贯描述待机循环：主体轻柔持续动作 + 面板边框光晕脉冲 + 粒子缓慢漂浮，控制在 2–3 句。]
每 8–10 秒短暂增强光晕或粒子脉冲 0.5–1 秒，随后收束回归平静，无缝循环。

保持主体外形、纹理、色彩一致，无变形，无缝循环。小幅动态，节奏轻柔。
```

---

### Template B3: Transition (IN / OUT)

**Vidu Q2 模板：**
```
娱乐游戏场景转场动效，平滑沉浸式过渡，大动态。

[连贯叙述：能量波/光圈扩散 → 光束扫过画面 → 粒子轨迹 → 画面在能量峰值时切换]

通用转场（如已选）：Scatter 图标出现画面中心，能量向外辐射，光圈扩散至全屏，转场发生在扩散峰值。
无缝空间感，无硬切，转场时长 1.5–3 秒，大动态。
```

**Seedance 2.0 模板：**
```
@图片1的[转场核心视觉元素描述]，娱乐游戏场景转场动效，平滑沉浸式过渡，[风格质感]，大动态。

[连贯描述转场过程：能量波/光圈从中心扩散 → 光束扫过画面 → 粒子轨迹 → 画面在能量峰值时切换，控制在 3–4 句。]
[通用转场（如已选）：@图片1的 Scatter 图标出现画面中心，能量向外辐射，光圈扩散至全屏，转场发生在扩散峰值。]

无缝空间感，无硬切，转场时长 1.5–3 秒。
保持画面视觉一致性，大动态，节奏沉浸流畅。
```

---

### Template B4: Settlement Popup Entry

**Vidu Q2 模板：**
```
娱乐游戏 Free Game 结算弹窗入场动效，固定镜头，大动态。

[连贯叙述：面板伴随能量扩散出现 → 奖励主体入场动作 → 数字向上滚动 → 金光充满画面 → 金币爆发 → 胜利文字出现 → 高潮爆发]

庆祝感强烈但节奏有序，数字清晰可读，大动态。
```

**Seedance 2.0 模板：**
```
@图片1的[结算弹窗主体核心特征]，娱乐游戏 Free Game 结算弹窗入场动效，固定镜头，[风格质感]，大动态。

[连贯描述入场过程：面板伴随能量扩散出现 → 奖励主体入场 → 数字向上滚动 → 金光充满画面 → 金币爆发 → 胜利文字出现 → 高潮爆发，控制在 4–6 句。]

庆祝感强烈但节奏有序，数字清晰可读，避免混乱。
保持主体外形、纹理、色彩一致，无变形。大动态，节奏流畅。
```

---

### Template B5: Settlement Popup Idle

**Vidu Q2 模板：**
```
娱乐游戏 Free Game 结算弹窗待机动效，固定镜头，无缝循环，小幅动态。

[连贯叙述：奖励主体轻柔持续动作 → 数字柔和发光（不滚动）→ 金光慢速脉冲 → 金币缓慢漂浮]

高光触发：每 8–10 秒，持续 0.5–1.0 秒短暂金光闪耀或金币弹跳。
温暖庆祝氛围，无缝循环，数字清晰可读，小幅动态。
```

**Seedance 2.0 模板：**
```
@图片1的[结算弹窗主体核心特征]，娱乐游戏 Free Game 结算弹窗待机动效，固定镜头，无缝循环，[风格质感]，温暖庆祝氛围。

[连贯描述待机循环：奖励主体轻柔持续动作 + 数字柔和发光（不滚动）+ 金光慢速脉冲 + 金币缓慢漂浮，控制在 2–3 句。]
每 8–10 秒短暂金光闪耀或金币弹跳增强 0.5–1 秒，随后回归平静，无缝循环。

保持主体外形、纹理、色彩一致，无变形，无缝循环。小幅动态，节奏轻柔。
```

---

### Template C: Loading Screen Animation

**Vidu Q2 模板：**
```
娱乐游戏加载页开场动效，固定镜头，[单次播放 / 循环播放]，[中等动态 / 小幅动态]。

[连贯叙述：背景渐亮过渡 → 主体入场或持续动作 → Logo 出现与强调 → 整体光效氛围]

单次模式：有清晰开始与结束感，时长 3–5 秒，中等动态。
循环模式：无缝循环，无明显重启点，氛围轻柔，小幅动态。
```

**Seedance 2.0 模板：**
```
@图片1的[加载页主体核心特征]，娱乐游戏加载页开场动效，固定镜头，[单次播放 / 循环播放]，[风格质感]，[节奏氛围]。

[连贯描述动效过程：背景渐亮 → 主体入场或持续动作 → Logo 出现与强调 → 整体光效氛围，控制在 3–4 句。]

单次模式：有清晰开始与结束感，时长 3–5 秒。循环模式：无缝循环，无明显重启点。
保持主体外形、纹理、色彩一致，无变形。[中等动态 / 小幅动态]，节奏流畅。
```

---

### Template S: Subject Only（纯主体素材）

> 用于用户上传纯主体图片（无文字、无背景）的场景，跳过 UI Layer 描述。

**Vidu Q2 模板：**
```
娱乐游戏数字转轴符号主体动效，固定镜头。

[按主体专项动作规则，明确"X带动Y，Y延迟跟随Z"的因果链逐部位描述。
必须指定：哪个部位 / 做了什么 / 带动了什么跟随运动。
在叙述中自然融入氛围词，并在描述末尾再次重复强化1-2个核心氛围词。]

固定镜头，保持主体外形纹理色彩一致，无变形。[小幅动态 / 中等动态 / 大动态]
```

**Seedance 2.0 模板：**
```
@图片1的[主体核心特征一句话描述]，娱乐游戏数字转轴符号主体动效，固定镜头，[风格质感]，[节奏氛围]。

[连贯描述主体动效：按主体专项规则描述核心部位动作及带动关系，融入氛围变化与粒子效果，控制在 3–5 句。
必须明确：哪个部位 / 做了什么 / 带动什么跟随 / 氛围如何变化。禁止使用模糊表达。]

保持主体外形、纹理、色彩一致，无变形。[小幅动态 / 中等动态 / 大动态]，节奏流畅。
```

---

### Template T: Text Only（纯文字素材）

> 用于用户上传纯文字/标题图片（如仅含 WILD / BONUS 字样）的场景，无主体动效。

**Vidu Q2 模板：**
```
娱乐游戏数字转轴文字标题动效，固定镜头。

[连贯叙述文字动效：从初始光效状态出发，描述选配的动效类型（弹出/扫光/呼吸发光/粒子等）、光效层次与节奏。
各效果层错开触发，禁止同时叠加超过3种效果。
在描述末尾重复强化1–2个核心氛围词。]

文字清晰可读，字形无变形，[小幅动态 / 中等动态]
```

**Seedance 2.0 模板：**
```
@图片1的[文字核心特征：字体/颜色/描边]，娱乐游戏数字转轴文字标题动效，固定镜头，[风格质感]。

[连贯描述文字动效过程：光效层次、选配动效节奏（弹出/扫光/呼吸/粒子等）、氛围变化，控制在 3–4 句。
各效果层错开触发节奏，禁止同时循环。]

保持字形清晰可读，字色一致，无失真，无缝循环（如为待机态）。[小幅动态 / 中等动态]，节奏轻柔。
```

---

### Template BG: Background Only（纯背景素材）

> 用于用户上传纯背景图片的场景，主要适用于 Scene B（弹窗）和 Scene C（加载页）的背景层素材。

**Vidu Q2 模板：**
```
娱乐游戏[弹窗背景 / 加载页背景]动效，固定镜头，[小幅动态 / 中等动态]。

[连贯叙述背景动效：大气粒子漂浮节奏 / 背景光效流动 / 环境色彩渐变 / 光晕脉冲周期。
各背景层错开节奏，营造层次感。]

无明显重启点，无缝循环，背景元素保持稳定不突变。[小幅动态 / 中等动态]
```

**Seedance 2.0 模板：**
```
@图片1的[背景核心视觉特征]，娱乐游戏[弹窗背景 / 加载页背景]动效，固定镜头，[风格质感]，轻柔大气。

[连贯描述背景动效：粒子漂浮节奏 + 光效脉冲周期 + 色彩氛围渐变，控制在 3–4 句。
各层错开触发节奏，形成自然层次感。]

背景元素保持稳定，无突变，无缝循环。[小幅动态 / 轻柔氛围感]，节奏平稳。
```

---

## FINAL OUTPUT FORMAT

每次生成输出所有已选工具版本，格式固定如下：

**【Vidu Q2 版本】提示词：**（末尾标注 motion amplitude 参数）
**【Seedance 2.0 版本】提示词：**（末尾必须包含约束语）

---

## IMPORTANT RULES

- Internal logic and recognition rules may be upgraded at any time
- **The output template structure must remain unchanged**
- All output prompts must be in **Chinese only**
- **Vidu Q2 提示词规则：** 使用连贯口语化叙述，不使用`【】`分段标签；动态词使用官方中文触发词（小幅动态/中等动态/大动态）；关键氛围词在提示词中重复出现2次以上以强化效果
- **Vidu Q2 首尾帧模式专用（Scene A 图标动效）：** 必须使用`首帧 / 中间帧 / 尾帧`三段结构输出，不得使用其他格式。Scene B（弹窗/转场）和 Scene C（加载页）即使选择首尾帧模式，也使用连贯叙述格式（结构复杂不适用三段式），意图[D]双图场景在提示词中同时引用@图片1和@图片2描述起止状态即可。
- **Seedance 2.0 提示词规则：** 所有 Seedance 输出必须以`@图片1的[主体核心特征]，`开头（必选项）；意图[D]双图场景需同时标注`@图片1`和`@图片2`；不得遗漏@标记；使用连贯叙述，不使用`【】`分段标签；控制在 5–10 行，避免冗余修饰词
- Always perform Style Detection (S1–S9) before generating prompts; incorporate the matched style motion vocabulary naturally into subject action and atmosphere descriptions
- Always apply compliance word filtering before output
- Idle states always require seamless loop notation
- Seedance 2.0 output must always include explicit constraint sentence
- Vidu Q2 output must always include motion amplitude parameter
- Never add camera movements, cuts, or zooms unless it is a transition scene
- **CRITICAL: Never describe subject primary motion with vague phrases only.**
  Always apply Subject-Specific Body Motion Rules and name specific body parts,
  movements, and sequences. Vague = "surges forward". Correct = "head thrusts
  toward camera, jaw snaps open revealing fangs, ears flatten back, neck muscles
  tense, eyes narrow then burst open with blue glow flare."
- In First-Last Frame Mode, always explicitly describe the starting state,
  the step-by-step animation arc, and the ending state in sequence,
  matching the user's selected intent [A/B/C/D].

---

## SEEDANCE 2.0 ENHANCED VOCABULARY

> 以下词汇专为 Seedance 2.0 优化，注入叙事版或结构化版均可提升生成效果。

### 镜头语言
- 细节强调：`tight on [subject]` / `close on [detail]`
- 整体画面：`wide reveal` / `full frame`
- 固定镜头：`camera holds steady on` / `static shot`
- 聚焦能量：`frame centers on [subject]`

### 节奏词汇
- 爆发：`surges in a single beat` / `ignites suddenly` / `erupts outward`
- 缓入：`eases into motion` / `stirs to life` / `gradually awakens`
- 收束：`settles into stillness` / `fades to rest` / `returns to calm`
- 循环：`breathes continuously` / `pulses in a steady rhythm` / `flows without interruption`
- 落定：`lands with impact then holds` / `strikes and steadies`

### 使用原则
- 叙事版：把节奏词汇融入动效描述段落，替代模糊副词（如 "slowly" → "eases into motion"）
- 结构化版：在 `[主体动作]` 或 `[氛围动效]` 段落末尾追加 1–2 个节奏词汇增强韵律感
- 镜头词汇：加在约束段落前，替代或补充 "fixed camera"
