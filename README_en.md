# image-prompt-reverse

![version](https://img.shields.io/badge/version-1.0.1-blue) ![released](https://img.shields.io/badge/status-released-brightgreen)

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

## Install / Load across tools
This is a standard agent-skills package (`<skill-name>/SKILL.md` + `references/`). It is **not tied to any specific client** and works as-is in WorkBuddy, Claude Code, Cursor, Codex, and any tool that supports long instructions. Core rule: the agent only needs to read `SKILL.md` and its referenced `references/*.md`. For detailed reproduction steps and per-tool loading notes, also see `tests/README.md` › "在各类工具中复现" (Load across tools); the two are kept in sync.

**WorkBuddy (user-level, recommended)**
```bash
cp -r image-prompt-reverse ~/.workbuddy/skills/
```
Project-level: copy into `<workspace>/.workbuddy/skills/`. A new session triggers automatically on image input; Step 8 image verification is opt-in (requires authorization + built-in ImageGen).

**Claude Code**
```bash
cp -r image-prompt-reverse ~/.claude/skills/
```
Native agent-skills support auto-discovers `SKILL.md`. You can also import it in `CLAUDE.md` via `@<path>/SKILL.md`, or fold key `SKILL.md` content into `CLAUDE.md` / `AGENTS.md` as persistent instructions.

**Cursor**
Create `image-prompt-reverse.mdc` under `.cursor/rules/`, paste the `SKILL.md` body and note the `references/*.md` to include; set the rule type to `always` (persistent) or `auto`/`manual` (on demand). Or paste the essentials in Settings › Rules for AI. (Newer versions also support `.cursor/skills/`.)

**Codex (OpenAI)**
Fold `SKILL.md` essentials (with `references/` path notes) into the repo-root `AGENTS.md` (or `codex.md`); for full capability, include the entire `SKILL.md` body + `references/` in the project context.

**Any tool supporting long instructions**
Paste the `SKILL.md` body (+ `references/*.md` as needed) as the system prompt / long context, then send the input image with "reverse this image" to reproduce.

> Note: tool loading entry points evolve across versions; follow each tool's official docs. Results are consistent as long as the Skill is correctly loaded. Step 8 image verification is WorkBuddy-only; other tools fall back to prompt-only delivery (does not affect the Step 0–7 output package — expected behavior).

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
├── tests/                   end-to-end test cases
│   ├── README.md            case guide (how to reproduce / case list)
│   ├── case-01-crt-sand-sky.md  walkthrough (CRT TV + sand + sky)
│   ├── assets/
│   │   └── case-01-input.jpg   test input image
│   └── NOTICE-assets.md      image license & attribution
├── RELEASE_NOTES.md         release notes (v1.0.1)
├── README.md
├── README_en.md
└── LICENSE
```

## Dependencies & Maintenance

- **Optional enhancement dependency**: `prompt-model-adaptation` (used only for Step 6 methodology naming, meta-usage, and output QA; the core reverse-engineering flow works independently if it is not installed).
- **Maintenance note**: If you maintain both the source copy and a user-level copy (`~/.workbuddy/skills/image-prompt-reverse`), sync them with `cp -r` after edits to avoid version drift.

## License
MIT — see [`LICENSE`](LICENSE).
