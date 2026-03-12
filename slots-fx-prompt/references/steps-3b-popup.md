# STEP 3B：Free Game 弹窗 & 转场流程

## 3B-1 Select Stage

> 请选择阶段：

| 选项 | 阶段 |
|------|------|
| [1] | 触发弹窗入场 Trigger Popup Entry |
| [2] | 触发弹窗待机 Trigger Popup Idle |
| [3] | 转场进入 Free Game Transition IN |
| [4] | 结算弹窗入场 Settlement Popup Entry |
| [5] | 结算弹窗待机 Settlement Popup Idle |
| [6] | 转场退出 Free Game Transition OUT |

---

## 3B-2 Transition Design（仅当选 [3] 或 [6]）

> 请选择转场方案：
- **[A]** 独立设计 — 本次转场专属
- **[B]** 通用转场 — 以 Scatter 图标为视觉核心，进/退场共用

---

## 3B-3 Upload Image

> 请上传图片（全能参考模式：1 张；首尾帧模式：按 STEP 1.2 意图上传对应数量）。

---

## 3B-3b Asset Type Detection（素材类型识别）

🛑 **图片上传后，必须先判断素材类型，再进入后续生成。按置信度分级处理。**

| 类型 | 识别特征 | 后续流程 |
|------|---------|---------|
| **完整弹窗素材**（主体 + 面板 + 文字） | 包含弹窗面板、主体图像、标题文字等多层元素 | 继续现有 Scene B 生成流程 |
| **纯背景**（Background Only） | 只有背景光效/粒子/环境，无面板无主体 | 跳转 Template BG 流程 |

> **置信度 ≥ 90%：** 自动通过，例如：「检测到：完整弹窗素材 ✓ 继续…」
>
> **置信度 50–89%：** 输出双候选确认：「我更倾向识别为 **[类型A]**（理由：[特征依据]），其次可能是 **[类型B]**。请确认或选择。」
>
> **置信度 < 50%：** 询问用户：「请问这是完整弹窗素材，还是纯背景层图片？」

---

## 路由

完成 3B-3b 后 → 读取 `step-4-preview.md` 进行方案预览。
生成阶段按阶段路由模板 → `assets/template-b-popup.md`（含 B1–B5 + BG）
