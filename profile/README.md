# Seer

### **Infrastructure for agents that actually *do* things.**

If you’re building agents that interface with the messy real world (GitHub, Asana, Gmail), "vibe coding" a system prompt isn't enough. Seer provides the primitives to move from flaky demos to deterministic, self-healing agents.

## 🛠 The Stack

### 1. Dynamic Tool Discovery (`tool_hub`)
Hardcoding 50 tools into a system prompt leads to hallucinations and context-window bloat.
* **The Solution:** We implement **Dynamic Tool Selection** at runtime. Your agent only "sees" and "loads" tools relevant to the current execution state, keeping the context lean and performance high.

### 2. Multi-Agent Delegation (`supervisor`)
Context-window pollution is the #1 killer of agent reliability.
* **The Problem:** One agent trying to do everything eventually loses the thread.
* **The Solution:** Our `supervisor` repo implements a **Supervisor-Worker** pattern. The supervisor manages high-level state and spawns ephemeral sub-agents for specific sub-tasks. This keeps the context for each task surgically clean.

### 3. Setup-Free Testing (`eval_agent`)
Generating test cases is boring; provisioning environments to run them is worse.
* **The Solution:** Our **Eval Agent** handles the "Setup Fatigue." It interviews your code to generate a spec, then **automatically provisions sandboxed integrations** (GitHub repos, Jira boards, etc.) to run the tests. You provide the goal; Seer provides the environment.

---

## 🏗 Repositories
* **[`seer`](https://github.com/seer-engg/seer):** The core ARE (Autonomous Reliability Engineering) engine.
* **[`supervisor`](https://github.com/seer-engg/supervisor):** Logic for spawning sub-agents and maintaining clean context boundaries.
* **[`tool_hub`](https://github.com/seer-engg/tool_hub):** Runtime discovery and dynamic tool routing.

## ⚖️ License & Contributions
We use **AGPL-3.0**. If you run a hosted version of Seer, you must share your modifications. 

Contributing requires a **Contributor License Agreement (CLA)** so we can support teams whose legal policies prevent them from using AGPL directly. See `CONTRIBUTING.md` for details.
