# Roadmap

This roadmap reflects the current direction of the project.  
It is intentionally focused, incremental, and biased toward shipping usable artifacts early.

The goal is not to build everything at once, but to validate the core idea:
**intent-aware shell suggestions that respect expert users.**

---

## v0.1 — Proof of Concept (Foundation)

**Goal:** Demonstrate real-time, read-only AI suggestions in a shell.

- zsh integration (initial target)
- Capture partial command input
- Collect minimal local context:
  - CWD
  - recent shell history
- Send context to LLM backend
- Receive a single-line suggestion
- Render suggestion inline (non-blocking, non-intrusive)
- No learning
- No persistence
- No auto-execution

This version proves feasibility and sets architectural boundaries.

---

## v0.2 — Architecture & Extensibility

**Goal:** Make the system modular and contributor-friendly.

- Abstract LLM backend interface
  - OpenAI adapter
  - Claude adapter
  - Custom / local adapter
- Separate concerns:
  - shell input capture
  - context collection
  - intent reasoning
  - suggestion rendering
- Add configuration file support
- Define strict output contracts for LLM responses

---

## v0.3 — Heuristics + Intent Confidence

**Goal:** Reduce noise and improve trust.

- Introduce confidence thresholds
- Silence suggestions when confidence is low
- Add basic heuristic layer before LLM calls:
  - obvious syntax completion
  - known tool patterns
- Add lightweight validation for suggested commands
- Prevent hallucinated tools and flags

---

## v0.4 — Workflow Awareness

**Goal:** Move from commands to workflows.

- Detect common workflow phases:
  - build → test
  - scan → enumerate → exploit
- Suggest *next-step* commands (still read-only)
- Optional pentesting-aware mode
- Respect OPSEC-aware defaults

---

## v0.5 — Learning (Opt-In)

**Goal:** Personalization without surveillance.

- Local-only learning
- Track preferred tools and flags
- Adapt suggestion ranking
- No cloud storage
- No cross-user learning unless explicitly enabled

---

## Future Considerations (Not Committed)

These ideas are intentionally **out of scope for now**:

- Auto-execution
- Autonomous agents
- Chat-style terminal UI
- Cloud-dependent mandatory features
- Heavy telemetry

They may be explored only if they align with the core philosophy.

---

## Guiding Rule

Each milestone must:
- improve usefulness
- preserve control
- avoid breaking flow

If a feature violates these, it does not belong.
