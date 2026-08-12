# image-prompt-reverse v1.0.1

> 发布日期：2026-08-12 ｜ 类型：Patch（质量与文档修复）｜ 相对版本：v1.0.0
> 作者：luozhi ｜ License：MIT

---

## 中文

### 摘要
本版本为质量与文档修复版：**补全 frontmatter 版本字段、明确触发边界与降级逻辑、新增端到端测试案例、并正式声明跨工具兼容性**（WorkBuddy / Claude Code / Cursor / Codex / 任意支持长指令的 agent）。无工作流逻辑变更，向后兼容。

### 变更明细

**修复（Fixes）**
- `SKILL.md` frontmatter 新增 `version: 1.0.1`（此前仅有 git tag `v1.0.0`，缺 frontmatter 字段）。
- 触发边界声明：明确仅当指向图像 / 图像生成模型（MJ / DALL·E / SD / Flux）时触发，降低近义误触。
- Step 8 出图验证降级边界显式化：未授权 / 无积分 / ImageGen 不可用时，退化为仅交付提示词（不出图）。
- 速查表单一来源：场景维度 / 惊艳方向速查表明确指向完整 `references`，消除轻度重复。

**新增（Added）**
- `tests/` 端到端测试案例：case-01（老式 CRT 电视 + 沙地草丛 + 蓝天，胶片复古味 / Midjourney），含输入图、走查记录、授权说明。
- `tests/README.md` 复现说明工具无关化：可在任意支持长指令的 agent 中复现。
- `SKILL.md`「跨工具兼容」声明 callout。
- 根 `README.md`「安装 / 跨工具加载」节细化各工具加载路径（Cursor `.cursor/rules/*.mdc` 规则类型、Claude Code `@SKILL.md` 引入、Codex `AGENTS.md`、通用长指令注入）。

**文档（Docs）**
- `README.md` / `README_en.md` 新增「依赖与维护」节（可选依赖 `prompt-model-adaptation` + 维护同步提示）。
- 授权标注更正：测试输入图原误标 CC0，实为 **Unsplash License**（作者 Pablo GarciaSaldaña），已在 `tests/NOTICE-assets.md` 说明。

### 已知限制
- Step 8 出图验证**仅 WorkBuddy 内置 ImageGen** 支持；其他工具无此入口时退化为仅交付提示词（预期行为，不影响 Step 0–7 输出包）。
- 未在真实运行态验证 WorkBuddy 自动触发命中率（需在真实会话环境观察）。

### ⬆️ 升级指引（从 v1.0.0 → v1.0.1，必读）
> 本版本为**向后兼容**的文档 / 元数据增量更新，**无需重新生成任何 prompt，也无需改动你的配置**。

1. **拉取源码**
   ```bash
   git pull            # 或重新 clone 最新 main
   ```
2. **若使用用户级副本（WorkBuddy 默认位置）** —— 用 `cp -r` 整体覆盖：
   ```bash
   cp -r image-prompt-reverse ~/.workbuddy/skills/
   ```
3. **若使用项目级副本** —— 复制到你的项目：
   ```bash
   cp -r image-prompt-reverse <workspace>/.workbuddy/skills/
   ```
4. **若在其他工具（Claude Code / Cursor / Codex / 通用长指令工具）** —— 按 `README.md`「安装 / 跨工具加载」节重新加载 `SKILL.md` 与其 `references/` 即可，无需其他改动。
5. **验证**：新会话丢一张图，确认 Skill 正常触发并产出完整输出包（分析块 → 还原版 → 惊艳增强版 → 3 变体 → 平台版 → 负向 → 原创边界）。

### 完整变更文件
- `SKILL.md`（version / 触发边界 / Step 8 降级 / 跨工具声明 / 速查表指向）
- `README.md` / `README_en.md`（依赖与维护 + 安装 / 跨工具加载细化）
- `tests/`（新增：README.md / case-01-crt-sand-sky.md / assets/case-01-input.jpg / NOTICE-assets.md）

---

## English

### Summary
A quality-and-docs patch release: **adds the missing frontmatter version field, clarifies trigger boundaries and degradation logic, adds an end-to-end test case, and formally declares cross-tool compatibility** (WorkBuddy / Claude Code / Cursor / Codex / any tool supporting long instructions). No workflow-logic changes; fully backward compatible.

### Changes

**Fixes**
- `SKILL.md` frontmatter now carries `version: 1.0.1` (previously only a `v1.0.0` git tag, no frontmatter field).
- Trigger-boundary note: fires only when the request targets an image / image-generation model (MJ / DALL·E / SD / Flux), reducing near-miss false triggers.
- Step 8 verification degradation made explicit: when unauthorized / no credits / ImageGen unavailable, it falls back to prompt-only delivery (no image).
- Single-source speed tables: scene-dimension / enhancement-direction quick tables now point to the full `references`, removing light duplication.

**Added**
- `tests/` end-to-end case: case-01 (vintage CRT TV + sandy grass + blue sky, filmic / Midjourney), with input image, walkthrough, and license note.
- `tests/README.md` reproduction instructions made tool-agnostic: reproducible in any long-instruction agent.
- `SKILL.md` "cross-tool compatibility" callout.
- Root `README.md` "Install / Load across tools" section with detailed per-tool paths (Cursor `.cursor/rules/*.mdc` rule types, Claude Code `@SKILL.md` import, Codex `AGENTS.md`, generic long-instruction injection).

**Docs**
- `README.md` / `README_en.md` new "Dependencies & Maintenance" section (optional `prompt-model-adaptation` dependency + sync note).
- License correction: the test input image was mislabeled CC0; it is actually **Unsplash License** (author Pablo GarciaSaldaña), documented in `tests/NOTICE-assets.md`.

### Known Limitations
- Step 8 image verification is **WorkBuddy-only (built-in ImageGen)**; other tools fall back to prompt-only delivery (expected, does not affect the Step 0–7 output package).
- Automatic-trigger hit rate under real WorkBuddy runtime has not been verified (requires a real session).

### ⬆️ Upgrade (from v1.0.0 → v1.0.1, read this)
> This is a **backward-compatible** docs/metadata incremental update — **no prompt regeneration or config change needed**.

1. **Pull source**
   ```bash
   git pull            # or re-clone the latest main
   ```
2. **If using the user-level copy (WorkBuddy default)** — overwrite with `cp -r`:
   ```bash
   cp -r image-prompt-reverse ~/.workbuddy/skills/
   ```
3. **If using a project-level copy**:
   ```bash
   cp -r image-prompt-reverse <workspace>/.workbuddy/skills/
   ```
4. **If using other tools (Claude Code / Cursor / Codex / generic long-instruction)** — reload `SKILL.md` and its `references/` per the "Install / Load across tools" section in `README.md`; no other changes needed.
5. **Verify**: drop an image in a new session and confirm the Skill triggers and emits the full output package.

### Files Changed
- `SKILL.md` (version / trigger boundary / Step 8 degradation / cross-tool note / table pointers)
- `README.md` / `README_en.md` (dependencies & maintenance + install / cross-tool paths)
- `tests/` (added: README.md / case-01-crt-sand-sky.md / assets/case-01-input.jpg / NOTICE-assets.md)
