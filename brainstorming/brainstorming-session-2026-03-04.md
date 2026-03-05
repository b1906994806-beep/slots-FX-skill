---
stepsCompleted: [1, 2, 3]
inputDocuments: ['lobby_icon_animation_skill_v3_claude.md']
session_topic: 'Slots 游戏动效 AI 提示词生成 Skill 设计'
session_goals: '基于现有 Lobby Icon Skill 框架，扩展设计覆盖 Slots 内部图标、Free Game 弹窗、加载页开场动画的统一提示词生成工作流'
selected_approach: 'ai-recommended'
techniques_used: ['question-storming', 'first-principles-thinking', 'scamper']
ideas_generated: []
context_file: 'lobby_icon_animation_skill_v3_claude.md'
---

# Brainstorming Session Results

**Facilitator:** Admin
**Date:** 2026-03-04

---

## Session Overview

**Topic:** Slots 游戏动效 AI 提示词生成 Skill 设计
**Goals:** 基于现有 Lobby Icon Skill 框架，扩展设计覆盖 Slots 内部图标、Free Game 弹窗、加载页开场动画的统一提示词生成工作流

### Context Guidance

参考基线：`lobby_icon_animation_skill_v3_claude.md`（已验证的 Lobby 大厅待机图标动效 Skill）

---

## 现有 Lobby Icon Skill 可复用经验

| 模式 | 说明 |
|------|------|
| 零配置输入 | 用户只上传图片，Skill 自动处理一切 |
| 三段式分析管线 | 图片输入 → 主体识别（分类）→ 图层拆解 → 动效映射 |
| 动效层级体系 | 主动效 → 次动效 → 点缀动效 → 高光触发 |
| 约束优先设计 | Always On 约束先于创意规则，明确禁止项比推荐项更重要 |
| 输出模板与逻辑解耦 | 输出结构固定不变，内部识别逻辑可随时升级 |
| 合规词汇替换表 | 禁用词 → 中性替换词映射，可扩展 |

---

## 完整 Skill 设计方案

### 一、全局配置（流程开始时一次选定）

```
1. 选择目标工具
   ├── Vidu Q2
   └── Seedance 2.0

2. 选择生成模式
   ├── 全能参考模式（上传参考图，AI 全程参照）
   └── 首尾帧模式（指定首帧 / 尾帧）
       └── 图标场景：同一张图，用户选首帧或尾帧
           弹窗/加载页：分别上传首帧图片 + 尾帧图片
```

---

### 二、完整输入流程

```
【全局配置】
├── 选择工具：Vidu Q2 / Seedance 2.0
├── 选择模式：全能参考模式 / 首尾帧模式
└── 若首尾帧：
    ├── 图标场景 → 选择图片作为首帧 / 尾帧（同一张图）
    └── 弹窗/加载页场景 → 分别上传首帧图片 + 尾帧图片

【场景选择】
├── A. 图标动效
│   ├── 选择图标类型
│   │   ├── 低级图标（一级强度）
│   │   ├── 高级图标（二级强度）
│   │   ├── Wild 图标（三级强度）
│   │   ├── Scatter 图标（三级强度）
│   │   └── Bonus 图标（三级强度）
│   ├── 选择动效状态（按类型显示可选项）
│   │   ├── 低级图标：中奖
│   │   ├── 高级图标：中奖
│   │   ├── Wild：待机 / 落定 / 中奖
│   │   ├── Scatter：待机 / 落定 / 中奖 / 期待抖动
│   │   └── Bonus：待机 / 落定 / 中奖
│   └── 上传图片 → 生成提示词
│
├── B. Free Game 弹窗 & 转场
│   ├── 选择阶段
│   │   ├── 触发弹窗入场
│   │   ├── 触发弹窗待机
│   │   ├── 转场进入 Free Game
│   │   │   └── 选择转场方案：独立设计 / 通用转场（以 Scatter 为核心）
│   │   ├── 结算弹窗入场
│   │   ├── 结算弹窗待机
│   │   └── 转场退出 Free Game
│   │       └── 选择转场方案：独立设计 / 通用转场（以 Scatter 为核心）
│   └── 上传图片 → 生成提示词
│
└── C. 加载页开场动画
    ├── 选择播放模式：单次 / 循环
    ├── 上传加载页图片（首尾帧模式下分别上传两张）
    └── 简单描述主体元素 → 生成提示词
```

---

### 三、图标类型 × 动效状态矩阵

| 图标类型 | 动效强度 | 待机 | 落定 | 中奖 | 期待抖动 |
|---------|--------|------|------|------|--------|
| 低级图标 | 一级 | — | — | ✓ | — |
| 高级图标 | 二级 | — | — | ✓ | — |
| Wild | 三级 | ✓ | ✓ | ✓ | — |
| Scatter | 三级 | ✓ | ✓ | ✓ | ✓ |
| Bonus | 三级 | ✓ | ✓ | ✓ | — |

> 注：各机台具体图标类型需单独确定，以上为通用框架

---

### 四、输出提示词模板

#### 4.1 图标动效模板（继承 Lobby Icon 四段式）

```
[场景标注] Mobile game slots reel symbol animation, fixed camera.

[主体动效] 描述图标主体的动作
[氛围动效] 描述背景光能量效果
[粒子光效] 描述粒子/光效
[标题/UI动效] 描述文字或边框动效（如有）

---

[高光触发] 每 8 秒触发一次增强效果（仅待机态适用）

[约束段落] 小幅度、平滑节奏、无缝循环，避免快速闪烁和剧烈运动
```

**强度映射：**
| 强度级别 | Vidu Q2 参数 | Seedance 关键词 |
|---------|------------|----------------|
| 一级（低级图标） | Small | Subtle / Gentle |
| 二级（高级图标） | Medium | Moderate / Smooth |
| 三级（特殊图标） | Large | Dynamic / Energetic |

---

#### 4.2 触发弹窗模板

```
[场景标注] Mobile game Free Game trigger popup animation.

[面板入场] 弹窗框体出现方式
[主体动效] 奖励主体动作
[氛围动效] 背景光能量
[粒子动效] 金币 / 星光 / 火花
[标题动效] 标题弹出
[强化效果] 爆发 / 金光

[约束段落] 流畅入场，避免穿帧，确保框体边界清晰
```

---

#### 4.3 转场动效模板

```
[场景标注] Mobile game scene transition animation, smooth and immersive.

[能量动效] 能量波 / 光圈扩散
[光线动效] 光束 / 扫光
[粒子动效] 星光 / 火花
[场景过渡] 画面切换方式

[通用转场附加说明（如选择）] Scatter 图标为视觉核心，承载转场能量焦点

[约束段落] 平滑过渡，保持沉浸感，避免硬切，画面衔接自然
```

---

#### 4.4 结算弹窗模板

```
[场景标注] Mobile game Free Game settlement popup animation.

[面板入场] 弹窗出现方式
[奖励主体] 宝箱 / 金币 / 图标动作
[数字动效] 金额数字滚动
[氛围动效] 金光 / 能量
[粒子动效] 金币喷射
[标题动效] 胜利文字展示
[强化效果] 爆发效果

[约束段落] 庆祝感强烈但不过度，数字清晰可读，整体节奏有序
```

---

#### 4.5 加载页开场动画模板

```
[场景标注] Mobile game loading screen opening animation.

[背景动效] 背景由暗到亮的过渡
[主体入场] [用户描述的主体元素] 登场方式
[Logo 动效] 游戏 Logo 出现与强调
[氛围动效] 整体光效与能量感

[约束段落]
- 单次模式：流畅完整，有明确的开始与结束感
- 循环模式：无缝衔接，长时展示不疲劳
```

---

### 五、双工具输出差异规范

| 维度 | Vidu Q2 输出规范 | Seedance 2.0 输出规范 |
|------|----------------|---------------------|
| 结构 | 主体 + 动作 + 场景 + 风格 + 构图 | 主体 + 动作 + 镜头 + 场景 + 风格 + **约束** |
| 字数 | 灵活，结构完整即可 | 控制在 30–200 词 |
| 强度表达 | 标注参数：motion amplitude: small/medium/large | 使用语言词汇：Slow / Gentle / Dynamic |
| 循环表达 | seamless loop / loop-safe | Continuous / Seamless Loop（显式写入约束段） |
| 约束段落 | 可选附加 | **必须**显式写出（no distortion / high detail / maintain consistency） |
| 语言 | 英文为主 | 英文为主 |

**每次输出格式：**
```
【Vidu Q2 版本】
中文：...
English: ...

【Seedance 2.0 版本】
中文：...
English: ...
```

---

### 六、合规词汇过滤层（扩展版）

**继承 Lobby Icon Skill 原有禁用词：**
- 777 / jackpot / slot machine / 任何赌博显性表达

**弹窗场景扩展禁用词：**
- win big / big win / mega win（直接使用）
- 具体奖励金额描述

**中性替换词：**
| 禁用词 | 替换为 |
|-------|-------|
| jackpot | grand reward / ultimate prize |
| slot machine | spinning device / reel device |
| big win | major reward / great achievement |
| win | collect / receive / unlock |
| 777 | symbol combination |

---

### 七、核心设计原则（SCAMPER 结论）

1. **选择优先于描述** — 用户通过菜单选项驱动 Skill，图标场景零文字输入
2. **模板固定，规则可扩展** — 输出结构稳定，主体识别规则持续迭代
3. **约束即质量** — 每套提示词末尾必须附加硬性约束段落
4. **强度参数化** — 三级强度通过结构化描述映射到工具参数
5. **场景自适应** — 不同场景加载不同模板，而非强行套用同一结构
6. **循环安全分级** — 待机态强制无缝循环，入场/退场/转场不强制
7. **双工具并行输出** — 单次生成即覆盖两套工具格式，减少重复操作

---

### 八、Skill 架构总览

```
Slots Animation Prompt Generator Skill
│
├── 全局配置层
│   ├── 工具选择（Vidu Q2 / Seedance 2.0）
│   └── 模式选择（全能参考 / 首尾帧）
│
├── 场景路由层
│   ├── 图标动效 → 类型选择 → 状态选择
│   ├── Free Game 弹窗 & 转场 → 阶段选择 → 转场方案选择
│   └── 加载页开场动画 → 播放模式选择
│
├── 图像分析层（继承 Lobby Icon Skill）
│   ├── 主体识别与分类
│   └── 图层自动拆解
│
├── 动效规则库
│   ├── 图标运动规则（按类型）
│   ├── 弹窗运动规则（按阶段）
│   ├── 转场运动规则
│   └── 加载页运动规则
│
├── 强度映射层
│   ├── 一级 → Small / Subtle
│   ├── 二级 → Medium / Moderate
│   └── 三级 → Large / Dynamic
│
├── 模板填充层
│   ├── 图标模板（四段式 + 高光触发）
│   ├── 触发弹窗模板（六段式）
│   ├── 转场模板（四段式）
│   ├── 结算弹窗模板（七段式）
│   └── 加载页模板（四段式）
│
├── 合规过滤层
│   └── 禁用词替换（统一模块）
│
└── 双语双工具输出层
    ├── Vidu Q2（中文 + 英文）
    └── Seedance 2.0（中文 + 英文）
```

---

*头脑风暴会话完成 — 2026-03-04*
*技法：问题风暴 → 第一性原理 → SCAMPER*
