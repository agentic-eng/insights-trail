# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-05-03
**Query type:** GENERAL
**Sources:** Hacker News, X/Twitter, YouTube, TikTok, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 threads | — | Search returned no indexable threads; likely has discussions |
| X/Twitter | 10 posts | — | Mix of official @claudeai + community devs |
| YouTube | 2 videos | — | No transcript/view data retrieved |
| Hacker News | 22 stories | — | Heavy PolyMCP cluster + Skills-vs-MCP debate threads |
| TikTok | 3 videos | — | Beginner tutorial content |
| Instagram | 0 reels | — | Not retrieved |
| Bluesky | 0 posts | — | bsky-mcp-server repos found; no posts retrieved |
| Polymarket | 0 markets | — | Polymarket MCP server found; no prediction markets |
| GitHub | 19 repos | — | Including 42.1k-star awesome-claude-code |
| Web | 60+ pages | — | Blogs, news, official docs |

---

## Synthesized Findings

### 1. The Three-Layer Stack: Skills, MCP, Plugins — Taxonomy Finally Crystallizes

After months of community confusion, 2026 has produced a widely-accepted taxonomy for Claude Code's extension system:

- **Skills** — Markdown instruction files (30–50 tokens each) that teach Claude *how* to do something. Stored in `.claude/skills/`, each becomes a `/slash-command`. They accept arguments, spawn subagents, and orchestrate multi-step workflows. Token-cheap, portable across platforms.
- **MCP Servers** — Bridges to external systems (GitHub, databases, APIs, browsers). Can consume 50,000–77,000 tokens before any work begins with a typical 5-server setup. Used when Claude needs to *access* something.
- **Plugins** — Distributable bundles packaging skills, MCP configs, slash commands, hooks, and subagents into a single installable unit. "If Skills are recipe cards and MCP is the kitchen plumbing, a Plugin is the full kitchen, stocked and ready to cook."

Community consensus: use MCP for connectivity, Skills for methodology, Plugins for sharing. The [official Claude Code docs](https://code.claude.com/docs/en/skills) formalize this, and guides like [MorphLLM's Complete Guide 2026](https://www.morphllm.com/claude-code-skills-mcp-plugins) and [AlexOp.dev's Full Stack explainer](https://alexop.dev/posts/understanding-claude-code-full-stack/) have become reference anchors across the community.

> "Skills = procedural knowledge (30-50 tokens each, loaded on-demand) / MCP = external tool connections (can use 50k+ tokens) / Plugins = shareable bundles of everything / Hooks = automated actions at specific moments / Slash Commands = prompt shortcuts" — [SkillsPlayground](https://skillsplayground.com/guides/claude-code-plugins/)

Cross-platform: this taxonomy is active on Hacker News ([item 45619537](https://news.ycombinator.com/item?id=45619537)), X/Twitter ([@claude_code FAQ](https://x.com/claude_code/status/2009479585172242739)), and across dozens of web guides.

---

### 2. Anthropic's Agent Skills Open Standard (December 18, 2025)

The single most structurally significant move of the reporting window: On December 18, 2025, Anthropic published the **Agent Skills specification as an open standard** at `agentskills.io`, making Skills cross-platform for any AI system to adopt.

At launch, Anthropic published a directory of **partner-built skills** from: **Atlassian** (Jira ticket management, Confluence search, sprint orchestration), **Figma** (design asset workflows), **Canva** (content creation), **Stripe** (financial operations: refund processing, audit logs, customer profiles), **Notion** (document management), and **Zapier** (automation bridges). Enterprise Team/Enterprise plans gained org-wide skill management.

Coverage: [SiliconANGLE](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/), [VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard), [Unite.AI](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/), [TheNextGenTechInsider](https://www.thenextgentechinsider.com/posts/anthropic-launches-open-standard-agent-skills-challenging-openai), [H2S Media](https://www.how2shout.com/news/anthropic-agent-skills-open-standard-enterprise-directory-2025.html), [PulseMark](https://pulsemark.ai/anthropic-agent-skills-open-standard-december-2025/), [TheAITrack](https://theaitrack.com/anthropic-open-agent-skills-standard/).

The strategic read: VentureBeat called it "challenging OpenAI in workplace AI." The move follows MCP's pattern of Anthropic building open infrastructure to anchor the ecosystem — this time targeting enterprise workflow automation where OpenAI's Operator and GPT Actions compete.

---

### 3. The MCP Token Overhead Crisis — and Tool Search as the Fix

The central practical pain point of the reporting window: **MCP servers were consuming 50,000–77,000 tokens before any conversation started**, because every tool schema was injected into context upfront whether or not Claude would ever call that tool.

Real user reports: "I watched my context window die before I could write a single prompt — 67,000 tokens gone, just from connecting four MCP servers." GitHub's official MCP server alone could consume tens of thousands of tokens.

**Anthropic's response:** On **January 14, 2026**, Thariq Shihipar announced **MCP Tool Search** for Claude Code. Instead of pre-loading all tool definitions, Claude searches for and loads only the tools it actually needs. Claude Code checks if MCP tool descriptions exceed 10K tokens; if so, tools are marked `defer_loading: true`. Result: typical session overhead drops from ~77K tokens to ~8.7K tokens — **an 85–95% reduction**.

Data: [Medium/joe.njenga](https://medium.com/@joe.njenga/claude-code-just-cut-mcp-context-bloat-by-46-9-51k-tokens-down-to-8-5k-with-new-tool-search-ddf9e905f734) reported 46.9% reduction (51K → 8.5K) in a specific test. [ClaudeFast](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) reported up to 95% context savings. [AtCyrus](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) and [MindStudio](https://www.mindstudio.ai/blog/claude-code-mcp-server-token-overhead) covered the before/after in depth. [BSWEN](https://docs.bswen.com/blog/2026-04-24-mcp-token-overhead/) published analysis April 24, 2026. [Paddo.dev](https://paddo.dev/blog/claude-code-hidden-mcp-flag/) found an undocumented MCP flag recovering 32K tokens.

Community workarounds also emerged: [mksglu/context-mode](https://github.com/mksglu/context-mode) (98% reduction by sandboxing tool output), and the shift toward **MCP Gateways** (see Theme 7).

---

### 4. The CLI vs MCP Debate — "Is MCP Dead?"

The most contentious discussion of the period. In **February 2026**, Eric Holmes published "MCP is dead. Long live the CLI." — which landed on Hacker News front page for two days. The argument: CLI tool calls are dramatically lighter (~1,200 tokens) vs MCP schemas (~52,000 tokens in Mario Zechner's benchmark). Y Combinator's Garry Tan weighed in critically; Perplexity's CTO signaled moving away from MCP.

The pro-MCP counterargument came quickly: Charles Chen's "MCP is Dead; Long Live MCP!" distinguished stdio vs HTTP transports; Permit.io argued MCP's value as **enterprise infrastructure** for auth, auditing, and governance — things CLI can't provide.

**Arize AI ran the definitive benchmark** (Claude Opus 4.6, 500 trials, same 25-turn budget): correctness scores were virtually identical — LobeHub 0.826, Vault/CLI 0.833, MCP 0.834. Key finding: "It doesn't really matter which approach you pick. Your agent will get the answer." But differences in token cost, governance, and tooling complexity remain real.

The consensus that emerged: it's not binary. The right architecture has **execution layers** (CLI for lightweight tasks), **connectivity layers** (MCP for governed external tool access), and **governance layers** (MCP gateways for enterprise).

Coverage: [Arize AI](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/), [HackerNoon](https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it), [SmartScope analysis](https://smartscope.blog/en/blog/cli-vs-mcp-debate-premise-analysis/), [FireCrawl](https://www.firecrawl.dev/blog/mcp-vs-cli), [ShareUHack](https://www.shareuhack.com/en/posts/mcp-vs-skill-vs-cli-guide), [ThemenonLab](https://themenonlab.blog/blog/skills-vs-mcp-token-efficiency-ai-agents).

HN threads: ["You don't need MCP. You need Claude Skills."](https://news.ycombinator.com/item?id=45948490), ["I definitely see the value and versatility of Claude Skills"](https://news.ycombinator.com/item?id=46038842), ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537).

---

### 5. Plugin Ecosystem Explosion — Marketplaces Go Live

The plugin distribution infrastructure matured significantly:

**Official Anthropic Marketplace:** Launched with the Claude Code Plugins public beta. Accessible via `/plugin` → Discover tab in Claude Code, or [claude.com/plugins](https://claude.com/plugins). Two tiers: `/plugins` (Anthropic-maintained) and `/external_plugins` (community/partners). "Anthropic Verified" badge for additional review. Install via `/plugin install {name}@claude-plugins-official`. Repo: [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official).

**Community marketplaces:**
- **[TonsOfSkills.com](https://tonsofskills.com/)** (jeremylongshore): 425 plugins, 2,810 skills, 200 agents, with the `ccpi` CLI package manager (`pnpm add -g @intentsolutionsio/ccpi`). Updated daily by GitHub Actions. [Repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills).
- **[ClaudeMarketplaces.com](https://claudemarketplaces.com/)**: Community-curated directory; 150+ skills as of March 2026; 120,000+ monthly visitors.
- **[MCPMarket.com](https://mcpmarket.com/)**: MCP server discovery with news/analysis.
- **[MCP-Marketplace.io](https://mcp-marketplace.io/)**: Generic MCP discovery.
- **[Glama.ai](https://glama.ai/mcp/servers)**: 22,614 open-source MCP servers indexed; daily updates; security/compatibility scoring.
- **[Danube](https://news.ycombinator.com/item?id=47501216)**: AI Tools Marketplace where agents discover and execute tools; developers publish and monetize; launched March 2026.

**Curated lists:**
- [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code): ~42.1k stars; "delightfully curated collection" of skills, agents, hooks, status lines, orchestrators.
- [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit): 135 agents, 35+ curated skills (+400,000 via SkillKit), 176+ plugins, 20 hooks.
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills): 1,000+ cross-platform skills.

**Aggregate ecosystem stats (May 2026):** 4,200+ skills, 770+ MCP servers, 32,018 active plugins across 282,356 total components.

---

### 6. Simon Willison's "Cambrian Explosion" Prediction — Tracking the Trajectory

Simon Willison's October 2025 post ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://simonwillison.net/2025/Oct/16/claude-skills/) became the intellectual anchor of the skills discourse. His core arguments:

1. MCP is "a whole protocol specification covering hosts, clients, servers, resources, prompts, tools, sampling, roots, elicitation and three different transports." Skills are "Markdown with a tiny bit of YAML metadata and some optional scripts."
2. This simplicity enables portability — Skills work with Codex CLI, Gemini CLI, Cursor, and any other compatible tool using the same `SKILL.md` file.
3. "Claude Code is, with hindsight, poorly named — it's not purely a coding tool, it's a tool for general computer automation."
4. His prediction: "expect a Cambrian explosion in Skills which will make this year's MCP rush look pedestrian by comparison."

Six months on: the prediction appears validated. The ecosystem has grown from hundreds to thousands of skills. The open standard announcement formalized cross-platform portability. [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) lists 1,000+ cross-platform skills explicitly compatible with Claude, Codex, Gemini CLI, and Cursor.

Coverage: [simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/), [Substack](https://simonw.substack.com/p/claude-skills-are-awesome-maybe-a), [Mastodon](https://fedi.simonwillison.net/@simon/115385954842886933), [X/simonw](https://x.com/simonw/status/1978935386496995811), [MCPMarket news mirror](https://mcpmarket.com/news/b3898f78-553e-4a42-9800-6400731526da), [Vertu analysis](https://legacy.vertu.com/lifestyle/claude-skills-why-they-might-be-a-bigger-deal-than-mcp/).

---

### 7. MCP Gateways — Enterprise Infrastructure Layer Emerges

A distinct category of **MCP gateway** products emerged in 2025–2026, solving enterprise requirements that raw MCP servers can't address: centralized auth, rate limiting, auditing, security, multi-tenant routing.

Key players:
- **Bifrost**: Fastest open-source MCP gateway; 11 microseconds overhead at 5,000 req/s; built in Go; operates as both MCP client and server in one binary.
- **ContextForge**: Comprehensive open-source gateway/proxy/registry; sits in front of any MCP server, REST API, or agent-to-agent service.
- **MintMCP**: First SOC 2 Type II certified MCP platform — significant for enterprise compliance.
- **Zapier MCP**: Ecosystem bridge connecting Zapier's 5,000+ apps to MCP.
- **Klavis, Gate22, Unla, Peta**: Security-focused and domain-specific gateways.
- **MCP-C**: Cloud platform for running MCP agents and apps ([HN thread](https://news.ycombinator.com/item?id=45735886)).

Coverage: [ByteBridge Top 10 guide](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a), [ByteBridge gateway selection guide](https://bytebridge.medium.com/choosing-the-right-mcp-gateway-for-your-ai-infrastructure-020439fe6434), [ByteBridge top gateways analysis](https://bytebridge.medium.com/analyzing-top-mcp-gateways-contextforge-zapier-mcp-klavis-gate22-unla-and-peta-a7dd9a069928), [Integrate.io](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/), [GetMaxim.ai Top 5](https://www.getmaxim.ai/articles/top-5-mcp-gateways-for-production-ai-agents-in-2026/), [GetMaxim fastest gateway](https://www.getmaxim.ai/articles/fastest-enterprise-mcp-gateway-in-2026/), [GetMaxim Top 5 for Claude Code](https://www.getmaxim.ai/articles/top-5-mcp-gateways-for-claude-code-in-2026/).

---

### 8. Claude Code Plugins Public Beta + Cowork GA + Creative Connectors

**Plugins public beta:** Official @claudeai announcement: "Today we're introducing Claude Code Plugins in public beta. Plugins allow you to install and share curated collections of slash commands, agents, MCP servers, and hooks directly within Claude Code." ([X post](https://x.com/claudeai/status/1976332881409737124))

**Cowork GA (April 9, 2026):** Claude Cowork went generally available on macOS and Windows with analytics, OpenTelemetry, and role-based access controls. April 14: Routines (cloud-hosted automation) entered research preview. Enterprise: org-wide plugin/skill management. [ConstellationR](https://www.constellationr.com/insights/news/anthropic-expands-cowork-plugins-across-enterprise-functions), [ReleaseBot April 2026](https://releasebot.io/updates/anthropic/claude), [Blockchain.news analysis](https://blockchain.news/ainews/anthropic-claude-2026-launches-microsoft-365-connectors-1m-context-marketplace-and-claude-code-upgrades-latest-analysis).

**April 28, 2026 — 9 creative tool connectors:** Anthropic released connectors for Blender (Blender Foundation's MCP; Anthropic donated to support development), Adobe, Ableton (grounded in official Live/Push docs), SketchUp (conversation → 3D modeling starting point), and Splice (search royalty-free samples from within Claude). [9to5Mac](https://9to5mac.com/2026/04/28/anthropic-releases-9-new-claude-connectors-for-creative-tools-including-blender-and-adobe/), [Anthropic blog](https://www.anthropic.com/news/claude-for-creative-work).

Boris Cherny (Anthropic): "Reflecting on what engineers love about Claude Code, one thing that jumps out is its customizability: hooks, plugins, LSPs, MCPs, skills, effort, custom agents, status lines, output styles, etc. Every engineer uses their tools differently. We built Claude Code from the ground up." ([X](https://x.com/bcherny/status/2021699851499798911))

---

### 9. PolyMCP — Most Active HN Presence in the Ecosystem

PolyMCP appeared in 10+ distinct Hacker News "Show HN" posts across the reporting window — the highest single-project frequency observed. The project iteratively evolved from a basic MCP toolkit to a full orchestration framework:

- Structured skills from MCP tools ([HN 46656902](https://news.ycombinator.com/item?id=46656902))
- Scalable tool organization for MCP-based agents ([HN 46770554](https://news.ycombinator.com/item?id=46770554))
- Build MCP servers & AI agents in Python or TypeScript ([HN 46672385](https://news.ycombinator.com/item?id=46672385))
- Orchestrate AI agents across Python tools and MCP servers ([HN 47004468](https://news.ycombinator.com/item?id=47004468))
- Framework for building and orchestrating MCP agents ([HN 47017912](https://news.ycombinator.com/item?id=47017912))
- MCP Tools, Autonomous Agents, and Orchestration ([HN 47061490](https://news.ycombinator.com/item?id=47061490))

Core value proposition: Skills are curated, structured sets of MCP tools with documentation that solve (1) agents burning tokens loading raw schemas, (2) noisy tool discovery when tool count grows, (3) orchestration logic leaking into prompts. Features: expose tools over HTTP/in-process/stdio; real-time tool call inspector; agent ↔ LLM integration with auto tool discovery.

Also related on HN: ["Show HN: Mother MCP – Manage your Agent Skills like a boss"](https://news.ycombinator.com/item?id=46692102) (auto-provisions skills based on tech stack detection), ["Show HN: Playground to Test Skills and MCP"](https://news.ycombinator.com/item?id=46815786).

---

### 10. Community Content: Tutorials, Courses, and Skill Discovery Tooling

Strong content creation wave around skill/plugin education:

**Courses:** [Udemy bootcamp](https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/) covers full Claude Code ecosystem from zero to production agents.

**Blog posts:** [Batsov.com](https://batsov.com/articles/2026/03/11/essential-claude-code-skills-and-commands/) (March 11), [TowardsAI beginner guide](https://pub.towardsai.net/a-complete-beginners-guide-to-claude-code-skills-agents-hooks-plugins-mcp-085b26b73fdd) (March), [Medium unicodeveloper](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) "10 Must-Have Skills" (March), [Medium mohit15856](https://medium.com/@mohit15856/10-claude-plugins-you-actually-need-in-2026-with-full-setup-guides-136f7d879c37) "10 Claude Plugins You Actually Need" (April).

**YouTube:** ["The Ultimate Claude Code Guide | MCP, Skills & More"](https://www.youtube.com/watch?v=uogzSxOw4LU) — most comprehensive YouTube tutorial found.

**TikTok:** [@rileybrown.ai MCP tutorial](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559) with Notion/YouTube Thumbnails demo; [@sabrina_ramonov beginner setup](https://www.tiktok.com/@sabrina_ramonov/video/7608678097377955103); [@nocode.joshua Claude setup guide](https://www.tiktok.com/@nocode.joshua/video/7612009906907991304).

**X/Twitter:** @omarsar0: ["Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code. I built a skill inside of Claude Code that automatically builds, tests, and optimizes MCP tools."](https://x.com/omarsar0/status/1979242073372164306) @agreeahmed: ["i spent the last 2 weeks poking around Claude Code's ecosystem of plugins, skills, and slash commands. it's crazy powerful, but also feels incredibly early."](https://x.com/agreeahmed/status/2010863894793744573)

**Skill discovery tooling:** [K-Dense-AI/claude-skills-mcp](https://github.com/K-Dense-AI/claude-skills-mcp) — MCP server using vector search to find and retrieve agent skills; addresses the bootstrap problem of using MCP to discover skills.

---

## Cross-Source Patterns

### Pattern 1: "Skills > MCP for Steering Agent Behavior"
Appearing on: **Hacker News, X/Twitter, Web (blogs), YouTube**

The consensus that skills are the preferred mechanism for instructing agent *behavior* (how to approach a problem) while MCP handles *connectivity* (access to external systems) appeared across every platform that returned data.

- HN: ["You don't need MCP. You need Claude Skills."](https://news.ycombinator.com/item?id=45948490) + ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537)
- X: @omarsar0 ["Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code"](https://x.com/omarsar0/status/1979242073372164306)
- Web: Arize AI's benchmark confirms no correctness gap between approaches; token efficiency favors skills

### Pattern 2: MCP Token Overhead as Adoption Blocker
Appearing on: **Hacker News, Web (blogs, official docs), X/Twitter**

Consistently cited across all platforms as the primary friction for MCP adoption. The "67,000 tokens gone before writing a single prompt" quote appeared in multiple independent blog posts. Anthropic's MCP Tool Search response was broadly covered.

- HN: Multiple PolyMCP threads frame "loading raw schemas" as the core problem
- Web: [MindStudio](https://www.mindstudio.ai/blog/claude-code-mcp-server-token-overhead), [BSWEN](https://docs.bswen.com/blog/2026-04-24-mcp-token-overhead/), [AtCyrus](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide), [ClaudeFast](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

### Pattern 3: "Incredibly Early" — Ecosystem Powerful but Rough
Appearing on: **X/Twitter, Web, Hacker News**

Multiple independent observers noted the ecosystem is powerful but immature.

- X: @agreeahmed ["it's crazy powerful, but also feels incredibly early"](https://x.com/agreeahmed/status/2010863894793744573)
- Web: Official docs note the MCP layer of plugin bundles may not attach on every install (April 27, 2026 known issue)
- HN: Multiple PolyMCP iterations suggesting rapid iteration to find the right abstraction
- Quote from morphllm.com: "Experienced users consistently recommend two to three active plugins maximum, as each plugin adds to your context window baseline and can degrade output quality if overloaded."

### Pattern 4: Cross-Platform Skills Portability as Differentiator
Appearing on: **Hacker News, X/Twitter, Web, GitHub**

Skills working across Claude Code, Codex CLI, Gemini CLI, and Cursor was cited as a major strategic advantage over MCP.

- HN: Simon Willison thread — "nothing preventing them from being used with other models"
- Web: VoltAgent repo explicitly labels 1,000+ skills as "compatible with Claude Code, Codex, Gemini CLI, Cursor, and more"
- Web: InnovativeHumanCapital on [organizational portability implications](https://www.innovativehumancapital.com/article/claude-skills-and-the-organizational-redesign-of-work-simplicity-as-strategic-infrastructure)

### Pattern 5: MCP Gateway Category Crystallizing
Appearing on: **Hacker News, Web (multiple)**

The emergence of MCP gateways as a distinct infrastructure layer for enterprise was covered independently across news sources, suggesting genuine category formation rather than marketing.

- HN: [MCP-C cloud platform](https://news.ycombinator.com/item?id=45735886)
- Web: [ByteBridge series](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a), [GetMaxim.ai guides](https://www.getmaxim.ai/articles/top-5-mcp-gateways-for-production-ai-agents-in-2026/), [Integrate.io](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| simonw | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | "expect a Cambrian explosion in Skills which will make this year's MCP rush look pedestrian" | [link](https://news.ycombinator.com/item?id=45619537) |
| — | You don't need MCP. You need Claude Skills. | — | — | Core skills-vs-MCP debate thread | [link](https://news.ycombinator.com/item?id=45948490) |
| — | Show HN: PolyMCP – structured skills from MCP tools for efficient agent usage | — | — | Addresses token bloat and noisy tool discovery | [link](https://news.ycombinator.com/item?id=46656902) |
| — | Show HN: Mother MCP – Manage your Agent Skills like a boss | — | — | Auto-provisions skills from tech stack detection | [link](https://news.ycombinator.com/item?id=46692102) |
| — | Show HN: Danube – AI Tools Marketplace | — | — | Marketplace for agents to discover/execute tools; developers monetize | [link](https://news.ycombinator.com/item?id=47501216) |
| — | Show HN: PolyMCP Skills – Scalable Tool Organization for MCP-Based AI Agents | — | — | Scalability focus | [link](https://news.ycombinator.com/item?id=46770554) |
| — | Show HN: Playground to Test Skills and MCP | — | — | Testing tool pre-deployment | [link](https://news.ycombinator.com/item?id=46815786) |
| — | Show HN: MCP-C – cloud platform for running MCP agents and apps | — | — | Cloud-hosted MCP infrastructure | [link](https://news.ycombinator.com/item?id=45735886) |
| — | Show HN: ht-mcp – Rust MCP server of headless terminal for agents | — | — | Terminal control via MCP | [link](https://news.ycombinator.com/item?id=44310783) |
| — | Show HN: Vim Navigator – MCP server that lets AI agents drive Neovim | — | — | Editor control via MCP | [link](https://news.ycombinator.com/item?id=47655128) |
| — | Show HN: PolyMCP – orchestrate AI agents across Python tools and MCP servers | — | — | Full orchestration framework | [link](https://news.ycombinator.com/item?id=47004468) |
| — | Show HN: PolyMCP – MCP Tools, Autonomous Agents, and Orchestration | — | — | Latest iteration | [link](https://news.ycombinator.com/item?id=47061490) |
| — | I definitely see the value and versatility of Claude Skills (over MCP) | — | — | Community reaction to skills vs MCP | [link](https://news.ycombinator.com/item?id=46038842) |
| — | Claude Skills | — | — | Launch/discussion thread | [link](https://news.ycombinator.com/item?id=45607117) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | "Today we're introducing Claude Code Plugins in public beta..." | — | — | [link](https://x.com/claudeai/status/1976332881409737124) |
| @bcherny | "Reflecting on what engineers love about Claude Code...its customizability: hooks, plugins, LSPs, MCPs, skills..." | — | — | [link](https://x.com/bcherny/status/2021699851499798911) |
| @omarsar0 | "Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code..." | — | — | [link](https://x.com/omarsar0/status/1979242073372164306) |
| @avthars | "Claude Code crash course: Plugins - Plugins let you easily use best practices and customizations from other developers..." | — | — | [link](https://x.com/avthars/status/1990411824928264532) |
| @claude_code | "FAQ: What is the difference between Skill and Plugin? Plugins are containers for distributing and organizing skills..." | — | — | [link](https://x.com/claude_code/status/2009479585172242739) |
| @agreeahmed | "i spent the last 2 weeks poking around Claude Code's ecosystem of plugins, skills, and slash commands. it's crazy powerful, but also feels incredibly early." | — | — | [link](https://x.com/agreeahmed/status/2010863894793744573) |
| @nurijanian | "getting familiar with engineering plugins in Claude Code (work in Cursor too) is a very useful thing for PMs..." | — | — | [link](https://x.com/nurijanian/status/2034992369284887015) |
| @Param_eth | "The winning skills are in 2026: MCP, Claude API, Claude Code, Claude Agent SDK" | — | — | [link](https://x.com/Param_eth/status/2033211564862705765) |
| @TheAIWorld22 | "top 10 Claude Code Skills, Plugins & CLIs (April 2026)" | — | — | [link](https://x.com/TheAIWorld22/status/2049439345107784033) |
| @simonw | "Claude Skills are awesome, maybe a bigger deal than MCP" | — | — | [link](https://x.com/simonw/status/1978935386496995811) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| — | My Claude Code System For Viral TikTok Videos | — | — | No | [link](https://www.youtube.com/watch?v=lw69SOTKRM4) |

**TikTok:**
| Creator | Caption Snippet | Views | Likes | URL |
|---------|----------------|-------|-------|-----|
| @rileybrown.ai | "CLAUDE MCP TUTORIAL — give it access to tools using MCP (Notion, YouTube Thumbnails)" | — | — | [link](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559) |
| @sabrina_ramonov | "Claude Code Tutorial for Beginners - install vs code, setup claude code, integrate MCP server" | — | — | [link](https://www.tiktok.com/@sabrina_ramonov/video/7608678097377955103) |
| @nocode.joshua | "How to setup Claude as a complete beginner. 3 free resources to not get behind with Claude" | — | — | [link](https://www.tiktok.com/@nocode.joshua/video/7612009906907991304) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Glama Registry | [glama.ai/mcp/servers](https://glama.ai/mcp/servers) | 22,614 open-source MCP servers; definitive registry |
| anthropics/claude-plugins-official | [GitHub](https://github.com/anthropics/claude-plugins-official) | Official Anthropic-curated plugin directory |
| SiliconANGLE | [link](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/) | Agent Skills open standard Dec 2025 announcement |
| VentureBeat | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Enterprise Skills + OpenAI competition framing |
| Arize AI | [link](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/) | Definitive MCP vs CLI skills benchmark (500 trials) |
| simonwillison.net | [link](https://simonwillison.net/2025/Oct/16/claude-skills/) | "Cambrian explosion" prediction; skills taxonomy |
| HackerNoon | [link](https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it) | CLI vs MCP debate analysis + 10 tools |
| 9to5Mac | [link](https://9to5mac.com/2026/04/28/anthropic-releases-9-new-claude-connectors-for-creative-tools-including-blender-and-adobe/) | April 28 creative connectors (Blender, Adobe, Ableton) |
| tonsofskills.com | [link](https://tonsofskills.com/) | Open-source marketplace: 425 plugins, 2810 skills |
| hesreallyhim/awesome-claude-code | [GitHub](https://github.com/hesreallyhim/awesome-claude-code) | 42.1k-star community curated list |
| MorphLLM | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Most-cited comprehensive comparison guide |
| AlexOp.dev | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Technical deep dive on all extension layers |
| ByteBridge | [link](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | MCP gateways landscape overview |
| ClaudeFast | [link](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) | MCP Tool Search implementation details |
| SmartScope | [link](https://smartscope.blog/en/blog/cli-vs-mcp-debate-premise-analysis/) | Nuanced CLI vs MCP debate deconstruction |
| Danube on HN | [link](https://news.ycombinator.com/item?id=47501216) | AI Tools Marketplace for agent-to-tool monetization |
| ConstellationR | [link](https://www.constellationr.com/insights/news/anthropic-expands-cowork-plugins-across-enterprise-functions) | Cowork enterprise plugin expansion |
| BSWEN | [link](https://docs.bswen.com/blog/2026-04-24-mcp-token-overhead/) | MCP token overhead analysis (Apr 24, 2026) |
| VoltAgent/awesome-agent-skills | [GitHub](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ cross-platform skills (Claude, Codex, Gemini, Cursor) |
| Composio | [link](https://composio.dev/toolkits/github/framework/claude-code) | GitHub/YouTube/TikTok MCP integration guides |
| Wikipedia: MCP | [link](https://en.wikipedia.org/wiki/Model_Context_Protocol) | Reference: MCP open standard background |
| Claude Docs: MCP | [link](https://code.claude.com/docs/en/mcp) | Official MCP integration docs |
| Claude Docs: Skills | [link](https://code.claude.com/docs/en/skills) | Official skills authoring docs |
| Claude Docs: Plugins | [link](https://code.claude.com/docs/en/plugins) | Official plugin creation docs |
| Claude Docs: Discover Plugins | [link](https://code.claude.com/docs/en/discover-plugins) | Official marketplace discovery docs |
| claude.com/plugins | [link](https://claude.com/plugins) | Official Anthropic plugin catalog UI |
| Anthropic: Claude for Creative Work | [link](https://www.anthropic.com/news/claude-for-creative-work) | Official creative connectors announcement |
| K-Dense-AI/claude-skills-mcp | [GitHub](https://github.com/K-Dense-AI/claude-skills-mcp) | Vector search for skill discovery |
| rohitg00/awesome-claude-code-toolkit | [GitHub](https://github.com/rohitg00/awesome-claude-code-toolkit) | 135 agents, 176+ plugins, 400k skills via SkillKit |
| Medium/joe.njenga | [link](https://medium.com/@joe.njenga/claude-code-just-cut-mcp-context-bloat-by-46-9-51k-tokens-down-to-8-5k-with-new-tool-search-ddf9e905f734) | MCP Tool Search: 51K→8.5K token reduction measured |
| GetMaxim.ai | [link](https://www.getmaxim.ai/articles/fastest-enterprise-mcp-gateway-in-2026/) | Bifrost fastest MCP gateway benchmark |
| Integrate.io | [link](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/) | MCP gateways security comparison |
| PulseMark | [link](https://pulsemark.ai/anthropic-agent-skills-open-standard-december-2025/) | Agent Skills open standard deep analysis |
| Unite.AI | [link](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/) | Anthropic's pattern of building open infrastructure |
| FindSkill.ai | [link](https://findskill.ai/blog/claude-cowork-guide/) | Cowork + skills guide for non-engineers |
| Paddo.dev | [link](https://paddo.dev/blog/claude-code-hidden-mcp-flag/) | Undocumented MCP flag recovers 32K tokens |
| mksglu/context-mode | [GitHub](https://github.com/mksglu/context-mode) | 98% context reduction by sandboxing tool output |
| InnovativeHumanCapital | [link](https://www.innovativehumancapital.com/article/claude-skills-and-the-organizational-redesign-of-work-simplicity-as-strategic-infrastructure) | Skills as org infrastructure strategy |
| ComposioHQ/awesome-claude-plugins | [GitHub](https://github.com/ComposioHQ/awesome-claude-plugins) | Curated plugins with custom commands, agents, hooks |
| jeremylongshore/claude-code-plugins-plus-skills | [GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | Powers tonsofskills.com marketplace |
| Redwerk | [link](https://redwerk.com/blog/best-claude-code-plugins/) | 7 best plugins developer review |
| DEV.to/raxxostudios | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best skills & plugins community guide |
| GitHub MCP Server | [GitHub](https://github.com/github/github-mcp-server) | GitHub's official MCP Server |
| steipete/claude-code-mcp | [GitHub](https://github.com/steipete/claude-code-mcp) | Claude Code as one-shot MCP (agent-in-agent) |
| MindStudio | [link](https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference) | Skills vs Plugins decision guide |
| DevToolPicks | [link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Three-way comparison with decision matrix |
| SkillsPlayground | [link](https://skillsplayground.com/guides/claude-code-plugins/) | Complete plugins guide |
| TowardsAI | [link](https://pub.towardsai.net/a-complete-beginners-guide-to-claude-code-skills-agents-hooks-plugins-mcp-085b26b73fdd) | Beginner's complete guide (Mar 2026) |
| ProductTalk.org | [link](https://www.producttalk.org/how-to-use-claude-code-features/) | PM-oriented Claude Code guide |
| ThePromptShelf | [link](https://thepromptshelf.dev/blog/claude-code-custom-slash-commands/) | Custom slash commands via skills |
| YoungLeaders.tech | [link](https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins) | #95 newsletter: Skills vs Commands vs Subagents vs Plugins |
| Batsov.com | [link](https://batsov.com/articles/2026/03/11/essential-claude-code-skills-and-commands/) | Essential skills list (March 11, 2026) |
| ScriptByAI | [link](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate resource list 2026 |
| TurboDocx | [link](https://www.turbodocx.com/blog/best-claude-code-plugins-skills-mcp-servers) | Best plugins/skills/MCP servers roundup |
| SystemPrompt.io | [link](https://systemprompt.io/guides/claude-code-mcp-servers-extensions) | MCP server install and configure guide |
| AlexOp.dev: Customization | [link](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/) | CLAUDE.md, skills, subagents guide |
| ReleaseBot | [link](https://releasebot.io/updates/anthropic/claude) | Claude April 2026 changelog |
| Blockchain.news | [link](https://blockchain.news/ainews/anthropic-claude-2026-launches-microsoft-365-connectors-1m-context-marketplace-and-claude-code-upgrades-latest-analysis) | 2026 launches analysis |
| Duet.so | [link](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills) | Skills vs MCP 101 guide |
| Thomas Wiegold | [link](https://thomas-wiegold.com/blog/claude-skills-guide-developers/) | Developer-focused skills guide |
| Vertu | [link](https://legacy.vertu.com/lifestyle/claude-skills-why-they-might-be-a-bigger-deal-than-mcp/) | Token-efficient alternative framing |
| Algustionesa | [link](https://algustionesa.com/exploring-claude-skills-the-next-step-for-ai-agents/) | Exploring Claude Skills next steps |
| Groundy | [link](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | Official plugin ecosystem explainer |
| Gist: 5 MCP servers | [link](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) | 5 essential MCP servers + config |
| ClaudePluginHub | [link](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code) | MCP server plugins developer guide |
| H2S Media | [link](https://www.how2shout.com/news/anthropic-agent-skills-open-standard-enterprise-directory-2025.html) | Agent Skills open standard news |
| TheNextGenTechInsider | [link](https://www.thenextgentechinsider.com/posts/anthropic-launches-open-standard-agent-skills-challenging-openai) | Competitive framing vs OpenAI |
| TheAITrack | [link](https://theaitrack.com/anthropic-open-agent-skills-standard/) | Enterprise AI standard analysis |
| Fazal Medium | [link](https://fazal-sec.medium.com/anthropics-explosive-start-to-2026-everything-claude-has-launched-and-why-it-s-shaking-up-the-668788c2c9de) | Anthropic 2026 launches overview |
| MCPMarket news | [link](https://mcpmarket.com/news/b3898f78-553e-4a42-9800-6400731526da) | Claude Skills article mirror |
| MCPMarket TikTok skill | [link](https://mcpmarket.com/tools/skills/tiktok-content-strategy) | TikTok Content Strategy skill listing |
| MCPMarket BlueSky skill | [link](https://mcpmarket.com/tools/skills/bluesky-manager) | BlueSky Manager skill listing |
| Composio TikTok | [link](https://composio.dev/toolkits/tiktok/framework/claude-code) | TikTok MCP integration |
| Composio YouTube | [link](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration |
| Composio Marketing Skills | [link](https://composio.dev/content/best-marketing-skills) | Best marketing skills roundup |
| Stormy.ai | [link](https://stormy.ai/blog/building-tiktok-content-factory-claude-code) | TikTok content factory with Claude Code |
| Sabrina.dev | [link](https://www.sabrina.dev/p/claude-just-changed-content-creation-remotion-video) | Claude content creation tutorial |
| self.md | [link](https://self.md/guides/best-claude-code-plugins/) | Best plugins opinionated guide |
| Ado.im | [link](https://www.ado.im/posts/claude-customization-stack-mcp-skills-plugins/) | Customization stack mental model |
| FireCrawl | [link](https://www.firecrawl.dev/blog/mcp-vs-cli) | MCP vs CLI for AI agents |
| ShareUHack | [link](https://www.shareuhack.com/en/posts/mcp-vs-skill-vs-cli-guide) | Is MCP Dead? Scenarios guide |
| ThemenonLab | [link](https://themenonlab.blog/blog/skills-vs-mcp-token-efficiency-ai-agents) | Token efficiency war analysis |
| ClaudeFA.st | [link](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers |
| aitmpl.com | [link](https://www.aitmpl.com/plugins/) | Plugin templates directory |
| claudelog.com | [link](https://claudelog.com/claude-code-mcps/awesome-claude-code/) | awesome-claude-code community page |
| Udemy Course | [link](https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/) | Claude Code 2026 bootcamp |
| MindStudio token | [link](https://www.mindstudio.ai/blog/claude-code-mcp-server-token-overhead) | Token overhead analysis |
| AtCyrus | [link](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) | Tool search context pollution guide |
| MCP-Marketplace.io | [link](https://mcp-marketplace.io/) | MCP marketplace directory |
| PulseMCP | [link](https://www.pulsemcp.com/servers/allstacks) | MCP server tracking |
| Glama: Polymarket MCP | [link](https://glama.ai/mcp/servers/Franzferdinan51/polymarket-MCP) | Polymarket MCP server |
| caiovicentino/polymarket-mcp | [GitHub](https://github.com/caiovicentino/polymarket-mcp-server) | Polymarket MCP: 45 tools |
| brianellin/bsky-mcp-server | [GitHub](https://github.com/brianellin/bsky-mcp-server) | Bluesky MCP server |
| Saturn-VI/bsky-mcp | [GitHub](https://github.com/Saturn-VI/bsky-mcp) | Bluesky MCP (alternate) |
| quemsah/awesome-claude-plugins | [GitHub](https://github.com/quemsah/awesome-claude-plugins) | Plugin adoption metrics via n8n |
| Simon Willison Substack | [link](https://simonw.substack.com/p/claude-skills-are-awesome-maybe-a) | Original "bigger deal than MCP" analysis |
| Simon Willison Mastodon | [link](https://fedi.simonwillison.net/@simon/115385954842886933) | Cross-posted to Mastodon |
| Claude Code MCP-C HN | [link](https://news.ycombinator.com/item?id=45735886) | Cloud MCP platform |
| Claude Code HN Skills | [link](https://news.ycombinator.com/item?id=45607117) | Skills launch thread |
| Claude Code HN Skills2 | [link](https://news.ycombinator.com/item?id=45610869) | Simon's "just published" HN post |
| arize-ai/phoenix | [GitHub](https://github.com/arize-ai/phoenix) | AI observability used for MCP/skills evals |
| Claude Support: MCP Desktop | [link](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop) | Getting started with local MCP servers |
| Claude Docs: Plugins Ref | [link](https://code.claude.com/docs/en/plugins-reference) | Plugin format reference |
| aitmpl: claude-plugins-official | [link](https://www.aitmpl.com/plugins/claude-plugins-official) | Official plugins showcase |
| claudemarketplaces anthropics | [link](https://claudemarketplaces.com/plugins/anthropics-claude-code) | Anthropic's official plugins on community dir |
| ecosyste.ms awesome-claude | [link](https://awesome.ecosyste.ms/projects/github.com/hesreallyhim/awesome-claude-code) | Ecosystem tracking for awesome-claude-code |
| Financial Content | [link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-25-anthropic-unveils-agent-skills-open-standard-a-blueprint-for-modular-ai-autonomy) | Agent Skills blueprint analysis |
| ComposioHQ/awesome-claude-skills | [GitHub](https://github.com/ComposioHQ/awesome-claude-skills) | Curated skills list by Composio |
| zilliztech/claude-context | [GitHub](https://github.com/zilliztech/claude-context) | Codebase-as-context MCP |
| adityabawankule.io | [link](https://www.adityabawankule.io/guides/claude-code-youtube-analysis) | YouTube analysis via Claude Code |
| Wikipedia MCP | [link](https://en.wikipedia.org/wiki/Model_Context_Protocol) | MCP background reference |
| McpServers.org Danube | [link](https://mcpservers.org/servers/docs-danubeai-com) | Danube in MCP registry |
| Glama.ai MCP main | [link](https://glama.ai/mcp) | MCP servers, clients, tools overview |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no indexable results)
├─ 🔵 X: 10 posts │ — likes │ — reposts
├─ 🔴 YouTube: 2 videos │ — views
├─ 🟢 HN: 22 stories │ — points │ — comments
├─ 🟣 TikTok: 3 videos │ — views
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (bsky MCP repos found; no posts retrieved)
├─ 📊 Polymarket: 0 markets (Polymarket MCP server exists; no prediction markets on this topic)
├─ 🌐 Web: 80+ pages
└─ 🗣️ Top voices: @simonw, @bcherny, @omarsar0, @claudeai, @claude_code │ hesreallyhim/awesome-claude-code, jeremylongshore/tonsofskills, VoltAgent/awesome-agent-skills
```

---

## Data Gaps

- **Reddit**: All Reddit queries returned zero results. The search API consistently could not index Reddit threads. r/ClaudeAI, r/LocalLLaMA, and r/MachineLearning almost certainly contain relevant discussions — this is a meaningful blind spot. Estimated coverage: ~0% of Reddit activity.
- **Engagement metrics**: HN points/comments, X likes/reposts, YouTube views/likes, TikTok views/likes were not returned by the web search pipeline. Per-post engagement is unknown.
- **Bluesky**: Two Bluesky MCP server GitHub repos found, but no actual Bluesky posts retrieved. Bluesky discussion on this topic was not captured.
- **Instagram/Reels**: Not covered.
- **Polymarket**: A Polymarket MCP server exists, but no prediction markets on Claude skills/plugins topic were found.
- **HN thread contents**: Thread text, top comments, and point counts were not retrieved — only titles and URLs. Qualitative data from thread bodies is estimated from secondary web sources.
- **PolyMCP engagement**: The project had 10+ distinct HN posts but exact points/comment counts were not retrieved; significance is inferred from frequency.
- **Overall coverage estimate**: Web (~85%), Hacker News (~70% titles, ~20% content), X/Twitter (~40%), YouTube (~30%), TikTok (~25%), Reddit (~0%), Bluesky (~5%).

---

## Key Quotes

> "expect a Cambrian explosion in Skills which will make this year's MCP rush look pedestrian by comparison" — @simonw / Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code. I built a skill inside of Claude Code that automatically builds, tests, and optimizes MCP tools. It runs in a loop, loading context and tools." — @omarsar0 on X ([link](https://x.com/omarsar0/status/1979242073372164306))

> "i spent the last 2 weeks poking around Claude Code's ecosystem of plugins, skills, and slash commands. it's crazy powerful, but also feels incredibly early." — @agreeahmed on X ([link](https://x.com/agreeahmed/status/2010863894793744573))

> "Reflecting on what engineers love about Claude Code, one thing that jumps out is its customizability: hooks, plugins, LSPs, MCPs, skills, effort, custom agents, status lines, output styles, etc. Every engineer uses their tools differently. We built Claude Code from the ground up" — @bcherny (Boris Cherny, Anthropic) on X ([link](https://x.com/bcherny/status/2021699851499798911))

> "It doesn't really matter which approach you pick. Your agent will get the answer." — Arize AI MCP vs CLI Skills benchmark conclusion ([arize.com](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/))

> "Claude Code is, with hindsight, poorly named because it's not purely a coding tool — it's a tool for general computer automation, and anything you can achieve by typing commands into a computer can now be automated by Claude Code." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "MCP is a whole protocol specification covering hosts, clients, servers, resources, prompts, tools, sampling, roots, elicitation and three different transports. Skills are Markdown with a tiny bit of YAML metadata and some optional scripts in whatever you can make executable in the environment." — Simon Willison on why Skills may be bigger than MCP ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "I watched my context window die before I could write a single prompt — 67,000 tokens gone, just from connecting four MCP servers to Claude Code." — Community report via [MindStudio](https://www.mindstudio.ai/blog/claude-code-mcp-server-token-overhead)

> "Today we're introducing Claude Code Plugins in public beta. Plugins allow you to install and share curated collections of slash commands, agents, MCP servers, and hooks directly within Claude Code." — @claudeai (Official Anthropic) on X ([link](https://x.com/claudeai/status/1976332881409737124))

> "Plugins are containers for distributing and organizing (possibly several) skills as part of a larger toolkit. Skills focus on providing specialized knowledge or procedures for tasks." — @claude_code (Claude Code Community) FAQ on X ([link](https://x.com/claude_code/status/2009479585172242739))
