# 目录结构重构需求记录（给 Claude）

## 目标

将当前 skill 重构为**三层渐进式披露结构**，让 Agent 先加载最小主流程，再按需加载规则和资源，减少 token 消耗。

## 目标目录结构

```text
slots-FX-skill/
├── skill.md
├── rules/
│   ├── core.md
│   ├── routing.md
│   └── output.md
├── templates/
│   ├── scene-a.md
│   ├── scene-b.md
│   ├── scene-c.md
│   └── single-layer.md
├── refs/
│   ├── style.md
│   ├── intensity.md
│   ├── compliance.md
│   └── vocabulary.md
└── brainstorming/
```

## 三层拆分原则

### 第一层：主控层

文件：`skill.md`

只保留最短主流程，不放长表格，不放大段解释。

应包含：

- `TRIGGER CONDITIONS`
- `MANDATORY EXECUTION RULES`
- `STEP 1`
- `STEP 2`
- `STEP 3A / 3B / 3C` 的最短入口
- `STEP 4` 的最短版
- 每一步需要转去读取哪个文件

### 第二层：规则层

文件：`rules/core.md`、`rules/routing.md`、`rules/output.md`

按功能拆规则，不放完整模板。

- `rules/core.md`
  - 全局硬限制
  - 主体动作必须具体
  - 镜头限制
  - 循环限制
  - 最小自检
- `rules/routing.md`
  - 素材识别
  - 低置信度双候选确认
  - 风格确认
  - 多主体主从规则
  - Scene A/B/C 路由
- `rules/output.md`
  - `FINAL OUTPUT FORMAT`
  - `IMPORTANT RULES`
  - Vidu / Seedance 输出要求
  - 首尾帧结构适用范围

### 第三层：资源层

文件：`templates/*` 和 `refs/*`

只在需要时加载。

- `templates/scene-a.md`
  - Template A
  - Template A2
- `templates/scene-b.md`
  - Template B1-B5
- `templates/scene-c.md`
  - Template C
- `templates/single-layer.md`
  - Template S
  - Template T
  - Template BG
- `refs/style.md`
  - `STYLE MOTION PROFILES`
- `refs/intensity.md`
  - `INTENSITY MAPPING`
- `refs/compliance.md`
  - `COMPLIANCE / WORDING RULES`
- `refs/vocabulary.md`
  - `SEEDANCE 2.0 ENHANCED VOCABULARY`

## 执行要求

- 主文件必须最短，只做入口和路由
- 规则文件不解释原理，只写可执行规则
- 模板文件只放模板，不写原理说明
- 资源文件只放查表内容
- `brainstorming/` 保留，但不参与运行时结构
- 不修改强规则逻辑
- 不改变输出格式结构
- 优先减少重复内容和英文镜像描述
- 如果 B1/B4、B2/B5 能参数化合并，可一并处理，但不要改变原有能力覆盖范围

## 推荐拆分顺序

1. 先抽 `rules/output.md`
2. 再抽 `refs/compliance.md`、`refs/intensity.md`、`refs/style.md`
3. 再拆 `templates/`
4. 最后把 `skill.md` 压成纯入口文件

## 补充原则

- 这是给 Agent 用的，不是给人类看的
- 对 Agent 没帮助的冗余解释应继续删除
- 若某些内容不值得独立文件，优先遵循“对 Agent 有用才保留”的原则
