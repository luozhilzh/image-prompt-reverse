# image-prompt-reverse

![version](https://img.shields.io/badge/version-1.0.1-blue) ![released](https://img.shields.io/badge/status-released-brightgreen)

> [English](README_en.md) · 中文

**图像反推提示词工程师 Skill** —— 把一张图反推成专业级 AI 图像提示词，并独家叠加「惊艳增强层」，把"还原同款"升级为电影感 / 胶片感 / 商业大片。

## 特性
- **拆图反推**：通用 / 字体Logo / 风景 / 摄影人像 / 插画 / 产品 / 美食 / 建筑室内 / 时尚 / 汽车 + 通用兜底
- **惊艳增强层**：14 个惊艳方向词库（电影感 / 胶片味 / 商业高级 / 赛博朋克 / 国风…）可自由组合
- **3 变体**：构图 shift / 光影 shift / 风格 shift（单点改，多选项）
- **平台适配**：Midjourney / DALL·E / Stable Diffusion / Flux
- **输出包**：图像分析块 + 还原版 + 惊艳增强版 + 3 变体 + 平台版 + 负向约束 + 原创边界
- **协同**：与 `prompt-model-adaptation` 方法论复用（Step 6 套其五步法）

## 安装 / 跨工具加载
本 skill 是标准 agent-skills 格式（`<skill-name>/SKILL.md` + `references/`），**不依赖特定客户端**，可原样用于 WorkBuddy、Claude Code、Cursor、Codex 及任意支持长指令的 agent。核心原则：让 agent 读到 `SKILL.md` 及其引用的 `references/*.md` 即可。详细的复现步骤与各工具加载要点亦见 `tests/README.md` 的「在各类工具中复现」，两处保持同步。

**WorkBuddy（用户级，推荐）**
```bash
cp -r image-prompt-reverse ~/.workbuddy/skills/
```
项目级：复制到 `<workspace>/.workbuddy/skills/`。新会话丢图即自动触发；Step 8 出图验证为 opt-in（需授权 + 内置 ImageGen）。

**Claude Code**
```bash
cp -r image-prompt-reverse ~/.claude/skills/
```
agent-skills 原生支持，会自动发现 `SKILL.md`；也可在 `CLAUDE.md` 用 `@<路径>/SKILL.md` 引入，或把 `SKILL.md` 关键内容并入 `CLAUDE.md` / `AGENTS.md` 作为常驻指令。

**Cursor**
在 `.cursor/rules/` 下新建 `image-prompt-reverse.mdc`，粘贴 `SKILL.md` 正文并注明引用 `references/*.md`；规则类型设为 `always`（常驻）或 `auto`/`manual`（按需）。或在 Settings › Rules for AI 粘贴要点。（新版亦支持 `.cursor/skills/`。）

**Codex (OpenAI)**
将 `SKILL.md` 要点（含 `references/` 路径说明）并入仓库根 `AGENTS.md`（或 `codex.md`）；完整能力则把 `SKILL.md` 全文 + `references/` 一并纳入项目上下文。

**任意支持长指令的工具**
直接粘贴 `SKILL.md` 正文（+ 按需 `references/*.md`）作为系统提示 / 长上下文，再发送输入图与「反推这张图」指令即可。

> 注：各工具加载入口随版本演进，以官方文档为准；只要 Skill 被正确加载，复现结果一致。Step 8 出图验证为 WorkBuddy 专属，其他工具无此入口时退化为仅交付提示词（不影响 Step 0–7 输出包，属预期行为）。

## 使用流程
1. 给一张图（或描述意图）
2. skill 自动拆图 → 最小追问（1–2 个：平台 / 惊艳方向 / 用途）
3. 产出：还原版 + 惊艳增强版 + 3 变体 + 平台适配版

详见 [`SKILL.md`](SKILL.md)。

## 目录结构
```
image-prompt-reverse/
├── SKILL.md                  角色 / 工作流 / 触发词
├── references/
│   ├── reverse-dimensions.md 全场景维度拆解
│   ├── enhancement-vocab.md  惊艳增强词库 + 负向词库
│   ├── platform-guides.md    MJ / DALL-E / SD / Flux 语法
│   └── templates.md          可复制反推 + 增强模板
├── assets/
│   └── analysis-form.md      结构化分析骨架
├── tests/                   端到端测试案例
│   ├── README.md            案例说明（如何复现 / 案例清单）
│   ├── case-01-crt-sand-sky.md  走查记录（CRT 电视 + 沙地 + 蓝天）
│   ├── assets/
│   │   └── case-01-input.jpg 测试输入图
│   └── NOTICE-assets.md     图片授权与署名
├── RELEASE_NOTES.md         发行说明（v1.0.1）
├── README.md
├── README_en.md
└── LICENSE
```

## 依赖与维护

- **可选增强依赖**：`prompt-model-adaptation`（仅用于 Step 6 方法论命名 / 元用法 / 产物 QA，不影响核心反推流程；未安装时本 Skill 仍可独立工作）。
- **维护提示**：若同时维护源码副本与本机用户级副本（`~/.workbuddy/skills/image-prompt-reverse`），修改后请用 `cp -r` 同步，避免两边版本不一致。

## 许可证
MIT —— 详见 [`LICENSE`](LICENSE)。
