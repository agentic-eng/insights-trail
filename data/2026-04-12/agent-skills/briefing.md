# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-12
**Query type:** GENERAL
**Sources:** X/Twitter, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 24 posts | 566 likes, 105 reposts, 64 replies | Top voices: @Dharmikpawar31, @AISecHub, @GHCopilotCLILog |
| Web | 29 pages | — | Script (8) + WebSearch supplements (21) |

---

## Synthesized Findings

### 1. Claude Code's Extension Model Is Crystallizing — and the Community Is Documenting It

The most-engaged content this cycle (203 likes, 47 reposts) is @Dharmikpawar31's "definitive Claude Code structure" thread, with a near-identical post from @dkare1009 (34 likes, 7 reposts). Both lay out the canonical directory layout practitioners are converging on:

- `CLAUDE.md` — project memory layer
- `.claude/` — the full extensions hub
  - `commands/` — reusable slash commands as `.md` files
  - `skills/` — auto-triggered workflows via `SKILL.md`
  - `agents/` — sub-agent definitions (`.yml`)
  - `plugins/` — packaged, shareable setups
  - `.mcp.json` — external tool (MCP server) connections

The conceptual split per Morph's 2026 guide: a **skill** is a cheat sheet (tells Claude *how* to behave), a **plugin** is a toolkit (packages skills + supporting files for sharing), and an **MCP server** is a bridge (running service giving Claude access to external tools like GitHub, Figma, databases).

Anthropic's official docs at `code.claude.com/docs/en/skills` and `code.claude.com/docs/en/plugins` formalize this. The `anthropics/skills` GitHub repo serves as the open standard reference (per WebSearch: OpenAI adopted the same format for Codex CLI and ChatGPT in December 2025).

Sources: X (@Dharmikpawar31, @dkare1009), Web (Morph, Anthropic Docs, DEV Community)

---

### 2. MCP Server Ecosystem: From Chaos to Governed Registry Infrastructure

The "Claude mcp/plugin ecosystem grew fast. Here's what's worth your time today" thread by @8020principal captures the current commonly-connected MCP server stack: Slack (channels, threads, messages), GitHub (repos, PRs, issues, CI/CD), Google Workspace (Calendar, Drive, Gmail), Brave Search (live web results), PostgreSQL/SQLite (natural-language SQL), and Memory Bank (persistent context).

But the bigger infrastructure story is enterprise governance:

- **Official MCP Registry** (`registry.modelcontextprotocol.io`) — Anthropic's canonical registry for MCP servers
- **Smithery** — closest equivalent to Docker Hub, 7,000+ servers, local CLI install or hosted remote
- **MCPMarket.com** — 10,000+ servers across 23+ categories
- **Kong MCP Registry** — single source of truth for enterprise tool access, governed by existing API security/identity infrastructure
- **AWS Agent Registry** (AgentCore, now in preview) — private, governed catalog for agents, tools, skills, MCP servers within an org
- **aregistry.ai** — centralized, curated registry for AI artifacts, launched ~April 2026
- **agentic-community/mcp-gateway-registry** (GitHub) — enterprise-ready MCP Gateway with OAuth, dynamic tool discovery, Keycloak/Entra integration

The friction point is clear: blog.icme.io calls MCP tool discovery "fundamentally broken" — *"Semantic search can't tell a good tool from a good description. Similarity is not satisfiability. Tool descriptions are ads, not specs. You need to be in every room where an agent might look for you."* TrueFoundry's registry comparison notes 8,600+ servers across all public registries — with no single front door.

Sources: X (@8020principal), Web (Stacklok, TrueFoundry, Kong, AWS, blog.icme.io, aregistry.ai)

---

### 3. Agent Skill Marketplaces Are Exploding — With Creator Economy Models

The agent skill marketplace space has fragmented into multiple large catalogs, each with different positioning:

| Marketplace | Scale | Differentiation |
|-------------|-------|-----------------|
| **LobeHub Skills** | 169,739 skills | Fastest-growing |
| **agentskill.sh** | 110,000+ skills | Cross-tool (Claude Code, Cursor, Copilot, Windsurf, 20+ tools) |
| **skills.sh** (Vercel) | 87,000+ skills | High-visibility hub, discovery + installation |
| **ClawHub** | 20,000+ skills | Detail-rich per-listing |
| **claudemarketplaces.com** | 150+ (curated) | Ratings + install counts |
| **SkillsMP** | Active | Claude, Codex & ChatGPT focus |
| **anthropics/skills** (GitHub) | Reference | Official open standard |

On the community-built GitHub side: `jeremylongshore/claude-code-plugins-plus-skills` packages 340 plugins + 1367 agent skills with its own **CCPI package manager** (`pnpm add -g @intentsolutionsio/ccpi`), supporting `ccpi search`, `ccpi install`, and `ccpi list`. `alirezarezvani/claude-skills` covers 232+ skills across Claude Code, Codex, Gemini CLI, and Cursor.

The creator economy angle is real: @AIAmbientPixels is building **Pixel Agents**, an AI agent marketplace where *"creators earn on every run"* (pay-per-run, 24 agents currently). @iamdavidoti is shipping BoostGPT with agent marketplace, pluggable interfaces, SSO, and workspace scoping. @web3wiztron describes skill marketplaces as *"essentially a Plug-and-Play architecture"* for modular agent logic.

Sources: X (@AIAmbientPixels, @web3wiztron, @iamdavidoti), Web (KDnuggets, skills.sh, SkillsMP, ClawHub, DEV Community)

---

### 4. ToolHive Adds Agent Skills to MCP Server Registry — A New Unified Primitive

The highest-signal infrastructure announcement this cycle: **Stacklok's ToolHive** added agent skills support on April 6, 2026. The distinction they draw: *"MCP servers give agents the raw tools they can call; skills give them the knowledge of when, why, and how to use those tools effectively."*

The implementation: skills are published to ToolHive's Registry Server (or any OCI registry / Git repo), installed via CLI, and automatically written to the AI client's skills directory. Namespaced with reverse-DNS notation for versioning and isolation. The Registry Server's new extensions API handles skill lifecycle alongside server entries.

GitHub Copilot CLI is making the same move: its March 28 weekly recap (@GHCopilotCLILog, 115 likes, 12 reposts) called out adding `~/.agents/skills/` as a **personal skill discovery directory**, "aligned with VS Code," and adding organization policy enforcement for third-party MCP servers. VS Code 1.110 (released March 4 per @_kkoga) added an Agent Debug panel that shows loaded prompts/skills/hooks in real time.

A parallel early-stage project: `orthogonalhq/apm` (GitHub) — "APM is the Agent Package Manager," a registry and management tool for Skills, Workflows, and Agent Apps. TypeScript + Rust, MIT license.

Sources: X (@GHCopilotCLILog, @_kkoga), Web (Stacklok Docs, GitHub/orthogonalhq)

---

### 5. Security: MCP/Plugin Ecosystem Introduces New Endpoint Risk

@AISecHub's **claudit-sec** announcement went viral (188 likes, 39 reposts) — a single-command security audit tool for Claude Desktop and Claude Code on macOS that gives visibility into MCP servers, extensions, plugins, connectors, scheduled tasks, and permissions.

The risk model it articulates: *"Claude Desktop introduces a new class of endpoint risk: AI agents with autonomous execution, persistent scheduled tasks, MCP server integrations, browser-control extensions, and OAuth-authenticated connectors to external services. Most of this configuration lives in JSON files scattered across different directories."*

GitHub Copilot's org-wide enforcement of third-party MCP server policies (noted above) is a direct institutional response to the same concern. The `mcp-gateway-registry` project offering Keycloak/Entra authentication for MCP tool access is another.

Sources: X (@AISecHub, @GHCopilotCLILog), Web (agentic-community/mcp-gateway-registry)

---

### 6. Skills Are Going Cross-CLI and Cross-Platform

The skills standard that originated with Anthropic/Claude Code is spreading:

- **OpenAI Codex CLI** adopted the same `SKILL.md` format (December 2025, per WebSearch)
- **GitHub Copilot** added `~/.agents/skills/` discovery, aligned with VS Code (March 2026)
- **agentskill.sh** supports 20+ AI tools: Claude Code, Cursor, Copilot, Windsurf, and others
- **alirezarezvani/claude-skills** explicitly supports Claude Code, Codex, Gemini CLI, Cursor — same skill, multiple agents
- **heurema/nex** (GitHub, Rust): "Cross-CLI plugin distribution for AI agents" — v0.15.0 released March 25
- `@gadievron` building a tool shipping with Skills + VS Code extensions first, MCP + Claude Code Plugins roadmapped next

The practical implication: SKILL.md files written for Claude Code can be re-used in Codex, Copilot, and Windsurf with minimal or no modification.

Sources: X (@gadievron, @GHCopilotCLILog), Web (OpenAI Docs, agentskill.sh, GitHub/alirezarezvani, GitHub/heurema)

---

### 7. Agent Economy: Payment Rails and Reputation Systems Emerging

A separate thread visible in the X data — the agentic economy layer on top of skill/tool marketplaces:

- **@WCovenant** (16 likes): A payment rail for agents on Solana — optimistic settlement, auto-finalizing jobs, bonded arbitrator for disputes. *"No ZK theater. No custom escrow per marketplace. One protocol, any agent."*
- **@XRPLRiskscore**: MCP server with 4 tools submitted to Anthropic's Claude plugin marketplace, payments via x402 (0.5 XRP per call) — *"no API keys needed"* for XRPL-native agent commerce
- **@armalo_ai**: Agent trust/reputation flywheel — *"Register → define pacts → earn trust score → join marketplace → higher scores unlock more value. Think FICO score meets governance layer for the AI agent economy."*
- **@NafaNisa**: NaraChain — agent-native blockchain with identity, registry, and service marketplace

Sources: X (@WCovenant, @XRPLRiskscore, @armalo_ai, @NafaNisa)

---

## Cross-Source Patterns

**Pattern 1: "Definitive structure" content is the highest-engagement format**
- Appeared on: X (multiple independent posts)
- Multiple unrelated creators posted near-identical "definitive Claude Code setup" threads within days of each other, all organically trending. Signals genuine confusion/demand around canonical directory layout. @Dharmikpawar31 (203 likes) and @dkare1009 (34 likes) are the top examples.
- Key quote: *"You don't need another Claude Code setup. Just this one."* — @Dharmikpawar31

**Pattern 2: Skills-as-standard is spreading to all major coding agents**
- Appeared on: X, Web (OpenAI Docs, GitHub, DEV Community)
- The SKILL.md format originated with Anthropic but is now used by Codex, Copilot, Windsurf, Cursor. This cross-adoption is happening without a formal standards body — pure de facto convergence.
- Key quote: *"The Agent Skills format was originally developed by Anthropic, released as an open standard, and has been adopted by a growing number of agent products."* — KDnuggets

**Pattern 3: MCP registry fragmentation creating real pain**
- Appeared on: Web (blog.icme.io, TrueFoundry, Kong, AWS)
- Every major cloud/tool provider is launching their own MCP registry. There is no single discovery layer. This is the same problem npm vs. pip vs. cargo vs. gem solved for code packages.
- Key quote: *"Agents have registries, package managers, skill directories, and protocol-native discovery layers. There is no single front door."* — blog.icme.io

**Pattern 4: Security consciousness arriving at the same time as ecosystem growth**
- Appeared on: X (claudit-sec), GitHub (mcp-gateway-registry), Web
- The security tooling is emerging in real time alongside the ecosystem proliferation, not after. claudit-sec got 188 likes the same week the ecosystem overview posts were trending.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Dharmikpawar31 | "You don't need another Claude Code setup. Just this one. Where do Skills go? How do Hooks work?" | 203 | 47 | https://x.com/Dharmikpawar31/status/2037792844916965714 |
| @AISecHub | "claudit-sec — Security audit tool for Claude Desktop/Code on macOS, visibility into MCP servers, plugins, scheduled tasks" | 188 | 39 | https://x.com/AISecHub/status/2035937270885142961 |
| @GHCopilotCLILog | "Org policy enforcement for third-party MCP servers; add ~/.agents/skills/ as personal skill discovery directory" | 115 | 12 | https://x.com/GHCopilotCLILog/status/2037937811857305685 |
| @dkare1009 | "You won't need any other project structure for Claude Code. CLAUDE.md → .claude/ → skills/ → hooks → MCP" | 34 | 7 | https://x.com/dkare1009/status/2035906942741151944 |
| @WCovenant | "The payment rail AI agents use to get paid without human approval. One protocol, any agent." | 16 | 0 | https://x.com/WCovenant/status/2043043821450097094 |
| @AIAmbientPixels | "Building Pixel Agents — AI agent marketplace where creators earn on every run" | 0 | 0 | https://x.com/AIAmbientPixels/status/2043038473201029302 |
| @XRPLRiskscore | "MCP server now has 4 tools; Submitted to @AnthropicAI Claude plugin marketplace; SKILL.md live" | 0 | 0 | https://x.com/XRPLRiskscore/status/2043097638006821118 |
| @web3wiztron | "The core of the kit is the Skills Marketplace. Modular, Plug-and-Play architecture." | 2 | 0 | https://x.com/web3wiztron/status/2043192663311098098 |
| @gadievron | "We provide Skills and VS Code extensions now; will add MCP servers and Claude Code Plugins later" | 1 | 0 | https://x.com/gadievron/status/2039004271635509655 |
| @iamdavidoti | "BoostGPT: agent marketplace, pluggable interfaces, SSO, workspace scoping coming" | 1 | 0 | https://x.com/iamdavidoti/status/2043221770811920576 |
| @grok | "Claude Code Resource Bible — 50+ tools, MCP servers, skills/extensions, multi-agent setups" | 0 | 0 | https://x.com/grok/status/2041383051519778935 |
| @8020principal | "The Claude mcp/plugin ecosystem grew fast: Slack, GitHub, Google Workspace, Brave, Postgres, Memory Bank" | 0 | 0 | https://x.com/8020principal/status/2035492336394961090 |
| @woon_wong23193 | "cc-update-all: bulk-updates ALL Claude Code plugins, MCP servers, Cursor/Windsurf extensions" | 3 | 0 | https://x.com/woon_wong23193/status/2034307414334525647 |
| @armalo_ai | "Flywheel: Register → trust score → marketplace → reputation. FICO score meets AI agent economy" | 0 | 0 | https://x.com/armalo_ai/status/2043159721079976355 |
| @mejba_92 | "Dev setup: Cursor + Claude Code, 12 extensions, 8 terminal tools, 4 MCP servers always connected" | 0 | 0 | https://x.com/mejba_92/status/2035852212648501543 |
| @NeuroBrowse | "Claude Desktop: MCP servers connected to Notion, Stripe, Supabase, Canva. Claude Code: VS Code" | 3 | 0 | https://x.com/NeuroBrowse/status/2037289560468521035 |
| @NafaNisa | "Claiming agent on #NaraChain — Agent-native blockchain with identity, registry, marketplace" | 0 | 0 | https://x.com/NafaNisa/status/2043228849052541164 |
| @nanoplasticity | "Nanoplasticity — AI agent marketplace for boutique digital agencies. Less overhead." | 0 | 0 | https://x.com/nanoplasticity/status/2043197747055210886 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs — Skills | https://code.claude.com/docs/en/skills | Official Anthropic skills documentation |
| Claude Code Docs — Plugins | https://code.claude.com/docs/en/plugins | Official plugin creation guide |
| Stacklok Docs | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | ToolHive adds agent skills to registry (April 6, 2026) |
| AWS | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry preview launch |
| Official MCP Registry | https://registry.modelcontextprotocol.io/ | Anthropic's canonical MCP server registry |
| Kong | https://konghq.com/products/mcp-registry | Enterprise MCP Registry with API governance |
| blog.icme.io | https://blog.icme.io/getting-found-by-agents-a-builders-guide-to-tool-discovery-in-2026/ | "MCP tool discovery is fundamentally broken" — builder's guide |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | MCP registry comparison: Smithery (7K+ servers), MCPMarket (10K+) |
| GitHub — mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth + dynamic tool discovery |
| GitHub — orthogonalhq/apm | https://github.com/orthogonalhq/apm | APM: Agent Package Manager for Skills, Workflows, Apps |
| GitHub — heurema/nex | https://github.com/heurema/nex | Cross-CLI plugin distribution for AI agents (Rust) |
| GitHub — anthropics/skills | https://github.com/anthropics/skills | Official open standard repo for Agent Skills |
| GitHub — jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 skills + CCPI package manager |
| GitHub — alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 232+ skills for Claude Code, Codex, Gemini CLI, Cursor |
| GitHub — anthropics/claude-code #41068 | https://github.com/anthropics/claude-code/issues/41068 | Feature request: Skill-Driven On-Demand MCP & Tool Loading |
| claudefa.st | https://claudefa.st/blog/tools | MCP Setup guide; Code Kit v5.0 for Agent Teams |
| agentpatch.ai | https://agentpatch.ai/blog/claude-code-extensions-2026 | Claude Code Extensions 2026 guide |
| ailog.page | https://ailog.page/7-claude-code-extensions-i-tested-these-are-the-ones-i-kept/ | 7 extensions worth installing, hands-on tested |
| aregistry.ai | https://aregistry.ai/ | Centralized curated registry for AI artifacts |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces comparison |
| skills.sh | https://skills.sh/ | Vercel's agent skills directory — 87,000+ skills |
| OpenAI Developers | https://developers.openai.com/codex/skills | OpenAI Codex adopts Anthropic's Agent Skills format |
| Google Cloud Blog | https://cloud.google.com/blog/topics/partners/google-cloud-ai-agent-marketplace | Google Cloud AI Agent Marketplace |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | GitHub Copilot extensibility: skills + MCP complete guide |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community skill directory, 150+ curated skills |
| SkillsMP | https://skillsmp.com | Claude + Codex + ChatGPT skill marketplace |
| composio.dev | https://composio.dev/content/top-claude-code-plugins | Top Claude Code plugins list (Figma, Playwright, Vercel, Postgres) |
| Morph | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs. MCP vs. Plugins technical comparison |
| calmops.com | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI Agent Skills reusable capabilities guide 2026 |

---

## Stats Block

```
├─ 🔵 X: 24 posts │ 566 likes │ 105 reposts
├─ 🌐 Web: 29 pages — Stacklok, TrueFoundry, KDnuggets, blog.icme.io, AWS, Kong, Morph, claudefa.st, agentpatch.ai, OpenAI Docs
└─ 🗣️ Top voices: @Dharmikpawar31 (203 likes), @AISecHub (188 likes), @GHCopilotCLILog (115 likes)
```

---

## Data Gaps

- **Reddit: 0 results** — All subreddit and global Reddit searches returned 403 (Forbidden) and 402 (Payment Required) errors. r/ClaudeAI, r/anthropic, r/mcp, r/MachineLearning, r/LocalLLaMA all hit rate limits. This is likely the highest-discussion community for this topic and its absence is significant.
- **YouTube: 0 results** — yt-dlp returned 0 results for this query. ScrapeCreators YouTube search returned 402. No video content captured despite this being an active YouTube tutorial space.
- **TikTok/Instagram: 0** — SC API returned 402 for both platforms.
- **Hacker News: 0** — No HN stories matched in the last 30 days (HN search ran fine, no payment error).
- **Bluesky: 0** — Not configured in this environment.
- **Polymarket: 0** — No prediction markets for this topic, as expected.
- **Signal noise**: Several X posts in the dataset are blockchain/crypto-focused agent economy posts (VET, NaraChain, XRPL) that are tangential to the Claude Code / MCP server core topic. Included for completeness; weighted lower in synthesis.
- **Approximate coverage**: ~40% of ideal. X and Web are strong; Reddit, YouTube, and TikTok (where practitioner discussion typically concentrates) are missing entirely.

---

## Key Quotes

> "You don't need another Claude Code setup. Just this one. Everyone kept asking: → Where do Skills go? → How do Hooks work? → How do you connect MCP servers?" — @Dharmikpawar31 on X ([link](https://x.com/Dharmikpawar31/status/2037792844916965714))

> "Claude Desktop introduces a new class of endpoint risk: AI agents with autonomous execution, persistent scheduled tasks, MCP server integrations, browser-control extensions, and OAuth-authenticated connectors. Most of this configuration lives in JSON files scattered across different directories." — @AISecHub on X ([link](https://x.com/AISecHub/status/2035937270885142961))

> "MCP servers give agents the raw tools they can call; skills give them the knowledge of when, why, and how to use those tools effectively." — Stacklok Docs ([link](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates))

> "MCP tool discovery is fundamentally broken. Semantic search can't tell a good tool from a good description. Similarity is not satisfiability. Tool descriptions are ads, not specs. You need to be in every room where an agent might look for you." — blog.icme.io ([link](https://blog.icme.io/getting-found-by-agents-a-builders-guide-to-tool-discovery-in-2026/))

> "Think FICO score meets governance layer for the AI agent economy." — @armalo_ai on X ([link](https://x.com/armalo_ai/status/2043159721079976355))

> "It's essentially a 'Plug-and-Play' architecture for alpha." — @web3wiztron on X ([link](https://x.com/web3wiztron/status/2043192663311098098))

> "The Agent Skills format was originally developed by Anthropic, released as an open standard, and has been adopted by a growing number of agent products." — KDnuggets ([link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents))

> "Organization policy enforcement for third-party MCP servers applied to all users. Add ~/.agents/skills/ as personal skill discovery directory aligned with VS Code." — @GHCopilotCLILog on X ([link](https://x.com/GHCopilotCLILog/status/2037937811857305685))

> "No ZK theater. No custom escrow per marketplace. One protocol, any agent." — @WCovenant on X ([link](https://x.com/WCovenant/status/2043043821450097094))

> "Claude Code ships with zero extensions — you need Skills and MCP servers to unlock its full potential." — ailog.page ([link](https://ailog.page/7-claude-code-extensions-i-tested-these-are-the-ones-i-kept/))
