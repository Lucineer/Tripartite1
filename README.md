# Tripartite1 🔍

You never get a compromised answer here. You get *no* answer, or one that three fully independent agents produced verbatim. No voting, no averaging—exact agreement only.

This is a prototype exploring multi-agent consensus, built for the Cocapn Fleet. It runs on a single Cloudflare Worker with zero dependencies.

**Live:** [tripartite1.casey-digennaro.workers.dev](https://tripartite1.casey-digennaro.workers.dev)

---

## Why It Exists

Agents make mistakes. Asking one agent to check its own work often fails. Tripartite1 doesn't try to build a perfect agent. Instead, it surfaces every disagreement by requiring three independent agents to agree exactly. You see the full divergence when they don't.

---

## Quick Start

1.  **Fork** this repo. The code is yours to modify.
2.  Deploy to Cloudflare Workers: `wrangler deploy`
3.  Edit agent logic or prompts in `src/lib.rs`

That's it. One Worker, no external services required by default.

---

## How It Works

Three isolated agents run the same query with no inter-agent communication:
- **Pathos:** Checks alignment with your original intent.
- **Logos:** Validates reasoning and factual consistency.
- **Ethos:** Assesses for potential harm or omission.

All three must return the same final answer, word for word. If any output differs, you see all three unredacted responses instead of a single answer.

---

## What Makes It Different

1.  **Unanimous consensus:** Rejects majority (2/3) agreement. Requires a perfect 3/3 match.
2.  **Complete isolation:** Agents cannot influence each other; no cross-talk or groupthink.
3.  **Failure as a feature:** Returns nothing rather than a potentially unreliable answer.

---

## Capabilities

- **Exact tripartite consensus:** All output requires verbatim agreement from three agents.
- **Independent execution:** Agents run in strict isolation with separate system prompts.
- **On-worker processing:** By default, all logic runs locally within the Worker.
- **Controlled data sharing:** Optional external calls only occur after automatic redaction of sensitive fields.
- **Full transparency:** Complete disagreement logs are shown on every consensus failure.
- **Fork-first design:** The entire system is built to be copied and modified.
- **MIT licensed:** Free for any use.

---

## Current Limitation

The strict unanimity rule can be overly brittle. If two agents produce identical, correct answers and the third differs by a single punctuation mark, you receive no consensus answer—only the three raw outputs. This design favors precision over recall.

---

Attribution: Superinstance and Lucineer (DiGennaro et al.)

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>