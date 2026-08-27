# AI Bootcamp Notes

## Key takeaway

Historically, craft excellence meant making teams more productive. That still applies to agents: tune codebases and harnesses so agents work better. That's what we control most when coding with AI.

---

## Industry direction

Large engineering organizations are moving from **AI-assisted coding** toward **agentic software development** — agents taking on increasingly complete pieces of the software lifecycle, not just autocomplete.

- **Microsoft** — transitioning from a traditional "software factory" to an **AI and agent factory**, with agents integrated across planning, development, review, security, operations, and modernization
- **GitHub** — autonomous coding agents in standard developer workflows; tasks delegated from issues through implementation, testing, PR creation, and review; multiple agent providers supported in the same workflow
- **Anthropic** — agent performance heavily influenced by the **harness and environment around the model**, including tests, task decomposition, context management, tooling, and structured handoffs

The shift is bigger than writing code faster with AI. As models become more capable, engineering leverage increasingly comes from designing the environment they operate in:

**better codebases → better context → better tools → better validation → better agent output**

Codebase and harness design is therefore a form of engineering craft: optimize the system so both humans and agents can work effectively.

---

## Harness & configuration

A **harness** helps agent models read and act effectively. Improving it should use fewer tokens or be more efficient.

| Layer | Purpose |
| --- | --- |
| **Personal** | Tweak how the coding agent works for your preferences |
| **Repo** | Configure how the agent operates for everyone on a repo |
| **Company** | Broad security and systems alignment |

Also set up environments before relying on coding agents. A **coding sandbox** is a guardrail that limits what the agent can do. **Memory** helps the agent learn; it is local to you.

---

## AGENTS.md

- Shown in context for every new thread — keep only essentials to cut token overhead
- Keep it small; some agents truncate large files
- [agents.md](https://agents.md) — explore and understand the format better

---

## Skills

A **skill** is a reusable set of instructions (name + description in markdown, allowed tools, instructions). Example format: `/review-code`.

- Tune skills so they load only when needed
- Skills guide agent behavior without always filling the context window

---

## Optimize the codebase for agents

- Keep files under ~300 lines
- Reduce noisy tool outputs
- Prefer simple / deterministic commands
- Use **spec-driven development**
- Agents can work with or reference multiple repositories natively

**Context window:** typically 200k–1M tokens; after that, compaction causes accuracy loss.

---

## Validation

| Approach | What it means |
| --- | --- |
| **Fast validation** | Formatting, linting, typechecking, focused unit tests, other deterministic checks |
| **Shift left** | Make important checks available before commit or PR creation |
| **End-to-end** | Exercise behavior through the real boundary that matters |
| **Independent review** | Second agent, different model, or human — catch missing requirements and risks |

**Evals** = systematic tests of an AI system's performance, accuracy, and behavior.

---

## Working with agents

| Concept | Notes |
| --- | --- |
| **Tools** | An agent can access different tools |
| **Grilling** | Strategy to help the agent figure out what you want |
| **Parallel execution** | Git worktrees = parallel checkouts of the same repo; Codex auto-creates per task |
| **Dev boxes** | Remote environments for heavy services |

**Don't patch bad output by hand and move on** — that teaches the system nothing. Workarounds also degrade the environment over time.

---

## Cursor-specific

- **Multitask** is powerful with Autopilot
- Broad asks can spin up as many sub-agents as needed
- **Autopilot** = "hand over this PR" and drive it toward merge-ready
- **Custom workflows / pstack** — Cursor plugin: skills that talk to each other and reach different levels of understanding or outcome

---

## Todos

- [ ] Explore and better understand [agents.md](https://agents.md)
- [ ] Look for skills repositories
- [ ] Look into loop engineering
- [ ] Look into plannotator
- [ ] Look into calldiff
