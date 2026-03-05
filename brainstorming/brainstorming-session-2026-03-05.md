---
stepsCompleted: [1, 2, 3]
inputDocuments: ['slots_animation_prompt_skill_v1_claude.md']
session_topic: 'slots_animation_prompt_skill_v1 优化'
session_goals: '输出质量提升（A）/ 使用体验优化（C）/ 工具适配深化（D）'
selected_approach: 'progressive-flow'
techniques_used: ['what-if-scenarios', 'six-thinking-hats', 'scamper', 'decision-tree-mapping']
ideas_generated: [13]
context_file: 'slots_animation_prompt_skill_v1_claude.md'
---

# Brainstorming Session Results

**Facilitator:** Admin
**Date:** 2026-03-05

---

## Session Overview

**Topic:** slots_animation_prompt_skill_v1 优化
**Goals:** 输出质量提升（A）/ 使用体验优化（C）/ 工具适配深化（D）

### Technique Selection

**Approach:** 渐进式流程（Progressive Technique Flow）

| 阶段 | 技法 | 目的 |
|------|------|------|
| Phase 1 — 发散探索 | What If Scenarios | 打破假设，生成原始想法 |
| Phase 2 — 规律识别 | Six Thinking Hats | 多维分析，优先排序 |
| Phase 3 — 方案深化 | SCAMPER Method | 系统优化，具体方案 |
| Phase 4 — 落地计划 | Decision Tree Mapping | 决策路径，执行清单 |

---

## Phase 1 — 发散探索（What If Scenarios）结果

**[使用体验 #1]**: 渐进式确认优先
*Concept*: 用户意图比图像识别更可靠。Skill 应先锁定"用户需要什么"，再调用图像分析——AI 的识别结论作为辅助确认呈现，而非主判断。
*Novelty*: "用户选+AI预填"模型，减少错误率同时保留自动化价值。

**[使用体验 #2]**: 智能预填+单步确认
*Concept*: AI 分析上传图片后，预填所有参数以一行摘要呈现确认："检测到：Scatter 图标 × 中奖动效 × 三级强度，确认生成？[Y/修改]"——多数情况用户只需回复Y。
*Novelty*: 4-6步选择压缩为1步确认，保留完整纠错能力。

**[使用体验 #3]**: 首尾帧为主默认模式
*Concept*: 用户实际以首尾帧模式为主，全能参考模式是少数情况。以首尾帧为默认路径，全能参考模式降级为"高级选项"。
*Novelty*: 默认路径反映真实使用频率，减少每次选择模式的摩擦。

**[工具适配 #4]**: Seedance 自然语言优势独立逻辑层
*Concept*: Seedance 2.0 对自然语言理解更强，应改用流畅叙事风格；Vidu 版保留结构化标签体系。两套真正独立优化的输出逻辑。
*Novelty*: 非同一内容的格式转换，而是两套基于工具特性的独立生成策略。

**[输出质量 #5]**: Seedance 双模式输出选项
*Concept*: Seedance 版提供「结构化版」和「自然叙事版」两种格式供用户选择，不强制替换。
*Novelty*: 扩展选项而非强制迁移，降低切换风险。

**[工具适配 #6]**: Seedance 镜头语言 + 节奏词汇专项库
*Concept*: 为 Seedance 建立专属词汇层——镜头语言（slow push in / tight on）和节奏词汇（surges in a single beat / eases into stillness）。当前 Skill 这两类词汇几乎缺失。
*Novelty*: 叠加"Seedance 增强词汇注入层"，不改变模板结构。

**[使用体验 #7]**: 首尾帧双工具描述分叉
*Concept*: Skill 在模板层面输出两套不同叙事策略：Vidu 精确部位序列，Seedance 情绪运动弧线。消除用户事后手动调整负担。
*Novelty*: 把用户的事后调整经验提前编码进 Skill，隐性知识显性化。

**[工具适配 #8]**: 主体复杂度驱动分叉策略
*Concept*: 有机复杂主体（动物/角色）强制分叉两套描述；简单几何主体（宝石/硬币）合并输出。差异化按需触发。
*Novelty*: 由主体类型自动决定，平衡精准度与简洁度。

**[输出质量 #9]**: 合规过滤精准分层
*Concept*: 「UI文字层」严格替换；「动效描述层」放宽，保留强动感词汇（triumph/surge/burst）。当前一刀切导致生成画面能量不足。
*Novelty*: 按词汇用途而非词汇本身决定是否替换。

**[工具适配 #10]**: Seedance 全文语境过滤应对策略
*Concept*: Seedance 用 LLM 读取整段提示词判断意图（非关键词匹配），需升级为"语境重构"策略而非词汇替换。
*Novelty*: 针对 LLM 过滤器的策略与关键词过滤器本质不同。

**[输出质量 #11]**: Seedance 语境锚定句
*Concept*: Seedance 版提示词开头加入语境定义句，如 "Mobile entertainment game symbol animation for a digital spinning reel device"，主动建立合法娱乐语境。
*Novelty*: 主动语境声明 vs. 被动词汇替换，从根本上改变过滤器判断起点。

**[使用体验 #12]**: 首尾帧问题表述重写
*Concept*: 将"首帧/尾帧"技术术语改写为用户意图语言——"让它动起来"（从图出发）/ "还原这一刻"（动效到达这里）/ "回到原位"（循环）/ "从A到B"（双图）。
*Novelty*: 从技术术语转向用户目标语言，同一功能理解成本大幅降低。

**[使用体验 #13]**: 首尾帧意图优先流程重设计（结构性修复）
*Concept*: 重设计为4种意图选项：[A]从这里开始运动 / [B]动效结束在这里 / [C]运动后回到原状态（首尾同图）/ [D]我有起始和结束两种状态（上传2张）。意图选定后再指导上传。
*Novelty*: "问意图→指导上传"替代"上传→问用途"，从根本上解决多图场景和循环场景的缺口。

---

## Phase 2 — 规律识别（Six Thinking Hats）结果

### ⚪ 白帽（事实确认）

| 事实 | 影响的想法 |
|------|-----------|
| 用户主用首尾帧模式 | #3 #7 #8 #13 |
| Seedance 自然语言理解更强 | #4 #5 #6 |
| Seedance 用 LLM 全文过滤 | #10 #11 |
| 当前流程需 4-6 步选择 | #1 #2 |
| 合规替换词削弱动效语气 | #9 |
| 首尾帧流程存在多图/循环场景缺口 | #13 |

### 🔴 红帽（用户高直觉优先级）
#1 #2 #3 #4 #5

### 最终优先级排序

| 优先级 | # | 想法 |
|--------|---|------|
| 🥇 P0 | #3 | 首尾帧为主默认路径 |
| 🥇 P0 | #13 | 首尾帧意图优先流程重设计 |
| 🥇 P0 | #12 | 首尾帧问题表述重写 |
| 🥇 P0 | #11 | Seedance 语境锚定句 |
| 🥈 P1 | #2 | 智能预填+单步确认 |
| 🥈 P1 | #4 | Seedance 独立叙事逻辑层 |
| 🥈 P1 | #6 | Seedance 镜头+节奏词汇库 |
| 🥉 P2 | #9 | 合规过滤分层 |
| 🥉 P2 | #8 | 主体复杂度分叉 |

---

## Phase 3 — 方案深化（SCAMPER）结果

### P0 组具体改法

**#13 首尾帧意图优先流程**
- **S（替换）**：把"上传→问意图"改为"问意图→上传"。STEP 1.2 追加意图选择，上传提示语根据意图动态变化。
- **E（删除）**：删除各模板末尾重复的首尾帧说明段落（Template A2/B1/B3/B4/C），统一在 STEP 1.2 处理。

**#12 首尾帧问题表述重写**
- **A（适应）**：借鉴视频编辑"入点/出点"语言：
  - [A] 让它动起来（从图出发）
  - [B] 还原这一刻（动效到达这里）
  - [C] 回到原位（循环）
  - [D] 从A到B（双图，分别上传）

**#3 首尾帧为主默认路径**
- **M（修改）**：STEP 1.2 默认项改为首尾帧模式；全能参考模式降为 [2]，标注"(高级)"。

**#11 Seedance 语境锚定句**
- **C（合并）**：把语境锚定句和现有场景标注行合并：
  `Mobile entertainment animation for a digital spinning reel game — [场景], fixed camera.`

### P1 组具体改法

**#4 Seedance 独立叙事逻辑层**
- **R（逆转）**：先写动效故事，末尾补约束。
- 示例（图标中奖叙事版）：
  ```
  A fierce tiger lunges forward as it claims victory —
  jaw snapping open to reveal gleaming fangs, eyes narrowing
  then bursting with golden light, neck muscles tensing as
  energy rings explode outward and coins shower down in arcs.
  Mobile entertainment animation, no camera movement,
  maintain visual consistency, Dynamic motion, seamless loop.
  ```

**#6 Seedance 镜头语言 + 节奏词汇库**
- **P（转用）**：从电影分镜表移植词汇系统：

  | 用途 | 词汇 |
  |------|------|
  | 强调细节 | `tight on [subject]` / `close on [detail]` |
  | 展示整体 | `wide reveal` / `full frame` |
  | 爆发瞬间 | `surges in a single beat` / `ignites suddenly` |
  | 缓入 | `eases into motion` / `stirs to life` |
  | 收束 | `settles into stillness` / `fades to rest` |
  | 循环感 | `breathes continuously` / `pulses in a steady rhythm` |

---

## Phase 4 — 落地计划（Decision Tree Mapping）

### 改动依赖树

```
slots_animation_prompt_skill_v1 优化路径
│
├── Batch 1（独立，立即可执行）
│   ├── ① 修改 STEP 1.2 默认模式（首尾帧↔全能参考互换）
│   └── ③ 删除各模板末尾重复的首尾帧说明段落
│
├── Batch 2（独立，8处批量替换）
│   └── ② 所有 Seedance 模板首行加语境锚定句
│
├── Batch 3（依赖 Batch 1）
│   └── ④ 首尾帧流程重设计（意图优先4选项 + 措辞重写）
│
└── Batch 4（依赖 Batch 3）
    ├── ⑤ Seedance 叙事版模板（优先 Template A）
    └── ⑥ Seedance 镜头语言 + 节奏词汇表（新增章节）
```

### 执行清单

| 批次 | 改动 | 位置 | 风险 |
|------|------|------|------|
| Batch 1 | ① STEP 1.2 默认模式调换 | STEP 1: Global Configuration | 低 |
| Batch 1 | ③ 删除模板末尾首尾帧说明 | Template A2/B1/B3/B4/C | 低 |
| Batch 2 | ② Seedance 语境锚定句 | 全部 Seedance 模板开头（8处）| 低 |
| Batch 3 | ④ 首尾帧意图优先流程 | STEP 1.2 重写 | 中 |
| Batch 4 | ⑤ Seedance 叙事版模板 | Template A 新增段落 | 中 |
| Batch 4 | ⑥ Seedance 词汇库 | IMPORTANT RULES 后新增章节 | 低 |

### 验证方式

- Batch 1-2：通读改动段落，确认措辞无歧义
- Batch 3：走一遍4个意图分支（A/B/C/D），确认上传说明正确
- Batch 4：用实际图片测试 Seedance 叙事版，对比结构化版生成效果

---

## 头脑风暴总结

**完成时间：** 2026-03-05
**技法序列：** What If Scenarios → Six Thinking Hats → SCAMPER → Decision Tree Mapping
**生成想法：** 13条
**落地改动：** 6项（Batch 1–4）

**核心结论：**
1. 首尾帧流程是最大体验痛点，需结构性重设计（意图优先）
2. Seedance 工具特性未被充分发挥，独立优化空间显著
3. P0 改动（Batch 1-2）可立即执行，低风险，高收益

---
