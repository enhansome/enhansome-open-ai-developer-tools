# Awesome Open AI Developer Tools with stars

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**A curated guide to the open-source AI stack — every layer, every proprietary tool you can replace.**

Coding agents · local inference · agent frameworks · vector DBs · RAG · evals · observability

**English** · [Türkçe](docs/languages/tr.md) · [简体中文](docs/languages/zh.md) · [Español](docs/languages/es.md) · [*add your language*](docs/community/translations.md) · [🌐 Website](https://sami-uysal.github.io/awesome-open-ai-developer-tools/)

***

Every entry answers three questions:

1. **What does it do?**
2. **What closed-source product does it replace?**
3. **Why would you pick it over the alternatives?**

Each entry also carries a maturity badge: 🟢 stable (production-ready) · 🟡 active (works great, moves fast) · 🟠 experimental (early, expect rough edges).

No affiliate links. No sponsored slots. OSI-licensed only — source-available tools are included but labeled.

> **On licenses:** the license shown for an entry is a pointer, not a guarantee — projects relicense, and this list lags. Read the `LICENSE` file in the repository before depending on one commercially. Where no license is shown, we have not confirmed it.

***

## Contents

* [Coding Agents & Pair Programmers](#coding-agents--pair-programmers)
* [Prompt-to-App Builders](#prompt-to-app-builders)
* [Autonomous & Persistent Agents](#autonomous--persistent-agents)
* [Agent Sandboxes & Browser Control](#agent-sandboxes--browser-control)
* [Agent Frameworks & Orchestration](#agent-frameworks--orchestration)
* [Model Context Protocol (MCP)](#model-context-protocol-mcp)
* [Local Inference Engines](#local-inference-engines)
* [Inference Servers & Gateways](#inference-servers--gateways)
* [Chat UIs & Frontends](#chat-uis--frontends)
* [Vector Databases](#vector-databases)
* [Embeddings & Rerankers](#embeddings--rerankers)
* [RAG Frameworks](#rag-frameworks)
* [Fine-Tuning & Training](#fine-tuning--training)
* [Evals, Testing & Guardrails](#evals-testing--guardrails)
* [Observability & LLMOps](#observability--llmops)
* [Speech, Vision & Multimodal](#speech-vision--multimodal)
* [Low-Code / Visual Builders](#low-code--visual-builders)
* [Open-Source Alternatives Cheat Sheet](#open-source-alternatives-cheat-sheet)
* [Choosing Your Stack](#choosing-your-stack)
* [Contributing](#contributing)

***

## Coding Agents & Pair Programmers

Agents that read, write, and refactor code in your repo.

### [aider](https://github.com/Aider-AI/aider) ⭐ 48,738 | 🐛 1,853 | 🌐 Python | 📅 2026-05-22

`Python` · `Apache-2.0` · CLI · 🟡 active

AI pair programming in your terminal. Maps your whole repository, edits files directly, and writes its own git commits.

* **Replaces:** GitHub Copilot, Cursor
* **Backends:** 100+ models via LiteLLM — Claude, GPT, Gemini, plus local models through Ollama or any OpenAI-compatible endpoint
* **Edge:** The repo map gives it whole-codebase context without dumping every file into the prompt. Auto-commits mean every AI edit is a revertable checkpoint. Editor-agnostic — works alongside VS Code, Neovim, Emacs, or nothing at all.

### [OpenCode](https://github.com/sst/opencode) ⭐ 203,964 | 🐛 5,708 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · TUI · 🟢 stable

Terminal-native coding agent with LSP integration — it loads the right language server so the model sees real type information, not guesses.

* **Replaces:** Claude Code, Cursor
* **Backends:** Anthropic, OpenAI, Google, local models; provider-agnostic by design
* **Edge:** LSP-grounded suggestions cut hallucinated APIs. Client/server split means you can drive one session from multiple clients.

### [Cline](https://github.com/cline/cline) ⭐ 67,477 | 🐛 1,213 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` · VS Code extension · 🟢 stable

Autonomous coding agent inside VS Code. Plans, edits files, runs terminal commands, and uses the browser — asking permission at each step.

* **Replaces:** Cursor Composer, Devin
* **Backends:** Anthropic, OpenAI, Google, AWS Bedrock, Azure, OpenRouter, Ollama, LM Studio
* **Edge:** Human-in-the-loop by default — every file diff and shell command needs approval. Plan/Act mode separation stops the agent from bulldozing a codebase.

### [Continue](https://github.com/continuedev/continue) ⭐ 35,760 | 🐛 938 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` · VS Code + JetBrains · 🟢 stable

Build your own AI code assistant — autocomplete, chat, and edit, configured with your own models and context providers.

* **Replaces:** GitHub Copilot
* **Backends:** Any — local (Ollama, llama.cpp) or hosted
* **Edge:** Fully configurable context providers (docs, terminal, git diff, codebase). Tab-autocomplete works well with small local models, so you can run genuinely offline.

### [OpenHands](https://github.com/All-Hands-AI/OpenHands) ⭐ 86,172 | 🐛 648 | 🌐 TypeScript | 📅 2026-09-04

`Python` · `MIT` · Web + headless · 🟢 stable

Agents that do what a developer does — modify code, run commands, browse the web, call APIs — inside a sandboxed runtime.

* **Replaces:** Devin
* **Backends:** Anything LiteLLM supports
* **Edge:** Real sandboxed execution (Docker) rather than a chat that pretends to run things. Headless and CLI modes make it scriptable in CI.

### [SWE-agent](https://github.com/SWE-agent/SWE-agent) ⭐ 20,219 | 🐛 92 | 🌐 Python | 📅 2026-08-31

`Python` · `MIT` · CLI · 🟡 active

Research-grade agent that turns a GitHub issue into a pull request.

* **Replaces:** Devin, issue-to-PR bots
* **Edge:** The agent-computer interface (ACI) is the point — carefully designed tools beat a bigger model. If you're building your own agent, read this codebase first.

### [Goose](https://github.com/block/goose) ⭐ 53,910 | 🐛 296 | 🌐 Rust | 📅 2026-09-04

`Rust` · `Apache-2.0` · CLI + desktop · 🟢 stable

Extensible autonomous agent from Block, now governed by the Linux Foundation. Installs, executes, edits, and tests — not just suggests.

* **Replaces:** Devin, Cursor agent mode
* **Backends:** Any provider, plus first-class MCP extension support
* **Edge:** More autonomous than aider — plans and iterates with less hand-holding. Vendor-neutral governance under the Linux Foundation means no rug-pull risk, which matters for tooling you standardize a team on.

### [BitFun](https://github.com/GCWing/BitFun) ⭐ 2,047 | 🐛 154 | 🌐 Rust | 📅 2026-09-04

`Rust + TypeScript` · `MIT` · Desktop + CLI · 🟡 active

Cross-platform coding and desktop agent that plans, edits, tests, and commits inside real Git repositories.

* **Replaces:** Cursor, Claude Desktop
* **Backends:** User-configured model providers; model-agnostic by design
* **Edge:** A Rust runtime binds each conversation to task-specific Mini Apps while retaining filesystem, terminal, Git, browser, desktop, and remote-workspace execution. A self-hostable zero-knowledge relay supports cross-device session control without routing workspace data through a vendor cloud.

### [Orkas](https://github.com/Orkas-AI/Orkas) ⭐ 1,705 | 🐛 13 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · Desktop · 🟡 active

Local-first desktop AI workforce where a Commander plans work and coordinates built-in specialists and external coding agents through one chat.

* **Replaces:** Cursor agent mode, cloud-hosted agent orchestrators
* **Backends:** Claude, OpenAI, Gemini, DeepSeek, Kimi, GLM, Qwen, MiniMax, Doubao, and compatible local model endpoints
* **Edge:** Orkas runs the orchestration layer on the user's machine: conversations, files, agent configuration, and model keys stay local, while the Commander can dispatch Claude Code, Codex, OpenCode, and Cline as local subprocesses alongside built-in agents.

### [ordewell](https://github.com/ordewell/ordewell) ⭐ 18 | 🐛 3 | 🌐 TypeScript | 📅 2026-09-02

`Rust` · `Apache-2.0` · CLI / TUI · 🟡 active

Plan-first CLI/TUI orchestrator that converts a single goal into an ordered, editable plan of coding-agent tasks.

* **Replaces:** Manual task decomposition and multi-agent CLI scripting
* **Backends:** Claude Code, Codex, OpenCode
* **Edge:** Features a read-only planner that generates explicit step-by-step agent plans before execution, with per-task runner, model, and mode assignment.

### [Atomic Agent](https://github.com/AtomicBot-ai/atomic-agent) ⭐ 2,490 | 🐛 25 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · CLI + TUI · 🟠 experimental

Local-first coding and desktop agent that runs open-weight models on your machine, with no account or API key needed to install and run it.

* **Replaces:** Claude Code, Cursor, GitHub Copilot
* **Backends:** Bundled `llama.cpp` fork for local quantized models, plus any OpenAI-compatible endpoint, with presets for OpenRouter, LM Studio, and Ollama Cloud
* **Edge:** Ships its own `llama.cpp` fork and manages the backend process itself, so a quantized local model stays usable across long multi-step runs without a separate server setup. The control loop and all state, including a five-layer memory store, stay on the machine, and 56 built-in tools cover browser, filesystem, git, and vision alongside external MCP servers. The README labels it a developer preview: APIs, commands, and config still move between releases.

### [Kilo Code](https://github.com/Kilo-Org/kilocode) ⭐ 27,174 | 🐛 562 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` · VS Code + JetBrains · 🟢 stable

Open-source IDE agent that merged the best of Roo Code and Cline into one extension.

* **Replaces:** Cursor, Windsurf
* **Edge:** Orchestrator mode splits a large task into subtasks handled by specialized modes. Absorbs upstream features from both parents, so it moves faster than either did alone.

### [Tabby](https://github.com/TabbyML/tabby) ⭐ 33,859 | 🐛 336 | 🌐 Rust | 📅 2026-06-30

`Rust` · `Apache-2.0` · Self-hosted server · 🟢 stable

Self-hosted AI coding assistant with its own inference server, no external API calls.

* **Replaces:** GitHub Copilot (enterprise)
* **Edge:** Runs on consumer GPUs, OpenAPI interface, and answers the compliance question ("where does our code go?") with "nowhere."

### [gpt-engineer](https://github.com/gpt-engineer-org/gpt-engineer) ⚠️ Archived

`Python` · `MIT` · CLI · 🟠 experimental

Describe a project in natural language; it writes and iterates on the whole codebase.

* **Edge:** Best for greenfield scaffolding rather than surgical edits on an existing repo.

***

## Prompt-to-App Builders

Prompt in, deployed full-stack app out.

### [bolt.diy](https://github.com/stackblitz-labs/bolt.diy) ⭐ 19,845 | 🐛 136 | 🌐 TypeScript | 📅 2026-02-07

`TypeScript` · `MIT` · 🟢 stable

Official open-source fork of Bolt.new. Prompt, run, edit, and deploy full-stack web apps in the browser — with the LLM of your choice.

* **Replaces:** Bolt.new, v0, Replit Agent
* **Backends:** OpenAI, Anthropic, Google, Groq, Mistral, DeepSeek, xAI, Ollama, LM Studio, OpenRouter, any OpenAI-compatible endpoint
* **Edge:** Self-hostable with zero telemetry. Multi-provider switching mid-project means you can start on a cheap model and escalate only where it matters.

### [Open Design](https://github.com/nexu-io/open-design) ⭐ 94,060 | 🐛 938 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` · Desktop + web · 🟠 experimental

Turns the coding agent you already have into a design engine — prototypes, landing pages, dashboards, slides, images, and video, exported as HTML/PDF/PPTX/MP4.

* **Replaces:** Claude Design, Figma Make
* **Backends:** BYOK through whatever agent is on your PATH — Claude Code, Codex, Cursor, Gemini, OpenCode, Qwen, and 20+ others
* **Edge:** Ships with a large library of brand-grade design-system packages, and every render reads a `DESIGN.md` brand contract, so output is consistent instead of randomly styled. Local-first: your brand assets never leave the machine.

### [OpenUI](https://github.com/wandb/openui) ⭐ 22,537 | 🐛 88 | 🌐 TypeScript | 📅 2026-08-27

`Python + TypeScript` · `Apache-2.0` · 🟡 active

Describe a UI, watch it render live, convert it to React/Svelte/Vue.

* **Replaces:** v0.dev
* **Edge:** Live iteration loop — describe the change, see it immediately. Works with local models via Ollama.

### [Dyad](https://github.com/dyad-sh/dyad) ⭐ 21,384 | 🐛 301 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` · Desktop · 🟢 stable

Local, open-source AI app builder. Runs on your machine, bring your own API keys.

* **Replaces:** Lovable, v0, Bolt
* **Edge:** No vendor lock-in and no cloud round-trip for your source code.

***

## Autonomous & Persistent Agents

Long-running agents with memory, goals, and self-direction.

### [OpenClaw](https://github.com/openclaw/openclaw) ⭐ 388,845 | 🐛 6,323 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · 🟡 active

Self-hosted personal AI assistant that runs on any OS and reaches you on any platform. One of the fastest-growing open-source projects ever.

* **Replaces:** ChatGPT desktop, Claude Desktop, Microsoft Copilot
* **Backends:** Any OpenAI-compatible API, Ollama, LocalAI
* **Edge:** Gateways into Telegram, Discord, Slack, WhatsApp, Signal, email, and CLI, so the agent reaches you where you already are — and can proactively message *you*. Large skill/plugin ecosystem. **Security note:** it holds credentials for your messaging accounts and runs autonomously; sandbox it and read the permission model before pointing it at anything sensitive.

### [Hivekeep](https://github.com/MarlBurroW/hivekeep) ⭐ 52 | 🐛 31 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · 🟡 active

Self-hosted platform to run a *team* of specialized AI agents that collaborate, keep persistent memory, and build their own tools, mini-apps, and plugins.

* **Replaces:** ChatGPT Team, Claude Desktop, hosted agent platforms
* **Backends:** Any OpenAI-compatible API, Ollama
* **Edge:** Multiple agents delegate to each other and share memory across months; a built-in web UI plus Telegram, Slack, Discord, and Matrix channels. Ships as a single container (Bun + SQLite), so the whole platform runs on modest hardware.

### [Hermes Agent](https://github.com/NousResearch/hermes-agent) ⭐ 241,377 | 🐛 39,567 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟡 active

Nous Research's self-improving agent — persistent memory, reusable skills, cron jobs, and 20+ messaging surfaces.

* **Replaces:** OpenAI Operator, Claude Desktop
* **Edge:** Closed learning loop: it creates skills from experience, refines them in use, and persists memory and session history in SQLite across restarts. Runs on a cheap VPS or serverless with no idle cost.

### [DeerFlow](https://github.com/bytedance/deer-flow) ⭐ 81,362 | 🐛 873 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟡 active

ByteDance's long-horizon "SuperAgent" harness — sandboxes, memory, skills, subagents, and a message gateway for tasks that run for minutes to hours.

* **Edge:** Built on LangGraph, but ships the whole runtime an agent actually needs (filesystem, memory, sandboxed execution, subagent spawning) instead of leaving you to assemble it. Hit #1 on GitHub Trending on the 2.0 release.

### [Open-Sable](https://github.com/IdeoaLabs/Open-Sable) ⭐ 25 | 🐛 0 | 🌐 Python | 📅 2026-05-22

`Python` · Local-first agent framework · 🟡 active

Autonomous agent with AGI-inspired cognitive subsystems — goals, working/episodic/long-term memory, metacognition, and tool use.

* **Edge:** Ollama-first with cloud fallback and a low-VRAM mode, so it genuinely runs on your own hardware. Memory decay and consolidation plus a watchdog/hot-reload supervisor make 24/7 operation realistic rather than aspirational.

### [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) ⭐ 187,120 | 🐛 568 | 🌐 Python | 📅 2026-09-04

`Python + TypeScript` · MIT (classic agent) / Polyform Shield (platform) · 🟢 stable

The project that started the autonomous-agent wave, now a low-code platform for building and running continuous agents.

* **Edge:** Visual block-based builder plus a library of pre-built agents. Note the license split — the classic agent is MIT, the newer platform is source-available, not OSI.

### [Letta](https://github.com/letta-ai/letta) ⭐ 24,621 | 🐛 39 | 📅 2026-08-23 (formerly MemGPT)

`Python` · `Apache-2.0` · 🟢 stable

Stateful agents with real long-term memory — the agent manages its own context window, paging memories in and out.

* **Replaces:** OpenAI Assistants API
* **Edge:** Memory is a first-class primitive backed by a database, not a vector-search bolt-on. Agents persist across sessions and are portable between models.

### [Mem0](https://github.com/mem0ai/mem0) ⭐ 64,706 | 🐛 725 | 🌐 Python | 📅 2026-09-04

`Python + TypeScript` · `Apache-2.0` · 🟢 stable

Memory layer you drop into any agent — extracts, stores, and retrieves facts about users across sessions.

* **Edge:** Framework-agnostic. Hybrid vector + graph store beats naively stuffing the chat log into a vector DB.

### [Khoj](https://github.com/khoj-ai/khoj) ⭐ 37,080 | 🐛 147 | 🌐 Python | 📅 2026-08-02

`Python` · `AGPL-3.0` · 🟢 stable

Self-hosted personal AI that searches your notes, documents, and the web; reachable from browser, Obsidian, and Emacs.

* **Replaces:** ChatGPT with memory, Notion AI
* **Edge:** Indexes *your* corpus locally. Runs fully offline with local models.

***

## Agent Sandboxes & Browser Control

Where agent-generated code actually runs, and how agents touch the web.

### [E2B](https://github.com/e2b-dev/E2B) ⭐ 13,674 | 🐛 47 | 🌐 Python | 📅 2026-09-04

`TypeScript + Go` · `Apache-2.0` · SDK + self-hostable infra · 🟢 stable

Secure cloud sandboxes for running AI-generated code, built on Firecracker microVMs.

* **Edge:** microVM isolation gives each sandbox its own kernel — a genuine security boundary, not just a container namespace. That distinction matters the moment you execute code a model wrote. Python and JS SDKs, plus [e2b-dev/infra](https://github.com/e2b-dev/infra) ⭐ 1,359 | 🐛 195 | 🌐 Go | 📅 2026-09-04 if you need to run the whole platform yourself.
* **Replaces:** proprietary code-interpreter backends

### [Daytona](https://github.com/daytonaio/daytona) ⭐ 71,803 | 🐛 453 | 📅 2026-07-24

`Go + TypeScript` · `Apache-2.0` · Server + SDK · 🟠 experimental

Sandbox runtime for AI agents with fast warm-pool starts and filesystems that persist across sessions.

* **Replaces:** E2B (when you need persistence over isolation strength)
* **Edge:** sandboxes can pause, resume, and outlive a single session, which is what long-horizon agents actually need. Container-based rather than microVM, so treat the isolation as weaker than E2B's — fine for your own code, think twice for genuinely untrusted input.

### [browser-use](https://github.com/browser-use/browser-use) ⭐ 112,274 | 🐛 395 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · Library · 🟡 active

Connects an LLM to a real browser so it can navigate, fill forms, and extract data.

* **Replaces:** Stagehand, MultiOn
* **Edge:** the most widely used open browser agent, with multi-tab handling and vision fallback when the DOM isn't enough. **Known weakness:** non-deterministic — the same goal takes different paths on different runs, which makes failures hard to reproduce, and vision calls on complex pages get expensive. Budget for retries and cap your spend.

### [Skyvern](https://github.com/Skyvern-AI/skyvern) ⭐ 22,930 | 🐛 219 | 🌐 Python | 📅 2026-09-04

`Python` · `AGPL-3.0` · Library + server · 🟢 stable

Browser automation driven by computer vision instead of DOM selectors.

* **Replaces:** Stagehand, brittle Playwright scraping suites
* **Edge:** because it navigates visually, a site redesign doesn't break your selectors — the usual reason scraping pipelines rot. **Check the license:** AGPL-3.0, and the anti-bot pieces are held back for the paid cloud. That combination rules it out for some commercial use.

### [Open Interpreter](https://github.com/openinterpreter/openinterpreter) ⭐ 68,239 | 🐛 11 | 🌐 Rust | 📅 2026-08-20

`Python` · `MIT` · CLI + Desktop · 🟢 stable

Lets Language Models run code locally on your computer to edit videos, analyze data, and control browsers.

* **Replaces:** OpenAI Code Interpreter (Advanced Data Analysis)
* **Backends:** Local models (Ollama, LM Studio) or hosted APIs (OpenAI, Anthropic)
* **Edge:** Runs directly in your local terminal environment with full access to system utilities, internet, and python packages without cloud execution limits.

***

## Agent Frameworks & Orchestration

Libraries for building multi-agent and tool-using systems.

### [LangGraph](https://github.com/langchain-ai/langgraph) ⭐ 41,055 | 🐛 750 | 🌐 Python | 📅 2026-09-03

`Python + JS` · `MIT` · 🟢 stable

Build agents as stateful graphs — nodes, edges, and explicit control flow, with checkpointing and human-in-the-loop interrupts.

* **Edge:** Durable execution: an agent can pause for hours awaiting human approval and resume with full state. The right choice when you need a *reliable* agent, not a demo.

### [CrewAI](https://github.com/crewAIInc/crewAI) ⭐ 58,089 | 🐛 726 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

Role-playing autonomous agents that collaborate — a "crew" with defined roles, goals, and tasks.

* **Replaces:** AutoGen, OpenAI Swarm
* **Edge:** Independent of LangChain, lean runtime. The role/task abstraction is the most intuitive on-ramp to multi-agent design. Flows give you event-driven control when crews are too loose.

### [AutoGen](https://github.com/microsoft/autogen) ⭐ 60,800 | 🐛 1,046 | 🌐 Python | 📅 2026-04-15

`Python + .NET` · `MIT` · 🟢 stable

Microsoft's framework for multi-agent conversation — agents talk to each other, execute code, and involve humans.

* **Edge:** Async event-driven core with a distributed runtime and cross-language support. AutoGen Studio gives a no-code prototyping UI.

### [smolagents](https://github.com/huggingface/smolagents) ⭐ 29,155 | 🐛 775 | 🌐 Python | 📅 2026-08-25

`Python` · `Apache-2.0` · 🟢 stable

Hugging Face's minimal agent library — the core logic is about a thousand lines.

* **Edge:** The fastest path to a working single-agent loop. Code agents write Python actions instead of emitting JSON tool calls, which is measurably more reliable for multi-step tasks. Read it end-to-end in an afternoon.

### [Google ADK](https://github.com/google/adk-python) ⭐ 21,410 | 🐛 497 | 🌐 Python | 📅 2026-09-04

`Python + Java` · `Apache-2.0` · 🟢 stable

Code-first toolkit for building, evaluating, and deploying multi-agent systems.

* **Edge:** Model-agnostic and deployment-agnostic despite the Google name. Built-in evaluation and a local dev UI close the "how do I know my agent got worse?" gap that most frameworks ignore.

### [Pydantic AI](https://github.com/pydantic/pydantic-ai) ⭐ 19,725 | 🐛 809 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

Agent framework from the Pydantic team — type-safe, structured outputs, dependency injection.

* **Edge:** If you already trust Pydantic for validation, this brings the same rigor to LLM I/O. Feels like FastAPI for agents.

### [DSPy](https://github.com/stanfordnlp/dspy) ⭐ 37,774 | 🐛 651 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

Program LLMs instead of prompting them — declare modules and let optimizers compile the prompts.

* **Edge:** Replaces manual prompt-tweaking with systematic optimization against a metric. Swap the model, recompile, keep the quality.

### [LiteLLM](https://github.com/BerriAI/litellm) ⭐ 58,043 | 🐛 4,932 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

One OpenAI-compatible interface for 100+ LLM providers, plus a proxy with keys, budgets, rate limits, and fallbacks.

* **Replaces:** OpenRouter (hosted)
* **Edge:** The single most useful piece of plumbing in the stack. Provider outage → automatic fallback. Per-team budgets and spend tracking come free.

### [Haystack](https://github.com/deepset-ai/haystack) ⭐ 26,417 | 🐛 104 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Production-oriented framework for composable RAG and agent pipelines.

* **Edge:** Explicit, inspectable pipeline graphs. Strong retriever/ranker ecosystem — favored when search quality is the hard part.

***

## Model Context Protocol (MCP)

The emerging standard for connecting models to tools and data.

### [MCP Specification](https://github.com/modelcontextprotocol/modelcontextprotocol) ⭐ 9,133 | 🐛 142 | 🌐 TypeScript | 📅 2026-09-04

`MIT` · 🟢 stable

The protocol itself — open standard for exposing tools, resources, and prompts to any LLM client.

* **Edge:** Write an integration once; every MCP-capable client (Claude Code, OpenCode, Cline, Continue, and more) can use it.

### [MCP Servers](https://github.com/modelcontextprotocol/servers) ⭐ 90,077 | 🐛 482 | 🌐 TypeScript | 📅 2026-09-03

`MIT` · 🟡 active

Reference implementations — filesystem, git, fetch, memory, and dozens of community servers.

* **Edge:** The fastest way to learn the protocol is to read a 200-line server that already works.

### [Mac Developer Bridge](https://github.com/alexanderradahl/mac-developer-bridge) ⭐ 23 | 🐛 4 | 🌐 JavaScript | 📅 2026-09-03

`JavaScript` · `MIT` · macOS / MCP · 🟠 experimental

Local MCP bridge that lets an existing ChatGPT conversation operate the Mac where the developer is already working: shell, unrestricted files, real PTY sessions, background jobs, and read-only Codex history.

* **Edge:** ChatGPT stays the reasoning layer and the bridge makes no model calls. Unlike a narrow filesystem or shell MCP, it is deliberately built for developer-machine parity and real interactive terminals. **Security tradeoff:** it is intentionally not sandboxed and runs with the macOS user's effective permissions, so it is only appropriate when that level of machine access is explicitly wanted.

### [MCP Inspector](https://github.com/modelcontextprotocol/inspector) ⭐ 10,828 | 🐛 42 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · 🟡 active

Official developer tool for testing and debugging MCP servers.

* **Edge:** shows you the actual protocol traffic — tool calls, resources, errors — instead of leaving you guessing why a client won't load your server. First thing to reach for when an MCP integration silently does nothing.

### [FastMCP](https://github.com/jlowin/fastmcp) ⭐ 27,525 | 🐛 306 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟡 active

The ergonomic way to build MCP servers and clients — decorator-based, like FastAPI.

* **Edge:** A working server in \~10 lines. Handles auth, deployment, proxying, and server composition.

### [octocode](https://github.com/Muvon/octocode) ⭐ 467 | 🐛 5 | 🌐 Rust | 📅 2026-09-04

`Rust` · `Apache-2.0` · 🟠 experimental

Local semantic code index with an MCP server on top — search and navigate a codebase by meaning, not grep.

* **Replaces:** the codebase indexing inside Cursor or Sourcegraph Cody
* **Backends:** local embeddings via fastembed, or a hosted provider if you'd rather offload it
* **Edge:** runs entirely locally, and embeddings are your choice. **Known weakness:** first index on a large repo is slow, and semantic search is genuinely bad at structural questions — "find every implementation of this trait" wants a structural index, not embeddings, so you need separate structural tools and have to know which kind of question you're asking before you search. Early-stage; treat it accordingly.

***

## Local Inference Engines

Run models on your own hardware.

### [Ollama](https://github.com/ollama/ollama) ⭐ 180,142 | 🐛 3,899 | 🌐 Go | 📅 2026-09-04

`Go` · `MIT` · 🟢 stable

Download and run open models with one command. The default entry point to local LLMs.

* **Replaces:** OpenAI API (for local workloads)
* **Edge:** `ollama run <model>` and you're done — it handles fetching, quantization, GPU offload, and serving an OpenAI-compatible API. The largest model library and the widest tool support of any local runtime.

### [llama.cpp](https://github.com/ggml-org/llama.cpp) ⭐ 127,044 | 🐛 2,409 | 🌐 C++ | 📅 2026-09-04

`C/C++` · `MIT` · 🟢 stable

The inference engine most local tooling is built on. Runs LLMs on CPU, CUDA, Metal, ROCm, Vulkan, and more.

* **Edge:** Extreme portability — a laptop, a Raspberry Pi, a Mac Studio, a server farm. GGUF quantization is the reason a large model fits on consumer hardware.

### [Jan](https://github.com/menloresearch/jan) ⭐ 44,335 | 🐛 509 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `AGPL-3.0` · Desktop · 🟢 stable

Offline ChatGPT alternative that runs entirely on your machine.

* **Replaces:** ChatGPT desktop, LM Studio (which is only partially open)
* **Edge:** Fully open desktop UX with local-first data storage, plus an optional OpenAI-compatible local server.

### [MLC LLM](https://github.com/mlc-ai/mlc-llm) ⭐ 23,134 | 🐛 339 | 🌐 Python | 📅 2026-08-17

`Python + C++` · `Apache-2.0` · 🟢 stable

Universal LLM deployment engine — native GPU acceleration on iOS, Android, desktop, and the browser.

* **Replaces:** Ollama (on mobile), cloud inference for on-device apps
* **Edge:** the only serious path to running an LLM on a phone's GPU. **Known weakness:** model support is limited to what's been compiled for the target, and when compilation or inference fails the errors are opaque.

### [WebLLM](https://github.com/mlc-ai/web-llm) ⭐ 18,976 | 🐛 149 | 🌐 TypeScript | 📅 2026-09-03

`TypeScript` · `Apache-2.0` · 🟢 stable

LLM inference entirely in the browser via WebGPU.

* **Edge:** no server, no API key, no data leaving the tab — which makes a whole class of privacy-sensitive apps possible. **Known weakness:** requires WebGPU, so Safari and Firefox support is the limiting factor, and out-of-memory device-lost errors are common on modest GPUs.

### [llamafile](https://github.com/Mozilla-Ocho/llamafile) ⭐ 25,875 | 🐛 213 | 🌐 C++ | 📅 2026-09-03

`C/C++` · `Apache-2.0` · 🟢 stable

Distribute an entire LLM as one executable file that runs on multiple OSes without installation.

* **Edge:** Unbeatable for shipping a model to a non-technical user. One file. Double-click. Done.

### [Rapid-MLX](https://github.com/raullenchai/Rapid-MLX) ⭐ 3,655 | 🐛 59 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟡 active

OpenAI-compatible inference server built specifically for Apple Silicon, on Apple's MLX framework.

* **Replaces:** Ollama / LM Studio (on a Mac)
* **Edge:** MLX-native quantization tuned for the unified-memory envelope, with grammar-constrained tool calling, reasoning separation, and vision — verified end-to-end against Claude Code, Cursor, Aider and Codex. `brew install rapid-mlx`, then `rapid-mlx serve <model>`.

***

## Inference Servers & Gateways

Serving models at scale.

### [vLLM](https://github.com/vllm-project/vllm) ⭐ 90,972 | 🐛 7,561 | 🌐 Python | 📅 2026-09-04

`Python + CUDA` · `Apache-2.0` · 🟢 stable

High-throughput, memory-efficient inference and serving engine — the de facto standard for self-hosted production LLM serving.

* **Replaces:** OpenAI API, Together AI
* **Edge:** PagedAttention plus continuous batching gives order-of-magnitude throughput gains over naive serving. Tensor/pipeline parallelism scales across GPUs; the OpenAI-compatible API means clients need no changes.

### [SGLang](https://github.com/sgl-project/sglang) ⭐ 35,448 | 🐛 5,177 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Fast serving framework with RadixAttention prefix caching and a structured generation language.

* **Edge:** Wins on workloads with heavy shared prefixes (agents, few-shot, multi-turn) where prefix-cache reuse dominates. Excellent constrained-decoding support.

### [LocalAI](https://github.com/mudler/LocalAI) ⭐ 48,862 | 🐛 211 | 🌐 Go | 📅 2026-09-04

`Go` · `MIT` · 🟢 stable

Drop-in replacement for the OpenAI API that runs locally across many backends and modalities — text, image, audio, embeddings.

* **Replaces:** OpenAI API, ElevenLabs API
* **Edge:** One server, many backends (llama.cpp, vLLM, transformers, whisper, diffusers). No GPU required. Point your existing OpenAI SDK at it and change nothing else.

### [Text Generation Inference](https://github.com/huggingface/text-generation-inference) ⚠️ Archived

`Rust + Python` · `Apache-2.0` · 🟢 stable

Hugging Face's production serving stack — the engine behind their inference endpoints.

* **Edge:** Battle-tested Rust web server, token streaming, and tight integration with the HF ecosystem.

### [Ray](https://github.com/ray-project/ray) ⭐ 43,700 | 🐛 3,566 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Distributed compute framework for scaling AI workloads — training, tuning, and multi-model serving via Ray Serve.

* **Edge:** For when one model on one box is no longer the problem. Model composition and autoscaling across a cluster.

### [Unified AI System](https://github.com/happy520ai/unified-ai-system) ⭐ 6 | 🐛 5 | 🌐 JavaScript | 📅 2026-09-04

`TypeScript + JavaScript` · `Apache-2.0` · `Self-hosted gateway + CLI` · 🟡 active

Terminal-first AI gateway that puts provider routing, governed agent and knowledge contracts, an HTTP API, and Codex MCP tools behind one self-hosted service.

* **Replaces:** ad hoc provider-specific proxy scripts when evaluating a local AI gateway control plane
* **Backends:** deterministic local fake provider by default; configurable adapters for NVIDIA and OpenAI-compatible upstream providers
* **Edge:** A fresh clone can prove the complete chat and MCP paths without credentials, while the CLI refuses to send when a real provider may be active unless the operator supplies `--allow-real-provider` for that command. Public-clone and container smoke checks keep the credential-free path under CI.

***

## Chat UIs & Frontends

### [Open WebUI](https://github.com/open-webui/open-webui) ⭐ 150,938 | 🐛 259 | 🌐 Python | 📅 2026-09-04

`Python + Svelte` · `BSD-3-Clause` (with branding clause) · 🟢 stable

Feature-rich, self-hosted AI interface — the default UI for Ollama and OpenAI-compatible backends.

* **Replaces:** ChatGPT Plus, Claude Pro
* **Edge:** Multi-user with RBAC, built-in RAG over uploaded documents, web search, image generation, voice, and a Python function/pipeline plugin system. Runs fully offline.

### [LibreChat](https://github.com/danny-avila/LibreChat) ⭐ 42,820 | 🐛 732 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · 🟢 stable

Every AI provider in one polished ChatGPT-style interface.

* **Replaces:** ChatGPT Plus, Poe
* **Edge:** Multi-provider in a single conversation, agents, code interpreter, artifacts, MCP support, and genuinely good multi-user auth. MIT with no branding restrictions.

### [Lobe Chat](https://github.com/lobehub/lobe-chat) ⭐ 82,240 | 🐛 879 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Apache-2.0` (with conditions) · 🟢 stable

Modern chat framework with a plugin and agent-market ecosystem.

* **Edge:** The best-looking option, with PWA and mobile support plus one-click Vercel deploy.

### [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) ⭐ 65,617 | 🐛 330 | 🌐 JavaScript | 📅 2026-09-04

`JavaScript` · `MIT` · 🟢 stable

All-in-one desktop and Docker app: chat with your documents, with agents and multi-user workspaces built in.

* **Edge:** Batteries-included RAG — embedder, vector DB, and UI ship together. Fastest path from "I have PDFs" to "I can ask them questions."

### [ThoughtDAG](https://github.com/chenxiachan/thoughtdag) ⭐ 342 | 🐛 4 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · Web · 🟠 experimental

A local-first visual LLM workspace where graph edges define what context the model receives.

* **Replaces:** linear chat interfaces for long-running LLM research
* **Backends:** Ollama and OpenAI-compatible endpoints
* **Edge:** Graph edges are execution semantics, not decoration: traversing a node's upstream DAG constructs the message history for the next request, so users can branch, merge, and prune context explicitly.

### [Persona](https://github.com/jayamitkatariya/personacli) ⭐ 19 | 🐛 1 | 🌐 TypeScript | 📅 2026-08-28

`TypeScript` · `MIT` · 🟡 active

Local-first workspace combining notes, tasks, and AI chat in your browser on your machine.

* **Replaces:** Notion AI, Obsidian + Copilot plugin
* **Edge:** Plain markdown files on disk — no accounts, no cloud, no database. The AI reads and edits your actual workspace files. Supports Ollama for fully local inference.

***

## Vector Databases

### [Qdrant](https://github.com/qdrant/qdrant) ⭐ 34,387 | 🐛 698 | 🌐 Rust | 📅 2026-09-04

`Rust` · `Apache-2.0` · 🟢 stable

Vector search engine with rich payload filtering, built for production.

* **Replaces:** Pinecone
* **Edge:** Written in Rust — predictable latency under load. Scalar/product/binary quantization cuts RAM dramatically. Filtered search stays accurate instead of degrading like naive pre/post-filtering.

### [Milvus](https://github.com/milvus-io/milvus) ⭐ 45,973 | 🐛 1,335 | 🌐 Go | 📅 2026-09-04

`Go + C++` · `Apache-2.0` · 🟢 stable

Distributed vector database built for billion-scale workloads.

* **Edge:** Separated storage and compute, GPU indexing — the heaviest-duty option when the corpus genuinely is enormous. Milvus Lite covers local dev.

### [Weaviate](https://github.com/weaviate/weaviate) ⭐ 16,785 | 🐛 710 | 🌐 Go | 📅 2026-09-04

`Go` · `BSD-3-Clause` · 🟢 stable

Vector database with built-in vectorization modules and a GraphQL API.

* **Edge:** Module system embeds data for you at ingest. Native hybrid (BM25 + vector) search and multi-tenancy.

### [Chroma](https://github.com/chroma-core/chroma) ⭐ 29,225 | 🐛 826 | 🌐 Rust | 📅 2026-09-03

`Rust + Python` · `Apache-2.0` · 🟢 stable

The batteries-included embedding database for AI applications.

* **Edge:** `pip install chromadb` and you have a working vector store in four lines. The right default for prototypes; scale out later if you must.

### [pgvector](https://github.com/pgvector/pgvector) ⭐ 22,909 | 🐛 14 | 🌐 C | 📅 2026-08-20

`C` · `PostgreSQL License` · 🟢 stable

Vector similarity search inside PostgreSQL.

* **Edge:** No new infrastructure. Your embeddings live next to your relational data with real transactions, joins, and backups. Start here unless you've measured a reason not to.

### [MongrelDB](https://github.com/visorcraft/MongrelDB) ⭐ 6 | 🐛 0 | 🌐 Rust | 📅 2026-09-02

`Rust` · `MIT OR Apache-2.0` · Embedded + server · 🟠 experimental

Columnar database with AI-native retrieval — dense ANN, sparse vectors, full-text, and metadata filters in one transactional engine.

* **Edge:** Not a pure vector store — dense ANN, sparse, and full-text indexes share one transactional row store, so hybrid search with RRF fusion runs without a separate vector service, keeping SQL, encryption-at-rest, and multi-user access. Companion [MongrelDB Viewer](https://github.com/visorcraft/MongrelDB-Viewer) ⭐ 3 | 🐛 0 | 🌐 Rust | 📅 2026-08-11 for schema, SQL, and ANN exploration.
* **Replaces:** Pinecone + a separate operational DB for RAG/agent memory

***

## Embeddings & Rerankers

The retrieval quality layer. Swapping your embedding model usually beats swapping your vector database.

### [FlagEmbedding / BGE](https://github.com/FlagOpen/FlagEmbedding) ⭐ 12,129 | 🐛 908 | 🌐 Python | 📅 2026-08-24

`Python` · `MIT` · 🟢 stable

The BGE family — BGE-M3 embeddings and the BGE reranker models.

* **Replaces:** OpenAI text-embedding-3, Cohere Embed, Cohere Rerank
* **Edge:** BGE-M3 does dense, sparse (lexical), and multi-vector retrieval from one model across 100+ languages, so you get hybrid search without running two systems. Pairing BGE-M3 with a BGE reranker is the default open retrieval stack, and it runs on your own hardware with no per-query cost.

### [Sentence Transformers](https://github.com/UKPLab/sentence-transformers) ⭐ 19,070 | 🐛 1,289 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

The library for computing, training, and fine-tuning text embeddings.

* **Edge:** the interface almost every open embedding model ships against — learn it once and every model on Hugging Face is available. Fine-tuning an embedding model on your own domain is usually the single highest-leverage RAG improvement, and this is how you do it.

***

## RAG Frameworks

### [LlamaIndex](https://github.com/run-llama/llama_index) ⭐ 52,021 | 🐛 704 | 🌐 Python | 📅 2026-09-03

`Python + TypeScript` · `MIT` · 🟢 stable

The data framework for LLM applications — ingestion, indexing, retrieval, and agentic workflows over your data.

* **Edge:** Hundreds of data connectors (LlamaHub) and the deepest library of retrieval strategies — hierarchical, recursive, hybrid, auto-merging. When naive top-k retrieval isn't good enough, the fix is usually already implemented here.

### [RAGFlow](https://github.com/infiniflow/ragflow) ⭐ 90,053 | 🐛 1,589 | 🌐 Go | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

RAG engine built on deep document understanding — layout-aware parsing of PDFs, tables, and scans.

* **Edge:** Document parsing is where most RAG systems actually fail. RAGFlow treats it as the core problem and shows you citation-grounded chunks so you can debug retrieval visually.

### [Dify](https://github.com/langgenius/dify) ⭐ 154,451 | 🐛 1,019 | 🌐 TypeScript | 📅 2026-09-04

`Python + TypeScript` · `Apache-2.0` (with conditions) · 🟢 stable

Production-ready platform for agentic workflows — visual builder, RAG pipeline, model management, and observability in one.

* **Replaces:** OpenAI GPTs platform, Vertex AI Agent Builder
* **Edge:** Non-engineers can build and ship an internal AI tool without touching code, while engineers keep API access to everything. Self-hosted, so your data stays put.

### [Docling](https://github.com/docling-project/docling) ⭐ 66,004 | 🐛 887 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

Parse PDF, DOCX, PPTX, HTML, and images into structured, LLM-ready formats.

* **Edge:** Layout and table-structure models that handle real-world documents. Plugs directly into LlamaIndex and LangChain.

### [Unstructured](https://github.com/Unstructured-IO/unstructured) ⭐ 15,389 | 🐛 303 | 🌐 HTML | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Preprocessing library for ingesting unstructured documents into ML pipelines.

* **Edge:** Broadest format coverage. The workhorse behind many production ingestion pipelines.

***

## Fine-Tuning & Training

### [Unsloth](https://github.com/unslothai/unsloth) ⭐ 75,615 | 🐛 1,408 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Fine-tune LLMs roughly 2x faster with far less VRAM, without accuracy loss.

* **Edge:** Hand-written Triton kernels and a manual backprop engine. Makes fine-tuning a mid-size model on a single free Colab GPU realistic instead of aspirational.

### [Axolotl](https://github.com/axolotl-ai-cloud/axolotl) ⭐ 12,440 | 🐛 248 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Post-training framework configured entirely through YAML — full fine-tune, LoRA, QLoRA, DPO, ORPO, and more.

* **Edge:** One config file describes the entire run, which makes experiments reproducible and diffable in git.

### [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) ⭐ 74,576 | 🐛 1,140 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Unified fine-tuning for 100+ models, with a web UI.

* **Edge:** Zero-code training via LlamaBoard. The widest model coverage of any tuning toolkit.

### [PEFT](https://github.com/huggingface/peft) ⭐ 21,636 | 🐛 81 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Hugging Face's parameter-efficient fine-tuning library — LoRA, QLoRA, adapters, prompt tuning.

* **Edge:** The reference implementation everything else builds on. Integrates directly with Transformers, Accelerate, and TRL.

### [Distilabel](https://github.com/argilla-io/distilabel) ⭐ 3,385 | 🐛 105 | 🌐 Python | 📅 2026-08-31

`Python` · `Apache-2.0` · 🟢 stable

Synthetic data pipelines for SFT and preference tuning, from the Argilla team.

* **Edge:** treats dataset generation as a reproducible pipeline rather than a pile of one-off scripts, and loops through Argilla so a human can curate what the model generated. The bottleneck in fine-tuning is almost always data, not compute.

### [TRL](https://github.com/huggingface/trl) ⭐ 19,223 | 🐛 332 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Train transformer models with reinforcement learning — SFT, DPO, GRPO, reward modeling.

* **Edge:** The standard path from a base model to an aligned, instruction-following one.

***

## Evals, Testing & Guardrails

### [promptfoo](https://github.com/promptfoo/promptfoo) ⭐ 24,820 | 🐛 573 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` · 🟢 stable

Test and evaluate prompts, agents, and RAG systems — plus LLM red teaming and vulnerability scanning.

* **Edge:** Declarative test cases in YAML that run in CI. Side-by-side model comparison plus adversarial red-teaming in one tool. Local-first — your prompts never leave your machine.

### [agent-qa](https://github.com/vostride/agent-qa) ⭐ 901 | 🐛 0 | 🌐 TypeScript | 📅 2026-08-03

`TypeScript` · `FSL-1.1-ALv2` (fair-code; converts to `Apache-2.0`) · CLI, dashboard, MCP · 🟠 experimental

The self-improving QA agent for software teams, with natural-language web and mobile tests that adapt when user interfaces change.

* **Backends:** OpenAI- and Anthropic-compatible endpoints, Gemini, and local models
* **Edge:** Stores product, suite, test, and healed-step observations as versioned execution memory, then reuses that context on later runs. Ships a dashboard, CLI, MCP server, and three agent skills in one repository.

### [ClawBench](https://github.com/reacher-z/ClawBench) ⭐ 645 | 🐛 59 | 🌐 Python | 📅 2026-09-01

`Python` · `Apache-2.0` · Docker/browser harness · 🟡 active

Evaluate web agents on 153 everyday tasks across 144 live websites, with the final submission request intercepted to keep runs side-effect-free.

* **Edge:** Captures session replay, screenshots, HTTP traffic, browser actions, and agent messages in one reproducible run, making failures diagnosable beyond a final pass/fail score.

### [DeepEval](https://github.com/confident-ai/deepeval) ⭐ 18,107 | 🐛 562 | 🌐 Python | 📅 2026-09-03

`Python` · `Apache-2.0` · 🟢 stable

"Pytest for LLMs" — unit-test LLM outputs with research-backed metrics.

* **Edge:** Feels like a normal test suite. G-Eval, faithfulness, answer relevancy, hallucination, and RAG-specific metrics run locally on the model of your choice.

### [Ragas](https://github.com/explodinggradients/ragas) ⭐ 15,620 | 🐛 592 | 🌐 Python | 📅 2026-02-24

`Python` · `Apache-2.0` · 🟢 stable

Evaluation toolkit for RAG pipelines.

* **Edge:** Splits retrieval quality from generation quality, so you know which half to fix. Can synthesize a test set from your own documents.

### [Guardrails](https://github.com/guardrails-ai/guardrails) ⭐ 7,354 | 🐛 83 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Add input/output validators to LLM applications — structure, safety, PII, and custom rules.

* **Edge:** Validators are composable and re-ask the model on failure rather than just erroring out.

### [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) ⭐ 7,063 | 🐛 215 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

Programmable rails for conversational systems, defined in the Colang modeling language.

* **Edge:** Dialogue-level control — keep a bot on topic, block jailbreaks, enforce a conversation flow.

### [Garak](https://github.com/NVIDIA/garak) ⭐ 9,109 | 🐛 411 | 🌐 Python | 📅 2026-09-04

`Python` · `Apache-2.0` · 🟢 stable

LLM vulnerability scanner — probes for prompt injection, jailbreaks, data leakage, and toxicity.

* **Edge:** `nmap` for language models. Run it before you ship, not after the incident.

***

## Observability & LLMOps

### [Langfuse](https://github.com/langfuse/langfuse) ⭐ 34,203 | 🐛 897 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `MIT` (core) · 🟢 stable

Open-source LLM engineering platform — tracing, evals, prompt management, and cost tracking.

* **Replaces:** LangSmith
* **Edge:** MIT-licensed core that you can genuinely self-host. Framework-agnostic via OpenTelemetry. Nested traces make multi-agent debugging tractable, and prompt versioning decouples prompt changes from deploys.

### [Phoenix](https://github.com/Arize-ai/phoenix) ⭐ 11,328 | 🐛 968 | 🌐 Python | 📅 2026-09-04

`Python + TypeScript` · `Elastic-2.0` · 🟢 stable

AI observability and evaluation, built on OpenTelemetry and OpenInference.

* **Edge:** Runs in a notebook for local debugging or as a server for production. Strong embedding-drift and retrieval-quality visualizations.

### [OpenLLMetry](https://github.com/traceloop/openllmetry) ⭐ 7,413 | 🐛 671 | 🌐 Python | 📅 2026-08-10

`Python + TypeScript` · `Apache-2.0` · 🟢 stable

OpenTelemetry instrumentation for LLM applications.

* **Edge:** Standards-based — ship traces to Datadog, Honeycomb, Grafana, or whatever you already run. No new observability vendor.

### [Helicone](https://github.com/Helicone/helicone) ⭐ 6,132 | 🐛 159 | 🌐 TypeScript | 📅 2026-08-31

`TypeScript` · `Apache-2.0` · 🟢 stable

Observability platform for LLM apps — one-line proxy integration, caching, and rate limiting.

* **Edge:** Change your base URL and you have logging. Lowest-friction start of any tool in this section.

### [Mydentify AI Model Cost Calculator](https://github.com/mitdralla/mydentify-ai-model-cost-calculator) ⭐ 0 | 🐛 0 | 🌐 JavaScript | 📅 2026-08-12

`JavaScript` · `MIT` · Browser app · 🟠 experimental

Dependency-free browser calculator for estimating AI model API costs from request volume, input and output tokens, cached input, and fixed per-request charges.

* **Edge:** Runs locally without API keys, accounts, cookies, analytics, or server-side processing. The tested formula separates cached from uncached input and keeps provider-specific pricing assumptions visible so estimates can be reviewed before a real bill is incurred.

***

## Speech, Vision & Multimodal

### [Whisper](https://github.com/openai/whisper) ⭐ 108,426 | 🐛 142 | 🌐 Python | 📅 2026-08-31 / [faster-whisper](https://github.com/SYSTRAN/faster-whisper) ⭐ 25,234 | 🐛 320 | 🌐 Python | 📅 2025-11-19 / [whisper.cpp](https://github.com/ggml-org/whisper.cpp) ⭐ 53,440 | 🐛 1,242 | 🌐 C++ | 📅 2026-09-04

`MIT` · 🟢 stable

Speech-to-text: the original model, the CTranslate2 port (substantially faster), and the C++ port (runs anywhere).

* **Replaces:** Google Speech-to-Text, AssemblyAI
* **Edge:** State-of-the-art multilingual ASR for free, on your own hardware. `whisper.cpp` runs real-time transcription on a laptop CPU.

### [WhisperX](https://github.com/m-bain/whisperX) ⭐ 23,895 | 🐛 218 | 🌐 Python | 📅 2026-08-30

`Python` · `BSD-2-Clause` · 🟢 stable

Whisper plus word-level timestamps and speaker diarization.

* **Edge:** If you need to know *who* said *what, when* — subtitles, meeting notes — this is the one.

### [Kokoro](https://github.com/hexgrad/kokoro) ⭐ 8,684 | 🐛 208 | 🌐 JavaScript | 📅 2025-08-06 / [Piper](https://github.com/OHF-Voice/piper1-gpl) ⭐ 5,452 | 🐛 124 | 🌐 C++ | 📅 2026-09-04

`Apache-2.0` / `GPL-3.0` · 🟢 stable

Text-to-speech. Kokoro is a tiny (\~82M parameter) model with quality far above its weight class; Piper is optimized for devices as small as a Raspberry Pi.

* **Replaces:** ElevenLabs
* **Edge:** Real-time TTS on CPU. Kokoro's small footprint makes it viable to bundle inside an app.

### [Pipecat](https://github.com/pipecat-ai/pipecat) ⭐ 15,220 | 🐛 297 | 🌐 Python | 📅 2026-09-04

`Python` · Library · 🟢 stable

Framework for real-time voice and multimodal conversational agents.

* **Replaces:** Vapi, Retell
* **Edge:** pluggable STT/TTS/LLM stages over WebRTC, plus speech-to-speech model support, so you can assemble a voice agent from open parts instead of renting a platform. **Known weakness:** maintainers' own issue tracker documents pipeline freezes, zombie function-call handlers after timeout, and multi-second latency in production. The linear pipeline model also fits multi-party conversation badly. Expect real engineering effort.

### [LiveKit Agents](https://github.com/livekit/agents) ⭐ 14,014 | 🐛 776 | 🌐 Python | 📅 2026-09-04

`Python + Node` · `Apache-2.0` · Framework · 🟢 stable

Realtime agent framework built on LiveKit's WebRTC infrastructure.

* **Replaces:** Vapi, Retell
* **Edge:** the room/participant model handles multi-party and interruption natively, where a linear pipeline has to fake it. If your voice agent needs more than one human in the call, start here rather than with a pipeline framework.

### [ComfyUI](https://github.com/comfyanonymous/ComfyUI) ⭐ 131,504 | 🐛 4,808 | 🌐 Python | 📅 2026-09-04

`Python` · `GPL-3.0` · 🟢 stable

Node-based interface for diffusion models — image, video, and audio generation pipelines.

* **Replaces:** Midjourney, DALL·E
* **Edge:** The graph *is* the program — every step is inspectable and reproducible, and workflows are shareable as JSON. Supports essentially every open image/video model within days of release.

### [Surya](https://github.com/datalab-to/surya) ⭐ 21,349 | 🐛 195 | 🌐 Python | 📅 2026-08-21

`Python` · `GPL-3.0` (commercial exceptions) · 🟡 active

Document OCR, layout analysis, and reading-order detection in 90+ languages.

* **Edge:** Layout, reading order, and table structure — not just raw character recognition. Essential upstream of any document RAG.

***

## Low-Code / Visual Builders

### [n8n](https://github.com/n8n-io/n8n) ⭐ 203,337 | 🐛 1,155 | 🌐 TypeScript | 📅 2026-09-04

`TypeScript` · `Sustainable Use License` (fair-code, source-available) · 🟢 stable

Workflow automation with native AI agent nodes — hundreds of integrations, self-hostable.

* **Replaces:** Zapier, Make
* **Edge:** Drop to JavaScript in any node when the visual builder runs out. AI agent nodes make it a legitimate agent runtime, not just a trigger-action tool. **Note:** fair-code, not OSI-approved — read the license before commercial use.

### [Flowise](https://github.com/FlowiseAI/Flowise) ⚠️ Archived

`TypeScript` · `Apache-2.0` (with conditions) · 🟢 stable

Drag-and-drop builder for LLM flows and agents.

* **Edge:** Fastest way to prototype a RAG chatbot visually and expose it as an API or embeddable widget.

### [Langflow](https://github.com/langflow-ai/langflow) ⭐ 154,247 | 🐛 1,032 | 🌐 Python | 📅 2026-09-04

`Python` · `MIT` · 🟢 stable

Visual framework for building multi-agent and RAG applications.

* **Edge:** Every visual component maps to real Python you can export and own. A good bridge between prototype and production code.

***

## Open-Source Alternatives Cheat Sheet

| You're paying for                   | Use instead                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| GitHub Copilot                      | [Continue](https://github.com/continuedev/continue) ⭐ 35,760 \| 🐛 938 \| 🌐 TypeScript \| 📅 2026-09-04, [Tabby](https://github.com/TabbyML/tabby) ⭐ 33,859 \| 🐛 336 \| 🌐 Rust \| 📅 2026-06-30, [aider](https://github.com/Aider-AI/aider) ⭐ 48,738 \| 🐛 1,853 \| 🌐 Python \| 📅 2026-05-22                                                                                                                                                                                                                        |
| Cursor / Windsurf                   | [Cline](https://github.com/cline/cline) ⭐ 67,477 \| 🐛 1,213 \| 🌐 TypeScript \| 📅 2026-09-04, [OpenCode](https://github.com/sst/opencode) ⭐ 203,964 \| 🐛 5,708 \| 🌐 TypeScript \| 📅 2026-09-04, [Continue](https://github.com/continuedev/continue) ⭐ 35,760 \| 🐛 938 \| 🌐 TypeScript \| 📅 2026-09-04, [BitFun](https://github.com/GCWing/BitFun) ⭐ 2,047 \| 🐛 154 \| 🌐 Rust \| 📅 2026-09-04, [Atomic Agent](https://github.com/AtomicBot-ai/atomic-agent) ⭐ 2,490 \| 🐛 25 \| 🌐 TypeScript \| 📅 2026-09-04 |
| Devin                               | [OpenHands](https://github.com/All-Hands-AI/OpenHands) ⭐ 86,172 \| 🐛 648 \| 🌐 TypeScript \| 📅 2026-09-04, [Goose](https://github.com/block/goose) ⭐ 53,910 \| 🐛 296 \| 🌐 Rust \| 📅 2026-09-04, [SWE-agent](https://github.com/SWE-agent/SWE-agent) ⭐ 20,219 \| 🐛 92 \| 🌐 Python \| 📅 2026-08-31                                                                                                                                                                                                                 |
| Claude Design / Figma Make          | [Open Design](https://github.com/nexu-io/open-design) ⭐ 94,060 \| 🐛 938 \| 🌐 TypeScript \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                                                                                                               |
| ChatGPT desktop / Copilot assistant | [OpenClaw](https://github.com/openclaw/openclaw) ⭐ 388,845 \| 🐛 6,323 \| 🌐 TypeScript \| 📅 2026-09-04, [Hermes Agent](https://github.com/NousResearch/hermes-agent) ⭐ 241,377 \| 🐛 39,567 \| 🌐 Python \| 📅 2026-09-04                                                                                                                                                                                                                                                                                              |
| Bolt.new / v0 / Lovable             | [bolt.diy](https://github.com/stackblitz-labs/bolt.diy) ⭐ 19,845 \| 🐛 136 \| 🌐 TypeScript \| 📅 2026-02-07, [OpenUI](https://github.com/wandb/openui) ⭐ 22,537 \| 🐛 88 \| 🌐 TypeScript \| 📅 2026-08-27, [Dyad](https://github.com/dyad-sh/dyad) ⭐ 21,384 \| 🐛 301 \| 🌐 TypeScript \| 📅 2026-09-04                                                                                                                                                                                                                |
| ChatGPT Plus / Claude Pro           | [Open WebUI](https://github.com/open-webui/open-webui) ⭐ 150,938 \| 🐛 259 \| 🌐 Python \| 📅 2026-09-04, [LibreChat](https://github.com/danny-avila/LibreChat) ⭐ 42,820 \| 🐛 732 \| 🌐 TypeScript \| 📅 2026-09-04, [Jan](https://github.com/menloresearch/jan) ⭐ 44,335 \| 🐛 509 \| 🌐 TypeScript \| 📅 2026-09-04                                                                                                                                                                                                   |
| OpenAI API (inference)              | [vLLM](https://github.com/vllm-project/vllm) ⭐ 90,972 \| 🐛 7,561 \| 🌐 Python \| 📅 2026-09-04, [Ollama](https://github.com/ollama/ollama) ⭐ 180,142 \| 🐛 3,899 \| 🌐 Go \| 📅 2026-09-04, [LocalAI](https://github.com/mudler/LocalAI) ⭐ 48,862 \| 🐛 211 \| 🌐 Go \| 📅 2026-09-04, [SGLang](https://github.com/sgl-project/sglang) ⭐ 35,448 \| 🐛 5,177 \| 🌐 Python \| 📅 2026-09-04                                                                                                                               |
| OpenAI Assistants API               | [Letta](https://github.com/letta-ai/letta) ⭐ 24,621 \| 🐛 39 \| 📅 2026-08-23, [Dify](https://github.com/langgenius/dify) ⭐ 154,451 \| 🐛 1,019 \| 🌐 TypeScript \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                                        |
| Pinecone                            | [Qdrant](https://github.com/qdrant/qdrant) ⭐ 34,387 \| 🐛 698 \| 🌐 Rust \| 📅 2026-09-04, [pgvector](https://github.com/pgvector/pgvector) ⭐ 22,909 \| 🐛 14 \| 🌐 C \| 📅 2026-08-20, [Chroma](https://github.com/chroma-core/chroma) ⭐ 29,225 \| 🐛 826 \| 🌐 Rust \| 📅 2026-09-03, [MongrelDB](https://github.com/visorcraft/MongrelDB) ⭐ 6 \| 🐛 0 \| 🌐 Rust \| 📅 2026-09-02                                                                                                                                     |
| LangSmith                           | [Langfuse](https://github.com/langfuse/langfuse) ⭐ 34,203 \| 🐛 897 \| 🌐 TypeScript \| 📅 2026-09-04, [Phoenix](https://github.com/Arize-ai/phoenix) ⭐ 11,328 \| 🐛 968 \| 🌐 Python \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                   |
| OpenRouter                          | [LiteLLM](https://github.com/BerriAI/litellm) ⭐ 58,043 \| 🐛 4,932 \| 🌐 Python \| 📅 2026-09-04 proxy                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ElevenLabs                          | [Kokoro](https://github.com/hexgrad/kokoro) ⭐ 8,684 \| 🐛 208 \| 🌐 JavaScript \| 📅 2025-08-06, [Piper](https://github.com/OHF-Voice/piper1-gpl) ⭐ 5,452 \| 🐛 124 \| 🌐 C++ \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                           |
| AssemblyAI / Deepgram               | [faster-whisper](https://github.com/SYSTRAN/faster-whisper) ⭐ 25,234 \| 🐛 320 \| 🌐 Python \| 📅 2025-11-19, [WhisperX](https://github.com/m-bain/whisperX) ⭐ 23,895 \| 🐛 218 \| 🌐 Python \| 📅 2026-08-30                                                                                                                                                                                                                                                                                                            |
| Midjourney / DALL·E                 | [ComfyUI](https://github.com/comfyanonymous/ComfyUI) ⭐ 131,504 \| 🐛 4,808 \| 🌐 Python \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Zapier / Make                       | [n8n](https://github.com/n8n-io/n8n) ⭐ 203,337 \| 🐛 1,155 \| 🌐 TypeScript \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Vapi / Retell                       | [LiveKit Agents](https://github.com/livekit/agents) ⭐ 14,014 \| 🐛 776 \| 🌐 Python \| 📅 2026-09-04, [Pipecat](https://github.com/pipecat-ai/pipecat) ⭐ 15,220 \| 🐛 297 \| 🌐 Python \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                                  |
| Cohere Embed / Rerank               | [FlagEmbedding / BGE](https://github.com/FlagOpen/FlagEmbedding) ⭐ 12,129 \| 🐛 908 \| 🌐 Python \| 📅 2026-08-24                                                                                                                                                                                                                                                                                                                                                                                                        |
| Browserbase / Stagehand             | [browser-use](https://github.com/browser-use/browser-use) ⭐ 112,274 \| 🐛 395 \| 🌐 Python \| 📅 2026-09-04, [Skyvern](https://github.com/Skyvern-AI/skyvern) ⭐ 22,930 \| 🐛 219 \| 🌐 Python \| 📅 2026-09-04                                                                                                                                                                                                                                                                                                           |
| OpenAI GPTs platform                | [Dify](https://github.com/langgenius/dify) ⭐ 154,451 \| 🐛 1,019 \| 🌐 TypeScript \| 📅 2026-09-04, [Flowise](https://github.com/FlowiseAI/Flowise) ⚠️ Archived                                                                                                                                                                                                                                                                                                                                                          |

***

## Choosing Your Stack

Start small. Every layer below is optional until it isn't.

**Solo developer, local-first, zero API cost**

```
Ollama → Continue (editor) + aider (terminal) → Open WebUI (chat)
```

**Small team shipping an AI product**

```
LiteLLM proxy → LangGraph or CrewAI → pgvector → Langfuse → promptfoo in CI
```

**Enterprise, self-hosted, compliance-bound**

```
vLLM (own GPUs) → LiteLLM (keys/budgets) → Qdrant → Dify or LangGraph
  → Langfuse (tracing) → Garak + NeMo Guardrails (safety)
```

**Document-heavy RAG**

```
Docling or RAGFlow (parsing) → LlamaIndex (retrieval) → Qdrant → Ragas (eval)
```

Three rules that save the most time:

1. **Put a gateway in front of your models from day one.** LiteLLM costs an afternoon and buys you provider switching, budgets, and fallbacks forever.
2. **Use Postgres + pgvector until you have measured a reason not to.** Most "we need a vector database" problems are actually retrieval-quality problems.
3. **Add tracing before you add features.** Debugging an untraced multi-agent system is guesswork.

***

## Contributing

PRs welcome. See [CONTRIBUTING.md](docs/community/contributing.md).

The bar for inclusion:

* OSI-approved license (source-available tools are allowed but must be labeled)
* Meaningfully maintained — commits within the last 6 months
* Solves a problem a developer actually has
* The entry explains *why you'd choose it*, not just what it does

## Contributors

<a href="https://github.com/Sami-Uysal/awesome-open-ai-developer-tools/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Sami-Uysal/awesome-open-ai-developer-tools" />
</a>

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, contributors have waived all copyright and related rights to this work.

***

> _Enhansomed by [enhansome](https://github.com/enhansome) on 2026-09-04._
