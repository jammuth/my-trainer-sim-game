# CLAUDE.md

Project-specific context for Claude Code. Shared rules (guardrails, TDD workflow, git, commits, secrets, reporting, tech-stack defaults) live in the global `~/.claude/CLAUDE.md`.

---

## Project Overview

**Trainer Sim** — a single-character, stat-raising management sim (adults only, 18+, high fantasy) in the vein of Slave Maker and Princess Maker 2. The player is a guild trainer who schedules a trainee's days over a 70-day contract (8 day slots + 4 evening slots per day) and is graded on her final stats, which pick one of three v1 endings. Content (characters, events, art) loads as drop-in data packs so the game is moddable; v1 is text-only.

- **Design doc:** [docs/game-design.md](docs/game-design.md) — the source of truth for the design; read it before working on gameplay, and update it in the same change when a design decision is made or changed. The original online draft is no longer kept in sync, so don't treat it as current.
- **Stack:** Godot, Linux-only for v1. Personal hobby project, no public release yet — favour getting a playable loop over polish.
- **Content rule:** every character is original (or properly licensed) and unambiguously adult; keep it that way in any content or mod tooling.
- **Undecided** (see the doc's Open questions): final stat list, exact stat/pay/threshold numbers, praise/punishment effects. Ask rather than invent these.
