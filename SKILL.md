---
name: decision-space-expansion
description: "Use multi-model committee to expand options before deciding."
version: 1.1.0
author: Moon (sscodeai)
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [decision, multi-model, committee, architecture, option-space, divergence-convergence]
    related_skills: [pi-autodev, claude-code, codex, opencode]
---

# Decision-Space Expansion — expand the option space before you decide

Core methodology (established 2026-08): **before making an important decision, use a heterogeneous multi-model committee to widen the option space, structure the divergence, then fold real constraints back in — and let a human make the final call.** Decide inside a space you intentionally expanded, not inside your own prior cognition.

The complete loop has three stages:

## Stage 1 — Diverge (widen the options)

- Feed the **same brief** to models from **different families** (Anthropic / OpenAI / DeepSeek / Google / local OSS), answered in isolation (invisible to each other — prevents anchoring).
- Assign a stance to each model: architecture / cost / security / product → plans naturally diverge.
- Any heterogeneous model pool works: provider aggregators, multiple CLIs (Claude Code, Codex, Gemini CLI, opencode), local Ollama/vLLM endpoints, or a self-hosted gateway. What matters is **model-family diversity, not count**.
- **Mandatory question patterns:**
  - *"Why didn't you choose X?"* — forces out excluded options + reasons (highest information density)
  - *"Give one non-mainstream option with a real justification."* — kicks the model off its training distribution
  - *"Where is this plan most vulnerable?"* — cross-examination a single model never performs on itself

## Stage 2 — Structure (sort the options)

Classify the proposals:
- **Consensus zone** → adopt directly (the parts with standard answers, e.g. a state machine + WebSocket for a queueing system).
- **True divergence zone** → worth human arbitration.
- **Pseudo-divergence zone** → noise, discard (e.g. PHP vs Go for a CRUD system is not a material difference).

## Stage 3 — Converge (decide with real constraints)

- Fold back real constraints: budget, team skills, timeline, market/region, compliance — let the AI weigh options **inside the already-expanded space**.
- Optional: `pyDecision` (AHP / TOPSIS / PROMETHEUS) turns options into comparable score tables.
- **Final review is always human.** Models fail confidently.

## Core beliefs

- Decision power = size of the option space, not the ability to pick. Your cognitive surface *is* your decision ceiling.
- Model disagreement = training-data geography/ecosystem bias + post-hoc rationalization, not deep reasoning. The most valuable divergence is the geography/ecosystem blind spot (e.g. China-region models raise ICP filing / WeChat mini-programs / Aliyun; Western models default to AWS).
- Same-model-multi-role gives role diversity only, not cognitive diversity — heterogeneous models produce real divergence.
- The committee expands your *known unknowns*; it cannot reach *unknown unknowns* — and being forced to understand the divergence while converging **is the cognitive growth**.
- Best posture: ask AI when you **don't know what you don't know**, not when you already know what you want.

## Pitfalls

- Don't treat the committee as an "auto-optimal-answer" machine — open fusion tools (MoA / LLM-Blender) merge answers by default and **delete the human arbitration step**, which is the opposite direction.
- Pseudo-divergence wastes time: models fabricate complete rationales for any assigned stance (preference first, reasons after).
- When requirements don't constrain the choice, models output their own familiar default — not an optimum.
- Models silently assume hidden constraints (concurrency, budget, team); humans must backfill the real ones.

## Output template

A decision report should include: option skeletons → consensus / true-divergence / pseudo-divergence zones → trade-offs for each true divergence → recommendation + rejection reasons → a one-liner on the point the human must decide.
