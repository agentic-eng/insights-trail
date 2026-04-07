# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-07
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 29 posts | 171 likes, 31 reposts | Several high-signal posts from Chinese AI community (@oragnes) |
| Hacker News | 23 stories | 143 points, 52 comments | Strong dev discussion; security DB thread top performer |
| Web | 30 pages | — | 3 WebSearch queries; official docs, InfoQ, KDnuggets, Spring.io |

---

## Synthesized Findings

### 1. Skills Are Becoming the Canonical Unit of Agent Knowledge

The clearest signal this month: a consensus is forming that "skills" — not tools, not MCP servers, not plugins — are the foundational unit of agent capability. HN's top discussion on this topic ("Skills are quietly becoming the unit of agent knowledge," 9pts, 13cmt at https://news.ycombinator.com/item?id=47475832) sparked a key debate: *"Will skills replace MCP servers eventually?"* and *"What do you think about checking the skills directly into the repo where they are useful?"* The thread drew 13 comments — the most of any non-top-scored story — signaling live controversy.

The HN community draws a clean conceptual line: a tool is atomic ("calculate compound interest"); a skill is orchestrational ("financial analysis" — encompassing domain knowledge, tool orchestration, and guided workflow). Skills encode *how* to use tools, not just what they do. Per cra.mr's analysis (https://cra.mr/mcp-skills-and-agents/), skills are reusable prompts with optional bundled artifacts, generally exposed to the system prompt with available skills listed for the agent.

Cross-platform: @Jaiinfoway_ on X framed the canonical Agent Development Kit as three-tiered: Memory (persistent configs) + Skills (modular execution) + Hooks (event-driven control) — https://x.com/Jaiinfoway_/status/2041417282828832887.

### 2. Marketplace Explosion: Three Competing Standards, Thousands of Skills

The skills distribution ecosystem has fragmented into several competing hubs, each with distinct scale:

- **SkillsMP** (https://skillsmp.com/) — 425,000+ skills indexed, supporting Claude, Codex & ChatGPT, built around the open SKILL.md standard
- **skills.sh** (Vercel-launched, https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/) — 87,000+ unique skills tracked since launch; InfoQ covered the launch at https://www.infoq.com/news/2026/02/vercel-agent-skills/
- **LobeHub Skills** — 169,739 skills indexed, one of the fastest-growing marketplaces
- **Claude-specific:** `claudemarketplaces.com` (https://claudemarketplaces.com/) aggregates Claude Code plugins, MCP servers, and skills; `jeremylongshore/claude-code-plugins-plus-skills` on GitHub (https://github.com/jeremylongshore/claude-code-plugins-plus-skills) ships 340 plugins + 1,367 agent skills with CCPI package manager
- **MCP registry:** loaditout-mcp-server (https://glama.ai/mcp/servers/loaditoutadmin/loaditout-mcp-server) indexes 20,000+ MCP servers with A/B/C/F security grading — only 20.5% of servers earn an A grade

The npm analogy is everywhere. KDnuggets framed it directly at https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents: "The emergence of this ecosystem could do for AI agent behaviors what npm did for JavaScript libraries."

### 3. Production-Grade Skill Collections: addyosmani/agent-skills and AI-Research-SKILLs

Two collections drew significant attention this week:

**addyosmani/agent-skills** (mentioned by @daisuke at https://x.com/daisuke/status/2041423270541697320): "Production-grade engineering skills for AI coding agents" — organized around a DEFINE → PLAN → BUILD → VERIFY → REVIEW → SHIP lifecycle. This is a direct attempt to encode software engineering best practices as reusable agent skills, not just automation scripts.

**AI-Research-SKILLs** (top X post by @oragnes, 118 likes, 25rt: https://x.com/oragnes/status/2040960583693201478): A Chinese-community-promoted library that plugs 87 AI tech stacks (fine-tuning, distributed training, RAG, evaluation, etc.) into agents as "professional knowledge cards" — blocking hallucinated APIs by grounding agents in actual documentation and real-world gotchas. It includes an Autoresearch engine for closed-loop autonomous research.

Also notable: **a collection of 35 Golang Agent Skills** (hn/samber, https://news.ycombinator.com/item?id=47487741) and **Production-ready Agent Skills + 17 agents + orchestration protocol** (hn/jungard, https://news.ycombinator.com/item?id=47363984), suggesting language-specific and production-focused skill libraries are proliferating.

### 4. Claude Code–Specific Skills & Tools

Several HN stories target Claude Code specifically:

- **BrowserHawk** — open-source autonomous QA agent skill for Claude Code (hn/JakubKontra, https://news.ycombinator.com/item?id=47574095)
- **Skills Manager** — manage AI agent skills across Claude, Cursor, and Copilot from one interface (hn/evergreenxx, 3pts, 9cmt: https://news.ycombinator.com/item?id=47423910) — the 9 comments suggest friction with cross-tool skill portability
- **"What Claude Code Leak Teaches Us About Agent Skills"** — hn/dev_chad (https://news.ycombinator.com/item?id=47605341): an analysis piece on how Claude Code's internals inform skill design
- **Anthropic official:** 13 free AI courses now cover Claude, Claude Code, API, Agent Skills, MCP, Bedrock, and Vertex AI — per @oragnes (https://x.com/oragnes/status/2041428820658643053). Anthropic's platform docs include a dedicated Agent Skills overview at https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview and the official Claude Code docs cover plugin discovery at https://code.claude.com/docs/en/discover-plugins.

### 5. Security: The Open Wound of Skill Marketplaces

The **Agent Skills Open Security Database** (hn/4ppsec, 36pts — highest-scored story this cycle: https://news.ycombinator.com/item?id=47402118) launched to track security risks introduced by agent skills. The community reaction was divided: one commenter said *"this whole concept of insecure skills is so dumb to me — if your engineers are installing and running random 'skills' found online it's the same as if you had engineers installing random npm packages"*, while others noted the database was "nice" once they understood what it was.

Corroborating data from loaditout-mcp-server's registry: only **20.5% of 20,652 MCP servers** earn an A security grade. The enterprise-ready MCP Gateway & Registry (https://github.com/agentic-community/mcp-gateway-registry) is a direct response — adding OAuth auth, Keycloak/Entra integration, and auditable tool access to address "scattered MCP server chaos."

The security concern is the same as npm's supply-chain problem: the ecosystem is moving faster than governance.

### 6. Self-Improving Agents and Academic Research on Skill Internalization

Two signals point toward skills becoming dynamic rather than static:

**SKILL0 paper** — @askalphaxiv (29 likes, 4rt: https://x.com/askalphaxiv/status/2041420021788705207): *"Most agent systems use skills like cheat sheets. It retrieves them at runtime, pastes them into the prompt, and hopes the model follows."* SKILL0 proposes in-context agentic reinforcement learning so agents *internalize* skills rather than just retrieving them — a qualitative shift from lookup to learning.

**Hermes Agent** — @hasamba (https://x.com/hasamba/status/2041412663519895777): a self-improving agent that auto-creates and refines skills, stores searchable session memory (FTS5), spawns parallel subagents, and runs across Telegram/Discord/CLI. Model-agnostic.

Per @jackadoresai on X: *"Specialized agent skills over generalist models. That's exactly where agentic coding is headed — those build time wins compound fast."* (https://x.com/jackadoresai/status/2041415998926995743)

### 7. Workflow Conversion and Vertical Skill Packs

Several tools aim to lower the barrier to skill creation:

- **n8n → agent skills converter** — turn n8n workflows into OpenClaw-compatible agent skills (hn/just-claw-it, https://news.ycombinator.com/item?id=47561083)
- **Orca** — executable skills and capabilities for AI agent workflows (hn/gfernandf, https://news.ycombinator.com/item?id=47584819)
- **Ink** — deploy full-stack apps from AI agents via MCP or Skills (hn/august-, 32pts: https://news.ycombinator.com/item?id=47337028) — raised VPC/auth questions in comments
- **AI agent skills for affiliate marketing** — vertical-specific Markdown skills that work with any LLM (hn/sonpiaz, https://news.ycombinator.com/item?id=47632530)
- **Gumroad founder's 9 open-source AI agent skills** (Minimalist Entrepreneurship) — @Jason23818126 (20 likes: https://x.com/Jason23818126/status/2041423273049919509): a business workflow in skill form, including /find-community, a deliberate inversion of "build product first"

---

## Cross-Source Patterns

**Pattern 1: Skills vs. MCP — Architecture Debate**
- HN: "Will skills replace MCP servers eventually?" (https://news.ycombinator.com/item?id=47475832), "Skills are quietly becoming the unit of agent knowledge"
- Web: cra.mr explicitly analyzes the distinction; FastMCP adds a Skills Provider (https://gofastmcp.com/servers/providers/skills); mcpservers.org has an Agent Skills Library section (https://mcpservers.org/agent-skills)
- Signal: Skills and MCP are converging — skills author knowledge, MCP servers expose tools; some platforms (Ink, loaditout) treat them as peer installation targets

**Pattern 2: Security Governance Lag**
- HN: Agent Skills Open Security Database (36pts, https://news.ycombinator.com/item?id=47402118)
- Web: Only 20.5% of 20,652 MCP servers earn an A grade (loaditout registry); enterprise MCP Gateway addresses OAuth/audit gaps (https://github.com/agentic-community/mcp-gateway-registry)
- Signal: The ecosystem is replicating npm's supply-chain vulnerability pattern; governance tooling is nascent

**Pattern 3: SKILL.md as Emerging Standard**
- Web: SkillsMP (425K+ skills), skills.sh (87K), LobeHub (169K) all built around SKILL.md; Anthropic official docs describe skills as SKILL.md files (https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- X: @daisuke cites addyosmani/agent-skills using the same format; @oragnes highlights Anthropic's official Agent Skills course
- HN: Multiple Show HN projects shipping SKILL.md-based packages
- Signal: SKILL.md is winning as the distribution format, analogous to Dockerfile or package.json

**Pattern 4: Chinese AI Community Driving Skill Adoption**
- X: @oragnes (118 likes on AI-Research-SKILLs, 2likes on Anthropic course summary) — dominant voice in Chinese-language agent skills content; @Jason23818126 (Gumroad 9 skills)
- Signal: The Chinese developer community is an early and active adopter; many top-engagement X posts are in Mandarin

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @oragnes | AI-Research-SKILLs: 87 AI tech stacks packaged as agent "knowledge cards," blocks hallucinated APIs | 118 | 25 | https://x.com/oragnes/status/2040960583693201478 |
| @askalphaxiv | SKILL0: In-Context Agentic RL for Skill Internalization — moving beyond cheat-sheet retrieval | 29 | 4 | https://x.com/askalphaxiv/status/2041420021788705207 |
| @Jason23818126 | Gumroad founder's 9 open-source AI Agent Skills — anti-intuitive business workflow | 20 | 1 | https://x.com/Jason23818126/status/2041423273049919509 |
| @daisuke | addyosmani/agent-skills: Production-grade engineering skills (DEFINE→PLAN→BUILD→VERIFY→REVIEW→SHIP) | — | — | https://x.com/daisuke/status/2041423270541697320 |
| @openapexmarket | Publishing free agent skills = seeding an ecosystem that doesn't exist yet | — | — | https://x.com/openapexmarket/status/2041426383084408999 |
| @jackadoresai | Specialized agent skills over generalist models — where agentic coding is headed | — | — | https://x.com/jackadoresai/status/2041415998926995743 |
| @hasamba | Hermes Agent: self-improving, auto-creates/refines skills, FTS5 memory, parallel subagents | — | — | https://x.com/hasamba/status/2041412663519895777 |
| @Jaiinfoway_ | Agent Development Kit: Memory + Skills (modular execution) + Hooks (event-driven) | — | — | https://x.com/Jaiinfoway_/status/2041417282828832887 |
| @oragnes | Anthropic 13 free courses: Claude, Claude Code, API, Agent Skills, MCP, Bedrock, Vertex AI | 2 | 1 | https://x.com/oragnes/status/2041428820658643053 |
| @oragnes | Anthropic free course list including Agent Skills entry course | 2 | — | https://x.com/oragnes/status/2041429329704587525 |
| @isxhyg | Selling time → selling agent time. Skills multiplied without writing more code | — | — | https://x.com/isxhyg/status/2041424151081341131 |
| @flanaksici47602 | NaraChain: agents with memory, skills, and reputation stored on-chain | — | — | https://x.com/flanaksici47602/status/2041410947948880112 |
| @gzmxbeth | On-chain agent skills/personality/behavioral boundaries with no IPFS | — | — | https://x.com/gzmxbeth/status/2041412071473176644 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| hn/4ppsec | Agent Skills – Open Security Database | 36 | 9 | "Installing random skills is the same as installing random npm packages" | https://news.ycombinator.com/item?id=47402118 |
| hn/chenxi9649 | Agent Skills: One-Shot PySpark from the CLI | 22 | 4 | "agent 'build me a churn model from this data' = YES PLEASE" | https://news.ycombinator.com/item?id=47534936 |
| hn/august- | Show HN: Ink – Deploy full-stack apps from AI agents via MCP or Skills | 32 | 6 | "Is Okta supported for auth, and how does bring your own cloud work?" | https://news.ycombinator.com/item?id=47337028 |
| hn/marioskales | Show HN: Skales – I built a desktop AI agent a 6-year-old can use | 12 | 6 | — | https://news.ycombinator.com/item?id=47613527 |
| hn/latand6 | Skills are quietly becoming the unit of agent knowledge | 9 | 13 | "Will skills replace MCP servers eventually?" | https://news.ycombinator.com/item?id=47475832 |
| hn/dev_chad | What Claude Code Leak Teaches Us About Agent Skills | 5 | 0 | — | https://news.ycombinator.com/item?id=47605341 |
| hn/evergreenxx | Skills Manager – manage AI agent skills across Claude, Cursor, Copilot | 3 | 9 | — | https://news.ycombinator.com/item?id=47423910 |
| hn/sonpiaz | Show HN: AI agent skills for affiliate marketing (Markdown, any LLM) | 3 | 0 | — | https://news.ycombinator.com/item?id=47632530 |
| hn/samber | A collection of 35 Golang Agent Skills | 3 | 2 | — | https://news.ycombinator.com/item?id=47487741 |
| hn/eterer | I built a package manager for agent skills | 3 | 1 | — | https://news.ycombinator.com/item?id=47489570 |
| hn/just-claw-it | Show HN: Built tool to turn n8n workflows into OpenClaw-compatible agent skills | 3 | 0 | — | https://news.ycombinator.com/item?id=47561083 |
| hn/gfernandf | Orca – Executable skills and capabilities for AI agent workflows | 3 | 1 | — | https://news.ycombinator.com/item?id=47584819 |
| hn/jungard | Production-ready Agent Skills, 17 agents, and a orchestration protocol | 3 | 1 | — | https://news.ycombinator.com/item?id=47363984 |
| hn/JakubKontra | BrowserHawk – Open-source autonomous QA agent skill for Claude Code | 3 | 0 | — | https://news.ycombinator.com/item?id=47574095 |
| hn/tadwork | Show HN: A small app that ships with AI agent skills to extend and audit it | 3 | 0 | — | https://news.ycombinator.com/item?id=47442521 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Claude Docs | https://code.claude.com/docs/en/discover-plugins | Official plugin marketplace discovery docs |
| Anthropic Platform Docs | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official Agent Skills API overview |
| GitHub: alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 220+ Claude Code skills for 10 coding agents |
| GitHub: jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 skills with CCPI package manager |
| GitHub: quemsah/awesome-claude-plugins | https://github.com/quemsah/awesome-claude-plugins | Automated plugin adoption metrics via n8n |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregated Claude Code plugins/skills/MCP directory |
| liteLLM Docs | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Managed Skills via liteLLM |
| SkillsMP | https://skillsmp.com/ | 425,000+ skills; Claude, Codex, ChatGPT |
| buildwithclaude.com | https://buildwithclaude.com/ | Community plugin marketplace |
| Scott Spence Blog | https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces | Organizing skills into plugin marketplaces |
| GitHub: microsoft/skills | https://github.com/microsoft/skills | Microsoft's skills/MCP/Agents.md repo for coding agents |
| Glama / loaditout-mcp-server | https://glama.ai/mcp/servers/loaditoutadmin/loaditout-mcp-server | 20,000+ MCP servers, A/B/C/F security grading |
| GitHub: agentic-community/mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth/Keycloak |
| mcpservers.org/agent-skills | https://mcpservers.org/agent-skills | Agent Skills Library on Awesome MCP Servers |
| PulseMCP | https://www.pulsemcp.com/servers/mrsimpson-agent-skills | Agent Skills MCP Server listing |
| cra.mr | https://cra.mr/mcp-skills-and-agents/ | Analysis: MCP, Skills, and Agents distinctions |
| Cloud Native Deep Dive | https://www.cloudnativedeepdive.com/managing-mcp-servers-and-tools-with-agentregistry/ | Managing MCP with Agentregistry OSS |
| FastMCP | https://gofastmcp.com/servers/providers/skills | Skills Provider in FastMCP framework |
| mcpservers.org | https://mcpservers.org | Main Awesome MCP Servers directory |
| MCPMarket | https://mcpmarket.com/server/agent-skills-1 | MCP Gateway for AI Agent Skill Management |
| OpenAI Developers | https://developers.openai.com/codex/skills | Codex Agent Skills official docs |
| GitHub: skillmatic-ai/awesome-agent-skills | https://github.com/skillmatic-ai/awesome-agent-skills | Definitive resource for agent skills patterns |
| Calmops | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI Agent Skills Complete Guide 2026 |
| johnoct.com | https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/ | Skills.sh: Missing Package Manager for Agent Capabilities |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 Agent Skill Marketplaces ranked |
| Spring.io | https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/ | Spring AI Agentic Patterns: Agent Skills |
| InfoQ | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Vercel Introduces Skills.sh announcement |
| Medium / Addo Zhang | https://addozhang.medium.com/agent-skills-deep-dive-building-a-reusable-skills-ecosystem-for-ai-agents-ccb1507b2c0f | Deep dive: Building a Reusable Skills Ecosystem |
| jacklandrin.com | https://www.jacklandrin.com/ai%20agent/2026/03/14/skills-cli-guide-using-npx-skills-to-supercharge-your-ai-agents.html | Skills-CLI Guide: npx skills usage |
| DEV Community | https://dev.to/lightningdev123/understanding-skills-in-ai-agents-essential-skills-developers-should-know-in-2026-49hd | Understanding Skills in AI Agents 2026 |

---

## Stats Block

```
├─ 🔵 X: 29 posts │ 171 likes │ 31 reposts
├─ 🟢 HN: 23 stories │ 143 points │ 52 comments
├─ 🌐 Web: 30 pages — Anthropic Docs, SkillsMP, KDnuggets, InfoQ, Spring.io, FastMCP, Scott Spence, Calmops, DEV Community, Medium
└─ 🗣️ Top voices: @oragnes (122 likes), @askalphaxiv (29 likes) │ hn/4ppsec (36pts), hn/august- (32pts)
```

---

## Data Gaps

- **Reddit: 0 threads** — ScrapeCreators returned HTTP 402 (Payment Required), likely quota exhaustion. The "agent-skills" query may have been too narrow; broader queries like "claude code plugins" or "MCP servers" might have returned results. Estimated coverage impact: significant — Reddit is where developer adoption discussions live.
- **Bluesky: error** — HTTP 403 Forbidden throughout the session. Bluesky discussions on agent skills/MCP are unrepresented.
- **YouTube: 0 videos** — yt-dlp search returned no results for "agent-skills" as a query. Tutorial and demo content on agent skills (likely substantial given the ecosystem activity) is entirely absent.
- **TikTok/Instagram: not activated** — INCLUDE_SOURCES not set for these platforms.
- **Approximate coverage:** ~55% of available signal. Developer community discussion (Reddit, HN, GitHub) is the richest vein for this topic; Reddit's absence is the most impactful gap.
- **Noise filtered:** 3 X posts excluded as off-topic (@achromatic_lady — fictional character context; @SRINIVASHK64 — government job training; @flanaksici47602/@gzmxbeth — blockchain/NFT agent gaming, retained for completeness in table).

---

## Key Quotes

> "Publishing free AI agent skills feels like seeding an ecosystem that doesn't exist yet. You're giving away tools hoping future autonomous agents will discover them and understand their value." — @openapexmarket on X ([link](https://x.com/openapexmarket/status/2041426383084408999))

> "Most agent systems use skills like cheat sheets. It retrieves them at runtime, pastes them into the prompt, and hopes the model follows." — @askalphaxiv on X, describing SKILL0 paper ([link](https://x.com/askalphaxiv/status/2041420021788705207))

> "If your engineers are installing and running random 'skills' found online it's the same as if you had engineers installing random npm packages." — hn/4ppsec commenter on Agent Skills Security DB ([link](https://news.ycombinator.com/item?id=47402118))

> "Will skills replace MCP servers eventually?" — hn/latand6 commenter on "Skills are quietly becoming the unit of agent knowledge" ([link](https://news.ycombinator.com/item?id=47475832))

> "Specialized agent skills over generalist models. That's exactly where agentic coding is headed — those build time wins compound fast." — @jackadoresai on X ([link](https://x.com/jackadoresai/status/2041415998926995743))

> "Selling time → selling agent time. Your skills multiplied without writing more code. Design prompts right, get paid while sleeping. This is the new freelancing." — @isxhyg on X ([link](https://x.com/isxhyg/status/2041424151081341131))

> "agent 'build me a churn model from this data' = YES PLEASE" — hn commenter on One-Shot PySpark agent skill ([link](https://news.ycombinator.com/item?id=47534936))

> "The emergence of this ecosystem could do for AI agent behaviors what npm did for JavaScript libraries and Docker Hub did for container images." — KDnuggets ([link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents))
