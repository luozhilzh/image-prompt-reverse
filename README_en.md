# image-prompt-reverse

**Image Prompt Reverse-engineering Skill** — reverse-engineer any image into professional-grade
AI image-generation prompts, with a unique "stunning enhancement layer" that upgrades a faithful
recreation into a cinematic / filmic / commercial blockbuster look.

## Features
- **Reverse by dimension**: General / Logo / Landscape / Portrait / Illustration / Product / Food /
  Architecture / Fashion / Automotive + generic fallback
- **Stunning enhancement layer**: 14 curated direction vocabularies (cinematic / filmic / editorial /
  cyberpunk / oriental …) freely combinable
- **3 variants**: composition shift / lighting shift / style shift (single-axis changes)
- **Platform adaptation**: Midjourney / DALL·E / Stable Diffusion / Flux
- **Output package**: analysis block + faithful version + enhanced version + 3 variants +
  platform version + negatives + originality boundary
- **Synergy**: reuses `prompt-model-adaptation` methodology (Step 6 follows its 5-step method)

## Install
This is a standard agent-skills package (`<skill-name>/SKILL.md`). Copy it into any tool's skills dir.

**WorkBuddy (user-level)**
```bash
cp -r image-prompt-reverse ~/.workbuddy/skills/
```
Project-level: copy into `<workspace>/.workbuddy/skills/`

**Claude Code**
```bash
cp -r image-prompt-reverse ~/.claude/skills/
```

**Cursor**
Newer versions support `.cursor/skills/`; older versions import `SKILL.md` as rules / instructions.

**Codex (OpenAI)**
Integrate `SKILL.md` body as `AGENTS.md` / instructions.

**Any tool supporting long instructions**
Paste `SKILL.md` + `references/` as the system prompt.

## Usage
1. Give an image (or describe intent)
2. The skill deconstructs it → asks 1–2 minimal questions (platform / direction / use)
3. Output: faithful + enhanced + 3 variants + platform-adapted prompts

See [`SKILL.md`](SKILL.md).

## Structure
```
image-prompt-reverse/
├── SKILL.md                  role / workflow / triggers
├── references/
│   ├── reverse-dimensions.md dimension breakdown
│   ├── enhancement-vocab.md  enhancement + negative vocab
│   ├── platform-guides.md    MJ / DALL-E / SD / Flux syntax
│   └── templates.md          copy-paste templates
├── assets/
│   └── analysis-form.md      analysis skeleton
├── README.md
├── README_en.md
└── LICENSE
```

## License
MIT — see [`LICENSE`](LICENSE).
