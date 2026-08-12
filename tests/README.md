# tests/ ｜ 端到端测试案例

本目录存放 `image-prompt-reverse` 的**手动端到端测试案例**，作为 Skill 的质量证据与用例文档。

## 为什么是「手动」而非「自动化」

反推提示词是 LLM 生成任务，输出不唯一、无法做断言式单测。因此本 Skill 的「测试」定义为：

> 给定一张固定输入图，按 `SKILL.md` 的 Step 0–7 走查，产出**结构完整、可复制粘贴**的提示词包（还原版 + 惊艳增强版 + 3 变体 + 平台适配版 + 负向约束 + 原创边界），且流程无断点。

每个案例包含：
- `assets/case-XX-input.jpg` —— 固定输入图（二进制，随版本受控）
- `case-XX-<主题>.md` —— 走查记录（分析块 + 全部 prompt + 结论）
- `NOTICE-assets.md` —— 输入图的授权与署名

## 如何复现 / 校验

> 本 Skill 基于 agent-skills 格式（`SKILL.md` + `references/`），**不依赖 WorkBuddy**，可在任意支持「Skill / 长指令 / 系统提示词」的 agent 中复现。

1. 打开 `assets/case-01-input.jpg`。
2. 在任意支持长指令的工具中加载本 Skill（见下方「在各类工具中复现」），发送该图并说「反推这张图 / 生成同款提示词」。
3. 比对产出是否包含：分析块 → 还原版（中英）→ 惊艳增强版 → 3 变体 → 平台适配版 → 负向约束 → 原创边界，且无截断。
4. 期望结论：流程可跑通、references 四件套均能被正确套用（见各案例 md 的「走查结论」）。
5. 关于 Step 8 出图验证：默认关。**仅 WorkBuddy** 提供内置 ImageGen 作为 opt-in 近似验证；其他工具无此能力时，退化为「仅交付提示词、不出图」，不影响 Step 0–7 输出包 —— 属预期行为，不算复现失败。

### 在各类工具中复现（加载本 Skill）

> 核心原则：让 agent 能读到本目录的 `SKILL.md`（及其引用的 `references/*.md`）即可。以下为各工具的典型加载方式，路径/入口随版本演进，以各工具官方文档为准；只要 Skill 被正确加载，复现结果一致。根目录 `README.md` 的「安装 / 跨工具加载」节含相同的路径说明，两处保持同步。

#### WorkBuddy
- **用户级（推荐）**：把本目录整体放到 `~/.workbuddy/skills/image-prompt-reverse/`（`SKILL.md` 在该目录下即可），新会话丢图即自动触发。
- **项目级**：放到 `<项目>/.workbuddy/skills/image-prompt-reverse/`，仅对当前项目生效。
- 触发后按 Step 0–7 走查；Step 8 出图验证为 opt-in（需授权 + 内置 ImageGen）。

#### Claude Code
- **agent-skills 原生**：把本目录放到项目级 `.claude/skills/image-prompt-reverse/`（或用户级 `~/.claude/skills/image-prompt-reverse/`），Claude Code 会自动发现 `SKILL.md`。
- 也可在 `CLAUDE.md` 中用 `@<相对路径>/SKILL.md` 引入，或把 `SKILL.md` 关键内容直接并入 `CLAUDE.md` / `AGENTS.md` 作为常驻指令。
- 会话中可用 Skill 机制引用本目录。

#### Cursor
- 在 `.cursor/rules/` 下新建 `image-prompt-reverse.mdc`，粘贴 `SKILL.md` 正文并注明引用 `references/*.md`；规则类型设为 `always`（常驻）或 `auto`/`manual`（按需）。
- 或在 Settings › Rules for AI 里粘贴 `SKILL.md` 要点。

#### Codex
- 将 `SKILL.md` 要点（含 `references/` 路径说明）并入仓库根 `AGENTS.md`（或 `codex.md`），Codex 启动时会作为指令加载。
- 如需完整能力，直接把 `SKILL.md` 全文 + `references/` 一并纳入项目上下文。

#### 其他支持长指令的工具（通用）
- 直接将 `SKILL.md` 正文（及按需引用的 `references/*.md`）作为系统指令 / 长上下文注入。
- 发送输入图与「反推这张图 / 生成同款提示词」指令，即可复现。

> 注：各工具对 agent-skills 的具体加载入口随版本演进，以上为「把 `SKILL.md` 作为指令/Skill 加载」的通用范式；只要能让 agent 读到 `SKILL.md` 与其引用的 `references`，复现结果一致。

## 案例清单

| 案例 | 输入图 | 主题 | 文件 |
|------|--------|------|------|
| case-01 | assets/case-01-input.jpg | 老式 CRT 电视 + 沙地草丛 + 蓝天（胶片复古味 / Midjourney） | case-01-crt-sand-sky.md |

## 授权

输入图均来自公开图源，授权与署名见 `NOTICE-assets.md`。本 Skill 的提示词产出本身遵循仓库根 `LICENSE`。
