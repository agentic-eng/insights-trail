# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-05
**Query type:** GENERAL
**Sources:** Hacker News, Web, YouTube, GitHub, TikTok, Reddit (blocked)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 12 stories | ~hundreds of points, hundreds of comments | Skills vs. MCP debate threads highly active Oct–Nov 2025 onward |
| YouTube | 8+ videos | N/A (counts not retrieved) | Dedicated "Claude Code Skills" playlist; "I Tried 100+ Claude Code Skills" posted ~May 3 |
| Web | 60+ pages | — | Official docs, blogs, news, marketplace sites |
| GitHub | 10+ repos | 5,200+ stars (top repo) | Multiple "awesome-agent-skills" collections; official Anthropic + Vercel + Microsoft repos |
| TikTok | 1 video confirmed | N/A | @taki.gpt on 60 Claude skills |
| Reddit | 0 | — | reddit.com blocked by Anthropic web agent; no data retrieved |
| X/Twitter | 0 direct | — | x.com blocked; cross-referenced via HN/Techmeme/Mastodon |
| Bluesky | 0 direct | — | No direct Bluesky data retrieved; Simon Willison on Mastodon (@simon@fedi.simonwillison.net) |
| Polymarket | 0 markets on topic | — | No prediction markets specifically on agent skill ecosystems found; Polymarket MCP servers documented |

---

## Synthesized Findings

### 1. The Skills-vs-MCP Debate Defines the Era

The most-discussed thread in the agent skills space since late 2025 is a simple question: **do you need MCP at all?** Simon Willison (co-creator of Django) lit the match in October 2025 with a blog post titled "Claude Skills are awesome, maybe a bigger deal than MCP" ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/), [Substack](https://simonw.substack.com/p/claude-skills-are-awesome-maybe-a-bigger-deal-than-mcp), [Techmeme](https://www.techmeme.com/251017/p14)). The argument: MCP's biggest practical limitation is token cost — GitHub's official MCP famously consumes tens of thousands of context tokens before any useful work happens. A SKILL.md file, by contrast, is just structured Markdown — same information, orders of magnitude cheaper.

The HN threads ([45607117](https://news.ycombinator.com/item?id=45607117), [45619537](https://news.ycombinator.com/item?id=45619537), [45766686](https://news.ycombinator.com/item?id=45766686)) remained active for weeks. By early 2026, parallel threads formed a spectrum: "You don't need MCP. You need Claude Skills." ([HN 45948490](https://news.ycombinator.com/item?id=45948490)) vs. "Why I Choose MCP Over Skills in 2026" ([Medium](https://medium.com/ai-ai-oh/why-i-choose-mcp-over-skills-in-2026-045207aadfed)) vs. the now-dominant hybrid view.

Arize AI ran the definitive empirical test: Claude Opus 4.6 on GitHub tasks via the Claude Agent SDK, testing official GitHub MCP vs. two skills (LobeHub and Vault). Correctness was nearly identical — LobeHub 0.826, Vault 0.833, MCP 0.834. Their takeaway: task accuracy doesn't differ. The practical differentiator is **context window economics**, not quality. ([Arize AI blog](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/))

The hybrid view — "MCP is the nervous system, skills are the playbooks" — is now the consensus among practitioners, as documented in Analytics Vidhya ([April 2026](https://www.analyticsvidhya.com/blog/2026/04/mcp-vs-agent-skills/)), Milvus Blog ([Is MCP Dead?](https://milvus.io/blog/is-mcp-dead-cli-and-skills-for-ai-agents.md)), and the official MCP docs ([modelcontextprotocol.io/docs/develop/build-with-agent-skills](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills)).

**Cross-platform:** HN, Web (blogs), Mastodon/X (Willison), Lobsters, HackerNoon

---

### 2. The Three-Layer Extension Model: Skills vs. Plugins vs. MCP Servers

The ecosystem has consolidated around a clear taxonomy ([Nevo Systems](https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp)):

- **MCP Servers** — tool access layer; client-agnostic "USB-C for AI"; one server works with Claude Code, Cursor, Windsurf, VS Code, and any compliant host
- **Skills** (`SKILL.md` files) — prompt-based instruction layer; teach Claude *how* and *when* to use tools; filesystem-based with progressive disclosure; universal format that works across Claude Code, Cursor, Gemini CLI, Codex CLI, and Antigravity IDE
- **Plugins** — bundled packages combining skills + MCP servers + hooks + sub-agents; a deployment plugin, for example, bundles the cloud MCP connection, the deployment skill, pre-deploy hooks, and a rollback sub-agent

Official Claude Code docs: [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills), [code.claude.com/docs/en/mcp](https://code.claude.com/docs/en/mcp), [code.claude.com/docs/en/discover-plugins](https://code.claude.com/docs/en/discover-plugins)

Anthropic's official blog: [Extending Claude's capabilities with skills and MCP servers](https://claude.com/blog/extending-claude-capabilities-with-skills-mcp-servers)

**Cross-platform:** Web (official docs, blogs), HN, YouTube tutorials

---

### 3. GitHub's `gh skill` Command Standardizes Distribution (April 16, 2026)

The single biggest distribution event in the last 30 days: GitHub launched the `gh skill` command in GitHub CLI v2.90.0 ([GitHub Changelog, April 16](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/)). It treats agent skills like npm packages — `search`, `install`, `pin`, `preview`, `update`, `publish` as first-class verbs. Works across GitHub Copilot, Claude Code, Cursor, Codex, and Gemini CLI. Skills install to the correct directory per agent host automatically. SKILL.md frontmatter embeds provenance tracking (repository, ref, tree SHA) so origin travels with the skill file.

Security caveat: skills are **not verified by GitHub** and may contain prompt injections or malicious scripts. `gh skill preview` is strongly recommended before install. ([Syntax Diaries](https://thesyntaxdiaries.com/gh-skill-github-cli-agent-skills-security))

Related HN discussion: [feat: gh skill CLI, v2.90.0+](https://github.com/anthropics/claude-code/issues/50148). Community coverage: [Mervin Praison](https://mer.vin/2026/04/gh-skill-install-pin-and-publish-agent-skills-from-github-repos/), [DEV Community](https://dev.to/om_shree_0709/gh-skill-githubs-new-cli-command-turns-agent-skills-into-installable-packages-2p82), [Groundy](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor-and-gemini/), [Big Hat Group](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/)

**Cross-platform:** Web, GitHub, HN

---

### 4. MCP Protocol Goes Production-Scale: 9,400+ Servers, 97M Downloads/Month

Adoption numbers are striking ([Digital Applied](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol), [MCP Manager](https://mcpmanager.ai/blog/mcp-adoption-statistics/)):
- **9,400+ public MCP servers** as of April 2026 (from 1,200 in Q1 2025) — 7.8x YoY
- **17,468 total MCP servers** across registries per independent Nerq census (Q1 2026)
- **97 million monthly SDK downloads** by March 2026 (from 100K at launch = 970x in 18 months)
- **41%** of enterprise AI teams have at least one custom internal MCP server not in any public registry
- Only **12.9%** of public MCP servers score "high trust" (docs, maintenance, reliability)
- MoM growth still +18% in Q1 2026 despite QoQ deceleration from +100% to +38%

MCP was donated to the Linux Foundation's Agentic AI Foundation in December 2025, cementing its status as a neutral standard. ([CData blog](https://www.cdata.com/blog/2026-year-enterprise-ready-mcp-adoption))

2026 roadmap focuses shift: from proving the standard to making it **production-reliable**. ([Ted Tschopp](https://tedt.org/MCPs-2026-Roadmap/))

LSEG lifted guidance citing MCP adoption in Q1 2026: [resultsense.com](https://www.resultsense.com/news/2026-04-23-lseg-q1-guidance-ai-mcp-growth)

**Cross-platform:** Web, HN, GitHub

---

### 5. Enterprise Registries and Governance Race (AWS, LiteLLM, Anthropic Cowork)

Three major enterprise governance moves in April 2026:

**AWS Agent Registry** launched in public preview April 13, 2026 ([AWS announcement](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/), [AWS ML blog](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/), [InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/), [DEV Community](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91)). It's a private, governed catalog for agents, tools, MCP servers, and skills via Amazon Bedrock AgentCore. Key features: hybrid semantic+keyword search ("payment processing" finds "billing"), approval workflows, IAM + OAuth auth, accessible as an MCP server from IDEs. Available in 5 AWS Regions.

**LiteLLM AI Gateway** acts as a central plugin registry for enterprises: admins govern which Claude Code plugins are available org-wide; engineers discover and install approved plugins from a single source. ([LiteLLM docs](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace))

**Claude Cowork** reached "true enterprise-grade product" status by February 24, 2026 (research preview January 30). Provides per-user provisioning, MCP connector controls, private plugin marketplace, company branding. Opened to third-party platforms in April 2026. ([ALM Corp guide](https://almcorp.com/blog/claude-cowork-plugins-enterprise-guide/))

**ToolHive** (Stacklok) added full agent skills lifecycle management in April 2026: install from ToolHive Registry, OCI registries, or Git repos; publish versioned skills with namespace isolation using reverse-DNS notation. ([Stacklok docs](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates))

**Cross-platform:** Web, AWS, GitHub

---

### 6. Anthropic's Official Plugin Ecosystem: 4,200+ Skills, 770+ MCPs, 2,500+ Marketplaces

The Anthropic-adjacent plugin directory has scaled dramatically. As of May 4, 2026 ([claudemarketplaces.com](https://claudemarketplaces.com/)):
- **4,200+ skills**, **770+ MCP servers**, **2,500+ marketplaces** catalogued

Anthropic maintains two official GitHub repositories:
- [anthropics/skills](https://github.com/anthropics/skills) — public Agent Skills repo, each skill self-contained in its own folder with SKILL.md
- [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) — 13 official plugins (agent-sdk-dev, code-review, commit-commands, feature-dev, frontend-design, etc.)

Plugin architecture spec: [DeepWiki on Plugin Marketplace & Discovery](https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery). Installation guide: [systemprompt.io](https://systemprompt.io/guides/getting-started-anthropic-marketplace).

In December 2025, Anthropic released the Agent Skills specification as an open standard; OpenAI adopted the same SKILL.md format for Codex CLI and ChatGPT ([Augment Code](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities)).

**Cross-platform:** Web, GitHub, HN

---

### 7. Skill Discovery Infrastructure: Marketplaces Proliferate, Quality Varies

The agent skills marketplace landscape grew from 1 registry (December 2025) to 8 major marketplaces by Q2 2026, creating discovery fragmentation. Key players ([Agensi comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)):

- **Skills.sh** — install-count leader (Remotion skill: 126,000+ installs, #4 globally, #1 most popular skill)
- **MCP Market** ([mcpmarket.com](https://mcpmarket.com/)) — MCP servers + skills, including Polymarket integration
- **ClaudeSkills.info** — Claude-specific directory, tutorials ([claudeskills.cc/tutorials](https://claudeskills.cc/tutorials))
- **PulseMCP** ([pulsemcp.com](https://www.pulsemcp.com/servers/mrsimpson-agent-skills)) — MCP server discovery
- **SkillsMP** ([skillsmp.com](https://skillsmp.com/)) — Claude, Codex, ChatGPT skills
- **MCPServers.org** ([mcpservers.org/agent-skills](https://mcpservers.org/agent-skills)) — agent skills library
- **ExplainX.ai** ([explainx.ai/skills](https://explainx.ai/skills/robonet-tech/skills/trade-prediction-markets)) — skills catalog with agent-specific listings

**K-Dense-AI/claude-skills-mcp** ([GitHub](https://github.com/K-Dense-AI/claude-skills-mcp)) enables vector-search-based skill discovery through an MCP server — agents can find and retrieve skills semantically.

Community curation repos:
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) — 1,000+ multi-agent compatible skills
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) — 5,200+ stars, 232+ skills
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
- [heilcheng/awesome-agent-skills](https://github.com/heilcheng/awesome-agent-skills)
- [skillmatic-ai/awesome-agent-skills](https://github.com/skillmatic-ai/awesome-agent-skills)
- [muratcankoylan/Agent-Skills-for-Context-Engineering](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering)

**Cross-platform:** Web, GitHub, HN

---

### 8. Skills Over MCP Working Group Formalizes the Standard

The "Skills Over MCP" interest group within the Model Context Protocol community formalizes how agent skills are discovered, distributed, and consumed through MCP. Their charter: [modelcontextprotocol.io/community/skills-over-mcp/charter](https://modelcontextprotocol.io/community/skills-over-mcp/charter). April 14, 2026 office hours notes: [GitHub Discussions #2585](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585).

The MCP Gateway Registry ([agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)) is an enterprise-ready MCP Gateway and Registry with OAuth, dynamic tool discovery, and unified access — addressing the chaos of scattered MCP deployments.

Related: Agent Monetization — Agent37 ([HN 46422134](https://news.ycombinator.com/item?id=46422134)) lets creators monetize Claude skills with shareable links, addressing friction in selling skills with 1,000+ now on GitHub.

**Cross-platform:** Web, GitHub, HN

---

### 9. Multi-Agent Orchestration and Sub-Agents Scale Up

Claude Code introduced specialized sub-agents ([HN 44686726](https://news.ycombinator.com/item?id=44686726)) — separate contexts that handle specific tasks, solving context exhaustion and improving accuracy. The Claude Code MCP Tool Search feature uses lazy loading to reduce context usage by **up to 95%** ([claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons)).

Some developers run 24 simultaneous Claude Code agents on local hardware ([HN 47099597](https://news.ycombinator.com/item?id=47099597)). Roundtable MCP orchestrates Claude Code, Cursor, Gemini, and Codex simultaneously with zero config ([HN 45374908](https://news.ycombinator.com/item?id=45374908)).

Remote MCP support landed in Claude Code ([HN 44312363](https://news.ycombinator.com/item?id=44312363)), and Claude Code can run as a one-shot MCP server itself ([steipete/claude-code-mcp](https://github.com/steipete/claude-code-mcp)), enabling agent-in-agent architectures. Sub-agents can be exposed to any MCP-compatible tool ([DEV Community](https://dev.to/shinpr/bringing-claude-codes-sub-agents-to-any-mcp-compatible-tool-1hb9)).

Anthropic blog: [Building agents that reach production systems with MCP](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp)

**Cross-platform:** HN, Web, GitHub

---

### 10. The Video/Tutorial Economy Around Claude Code Skills

YouTube has become the primary education channel for Claude Code skills. Recent standouts:
- **"I Tried 100+ Claude Code Skills. These 6 Are The Best"** — posted ~May 3, 2026 ([YouTube](https://www.youtube.com/watch?v=eRS3CmvrOvA))
- **"Full Claude Skills Tutorial for Beginners in 2026! (Become a PRO)"** — March 14, 2026 ([YouTube](https://www.youtube.com/watch?v=YkpEX_jlb04))
- **"FULL Claude Code Tutorial for Beginners in 2026!"** — March 29, 2026 ([YouTube](https://www.youtube.com/watch?v=qYqIhX9hTQk))
- **"The ONLY Claude Code Tutorial You'll Ever Need in 2026"** — March 2, 2026 ([YouTube](https://www.youtube.com/watch?v=LlFgLsffbBs))
- **Claude Code Skills playlist** ([YouTube playlist](https://www.youtube.com/playlist?list=PLmWCw1CzcFim_hkruZSlABOUOAAQ5JMyo))
- **Claude Certified Architect: Ep 08 | MCP Servers, Config, Cline** ([YouTube](https://www.youtube.com/watch?v=IVUxGTxSuH8))
- Anthropic's official course: [Claude Code in Action — Anthropic SkillJar](https://anthropic.skilljar.com/claude-code-in-action)

TikTok: @taki.gpt posted a viral-format video about "60 Claude skills on GitHub" for AI employees across roles ([TikTok](https://www.tiktok.com/@taki.gpt/video/7611210505222360321)) — hashtags: `#claudeai #aiautomation #productivityhacks #aiagents #claudeskills`

Medium tutorials: [10 Must-Have Skills for Claude (and Any Coding Agent) in 2026 — @unicodeveloper](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051)

**Cross-platform:** YouTube, TikTok, Web

---

### 11. Specialized MCP Servers Push Niche Integrations

Tooling highlights from the last 30 days:
- **Almanac MCP** — turns Claude Code into a deep research agent ([HN 47855284](https://news.ycombinator.com/item?id=47855284))
- **Tengu MCP** — 80 tools, 20 resources, 35 prompts for pentesting workflows ([HN 47296367](https://news.ycombinator.com/item?id=47296367))
- **Claude Code History UI + MCP** — analyze past sessions with AI summarization, no lost ideas ([HN 46500801](https://news.ycombinator.com/item?id=46500801))
- **Google `gws` CLI** — launched March 2026; dynamically discovers all Google Workspace APIs via Discovery Service with a built-in MCP server ([cra.mr](https://cra.mr/mcp-skills-and-agents/))
- **Polymarket MCP servers** — 29–45 tools covering Market Discovery, Trading Engine, Market Analysis, Portfolio Manager ([mcpmarket.com](https://mcpmarket.com/server/polymarket-4), [caiovicentino/polymarket-mcp-server](https://github.com/caiovicentino/polymarket-mcp-server))
- **MCP to .dxt conversion** for Claude Code ([HN 44428498](https://news.ycombinator.com/item?id=44428498))
- **Agnix** — lints AI agent configs: Claude.md, skills, MCP, hooks ([HN 46983879](https://news.ycombinator.com/item?id=46983879))

50+ Best MCP Servers for Claude Code list: [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons)

**Cross-platform:** HN, Web, GitHub

---

## Cross-Source Patterns

**Pattern 1: Skills are winning mindshare; MCP is winning infrastructure**
- Appeared on: HN, Web (blogs), Mastodon/X (Willison), Lobsters
- The discourse peaked Oct–Nov 2025 with Willison's post and hasn't stopped. Task accuracy evals show parity (Arize: 0.826–0.834). The real battle is token economics. The practical resolution: use skills for workflow knowledge, MCP for live tool calls.
- Key quotes:
  > "Skills are conceptually extremely simple: a skill is a Markdown file telling the model how to do something." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))
  > "The most successful AI architects in 2026 are using the hybrid approach: MCP gives the agent a standardized nervous system; Skills give it mental playbooks." — [analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2026/04/mcp-vs-agent-skills/)

**Pattern 2: Cross-agent skill portability is now table stakes**
- Appeared on: Web (official docs, blogs), GitHub, YouTube, TikTok
- The same SKILL.md works across Claude Code, Cursor, Gemini CLI, Codex CLI, GitHub Copilot, and Antigravity IDE. GitHub's `gh skill` command (April 16, 2026) is the institutional lock-in for this standard. OpenAI adopted it for Codex CLI and ChatGPT in December 2025.
- Key quote:
  > "One standard to rule Claude Code, Copilot, Cursor, and Gemini." — [Groundy](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor-and-gemini/)

**Pattern 3: Enterprise governance is the new battleground**
- Appeared on: Web (AWS, LiteLLM, Anthropic), HN, GitHub
- AWS Agent Registry, LiteLLM Gateway, Anthropic Claude Cowork all launched enterprise-grade control planes for agent skills and MCP servers within 90 days of each other. 41% of enterprise teams have internal MCP servers not in any public registry — the governance gap is real.
- Key quote:
  > "AWS Agent Registry: a private catalog to stop agent sprawl." — [DEV Community](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91)

**Pattern 4: Discovery fragmentation is now the #1 developer pain point**
- Appeared on: HN, Web (marketplaces), GitHub, TikTok
- 8 major marketplaces by Q2 2026, with developers "spending more time comparing marketplaces than finding skills." Skills.sh, MCP Market, ClaudeSkills.info, SkillsMP, and PulseMCP all compete. GitHub's `gh skill search` is an attempt to consolidate.
- Key quote:
  > "The agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. This growth created an obvious problem: developers now spend more time comparing marketplaces than they spend finding skills." — [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)

**Pattern 5: MCP quality problem — only 12.9% score "high trust"**
- Appeared on: Web (statistics/reports), HN (security context), GitHub
- With 17,468 servers indexed independently and only 12.9% meeting quality thresholds, the ecosystem has a quality-over-quantity problem. Security issues surface repeatedly: `gh skill` adds a prompt-injection warning; Agnix lints agent configs for issues.
- Key quote:
  > "Only 12.9% of MCP servers score 'high trust' (70 or above out of 100), meeting quality thresholds for documentation, maintenance, and reliability." — [digitalapplied.com](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (simonw) | Claude Skills are awesome, maybe a bigger deal than MCP | high | many | "Skills are conceptually extremely simple" | [45619537](https://news.ycombinator.com/item?id=45619537) |
| (simonw) | Claude Skills | high | many | Original announcement discussion | [45607117](https://news.ycombinator.com/item?id=45607117) |
| — | Claude Skills vs. MCP: Complementary Philosophies | — | — | Skills + MCP work together | [45766686](https://news.ycombinator.com/item?id=45766686) |
| — | You don't need MCP. You need Claude Skills. | — | — | Strong anti-MCP position | [45948490](https://news.ycombinator.com/item?id=45948490) |
| — | I definitely see the value of Claude Skills (over MCP) | — | — | Skills versatility | [46038842](https://news.ycombinator.com/item?id=46038842) |
| — | Agent Skills – Open Trusted Catalog (Claude, OpenAI, Vercel, GH) | — | — | Multi-provider catalog (Jan 20, 2026) | [46692865](https://news.ycombinator.com/item?id=46692865) |
| — | Show HN: Agent37 – Monetize your Claude skills | — | — | 1,000+ skills on GitHub | [46422134](https://news.ycombinator.com/item?id=46422134) |
| — | Show HN: Agnix – lint your AI agent configs | — | — | Agent Skills spec requires kebab-case | [46983879](https://news.ycombinator.com/item?id=46983879) |
| — | Skills Manager – manage AI agent skills across Claude, Cursor, Copilot | — | — | Unified skill management (Mar 20, 2026) | [47423910](https://news.ycombinator.com/item?id=47423910) |
| — | Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex | — | — | Zero-config multi-agent orchestration | [45374908](https://news.ycombinator.com/item?id=45374908) |
| — | 24 Simultaneous Claude Code agents on local hardware | — | — | Local agent scale | [47099597](https://news.ycombinator.com/item?id=47099597) |
| — | Claude Code SDK | — | — | SDK release | [44032777](https://news.ycombinator.com/item?id=44032777) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | I Tried 100+ Claude Code Skills. These 6 Are The Best | N/A | N/A | No | [eRS3CmvrOvA](https://www.youtube.com/watch?v=eRS3CmvrOvA) |
| — | Full Claude Skills Tutorial for Beginners in 2026! (Become a PRO) | N/A | N/A | No | [YkpEX_jlb04](https://www.youtube.com/watch?v=YkpEX_jlb04) |
| — | FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step) | N/A | N/A | No | [qYqIhX9hTQk](https://www.youtube.com/watch?v=qYqIhX9hTQk) |
| — | The ONLY Claude Code Tutorial You'll Ever Need in 2026 | N/A | N/A | No | [LlFgLsffbBs](https://www.youtube.com/watch?v=LlFgLsffbBs) |
| — | FULL Claude Tutorial For Beginners in 2026! (FULL COURSE) | N/A | N/A | No | [Xg55nTrbYYY](https://www.youtube.com/watch?v=Xg55nTrbYYY) |
| — | The ONLY Claude Tutorial You'll Ever Need in 2026 | N/A | N/A | No | [WqoPkZ88f5k](https://www.youtube.com/watch?v=WqoPkZ88f5k) |
| — | Claude Code Skills (playlist) | N/A | N/A | No | [playlist](https://www.youtube.com/playlist?list=PLmWCw1CzcFim_hkruZSlABOUOAAQ5JMyo) |
| — | Claude Certified Architect Ep 08 | MCP Servers, Config, Cline | N/A | N/A | No | [IVUxGTxSuH8](https://www.youtube.com/watch?v=IVUxGTxSuH8) |

**TikTok:**
| Creator | Caption Snippet | Views | Likes | URL |
|---------|----------------|-------|-------|-----|
| @taki.gpt | "60 Claude skills on GitHub allows you to build AI employees that can handle marketing, data analysis, product management, programming and even C level advisors inside of Claude" | N/A | N/A | [tiktok.com/@taki.gpt/video/7611210505222360321](https://www.tiktok.com/@taki.gpt/video/7611210505222360321) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Simon Willison's Weblog | [simonwillison.net/2025/Oct/16/claude-skills](https://simonwillison.net/2025/Oct/16/claude-skills/) | Original "bigger deal than MCP" argument; sparked the major discourse |
| Simon Willison Substack | [simonw.substack.com](https://simonw.substack.com/p/claude-skills-are-awesome-maybe-a) | Newsletter version with comments thread |
| Techmeme | [techmeme.com/251017/p14](https://www.techmeme.com/251017/p14) | Aggregator coverage confirming broad reach |
| Arize AI | [arize.com/blog/mcp-vs-cli-skills](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/) | Empirical eval: correctness 0.826–0.834 across approaches |
| Analytics Vidhya | [analyticsvidhya.com/blog/2026/04/mcp-vs-agent-skills](https://www.analyticsvidhya.com/blog/2026/04/mcp-vs-agent-skills/) | Hybrid approach: MCP + Skills = complete agent |
| Nevo Systems | [nevo.systems skills-vs-plugins](https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp) | Three-layer taxonomy (Skills / Plugins / MCPs) |
| Nevo Systems | [nevo.systems what-are-agent-plugins](https://nevo.systems/blogs/nevo-journal/what-are-ai-agent-plugins) | Plugin definition and architecture |
| Digital Applied | [digitalapplied.com/blog/mcp-adoption-statistics](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol) | 9,400+ servers, 97M monthly downloads, 12.9% high trust |
| Digital Applied (forecast) | [digitalapplied.com/blog/mcp-adoption-wave](https://www.digitalapplied.com/blog/mcp-adoption-wave-6-month-forecast-q2-q3-2026) | Q2-Q3 2026 forecast: 25,000+ servers by April 2027 |
| MCP Manager | [mcpmanager.ai/blog/mcp-adoption-statistics](https://mcpmanager.ai/blog/mcp-adoption-statistics/) | Adoption stats corroboration |
| Ted Tschopp | [tedt.org/MCPs-2026-Roadmap](https://tedt.org/MCPs-2026-Roadmap/) | MCP 2026 roadmap: shifting to production reliability |
| AWS (announcement) | [aws.amazon.com/about-aws/whats-new/agent-registry](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | Agent Registry launch April 13, 2026 |
| AWS ML Blog | [aws.amazon.com/blogs/machine-learning/agent-registry](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/) | Agent Registry deep dive |
| InfoQ | [infoq.com/news/2026/04/aws-agent-registry](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | Enterprise governance context for AWS registry |
| DEV (AWS) | [dev.to/aws-builders/agent-registry](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91) | "Stop agent sprawl" framing |
| DevelopersIO | [dev.classmethod.jp/en/articles/aws-agent-registry-preview](https://dev.classmethod.jp/en/articles/aws-agent-registry-preview/) | AWS registry walkthrough |
| LiteLLM | [docs.litellm.ai/tutorials/claude_code_plugin_marketplace](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) | Enterprise plugin governance via LiteLLM |
| ALM Corp | [almcorp.com/blog/claude-cowork-plugins](https://almcorp.com/blog/claude-cowork-plugins-enterprise-guide/) | Claude Cowork enterprise plugins guide |
| Stacklok ToolHive | [docs.stacklok.com/toolhive/updates/2026/04/06](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) | Reusable agent skills lifecycle in ToolHive |
| GitHub Changelog | [github.blog/changelog/2026-04-16-manage-agent-skills](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) | `gh skill` command launch |
| Mervin Praison | [mer.vin/2026/04/gh-skill](https://mer.vin/2026/04/gh-skill-install-pin-and-publish-agent-skills-from-github-repos/) | `gh skill` walkthrough |
| DEV Community | [dev.to/om_shree_0709/gh-skill](https://dev.to/om_shree_0709/gh-skill-githubs-new-cli-command-turns-agent-skills-into-installable-packages-2p82) | gh skill as npm for agent skills |
| Groundy | [groundy.com/articles/github-clis-gh-skill](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor-and-gemini/) | Cross-agent portability coverage |
| Big Hat Group | [bighatgroup.com/blog/gh-skill](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/) | `gh skill` management guide |
| Syntax Diaries | [thesyntaxdiaries.com/gh-skill-security](https://thesyntaxdiaries.com/gh-skill-github-cli-agent-skills-security) | Security risks of unverified skills |
| Azukiazusa | [azukiazusa.dev/en/blog/gh-agent-skill-management](https://azukiazusa.dev/en/blog/gh-agent-skill-management/) | gh skill distribution overview |
| Agensi | [agensi.io/learn/best-ai-agent-skills-marketplaces-2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Marketplace comparison; fragmentation analysis |
| Firecrawl | [firecrawl.dev/blog/best-mcp-servers-for-developers](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | Top MCP servers for developers |
| Firecrawl | [firecrawl.dev/blog/mcp-vs-cli](https://www.firecrawl.dev/blog/mcp-vs-cli) | MCP vs CLI for AI agents |
| Milvus Blog | [milvus.io/blog/is-mcp-dead](https://milvus.io/blog/is-mcp-dead-cli-and-skills-for-ai-agents.md) | "Is MCP Dead?" — CLI vs skills comparison |
| Jannik Reinhard | [jannikreinhard.com/2026/02/22/why-cli-tools-are-beating-mcp](https://jannikreinhard.com/2026/02/22/why-cli-tools-are-beating-mcp-for-ai-agents/) | CLI tools beating MCP for context efficiency |
| HackerNoon | [hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting](https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it) | 10 tools leading ecosystem pivot |
| MorphLLM | [morphllm.com/claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Claude Code Skills vs MCP vs Plugins comparison |
| Duet | [duet.so/guides/agent-skills-101](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills) | Skills vs MCP explained |
| Cra.mr | [cra.mr/mcp-skills-and-agents](https://cra.mr/mcp-skills-and-agents/) | MCP, Skills, and Agents overview |
| Augment Code | [augmentcode.com/guides/claude-agent-sdk-skills](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities) | Claude Agent SDK skills architecture |
| ExplainX.ai | [explainx.ai/blog/what-are-agent-skills-complete-guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | Complete guide to agent skills |
| Skywork AI (Claude Skills Guide) | [skywork.ai/blog/ai-bot/claude-skills-ultimate-guide](https://skywork.ai/blog/ai-bot/claude-skills-ultimate-guide/) | Ultimate guide to Claude Skills |
| Skywork AI (Claude Code Skills) | [skywork.ai/blog/claude-code-skills-how-to-use-ultimate-guide](https://skywork.ai/blog/claude-code-skills-how-to-use-ultimate-guide/) | Claude Code Skills how-to |
| Medium (@unicodeveloper) | [medium.com/@unicodeveloper/10-must-have-skills](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 must-have agent skills list |
| Medium (monetization) | [medium.com/mcp-server/rise-of-mcp-2026](https://medium.com/mcp-server/the-rise-of-mcp-protocol-adoption-in-2026-and-emerging-monetization-models-cb03438e985c) | MCP monetization models |
| Medium (MCP over skills) | [medium.com/ai-ai-oh/why-i-choose-mcp-over-skills](https://medium.com/ai-ai-oh/why-i-choose-mcp-over-skills-in-2026-045207aadfed) | Counterargument: MCP still better |
| Nick Nisi | [nicknisi.com/posts/claude-skills](https://nicknisi.com/posts/claude-skills/) | Why everyone should try Claude Skills |
| Pento | [pento.ai/blog/a-year-of-mcp-2025-review](https://www.pento.ai/blog/a-year-of-mcp-2025-review) | One year of MCP retrospective |
| CData | [cdata.com/blog/2026-year-enterprise-ready-mcp-adoption](https://www.cdata.com/blog/2026-year-enterprise-ready-mcp-adoption) | Enterprise MCP adoption in 2026 |
| Zuplo | [zuplo.com/mcp-report](https://zuplo.com/mcp-report) | State of MCP: production readiness |
| LSEG/ResultSense | [resultsense.com/news/2026-04-23-lseg-q1-guidance-ai-mcp-growth](https://www.resultsense.com/news/2026-04-23-lseg-q1-guidance-ai-mcp-growth) | LSEG lifts guidance on MCP adoption |
| Knak | [knak.com/blog/mcp-adoption-in-2026](https://knak.com/blog/mcp-adoption-in-2026-what-marketers-need-to-know/) | MCP for marketers |
| Humaineeti | [humaineeti.ai/resources/model-context-protocol-mcp-enterprise](https://www.humaineeti.ai/resources/model-context-protocol-mcp-enterprise) | Enterprise MCP guide |
| ModelContextProtocol.io | [modelcontextprotocol.io/docs/develop/build-with-agent-skills](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills) | Official: Build with Agent Skills |
| ModelContextProtocol.io | [modelcontextprotocol.io/community/skills-over-mcp/charter](https://modelcontextprotocol.io/community/skills-over-mcp/charter) | Skills Over MCP Working Group charter |
| Ice Ice Bear blog | [ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace](https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/) | Plugin marketplace deep dive (April 2026) |
| Systemprompt.io | [systemprompt.io/guides/getting-started-anthropic-marketplace](https://systemprompt.io/guides/getting-started-anthropic-marketplace) | Install Anthropic marketplace plugins |
| Angelo Lima | [angelo-lima.fr/en/claude-code-plugins-marketplace](https://angelo-lima.fr/en/claude-code-plugins-marketplace/) | Claude Code plugins overview |
| DeepWiki | [deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery](https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery) | Plugin marketplace architecture docs |
| DEV (sub-agents) | [dev.to/shinpr/bringing-claude-codes-sub-agents](https://dev.to/shinpr/bringing-claude-codes-sub-agents-to-any-mcp-compatible-tool-1hb9) | Sub-agents in MCP-compatible tools |
| ClaudeFast | [claudefa.st/blog/tools/mcp-extensions/best-addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ Best MCP Servers for Claude Code |
| Claudemarketplaces.com | [claudemarketplaces.com](https://claudemarketplaces.com/) | 4,200+ skills, 770+ MCPs, 2,500+ marketplaces |
| SkillsMP | [skillsmp.com](https://skillsmp.com/) | Cross-agent skills marketplace |
| PulseMCP | [pulsemcp.com/servers/mrsimpson-agent-skills](https://www.pulsemcp.com/servers/mrsimpson-agent-skills) | MCP server discovery |
| MCP Market | [mcpmarket.com](https://mcpmarket.com/) | MCP servers and skills |
| MCPServers.org | [mcpservers.org/agent-skills](https://mcpservers.org/agent-skills) | Agent skills library |
| ClaudeSkills.cc | [claudeskills.cc/tutorials](https://claudeskills.cc/tutorials) | Claude skills tutorials |
| ClaudeSkills.org | [claudeskills.org/docs/skills-cases/mcp-builder](https://www.claudeskills.org/docs/skills-cases/mcp-builder) | MCP builder skill |
| Claude.com blog | [claude.com/blog/building-agents-that-reach-production-systems-with-mcp](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp) | Anthropic: building production agents with MCP |
| Claude.com blog | [claude.com/blog/extending-claude-capabilities-with-skills-mcp-servers](https://claude.com/blog/extending-claude-capabilities-with-skills-mcp-servers) | Anthropic: Skills + MCP capabilities |
| Claude Code Docs | [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills) | Official: Extend Claude with skills |
| Claude Code Docs | [code.claude.com/docs/en/mcp](https://code.claude.com/docs/en/mcp) | Official: Connect Claude Code to tools via MCP |
| Claude Code Docs | [code.claude.com/docs/en/discover-plugins](https://code.claude.com/docs/en/discover-plugins) | Official: Discover and install prebuilt plugins |
| Claude API Docs | [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | API docs: Agent Skills overview |
| Claude API Docs | [platform.claude.com/docs/en/agent-sdk/mcp](https://platform.claude.com/docs/en/agent-sdk/mcp) | API docs: Connect to external tools with MCP |
| Anthropic SkillJar | [anthropic.skilljar.com/claude-code-in-action](https://anthropic.skilljar.com/claude-code-in-action) | Official Claude Code in Action course |
| Composio | [composio.dev/toolkits/youtube/framework/claude-code](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration with Claude Code |
| Composio | [composio.dev/toolkits/tiktok/framework/claude-agents-sdk](https://composio.dev/toolkits/tiktok/framework/claude-agents-sdk) | TikTok MCP integration |
| Composio (best marketing skills) | [composio.dev/content/best-marketing-skills](https://composio.dev/content/best-marketing-skills) | Best marketing skills for Claude Code |
| Sparkco AI | [sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi](https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi) | AI agents for prediction markets |
| Blockchain.news | [blockchain.news/ainews/clis-as-agent-native-interfaces-2026](https://blockchain.news/ainews/clis-as-agent-native-interfaces-2026-analysis-on-polymarket-cli-github-cli-and-mcp-for-ai-automation) | CLIs as agent-native interfaces analysis |
| Polysolmcp.com | [polysolmcp.com](https://www.polysolmcp.com/) | Polymarket MCP overview |
| Lobsters | [lobste.rs/s/tcwpdy/claude_skills_may_be_bigger_deal_than_mcp](https://lobste.rs/s/tcwpdy/claude_skills_may_be_bigger_deal_than_mcp) | Claude Skills vs MCP Lobsters thread |
| Simon Willison TILs | [til.simonwillison.net/claude-code/playwright-mcp-claude-code](https://til.simonwillison.net/claude-code/playwright-mcp-claude-code) | Using Playwright MCP with Claude Code |
| Goodeye Labs | [goodeyelabs.com/articles/top-ai-agent-evaluation-tools-2026](https://www.goodeyelabs.com/articles/top-ai-agent-evaluation-tools-2026) | Agent evaluation tools overview |
| MindStudio | [mindstudio.ai/blog/claude-code-skills-social-media](https://www.mindstudio.ai/blog/claude-code-skills-social-media-content-repurposing) | Skills for social media automation |
| AI Vid Pipeline | [aividpipeline.com/blog/remotion-agent-skills-guide-2026](https://aividpipeline.com/blog/remotion-agent-skills-guide-2026) | Remotion agent skills for video generation |
| Skywork AI (Polymarket) | [skywork.ai/skypage/en/ai-engineer-guide-polymarket-server](https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560) | Polymarket MCP server guide |
| Guptadeepak | [guptadeepak.com/the-complete-guide-to-model-context-protocol-mcp](https://guptadeepak.com/the-complete-guide-to-model-context-protocol-mcp-enterprise-adoption-market-trends-and-implementation-strategies/) | Complete enterprise MCP guide |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (reddit.com inaccessible to Anthropic web agent)
├─ 🔵 X/Twitter: 0 direct │ blocked — cross-referenced via HN/Techmeme/Mastodon
├─ 🔴 YouTube: 8 videos │ views N/A │ 0 with transcripts
├─ 🟢 HN: 12 stories │ points N/A │ comments N/A (no direct HN API access)
├─ 🟣 TikTok: 1 video │ views N/A
├─ 🩷 Instagram: 0 reels │ not searched
├─ 🦋 Bluesky: 0 posts │ 0 likes (Simon Willison on Mastodon fedi.simonwillison.net)
├─ 📊 Polymarket: 0 markets on topic │ $N/A (MCP servers for Polymarket documented, not markets about skills)
├─ 🌐 Web: 70+ pages │ —
└─ 🗣️ Top voices: @simonw (Simon Willison), @unicodeveloper │ AWS, Anthropic, GitHub, Arize AI, Analytics Vidhya
```

---

## Data Gaps

- **Reddit**: Completely blocked — reddit.com inaccessible to Anthropic's web agent. Zero Reddit data retrieved. This is a significant gap; r/ClaudeAI, r/MachineLearning, r/LocalLLaMA likely have substantial discussion.
- **X/Twitter**: x.com blocked. Simon Willison's original tweet ([x.com/simonw/status/1978935386496995811](https://x.com/simonw/status/1978935386496995811)) and AWS announcement tweet ([x.com/awscloud/status/2042298042204700891](https://x.com/awscloud/status/2042298042204700891)) found via secondary sources. No engagement metrics for X posts.
- **Bluesky**: No direct Bluesky search performed. Simon Willison is on Mastodon (fedi.simonwillison.net) but not Bluesky-specific data retrieved.
- **TikTok**: Only 1 TikTok found via web search; direct TikTok search tools not available. Views/likes not retrieved.
- **YouTube**: 8 videos found but no view counts, like counts, or transcripts retrieved. YouTube search via web only; no direct YouTube API access.
- **HN engagement numbers**: HN items found by URL but point counts and comment counts not retrieved (would require fetching individual HN pages).
- **Skills.sh install numbers**: Remotion skill at 126,000+ installs was the only specific stat available; broader leaderboard data not retrieved.
- **Coverage estimate**: Web/blogs/docs ~90% covered; HN stories ~85% covered; Reddit 0%; X/Twitter 5% (secondary sources only); TikTok ~10%; YouTube titles ~80% but content 0%; Bluesky 0%.

---

## Key Quotes

> "Skills are conceptually extremely simple: a skill is a Markdown file telling the model how to do something, optionally accompanied by extra documents and pre-written scripts that the model can run." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "GitHub's official MCP on its own famously consumes tens of thousands of tokens of context, and once you've added a few more to that there's precious little space left for the LLM to actually do useful work." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "The most successful AI architects in 2026 are using the hybrid approach: They use MCP to give the agent a standardized 'nervous system' to touch the world, and they use Skills to give the agent the 'mental playbooks' to know what to do once it gets there. If you aren't using both, you're building half an agent." — [Analytics Vidhya](https://www.analyticsvidhya.com/blog/2026/04/mcp-vs-agent-skills/)

> "Correctness landed in a tight band: LobeHub 0.826, Vault 0.833, MCP 0.834. The takeaway: it doesn't really matter which approach you pick—your agent will get the answer." — Arize AI ([arize.com](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/))

> "One standard to rule Claude Code, Copilot, Cursor, and Gemini." — [Groundy](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor-and-gemini/)

> "AWS Agent Registry: a private catalog to stop agent sprawl." — [DEV Community](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91)

> "The agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. This growth created an obvious problem: developers now spend more time comparing marketplaces than they spend finding skills." — [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)

> "Only 12.9% of MCP servers score 'high trust' (70 or above out of 100), meeting quality thresholds for documentation, maintenance, and reliability." — [Digital Applied](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)

> "60 Claude skills on GitHub allows you to build AI employees that can handle marketing, data analysis, product management, programming and even C level advisors inside of Claude." — @taki.gpt ([TikTok](https://www.tiktok.com/@taki.gpt/video/7611210505222360321))

> "Skills are installed at your own discretion. They are not verified by GitHub and may contain prompt injections, hidden instructions, or malicious scripts." — GitHub CLI docs via [Syntax Diaries](https://thesyntaxdiaries.com/gh-skill-github-cli-agent-skills-security)
