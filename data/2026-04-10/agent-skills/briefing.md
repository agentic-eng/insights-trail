# Agent Skills & Claude Code Plugin Ecosystem — Daily Briefing
**Date:** 2026-04-10
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 13 posts | 495 likes, 69 reposts | Top post: 212 likes (@NainsiDwiv50980 "Resource Bible") |
| Hacker News | 3 stories | 16 points, 2 comments | /buddy rebuild, LLM Router, Docker leak |
| Web | 35+ pages | — | via raw script (9) + WebSearch supplemental (26+) |

---

## Synthesized Findings

### 1. The Discovery Gap: Most Claude Code Users Are Leaving Power on the Table

The dominant narrative across X this week is a sharp divide between casual Claude Code users and power users who treat it as an operating system. The most-liked post in the dataset (@NainsiDwiv50980, 212 likes) frames a "Claude Code Resource Bible" of 54 tools — agents, MCP servers, skills, and automation — as an edge most people haven't discovered. @Suryanshti777 (52 likes) put it most crisply: *"Most people use Claude Code like a chat. Power users use it like an operating system."* The full capability list — isolated worktrees, multi-agent code reviews, cron-like loops, parallel batch changes, auto-loaded skills, GitHub/Slack/DB connections via MCP, project rules via CLAUDE.md — reads less like a feature list and more like a manifesto for a new computing paradigm.

This framing is echoed across multiple posts and blog guides from the same period. Skillbrew's guide (https://skillbrew.dev/blog/how-to-configure-claude-agent-skills-mcp-servers-rules-and-prompts-explained) calls skills, MCP servers, rules, and prompts the "four pillars" most developers leave untouched. The systemprompt.io architecture guide (https://systemprompt.io/guides/claude-skills-vs-agents-vs-mcp) explicitly maps Skills vs Subagents vs MCP Servers as three distinct extension layers requiring deliberate architectural choices.

Relevant URLs:
- https://x.com/NainsiDwiv50980/status/2041997164155695367
- https://x.com/Suryanshti777/status/2041751972169298326
- https://skillbrew.dev/blog/how-to-configure-claude-agent-skills-mcp-servers-rules-and-prompts-explained
- https://systemprompt.io/guides/claude-skills-vs-agents-vs-mcp
- https://alexop.dev/posts/understanding-claude-code-full-stack/
- https://www.morphllm.com/claude-code-extensions

### 2. Marketplace Proliferation: Dozens of Directories Are Racing to Own Discovery

A wave of skill/plugin directories launched or updated in the last 30 days:

- **claudemarketplaces.com** (https://claudemarketplaces.com/) — community-curated, 150+ skills as of March 2026, just added browse-by-category (frontend, backend, testing, SEO, design, AI & agent building), per @mertduzgun (https://x.com/mertduzgun/status/2042283912643154383).
- **AgentHub** (https://x.com/kranirudha/status/2042506431493214325) — launched April 10 as open-source community plugin marketplace; 299 plugins from 73 authors, installable with a single command, covering skills, agents, hooks, and MCP servers.
- **claude-plugins.dev** (https://claude-plugins.dev/) — community registry with CLI, auto-indexed from GitHub.
- **mcpmarket.com** (https://mcpmarket.com/) — 10,000+ MCP servers across 23+ categories; also hosts https://mcpmarket.com/tools/skills for Claude/ChatGPT/Codex skills.
- **lobehub.com/skills** (https://lobehub.com/skills) — multi-agent skills marketplace spanning Claude, Codex, ChatGPT.
- **glama.ai** (https://glama.ai/mcp/servers) — 21,173 MCP servers indexed as of 2026-04-10 (the largest public catalog found).
- **agenticmarket.dev** (https://agenticmarket.dev/servers) — MCP server registry with submit/browse flow.
- **awesome-agent-skills** (https://x.com/haileyhmt/status/2041637820385608189) — GitHub list hit 3.7k stars with 30+ contributors, now live as a browsable web directory alongside awesome-claude-code, awesome-design-md, awesome-openclaw-skills, and awesome-mcp-servers.

The sheer proliferation of registries is itself the story: there's no single canonical store, and the community is experimenting with which model (curated marketplace, GitHub awesome list, CLI registry, enterprise gateway) will win.

Relevant URLs:
- https://claudemarketplaces.com/
- https://x.com/kranirudha/status/2042506431493214325
- https://x.com/mertduzgun/status/2042283912643154383
- https://claude-plugins.dev/
- https://claude-plugins.dev/skills
- https://mcpmarket.com/
- https://mcpmarket.com/tools/skills
- https://lobehub.com/skills
- https://glama.ai/mcp/servers
- https://agenticmarket.dev/servers
- https://x.com/haileyhmt/status/2041637820385608189
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers
- https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4

### 3. MCP Server Ecosystem Scale: From 1,000 to 21,000+ Servers in ~18 Months

The MCP ecosystem has undergone explosive growth. A 2025 baseline of roughly 1,000 community servers has ballooned to 21,173 indexed on glama.ai alone as of April 10, 2026, with mcpmarket.com cataloging 10,000+ across 23 categories. The official MCP Registry (https://registry.modelcontextprotocol.io/) launched with a v0.1 API freeze in October 2025 and the MCP v2.1 specification introduced Server Cards — structured server metadata via a `.well-known` URL enabling crawlers and registries to discover capabilities without connecting.

GitHub launched its own MCP Registry (https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/) as a discovery hub for GitHub Copilot and any MCP-compatible AI tool. Enterprise solutions have emerged from Kong (https://konghq.com/products/mcp-registry) and the open-source agentic-community/mcp-gateway-registry (https://github.com/agentic-community/mcp-gateway-registry), offering OAuth-authenticated governance with Keycloak/Entra integration. Stacklok's ToolHive Catalog (https://pkg.go.dev/github.com/stacklok/toolhive-catalog, https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) introduced reusable agent skills as a first-class concept alongside MCP servers.

GoReleaser added experimental MCP server registry publishing support (https://goreleaser.com/customization/publish/mcp/), suggesting distribution tooling is maturing toward standard packaging.

The most-recommended power MCPs cited on X: Official MCP Servers, GitHub MCP, Playwright MCP, Figma Context MCP (@aigoldrushh, https://x.com/aigoldrushh/status/2041974531695218956).

Relevant URLs:
- https://registry.modelcontextprotocol.io/
- https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/
- https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/
- https://konghq.com/products/mcp-registry
- https://github.com/agentic-community/mcp-gateway-registry
- https://pkg.go.dev/github.com/stacklok/toolhive-catalog
- https://docs.stacklok.com/toolhive/updates/2026/04/06/updates
- https://goreleaser.com/customization/publish/mcp/
- https://glama.ai/mcp/servers
- https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026
- https://www.truefoundry.com/blog/best-mcp-registries
- https://www.truefoundry.com/blog/what-is-mcp-registry
- https://thenewstack.io/model-context-protocol-roadmap-2026/
- https://dasroot.net/posts/2026/04/model-context-protocol-mcp-technical-deep-dive/
- https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us
- https://x.com/aigoldrushh/status/2041974531695218956
- https://claudefa.st/blog/tools/mcp-extensions/best-addons
- https://aiproductivity.ai/blog/claude-code-mcp-servers/
- https://claudefa.st/blog/tools
- https://machalliance.org/mach-alliance-mcp-registry

### 4. Community Skill Repos: Open-Source Configs Going Mainstream

A notable trend: power users are open-sourcing their full Claude Code configurations. @shih26724 (https://x.com/shih26724/status/2041931642974171343) published their entire `~/.claude/` config — 192 skills, 77 commands, 282 agents, 23 MCP servers — framing it as "a governed AI system that plans, delegates, and ships autonomously." @elCholoCat described a team setup of 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier, and a review gate on every code change, saying: *"claude code is basically a second brain at this point."*

On GitHub, community skill repositories have reached significant scale:
- **jeremylongshore/claude-code-plugins-plus-skills** (https://github.com/jeremylongshore/claude-code-plugins-plus-skills): 340 plugins + 1367 agent skills with CCPI package manager
- **VoltAgent/awesome-agent-skills** (https://github.com/VoltAgent/awesome-agent-skills): 1000+ agent skills, 3.7k stars, compatible with Claude Code, Codex, Antigravity, Gemini CLI, Cursor
- **alirezarezvani/claude-skills** (https://github.com/alirezarezvani/claude-skills): 220+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents
- **anthropics/skills** (https://github.com/anthropics/skills): Official Anthropic public skills repository — demonstrating the range from creative to enterprise workflows
- **quemsah/awesome-claude-plugins** (https://github.com/quemsah/awesome-claude-plugins): Automated n8n-powered tracking of plugin adoption metrics across GitHub repos
- **shinpr/claude-code-workflows** (https://github.com/shinpr/claude-code-workflows): Production-ready multi-agent orchestration workflows

The stormy.ai "2026 Skill Economy" piece (https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills) captures the macro shift: where 2024 entrepreneurs sold "Mega-Prompts," by 2026 those are "low-leverage fossils" — persistent folder-based skill packages are the new commodity.

Relevant URLs:
- https://x.com/shih26724/status/2041931642974171343
- https://x.com/elCholoCat/status/2041581965619404880
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- https://github.com/VoltAgent/awesome-agent-skills
- https://github.com/alirezarezvani/claude-skills
- https://github.com/anthropics/skills
- https://github.com/quemsah/awesome-claude-plugins
- https://github.com/shinpr/claude-code-workflows
- https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills
- https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development
- https://findskill.ai/blog/claude-cowork-guide/

### 5. Security: The MCP Attack Surface Nobody Is Watching

Security is emerging as a friction point in the MCP ecosystem. On X, @alphabatcher (48 likes, https://x.com/alphabatcher/status/2042225554036793578) posted a list of security settings "most Claude Code users never touch" — sandbox mode, credential blocking, .env isolation, disabling auto-loading MCP servers — warning that ignoring these settings can cost "$10k in a single night." The claim is dramatic but signals real concern.

On Hacker News (https://futuresearch.ai/blog/mcp-leaks-docker-containers/), an 8-point story revealed that Claude Code's MCP config can silently orphan Docker containers — a resource leak with operational consequences.

Most alarmingly, @type0press (https://x.com/type0press/status/2041679905545712044) reported that a Chinese state group (GTG-1002) used Claude Code to autonomously run 80-90% of an espionage operation against 30 targets — with humans intervening at only 4-6 decision points per campaign. The warning: *"The 8,000 exposed MCP servers on the internet are the warning sign that most enterprises are not watching."*

A 2026 CData audit found 82% of 2,600+ reviewed MCP servers were vulnerable to path traversal and 67% to code injection — numbers cited in multiple web guides. The feature request at anthropics/claude-code #38253 (https://github.com/anthropics/claude-code/issues/38253) for auto-discovering skills via a `skill://` resource protocol suggests the community is actively thinking about secure, standardized discovery mechanisms.

Relevant URLs:
- https://x.com/alphabatcher/status/2042225554036793578
- https://futuresearch.ai/blog/mcp-leaks-docker-containers/
- https://x.com/type0press/status/2041679905545712044
- https://github.com/anthropics/claude-code/issues/38253
- https://scottspence.com/posts/mcpick-manage-mcp-servers-and-plugins-in-claude-code

### 6. Infrastructure Tooling: Gateways, Routers, and Context Management

Several new tools aim to solve MCP sprawl. On Hacker News, **LLM Router** (https://github.com/ypollak2/llm-router, 4 pts) routes Claude Code tasks to cheaper models — addressing the $200/month Claude Code cost pain that @_vmlops (154 likes, https://x.com/_vmlops/status/2041767186663186483) highlighted by pointing to Goose (Block's free open-source alternative that also supports MCP servers).

@BobEcho89 (https://x.com/BobEcho89/status/2041577028814827635) launched **AAI Gateway** — a single MCP connection that manages all downstream MCP servers and skills, claiming 99% context token savings, natural language search & install, and portability across Claude Code, Codex, and OpenCode. The claude-buddy project (https://github.com/1270011/claude-buddy, HN 4 pts) rebuilt Claude Code's removed `/buddy` companion as a permanent MCP app.

The claudefa.st blog (https://claudefa.st/blog/tools) notes Code Kit v5.0 was released for Claude Code's new Agent Teams feature, and their MCP setup guide promises 6-line, 2-minute configuration. Morph's MCP server (https://www.morphllm.com/claude-code-skills-mcp-plugins) is cited as the most-installed extension with 35% faster edits and 40% reduction in context rot.

Enterprise MCP deployments hit a new milestone: Sysdig's MCP Server is now available on AWS Marketplace (@TakaoShimizu1, https://x.com/TakaoShimizu1/status/2041400277891473599), signaling enterprise-grade validation.

Relevant URLs:
- https://github.com/ypollak2/llm-router
- https://x.com/_vmlops/status/2041767186663186483
- https://x.com/BobEcho89/status/2041577028814827635
- https://github.com/1270011/claude-buddy
- https://x.com/TakaoShimizu1/status/2041400277891473599
- https://www.morphllm.com/claude-code-skills-mcp-plugins
- https://claudefa.st/blog/tools
- https://claudelog.com/claude-code-mcps/reddit-mcp/
- https://releasebot.io/updates/anthropic/claude-code
- https://code.claude.com/docs/en/plugins
- https://github.com/anthropics/claude-code/blob/main/plugins/README.md
- https://www.morphllm.com/claude-code-extensions

---

## Cross-Source Patterns

**Pattern 1: "You're not using it right" — the power user education wave**
- Platforms: X (dominant), Web
- Every major X post this week frames Claude Code skills/MCP as under-discovered. The 212-like "Resource Bible" post, the "operating system vs chat" post, the open-sourced ~/.claude/ config — all share the same hook. Multiple web guides mirror this framing. This is not organic discovery; it's a coordinated education moment with commercial incentive (most posts link to external resources or products).
- Key quote: *"Claude Code isn't just prompting — it's sessions, agents, skills, hooks, MCP servers, and workflows."* — @Suryanshti777

**Pattern 2: Marketplace proliferation without a clear winner**
- Platforms: X, Web
- At least 8 distinct skill/plugin directories are active (claudemarketplaces.com, AgentHub, claude-plugins.dev, mcpmarket.com, lobehub.com, glama.ai, agenticmarket.dev, awesome-agent-skills). The official MCP Registry exists but isn't dominating discovery conversation. No single store has emerged as the App Store equivalent.
- Key quote: *"you can now browse skills, mcp servers, and plugins by what they actually do"* — @mertduzgun on claudemarketplaces.com categories

**Pattern 3: Security as the ignored underside of MCP adoption**
- Platforms: X, Hacker News
- @alphabatcher on X and the HN Docker leak story both surface MCP security gaps. The espionage use case on X and the path traversal audit numbers from Web sources compound into a coherent warning: the ecosystem is growing faster than security practices. Enterprise governance tools (Kong, agentic-community gateway) are the proposed solution.
- Key quote: *"The 8,000 exposed MCP servers on the internet are the warning sign that most enterprises are not watching."* — @type0press

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @NainsiDwiv50980 | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack." | 212 | 31 | https://x.com/NainsiDwiv50980/status/2041997164155695367 |
| @_vmlops | "claude code costs $200/month github copilot costs $19/month jack dorsey's company just said what if it was free? goose is a free, open source ai agent... supports mcp servers." | 154 | 18 | https://x.com/_vmlops/status/2041767186663186483 |
| @alphabatcher | "Security settings most Claude Code users never touch: Enable sandbox, Block credential access, Block .env files separately, Disable outbound commands... Most people ignore all of this and take losses of $10k in a single night" | 48 | 4 | https://x.com/alphabatcher/status/2042225554036793578 |
| @Suryanshti777 | "Most people use Claude Code like a chat. Power users use it like an operating system. This cheatsheet is basically the difference." | 52 | 12 | https://x.com/Suryanshti777/status/2041751972169298326 |
| @haileyhmt | "Grateful for 3.7k stars, multiple citations, and 30+ contributors on awesome-agent-skills, now live as a directory" | 12 | 1 | https://x.com/haileyhmt/status/2041637820385608189 |
| @aigoldrushh | "Claude Code on itself is powerful. But... these MCP's make your advantage absolutely UNFAIR." | 13 | 3 | https://x.com/aigoldrushh/status/2041974531695218956 |
| @mertduzgun | "just added categories to claude code marketplaces — you can now browse skills, mcp servers, and plugins by what they actually do" | 3 | 0 | https://x.com/mertduzgun/status/2042283912643154383 |
| @kranirudha | "Meet AgentHub 🚀 An open source community plugin marketplace for claude code 299 plugins from 73 authors so far and growing..." | 0 | 0 | https://x.com/kranirudha/status/2042506431493214325 |
| @shih26724 | "Stop treating Claude Code like a chatbot. I open-sourced my full ~/.claude/ config: 192 skills · 77 commands · 282 agents · 23 MCP servers" | 0 | 0 | https://x.com/shih26724/status/2041931642974171343 |
| @type0press | "A Chinese state group used Anthropic's Claude Code to run 80-90% of an espionage operation autonomously, hitting 30 targets at machine speed" | 0 | 0 | https://x.com/type0press/status/2041679905545712044 |
| @elCholoCat | "we're running 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier... claude code is basically a second brain at this point" | 0 | 0 | https://x.com/elCholoCat/status/2041581965619404880 |
| @BobEcho89 | "Tired of bloated MCP configs? I built AAI Gateway — one MCP connection to manage all your MCP servers & skills. ✅ 99% context token savings" | 0 | 0 | https://x.com/BobEcho89/status/2041577028814827635 |
| @TakaoShimizu1 | "Sysdig Model Context Protocol (MCP) Server now available on AWS Marketplace" | 1 | 0 | https://x.com/TakaoShimizu1/status/2041400277891473599 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (anon) | I rebuilt Claude Code's removed /buddy companion as a permanent MCP app | 4 | 0 | — | https://github.com/1270011/claude-buddy |
| (anon) | LLM Router – MCP server that routes Claude Code tasks to cheaper models | 4 | 0 | — | https://github.com/ypollak2/llm-router |
| (anon) | Claude Code's MCP config can silently orphan Docker containers | 8 | 2 | — | https://futuresearch.ai/blog/mcp-leaks-docker-containers/ |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Glama | https://glama.ai/mcp/servers | 21,173 MCP servers indexed as of 2026-04-10 — largest public catalog |
| claudefa.st | https://claudefa.st/blog/tools | Code Kit v5.0 for Agent Teams; 6-line MCP setup guide |
| pkg.go.dev (ToolHive) | https://pkg.go.dev/github.com/stacklok/toolhive-catalog | ToolHive Catalog of MCP servers and agent skills (Apache-2.0) |
| GitHub (anthropics/claude-code) | https://github.com/anthropics/claude-code/issues/38253 | Feature request: auto-discover skills from MCP servers via skill:// protocol; 87K repo stars |
| AgenticMarket | https://agenticmarket.dev/servers | MCP server registry with submit/browse flow |
| GoReleaser | https://goreleaser.com/customization/publish/mcp/ | Experimental MCP registry publishing (v2.13+) |
| Skillbrew | https://skillbrew.dev/blog/how-to-configure-claude-agent-skills-mcp-servers-rules-and-prompts-explained | Four-pillar guide: skills, MCP servers, rules, prompts |
| systemprompt.io | https://systemprompt.io/guides/claude-skills-vs-agents-vs-mcp | Runtime architecture guide: Skills vs Subagents vs MCP Servers |
| AI:PRODUCTIVITY | https://aiproductivity.ai/blog/claude-code-mcp-servers/ | Claude Code MCP Servers setup guide 2026 |
| Official MCP Registry | https://registry.modelcontextprotocol.io/ | Canonical registry, v0.1 API freeze (Oct 2025) |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/ | MCP Registry preview announcement |
| GitHub Blog | https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/ | GitHub MCP Registry launch |
| Kong | https://konghq.com/products/mcp-registry | Enterprise MCP Registry with governance |
| agentic-community | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth/Keycloak |
| StackLok Docs | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | ToolHive agent skills: reusable instruction bundles |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | MCP Registry comparison; Smithery = Docker Hub equivalent with 7K servers |
| TrueFoundry | https://www.truefoundry.com/blog/what-is-mcp-registry | What is MCP Registry architecture guide |
| The New Stack | https://thenewstack.io/model-context-protocol-roadmap-2026/ | MCP v2.1 Server Cards spec; production-readiness roadmap |
| dasroot.net | https://dasroot.net/posts/2026/04/model-context-protocol-mcp-technical-deep-dive/ | MCP technical deep dive |
| Context Studios | https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us | MCP v1.27 release analysis |
| jeremylongshore (GitHub) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 agent skills; CCPI package manager |
| VoltAgent (GitHub) | https://github.com/VoltAgent/awesome-agent-skills | 1000+ agent skills; 3.7k stars; multi-agent compatible |
| alirezarezvani (GitHub) | https://github.com/alirezarezvani/claude-skills | 220+ Claude Code skills for 10+ coding agents |
| anthropics/skills (GitHub) | https://github.com/anthropics/skills | Official Anthropic Agent Skills public repo |
| claude-plugins.dev | https://claude-plugins.dev/ | Community registry with CLI; auto-indexed from GitHub |
| claude-plugins.dev | https://claude-plugins.dev/skills | Skills discovery directory |
| DEV Community | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best Claude Code Skills & Plugins 2026 guide |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Claude Code full stack: MCP, Skills, Subagents, Hooks explained |
| Morph | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins guide; Morph = most-installed extension |
| Morph | https://www.morphllm.com/claude-code-extensions | Extensions guide 2026 |
| Scott Spence | https://scottspence.com/posts/mcpick-manage-mcp-servers-and-plugins-in-claude-code | McPick: MCP management tool |
| Stormy AI | https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills | 2026 Skill Economy: from prompts to persistent MCP skills |
| Releasebot | https://releasebot.io/updates/anthropic/claude-code | Claude Code April 2026 release notes |
| MCP Market | https://mcpmarket.com/ | 10,000+ MCP servers; 23 categories |
| MCP Market Skills | https://mcpmarket.com/tools/skills | Agent skills directory |
| LobeHub | https://lobehub.com/skills | Multi-agent skills marketplace |
| TurboDocx | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best skills/plugins/MCP guide |
| ClaudeFA.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP Servers for Claude Code |
| FindSkill.ai | https://findskill.ai/blog/claude-cowork-guide/ | Claude Cowork Guide 2026 |
| BrightCoding | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | 270+ AI Agent Tools overview |
| MACH Alliance | https://machalliance.org/mach-alliance-mcp-registry | MACH Alliance MCP Registry |
| MCPMarket Daily | https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026 | Top MCP Servers March 4, 2026 |
| quemsah (GitHub) | https://github.com/quemsah/awesome-claude-plugins | Plugin adoption metrics via n8n |
| shinpr (GitHub) | https://github.com/shinpr/claude-code-workflows | Production-ready Claude Code workflows |
| ClaudeLog | https://claudelog.com/claude-code-mcps/reddit-mcp/ | Claude Code MCP guides |
| Official Docs | https://code.claude.com/docs/en/plugins | Claude Code plugin documentation |

---

## Stats Block

```
├─ 🔵 X: 13 posts │ 495 likes │ 69 reposts
├─ 🟡 HN: 3 stories │ 16 points │ 2 comments
├─ 🌐 Web: 46 pages — Glama, MCP Market, TrueFoundry, The New Stack, GitHub Blog, Morph, claudefa.st, Stormy AI, ToolHive, Context Studios
└─ 🗣️ Top voices: @NainsiDwiv50980 (212 likes), @_vmlops (154 likes), @Suryanshti777 (52 likes), @alphabatcher (48 likes)
```

---

## Data Gaps

- **Reddit: 0 posts** — All subreddit searches (r/ClaudeAI, r/anthropic, r/MachineLearning, r/artificial, r/LocalLLaMA) returned HTTP 402 or 403 errors. Reddit is rate-limited/paywalled in this environment. This is a significant gap: r/ClaudeAI and r/LocalLLaMA likely have active threads on MCP setup and skill sharing.
- **YouTube: 0 videos** — yt-dlp returned 0 results for all topic variants. Tutorial content on Claude Code MCP setup is almost certainly active on YouTube but not captured here.
- **TikTok/Instagram: 0** — SC API returned HTTP 402. Likely low relevance for this technical topic regardless.
- **Bluesky/Polymarket: 0** — Not configured / no relevant prediction markets found.
- **X coverage is thin** — 13 posts with heavy concentration in power-user tutorial threads. Missing: developer complaints, enterprise adoption discussions, pricing debates beyond the Goose comparison.
- **Estimated coverage:** ~40% of total discourse (good Web/X signal, missing Reddit/YouTube which are the highest-signal communities for this topic).
- **Noise:** The "Resource Bible" / "most people don't know this" X post pattern is semi-viral marketing; some posts link to affiliate or commercial products (morphllm.com, claudefa.st).

---

## Key Quotes

> "Most people use Claude Code like a chat. Power users use it like an operating system. This cheatsheet is basically the difference." — @Suryanshti777 on X ([link](https://x.com/Suryanshti777/status/2041751972169298326))

> "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack. That's your edge." — @NainsiDwiv50980 on X ([link](https://x.com/NainsiDwiv50980/status/2041997164155695367))

> "claude code is basically a second brain at this point" — @elCholoCat on X ([link](https://x.com/elCholoCat/status/2041581965619404880))

> "The 8,000 exposed MCP servers on the internet are the warning sign that most enterprises are not watching." — @type0press on X ([link](https://x.com/type0press/status/2041679905545712044))

> "Tired of bloated MCP configs? I built AAI Gateway — one MCP connection to manage all your MCP servers & skills. ✅ 99% context token savings" — @BobEcho89 on X ([link](https://x.com/BobEcho89/status/2041577028814827635))

> "Stop treating Claude Code like a chatbot. I open-sourced my full ~/.claude/ config: 192 skills · 77 commands · 282 agents · 23 MCP servers" — @shih26724 on X ([link](https://x.com/shih26724/status/2041931642974171343))

> "Grateful for 3.7k stars, multiple citations, and 30+ contributors on awesome-agent-skills, now live as a directory" — @haileyhmt on X ([link](https://x.com/haileyhmt/status/2041637820385608189))

> "Claude Code on itself is powerful. But... these MCP's make your advantage absolutely UNFAIR." — @aigoldrushh on X ([link](https://x.com/aigoldrushh/status/2041974531695218956))
