# Multi-Agent Knowledge Guide — Interactive Demo

> **What this is:** A self-contained, interactive walkthrough of the Multi-Agent Knowledge Guide architecture documented in the [companion white paper](https://prachidevgaonkar.github.io/Multiagent-Knowledge-Guide-GCP/). No backend, no setup — open the HTML file and step through real scenarios to see how the system actually behaves.

---

## Why this exists

The white paper explains the design. This demo shows the experience. After sharing the paper, the most common question was *"what does it actually feel like to use?"* — so this simulates the full agent interaction: a query comes in, the Orchestrator classifies intent and routes it, one or more specialist agents respond, and (for cross-domain queries) the results get aggregated into a single answer.

Nothing here calls a live model. Every response is a scripted recreation of real interaction patterns from the POC, built so the underlying architecture is visible and explorable without any setup.

---

## What's inside

**Architecture diagram** — the four-layer system end to end: Google Chat → Cloud Function (async dispatch via Cloud Tasks) → Orchestrator Agent → data sources (Cloud Storage, BigQuery, code files saved in txt format).

The Orchestrator layer is built through **Vertex AI Agent Designer** — prompt-driven configuration rather than hand-written routing code. Intent classification, routing rules, and response aggregation all live in configuration and system prompts.

**Five interactive scenarios** — each one runs as an animated step-through with a "Run scenario" button:

| Scenario | Prompt | What it shows |
|---|---|---|
| 📄 Functional Spec | *"Share the functional specification for the Knowledge Guide agent"* | Doc Agent returning a structured spec pulled from Cloud Storage |
| 🐛 New Issues & Features | *"List 5 new issues or feature requests for the agent"* | Issue Agent generating SQL at `temperature=0`, returning a formatted table |
| 💻 Technical Stack | *"Explain the technical stack for backend deploy.py"* | Code Agent surfacing an actual file snapshot plus a stack breakdown |
| 🔀 Issues + Code Snapshot | *"List open issues and help me with the relevant code snapshot"* | Issue Agent and Code Agent running in parallel, Orchestrator aggregating both into one response |
| 🚀 Onboarding Journey | *"Share the onboarding journey for a Full-Stack Developer"* | Doc Agent synthesising a 5-step path across program docs, team structure, delivery status, and code repositories |

Each scenario shows the **routing trace** (which agent(s) were called and why), realistic data freshness warnings, and response formats that match what each agent actually returns — tables, SQL, code blocks, structured specs.

**Lessons, issues, and roadmap** — pulled directly from the white paper: what worked, what didn't, the three active issues still being worked through, and where the system goes next (multimodal outputs, voice, continuous evaluation, governed self-improvement).

---

## How to use it

1. Download `multi-agent-demo.html`
2. Open it in any browser — no server, no install, no dependencies
3. Pick a scenario tab and click **Run scenario** to watch it play out

To host it publicly, enable **GitHub Pages** on this repo (Settings → Pages → deploy from branch) and link directly to the file.

---

## Related

- 📄 [White paper — Multi-Agent Knowledge Guide on Google Cloud Vertex AI](https://prachidevgaonkar.github.io/Multiagent-Knowledge-Guide-GCP/)

---
