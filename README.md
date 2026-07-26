# image-prompt-reverse

> [English](README_en.md) · 中文

**图像反推提示词工程师 Skill** —— 把一张图反推成专业级 AI 图像提示词，并独家叠加「惊艳增强层」，把"还原同款"升级为电影感 / 胶片感 / 商业大片。

## 特性
- **拆图反推**：通用 / 字体Logo / 风景 / 摄影人像 / 插画 / 产品 / 美食 / 建筑室内 / 时尚 / 汽车 + 通用兜底
- **惊艳增强层**：14 个惊艳方向词库（电影感 / 胶片味 / 商业高级 / 赛博朋克 / 国风…）可自由组合
- **3 变体**：构图 shift / 光影 shift / 风格 shift（单点改，多选项）
- **平台适配**：Midjourney / DALL·E / Stable Diffusion / Flux
- **输出包**：图像分析块 + 还原版 + 惊艳增强版 + 3 变体 + 平台版 + 负向约束 + 原创边界
- **协同**：与 `prompt-model-adaptation` 方法论复用（Step 6 套其五步法）

## 安装
本 skill 是标准 agent-skills 格式（`<skill-name>/SKILL.md`），复制到任意支持工具的 skills 目录即可。

**WorkBuddy（用户级）**
```bash
cp -r image-prompt-reverse ~/.workbuddy/skills/
```
项目级：复制到 `<workspace>/.workbuddy/skills/`

**Claude Code**
```bash
cp -r image-prompt-reverse ~/.claude/skills/
```

**Cursor**
新版支持 `.cursor/skills/`；旧版把 `SKILL.md` 内容作为 rules / 指令导入。

**Codex (OpenAI)**
把 `SKILL.md` 正文作为 `AGENTS.md` / instructions 整合。

**任意支持长指令的工具**
直接粘贴 `SKILL.md` + `references/` 内容作为系统提示。

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
├── README.md
├── README_en.md
└── LICENSE
```

## 许可证
MIT —— 详见 [`LICENSE`](LICENSE)。
