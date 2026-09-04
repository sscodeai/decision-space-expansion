# Decision-Space Expansion

> **Expand the option space before you decide.**

A decision methodology distilled from the `decision-workbench` project: before making an important decision, use a **heterogeneous multi-model committee** to widen the option space, structure the divergence, then fold real constraints back in — and let a **human make the final call**.

## Why

- **Decision power = size of the option space**, not the ability to pick. Your cognitive surface *is* your decision ceiling.
- A single model (or one model in many roles) only re-samples its own training distribution. **True divergence requires different model families** (Anthropic / OpenAI / DeepSeek / Google / local OSS), isolated from each other to prevent anchoring.
- Model disagreement is often post-hoc rationalization + ecosystem bias — but ecosystem blind spots are exactly the highest-value divergence (e.g. CN models raise ICP/WeChat/Aliyun; Western models default to AWS).

## The loop (3 stages)

### 1. Diverge — widen the options

- Feed the **same brief** to models from **different families**, isolated (invisible to each other).
- Assign stances per model: architecture / cost / security / product → natural divergence.
- **Mandatory question patterns:**
  - *"Why didn't you choose X?"* — forces out excluded options + reasons (highest information density)
  - *"Give one non-mainstream option with a real justification."* — kicks the model off its training distribution
  - *"Where is this plan most vulnerable?"* — cross-examination a single model never performs on itself

### 2. Structure — sort the options

- **Consensus zone** → adopt directly (standard-answer parts of the system).
- **True divergence zone** → worth human arbitration.
- **Pseudo-divergence zone** → noise, discard (e.g. PHP vs Go for a CRUD system is not a material difference).

### 3. Converge — decide with real constraints

- Fold back real constraints: budget, team skills, timeline, market, compliance.
- Optional: `pyDecision` (AHP/TOPSIS/PROMETHEUS) turns options into comparable score tables.
- **Final review is always human.** Models fail confidently.

## Core beliefs

- *"AI shouldn't make important decisions for you. It should make the decision space harder for you to misunderstand."*
- The committee expands your *known unknowns*; it cannot reach *unknown unknowns* — and being forced to understand the divergence while converging **is the cognitive growth**.
- Best posture: ask AI when you **don't know what you don't know**, not when you already know what you want.

## Pitfalls

- Don't treat the committee as an "auto-optimal-answer" machine — open tools (MoA / LLM-Blender) fuse answers by default and **delete the human arbitration step**, which is the opposite direction.
- Pseudo-divergence wastes time: models will fabricate complete rationales for any assigned stance.
- When requirements don't constrain the choice, models output their own familiar default — not an optimum.
- Models silently assume hidden constraints (concurrency, budget, team); humans must backfill the real ones.

## Install into AI tools

This repository ships the methodology in the **Agent Skills** format (a single Markdown file with YAML frontmatter). It works with any tool that can consume instruction files — no code, no dependencies.

| Tool | Where to put it |
|---|---|
| **Claude Code** | `~/.claude/skills/decision-space-expansion/SKILL.md` (global) or `.claude/skills/decision-space-expansion/SKILL.md` (per-project) |
| **Cursor / Windsurf** | `.cursor/skills/decision-space-expansion/SKILL.md`, or `.cursor/rules/` |
| **OpenAI Codex** | Put the core method into `AGENTS.md`, or point Codex at the file as reference docs |
| **Gemini CLI** | `~/.gemini/skills/` (agent skills are supported) |
| **Any agent / chat** | Paste the SKILL.md content into the conversation, or `cat SKILL.md` and follow it |

> Note: `SKILL.md` is tool-agnostic. Swap "different model families" for whatever pool your environment can reach (aggregator, multi-CLI, local Ollama/vLLM) — the method stays the same.

## Files

- `README.md` — this human-readable summary
- `SKILL.md` — full skill definition (frontmatter + body), consumable by Claude Code, Cursor, Codex, Gemini CLI, Hermes, and any Markdown-reading agent

Related: the reference implementation lives in the `decision-workbench` repository (FastAPI + React, mock zero-key, 31 tests, hidden-gold eval: single-model 26% → naive multi-agent 78% → decision-workbench 100% / 12).

## License

MIT
