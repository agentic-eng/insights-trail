# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-23
**Query type:** GENERAL
**Sources:** Hacker News, YouTube, Web, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 9 stories | ~1,606 pts, ~808 comments | Top stories from Oct 2025; April items low engagement |
| YouTube | 10 videos | — | Views unavailable; 1 video in last 30 days |
| Web | 80+ pages | — | via WebSearch + WebFetch |
| Reddit | — | — | Direct fetch blocked; 4,200+ weekly r/ClaudeCode contributors per third-party summary |
| X/Twitter | — | — | Excluded per spec |
| Bluesky | — | — | No results found |
| Polymarket | — | — | No relevant markets found |
| TikTok | — | — | No results found |
| Instagram | — | — | No results found |

---

## Synthesized Findings

### 1. Agent Skills Becomes a Cross-Industry Open Standard

What started as an Anthropic internal pattern in Claude Code has become the dominant open standard for AI agent extensibility. Anthropic published the format on October 16, 2025 and formally opened it on December 18, 2025. As of April 2026, **agentskills.io** lists 35+ platforms that have adopted the standard, including GitHub Copilot, Cursor, VS Code, OpenAI Codex, Gemini CLI (Google), Roo Code, Letta, OpenHands, Spring AI, Databricks Genie Code, Snowflake Cortex Code, JetBrains Junie, and dozens more.

The core format is deliberately minimal: a folder with a `SKILL.md` file containing YAML frontmatter (`name` and `description`) plus natural-language instructions. Optional subdirectories hold scripts, references, templates, and assets. The architecture relies on **progressive disclosure** — agents load only skill names and descriptions at startup (~100 tokens each), fetch full instructions when task context matches (~5k tokens), and load bundled files only as needed.

> "The Agent Skills format was originally developed by Anthropic, released as an open standard, and has been adopted by a growing number of agent products." — [agentskills.io](https://agentskills.io/home)

> "There was no standards committee, no joint announcement, and no formal specification. And yet today, a skill definition written for Claude can be adapted for GPT-4o or Gemini in minutes." — [MindStudio, March 29, 2026](https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google)

**Platforms discussing this theme:** Hacker News, Web (VentureBeat, SiliconAngle, The New Stack, AI Business, MindStudio, inference.sh, New Stack)

Sources: [Anthropic Engineering](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [agentskills.io](https://agentskills.io/home) · [SiliconAngle](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/) · [VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) · [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) · [AI Business](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) · [inference.sh](https://inference.sh/blog/skills/agent-skills-overview) · [deepwiki spec](https://deepwiki.com/anthropics/skills/6.1-agent-skills-specification) · [Medium explainer](https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71) · [Agent Skills API docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [GitHub anthropics/skills](https://github.com/anthropics/skills)

---

### 2. Skills vs. MCP vs. Plugins: The Tripartite Debate

The most-discussed question across all platforms is the relationship between three overlapping primitives. Anthropic's official taxonomy (from [claude.com/blog/skills-explained](https://claude.com/blog/skills-explained), Nov 2025) is:

| Aspect | Skills | Plugins | MCP |
|--------|--------|---------|-----|
| Provides | Procedural knowledge | Bundled distribution unit | Tool connectivity |
| Analogy | Recipe card | Full kitchen (stocked) | Kitchen plumbing |
| Persistence | Across conversations | Installable package | Continuous connection |
| Typical size | ~100–5,000 tokens on-demand | Contains Skills + MCP + commands | Can front-load 50k+ tokens |

The community shorthand: **MCP is the plumbing, Skills are the instructions, Plugins are the install package.** A plugin can bundle multiple skills, MCP connectors, slash commands, and subagents.

HN commenters challenged the significance of skills. **tptacek** called the actual innovation **tool calling**, not MCP specifically. **pants2** characterized skills as "a design pattern / prompt engineering trick." But **simonw** (Simon Willison) defended the distinction: the key is *automated discovery* — "Claude now scans skill folders for YAML metadata, enabling self-directed tool selection without manual user intervention."

Hacker News thread ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) (738 pts, 370 comments):
> "tptacek: the actual innovation centers on tool calling capabilities, not MCP specifically, with skills being an improved context-management approach compared to MCPs' token-heavy front-loading of API documentation."

A typical 5-server MCP setup with 58 tools uses ~55,000 tokens before any conversation starts. Skills address this by loading only the metadata until invoked — key for running 50+ capabilities simultaneously.

**Platforms discussing this theme:** Hacker News, YouTube (multiple comparison videos), Web (devtoolpicks.com, morphllm.com, buildtolaunch.substack.com, alexop.dev)

Sources: [claude.com/blog/skills-explained](https://claude.com/blog/skills-explained) · [HN 45619537](https://news.ycombinator.com/item?id=45619537) · [HN 45607117](https://news.ycombinator.com/item?id=45607117) · [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) · [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [buildtolaunch Substack](https://buildtolaunch.substack.com/p/claude-code-mcp-vs-plugins-vs-skills) · [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [agensi.io](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [YouTube: Agent Skills vs MCP](https://www.youtube.com/watch?v=6wdvSH61xGw) · [YouTube: Claude Skills vs MCP](https://www.youtube.com/watch?v=qthyl0GCpDo) · [YouTube: "bigger than MCP"](https://www.youtube.com/watch?v=1WImBwiA7RA)

---

### 3. GitHub CLI `gh skill` — April 16, 2026 (Most Recent Major Development)

On April 16, 2026, GitHub shipped **`gh skill`** as part of GitHub CLI v2.90.0, marking the first time a major platform provider shipped a first-class agent skill distribution tool. This is the single most significant event within the last 30 days for this topic.

`gh skill install` installs agent skills from any GitHub repository or local directory into either user scope (home directory, available everywhere) or project scope (inside a git repo). The `--pin` flag locks a skill to a specific tag or commit SHA for reproducible environments.

Supported agents in the initial release: GitHub Copilot, Claude Code, Cursor, Codex, Gemini CLI, Antigravity, Amp, Goose, Junie, OpenCode, Windsurf, and more.

A parallel GitHub issue ([anthropics/claude-code#50148](https://github.com/anthropics/claude-code/issues/50148)) requests first-class remote skill source integration as a step toward programmatic config access across all Claude surfaces.

Sources: [GitHub Changelog](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) · [gh skill manual](https://cli.github.com/manual/gh_skill) · [gh skill install](https://cli.github.com/manual/gh_skill_install) · [CLI release v2.90.0](https://github.com/cli/cli/releases/tag/v2.90.0) · [CLI release v2.91.0](https://github.com/cli/cli/releases/tag/v2.91.0) · [azukiazusa.dev](https://azukiazusa.dev/en/blog/gh-agent-skill-management/) · [bighatgroup.com](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/) · [daily.dev](https://app.daily.dev/posts/manage-agent-skills-with-github-cli-cwqtearpx) · [Claude Code issue #50148](https://github.com/anthropics/claude-code/issues/50148)

---

### 4. The Marketplace Explosion: Five Competing Distribution Platforms

Multiple distribution platforms have emerged, each with different positioning:

| Platform | Scale | Model | Security |
|----------|-------|-------|----------|
| [skills.sh](https://skills.sh/) (Vercel) | 87,000+ tracked skills | Open marketplace, `npx skills add` | Snyk scanning integrated at publish |
| [skillsmp.com](https://skillsmp.com/) | 66,500+ skills | Community-crawled GitHub, semantic search | No quality gate; verify before install |
| [tonsofskills.com](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) (ccpi) | 423 plugins, 2,849 skills, 177 agents | `pnpm add -g @intentsolutionsio/ccpi` | Open source |
| [claudemarketplaces.com](https://claudemarketplaces.com/) | Directory | Claude Code specific | — |
| [agentpatch.ai](https://agentpatch.ai/blog/mcp-marketplace-agentpatch/) | MCP focused | Hosts, manages, bills for MCP servers | Managed hosting |

skills.sh launched January 20, 2026 and hit 20,000 installs within 6 hours — a signal of pent-up demand for a governed install path. SkillsMP's 66,500+ skills reflects the community's independent crawling of GitHub SKILL.md files, most of which predate any formal marketplace.

KDNuggets' analysis identifies the **discovery-vs-quality tension** as the core problem: "Shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction."

**Platforms discussing this theme:** Web (KDNuggets, SmartScope, VirtualUncle, buildmvpfast, calmops, termdock)

Sources: [skills.sh](https://skills.sh/) · [skillsmp.com](https://skillsmp.com/) · [SmartScope SkillsMP review](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) · [KDNuggets top 5](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) · [tonsofskills/ccpi GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [agentpatch.ai](https://agentpatch.ai/blog/mcp-marketplace-agentpatch/) · [mcpservers.org agent-skills library](https://mcpservers.org/agent-skills) · [MCPMarket April 16 rankings](https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026) · [buildmvpfast "new npm"](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) · [virtualuncle skills.sh guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)

---

### 5. Claude Code April 2026 Updates: Skills, MCP, and Plugin Hardening

Anthropic shipped multiple Claude Code point releases in April 2026 tightening all three layers:

**Skills**: The model can now discover and invoke built-in slash commands (`/init`, `/review`, `/security-review`) via the Skill tool (v2.1.108). The `/skills` menu gained token-count sorting (`t` key) to help users understand context consumption (v2.1.111). Skills with `disable-model-invocation: true` now work properly when invoked mid-message.

**MCP**: Faster startup with multiple stdio servers (v2.1.116); resources/templates listing deferred to first mention; `/doctor` warns on duplicate MCP server config across scopes; fixed tool calls hanging when server connections drop (v2.1.110); stalled subagents now fail cleanly after 10 minutes.

**Plugins**: Plugin install automatically installs missing dependencies on already-installed plugins (v2.1.117); `blockedMarketplaces` and `strictKnownMarketplaces` settings enforced enterprise-wide during install/update/refresh; background monitor support added via `monitors` manifest key (v2.1.105).

An earlier April 2026 release also shipped the **MCP Tool Search / lazy loading** feature — MCP servers now load tool names only at startup and fetch full schemas on demand via ToolSearch, reducing context usage by up to 95% with large toolsets.

Sources: [releasebot.io Claude Code](https://releasebot.io/updates/anthropic/claude-code) · [Claude Code MCP docs](https://code.claude.com/docs/en/mcp) · [Claude Code plugin docs](https://code.claude.com/docs/en/plugins) · [MCPMarket.com](https://mcpmarket.com/) · [claudefa.st 50+ MCP servers](https://claudefa.st/blog/tools/mcp-extensions/best-addons) · [scottspence.com MCP setup](https://scottspence.com/posts/configuring-mcp-tools-in-claude-code) · [dextralabs enterprise guide](https://dextralabs.com/blog/claude-code-mcp-enterprise-ai-integrations/) · [MindStudio MCP guide](https://www.mindstudio.ai/blog/how-to-use-mcp-servers-with-claude-code) · [markaicode MCP integration](https://markaicode.com/claude-code-mcp-integration/) · [support.claude.com MCP setup](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop) · [generect.com Claude MCP guide](https://generect.com/blog/claude-mcp/)

---

### 6. ToxicSkills: The Security Wake-Up Call

On February 5, 2026, Snyk Labs published the **ToxicSkills study** — the first large-scale security audit of AI agent skills — scanning 3,984 publicly listed skills across all major registries. The findings were alarming:

- **36.82% (1,467 skills)** contained at least one security flaw
- **13.4% (534 skills)** contained critical-level issues
- **76 skills** were confirmed malicious (credential theft, backdoors, data exfiltration)
- **5 of the top 7 most-downloaded skills** on ClawHub were malware

The attack surface is novel: Skills are markdown files that execute with the full privileges of the host agent — filesystem access, terminal execution, network requests, and credential visibility. The primary attack pattern is prompt injection combined with shell payloads.

SpecWeave's response was a two-tier scanning approach: pattern scanning (75% detection) + LLM-based semantic analysis, achieving 100% detection against real samples.

> "When you install a skill, you are handing an AI agent instructions that it will follow implicitly." — SpecWeave, Feb 21, 2026

The research triggered supply-chain governance conversations across the developer community and was a key driver behind skills.sh's Snyk integration at launch.

**Platforms discussing this theme:** Web (AICerts, SkillShield, Barrack AI, SpecWeave, Penligent, CyberDesserts, daily.dev, Doug Seven's blog)

Sources: [AICerts Snyk audit](https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/) · [SkillShield ToxicSkills](https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/) · [Barrack AI](https://blog.barrack.ai/openclaw-security-vulnerabilities-2026/) · [SpecWeave blog](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/) · [SpecWeave GitHub docs](https://github.com/anton-abyzov/specweave/blob/develop/docs-site/blog/2026-02-21-toxicskills-why-your-ai-agent-skills-need-verification.md) · [Snyk daily.dev](https://app.daily.dev/posts/snyk-finds-prompt-injection-in-36-1467-malicious-payloads-in-a-toxicskills-study-of-agent-skills-s-0bdgmynfg) · [Penligent OpenClaw VirusTotal](https://www.penligent.ai/hackinglabs/openclaw-virustotal-clawhub-skill-scanning-turns-the-marketplace-into-a-supply-chain-boundary/) · [Doug Seven Trust Without Verification](https://dougseven.com/2026/02/09/trust-without-verification/) · [CyberDesserts OpenClaw](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/) · [Snyk top Claude skills for security](https://snyk.io/articles/top-claude-skills-cybersecurity-hacking-vulnerability-scanning/)

---

### 7. MCP Ecosystem Matures: 500+ Servers, 97M Monthly SDK Downloads

The MCP (Model Context Protocol) ecosystem reached a milestone scale in April 2026: 500+ servers, 97 million monthly SDK downloads, and official client support across every major code editor. Multiple "MCP gateway" solutions have emerged as enterprise-grade proxies that sit between AI agents and MCP servers, centralizing auth, authorization, auditing, and traffic management.

Popular MCP servers for Claude Code include Figma (read designs, extract tokens), Playwright (browser automation, E2E testing), Vercel (deploy, check logs), PostgreSQL (query databases), and GitHub (create PRs, review issues). Google Stitch launched an official MCP server + Agent Skills bundle, highlighted in a recent YouTube video.

MCP Channels — letting MCP servers push messages into Claude sessions (Telegram, Discord, webhooks) — are still in research preview as of April 2026.

**Platforms discussing this theme:** Web (MCPMarket, LobeHub, AgentPatch, Awesome MCP Servers, Taskade, ByteBridge Medium, Microsoft Learn, Databar)

Sources: [mcpmarket.com](https://mcpmarket.com/) · [MCPMarket April 21 top list](https://mcpmarket.com/daily/top-mcp-server-list-april-21-2026) · [mcpservers.org](https://mcpservers.org) · [lobehub.com/mcp](https://lobehub.com/mcp) · [agentpatch.ai MCP marketplace](https://agentpatch.ai/blog/mcp-marketplace-agentpatch/) · [taskade.com 15 best](https://www.taskade.com/blog/mcp-servers) · [ByteBridge MCP gateways](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) · [Microsoft Learn MCP tools](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) · [Databar MCP for sales](https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026) · [Harishgarg MCP index](https://mcp.harishgarg.com/use/ai-agent-marketplace-index/mcp-server/with/perplexity) · [claude.com MCP production blog](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp)

---

### 8. Tooling Layer: Managing the Sprawl

As developers accumulate dozens of skills, MCP servers, and CLAUDE.md files, management tooling has emerged as its own category.

**Ensemble** (macOS app, ~Feb 2026): GUI for organizing Skills and MCPs, bundling into workflow presets, one-click deployment, Finder integration, automated classification. Built with Tauri 2 (Rust + React), MIT license. Show HN post was low-engagement but the creator's motivation captured a real pain:
> "Once you have a few dozen Skills, a handful of MCP servers, and CLAUDE.md files scattered across projects, managing them through ~/.claude.json and manual file editing gets old fast." — IO0oI, HN

**skills-manager** ([xingkongliang/skills-manager](https://github.com/xingkongliang/skills-manager)): Lightweight desktop app to manage, sync, and organize AI agent skills across 15+ coding tools — Cursor, Claude Code, Codex, Copilot.

**`gh skill`**: Command-line first-class management with pinning, scoping, multi-agent support (April 2026).

The Composio-maintained **awesome-claude-plugins** ([GitHub](https://github.com/ComposioHQ/awesome-claude-plugins)) and hesreallyhim's **awesome-claude-code** ([GitHub](https://github.com/hesreallyhim/awesome-claude-code)) serve as community-curated discovery layers.

Sources: [HN Ensemble](https://news.ycombinator.com/item?id=46922223) · [ComposioHQ awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) · [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) · [skills-manager](https://github.com/xingkongliang/skills-manager) · [quemsah/awesome-claude-plugins metrics](https://github.com/quemsah/awesome-claude-plugins) · [claude-code-tips 45 tips](https://github.com/ykdojo/claude-code-tips) · [levnikolaevich/claude-code-skills](https://github.com/levnikolaevich/claude-code-skills) · [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)

---

## Cross-Source Patterns

### Pattern 1: Context Efficiency as the Core Competitive Differentiator

**Signal:** Skills' token-efficiency claim — "30–50 tokens each, loaded on-demand" vs. MCP's 50k+ front-loading — appears across Hacker News, YouTube, and multiple blog posts as the primary reason developers choose Skills over MCP for workflow automation.

**Platforms:** Hacker News (tptacek, simonw), Web (morphllm.com, devtoolpicks.com, claude.com official blog), YouTube comparison videos

**Key quotes:**
- "MCP alone consumes tens of thousands of tokens" — [simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/)
- "A typical five-server setup with 58 tools uses approximately 55,000 tokens before any conversation starts." — [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)
- tptacek on HN: skills are "an improved context-management approach compared to MCPs' token-heavy front-loading"

---

### Pattern 2: Security as the Unresolved Bottleneck for Ecosystem Growth

**Signal:** The ToxicSkills research (Feb 2026) showing 36.82% vulnerability rate was cited in security blogs, community discussion, and is directly referenced as a driver for skills.sh's Snyk integration. No major marketplace had proactive security scanning before the research published.

**Platforms:** Web (AICerts, SkillShield, SpecWeave, Barrack AI, Penligent, Doug Seven, CyberDesserts), implicitly referenced in skills.sh launch coverage

**Key quotes:**
- "When you install a skill, you are handing an AI agent instructions that it will follow implicitly." — SpecWeave
- "534 (13.4%) contained critical-level issues... 76 were confirmed malicious" — ToxicSkills study

---

### Pattern 3: GitHub as the De Facto Registry Layer

**Signal:** The `gh skill` CLI launch (April 16, 2026) formalized what was already organic behavior — GitHub repositories as the actual distribution mechanism for skills, with marketplaces as discovery/search layers on top. GitHub stars serve as the default quality signal on SkillsMP and VoltAgent's awesome list.

**Platforms:** Web (GitHub Changelog, azukiazusa, BigHatGroup, daily.dev), Hacker News discussion of plugin discovery

**Key quotes:**
- "gh skill install allows you to install agent skills from a GitHub repository or local directory" — GitHub CLI docs
- "Agent Skills Are the New npm" — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

---

### Pattern 4: The Principal-Agent Documentation Insight

**Signal:** Multiple HN commenters in the Oct 2025 Claude Skills thread identified a structural reason why AI-targeted documentation outperforms human-targeted documentation: writing context docs for an AI assistant solving your immediate problem creates stronger incentive alignment than writing for hypothetical future humans.

**Platforms:** Hacker News (michael1999, 7thpower, emn13, simonw), later echoed in blog posts

**Key quotes:**
- **7thpower**: "documentation written for AI assistants solving your immediate needs generates stronger incentive structures than documentation for hypothetical future human readers"
- **michael1999**: three theories — faster feedback loops, AI reduces docs costs, programmers motivated by personal productivity
- **emn13**: "the real breakthrough involves targeting current, specific problems rather than predicting future needs"

---

## Per-Platform Tables

### Hacker News
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| simonw (orig) | Claude Skills | 816 | 427 | "Claude Skills are awesome, maybe a bigger deal than MCP" | [link](https://news.ycombinator.com/item?id=45607117) |
| (community) | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | tptacek: "skills are improved context-management vs MCPs' token-heavy front-loading" | [link](https://news.ycombinator.com/item?id=45619537) |
| (community) | Customize Claude Code with plugins | 48 | 9 | joesaunderson: launched claudecodemarketplace.com | [link](https://news.ycombinator.com/item?id=45530150) |
| IO0oI | Show HN: Ensemble – macOS App | 1 | 1 | "managing them through ~/.claude.json and manual file editing gets old fast" | [link](https://news.ycombinator.com/item?id=46922223) |
| jungard | Claude Code Skills and Plugins as an Open Source Project | 2 | 1 | "180+ production-ready skills and plugins for Claude Code, OpenAI Codex, Gemini CLI" | [link](https://news.ycombinator.com/item?id=47321892) |
| (community) | Anatomy of the .claude/ folder | — | — | — | [link](https://news.ycombinator.com/item?id=47543139) |
| (community) | Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP | — | — | — | [link](https://news.ycombinator.com/item?id=45642911) |
| (community) | CLAUDE.md, Skills, Agents, MCP, slash commands | — | — | — | [link](https://news.ycombinator.com/item?id=46396930) |
| (community) | Claude Code Emergent Behavior: When Skills Combine | — | — | — | [link](https://news.ycombinator.com/item?id=46531794) |

*Note: Top HN stories are from Oct 2025, outside last 30 days. April 2026 items have very low engagement, suggesting peak HN discussion has passed for this topic.*

---

### YouTube
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | Agent Skills or MCP in the era of Claude Code? | — | — | No | [link](https://www.youtube.com/watch?v=pvxNcQTcIy4) |
| — | How I Use Claude Code With Skills, MCP, Agents & Plugins | — | — | No | [link](https://www.youtube.com/watch?v=jzf7DQa2CAc) |
| — | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) ★ | — | — | No | [link](https://www.youtube.com/watch?v=KjEFy5wjFQg) |
| — | Google Stitch MCP Just Made Claude Code 10x Better | — | — | No | [link](https://www.youtube.com/shorts/a8SlmCdJcNM) |
| — | Better With This Setup (CLAUDE.md + Skills + MCPs) | — | — | No | [link](https://www.youtube.com/watch?v=pBHKTojO1YY) |
| — | Claude Code Skills just Built me an AI Agent Team (2026 Guide) | — | — | No | [link](https://www.youtube.com/watch?v=OdtGN27LchE) |
| — | Agent Skills vs MCP: What's the difference? | — | — | No | [link](https://www.youtube.com/watch?v=6wdvSH61xGw) |
| — | Claude Skills Explained: 4 Skills to 10x Your Coding Workflow | — | — | No | [link](https://www.youtube.com/watch?v=bFC1QGEQ2E8) |
| — | Claude Skills - the SOP for your agent that is bigger than MCP | — | — | No | [link](https://www.youtube.com/watch?v=1WImBwiA7RA) |
| — | Claude Skills vs MCP: What's the Difference and When to Use Each? | — | — | No | [link](https://www.youtube.com/watch?v=qthyl0GCpDo) |

*★ = within last 30 days (uploaded ~April 9, 2026). YouTube metadata (views/likes) unavailable via current fetch methods.*

---

### Web
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Official Skills architecture; progressive disclosure design |
| claude.com/blog/skills-explained | [link](https://claude.com/blog/skills-explained) | Canonical 5-primitive comparison (Skills/Prompts/Projects/Subagents/MCP) |
| agentskills.io | [link](https://agentskills.io/home) | Open standard site; 35+ adopting platforms listed |
| simonwillison.net | [link](https://simonwillison.net/2025/Oct/16/claude-skills/) | "Bigger than MCP" thesis; token efficiency argument |
| SiliconAngle | [link](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/) | Dec 18, 2025: open standard announcement |
| VentureBeat | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Enterprise launch coverage |
| The New Stack | [link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Industry standards framing |
| MindStudio | [link](https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google) | Cross-provider convergence; de facto standard without committee |
| inference.sh | [link](https://inference.sh/blog/skills/agent-skills-overview) | skills.sh distribution platform; multi-agent compatibility |
| GitHub Changelog | [link](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) | gh skill CLI launch April 16, 2026 |
| GitHub CLI manual | [link](https://cli.github.com/manual/gh_skill) | gh skill command reference |
| CLI Release v2.90.0 | [link](https://github.com/cli/cli/releases/tag/v2.90.0) | Release notes |
| azukiazusa.dev | [link](https://azukiazusa.dev/en/blog/gh-agent-skill-management/) | gh skill explainer |
| BigHatGroup | [link](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/) | gh skill for Copilot, Claude Code, Cursor |
| SpecWeave (Feb 21) | [link](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/) | ToxicSkills 36% vulnerability rate; two-tier scanning solution |
| AICerts | [link](https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/) | Snyk ToxicSkills audit |
| SkillShield | [link](https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/) | ToxicSkills implications for OpenClaw users |
| Doug Seven | [link](https://dougseven.com/2026/02/09/trust-without-verification/) | "Trust Without Verification" — security framing |
| Penligent | [link](https://www.penligent.ai/hackinglabs/openclaw-virustotal-clawhub-skill-scanning-turns-the-marketplace-into-a-supply-chain-boundary/) | VirusTotal integration as supply-chain boundary |
| skills.sh | [link](https://skills.sh/) | Vercel marketplace; 87k+ skills; Snyk-scanned |
| SkillsMP | [link](https://skillsmp.com/) | 66,500+ community-indexed skills |
| tonsofskills/ccpi | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 2,849 skills, 423 plugins, ccpi CLI |
| VoltAgent/awesome | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1000+ curated cross-platform skills |
| claudemarketplaces.com | [link](https://claudemarketplaces.com/) | Claude-specific directory |
| KDNuggets | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 marketplaces comparison |
| buildmvpfast | [link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) | "Agent Skills Are the New npm" framing |
| MCPMarket | [link](https://mcpmarket.com/) | MCP server directory |
| MCPMarket daily skills | [link](https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026) | April 16 daily rankings |
| agentpatch.ai | [link](https://agentpatch.ai/blog/mcp-marketplace-agentpatch/) | MCP marketplace-as-a-service |
| LobeHub MCP | [link](https://lobehub.com/mcp) | MCP server marketplace |
| mcpservers.org | [link](https://mcpservers.org) | Awesome MCP Servers collection |
| Taskade | [link](https://www.taskade.com/blog/mcp-servers) | 15 best MCP servers 2026 |
| ByteBridge | [link](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | MCP gateways overview |
| releasebot.io | [link](https://releasebot.io/updates/anthropic/claude-code) | Claude Code April 2026 release notes |
| alexop.dev | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Full-stack explainer: MCP+Skills+Subagents+Hooks |
| devtoolpicks.com | [link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Skills vs MCP vs Plugins decision guide |
| morphllm.com | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Complete guide 2026 |
| buildtolaunch Substack | [link](https://buildtolaunch.substack.com/p/claude-code-mcp-vs-plugins-vs-skills) | MCP vs Plugins vs Skills decision |
| DEV.to raxxostudios | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best Skills & Plugins 2026 guide |
| DEV.to williamwangai | [link](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Skills vs MCP guide |
| DEV.to Claude vs Codex | [link](https://dev.to/_46ea277e677b888e0cd13/claude-code-vs-codex-2026-what-500-reddit-developers-really-think-31pb) | 500+ Reddit dev sentiment |
| Composio top plugins | [link](https://composio.dev/content/top-claude-code-plugins) | Top 10 Claude Code plugins |
| TurboDocx | [link](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best Plugins, Skills & MCP Servers |
| agensi.io | [link](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Plugins vs Skills explained |
| claudefa.st | [link](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ Best MCP Servers for Claude Code |
| scriptbyai.com | [link](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate Claude Code Resource List 2026 |
| firecrawl.dev | [link](https://www.firecrawl.dev/blog/best-claude-code-plugins) | Top 10 Claude Code Plugins 2026 |
| self.md | [link](https://self.md/guides/best-claude-code-plugins/) | Best claude code plugins 2026 |
| mejba.me | [link](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 Skills, Plugins & CLIs 2026 |
| composio.dev awesome-claude-plugins | [link](https://github.com/ComposioHQ/awesome-claude-plugins) | Curated plugin list |
| quemsah/awesome-claude-plugins | [link](https://github.com/quemsah/awesome-claude-plugins) | Plugin adoption metrics via n8n |
| hesreallyhim/awesome-claude-code | [link](https://github.com/hesreallyhim/awesome-claude-code) | Curated awesome list |
| levnikolaevich/claude-code-skills | [link](https://github.com/levnikolaevich/claude-code-skills) | Plugin suite + MCP servers |
| skills-manager | [link](https://github.com/xingkongliang/skills-manager) | Desktop management app for 15+ tools |
| claude-code-tips | [link](https://github.com/ykdojo/claude-code-tips) | 45 tips including dx plugin |
| VoltAgent/awesome-agent-skills | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1000+ curated agent skills |
| Claude Code issue #50148 | [link](https://github.com/anthropics/claude-code/issues/50148) | gh skill integration request |
| AI Business | [link](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) | Skills open standard launch |
| Platform docs: claude.com MCP | [link](https://code.claude.com/docs/en/mcp) | Official MCP docs |
| Platform docs: claude.com plugins | [link](https://code.claude.com/docs/en/plugins) | Official plugin docs |
| Platform docs: Agent Skills API | [link](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | Agent Skills API docs |
| support.claude.com MCP | [link](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop) | Getting started with local MCP |
| deepwiki spec | [link](https://deepwiki.com/anthropics/skills/6.1-agent-skills-specification) | Skills specification |
| deepwiki Microsoft | [link](https://deepwiki.com/microsoft/agent-skills/4-plugins) | Microsoft agent-skills plugins |
| Microsoft Learn | [link](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) | Using MCP Tools |
| Microsoft .NET Blog | [link](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | .NET Skills integration |
| Spring AI Blog | [link](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/) | Spring AI Agent Skills (Jan 2026) |
| claude.com MCP production | [link](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp) | MCP in production |
| Digital Applied | [link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | AI Agent Marketplaces 2026: Discovery |
| aitooldiscovery.com | [link](https://www.aitooldiscovery.com/guides/claude-code-reddit) | Claude Code Reddit community data |
| anandbg.com | [link](https://anandbg.com/blog/claude-skills-comprehensive-guide-2026) | Comprehensive guide |
| calmops.com | [link](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) | Complete guide 2026 |
| termdock.com | [link](https://www.termdock.com/en/blog/agent-skills-guide) | Agent Skills Guide 2026 |
| popularaitools.ai | [link](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | Popular AI Tools guide |
| generect.com | [link](https://generect.com/blog/claude-mcp/) | Ultimate Claude MCP guide |
| scottspence.com | [link](https://scottspence.com/posts/configuring-mcp-tools-in-claude-code) | MCP configuration guide |
| dextralabs.com | [link](https://dextralabs.com/blog/claude-code-mcp-enterprise-ai-integrations/) | Enterprise MCP integration |
| markaicode.com | [link](https://markaicode.com/claude-code-mcp-integration/) | MCP integration guide |
| MindStudio MCP | [link](https://www.mindstudio.ai/blog/how-to-use-mcp-servers-with-claude-code) | MCP with Claude Code |
| smartscope.blog | [link](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) | SkillsMP review |
| virtualuncle | [link](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | skills.sh guide |
| MCPMarket SkillsMP | [link](https://mcpmarket.com/server/skillsmp) | MCP Market listing |
| Barrack AI | [link](https://blog.barrack.ai/openclaw-security-vulnerabilities-2026/) | OpenClaw security |
| CyberDesserts | [link](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/) | OpenClaw malicious skills |
| Snyk cybersecurity skills | [link](https://snyk.io/articles/top-claude-skills-cybersecurity-hacking-vulnerability-scanning/) | Top Claude skills for security |
| daily.dev ToxicSkills | [link](https://app.daily.dev/posts/snyk-finds-prompt-injection-in-36-1467-malicious-payloads-in-a-toxicskills-study-of-agent-skills-s-0bdgmynfg) | ToxicSkills coverage |
| daily.dev gh skill | [link](https://app.daily.dev/posts/manage-agent-skills-with-github-cli-cwqtearpx) | gh skill coverage |

---

## Stats Block

```
├─ 🟠 Reddit: — direct fetch blocked │ r/ClaudeCode 4,200+ weekly contributors (3rd-party estimate)
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 10 videos │ views/likes unavailable │ 0 with transcripts │ 1 in last 30 days
├─ 🟢 HN: 9 stories │ ~1,606 pts (top 2 stories) │ ~808 comments │ top engagement from Oct 2025
├─ 🟣 TikTok: 0 videos │ no results
├─ 🩷 Instagram: 0 reels │ no results
├─ 🦋 Bluesky: 0 posts │ no results found
├─ 📊 Polymarket: 0 markets │ no relevant markets
├─ 🌐 Web: 80+ pages │ via WebSearch + WebFetch
└─ 🗣️ Top voices: @simonw (Simon Willison) │ @tptacek (Thomas Ptacek) │ r/ClaudeCode, r/ClaudeAI
```

---

## Data Gaps

- **Reddit**: Direct Reddit fetch blocked. Community data sourced from third-party summaries (aitooldiscovery.com, DEV.to analysis of 500+ Reddit developers). No specific thread URLs from within the last 30 days collected. r/ClaudeCode has 4,200+ weekly contributors per aggregate data — high confidence the discussion is active but no granular thread-level data.
- **YouTube**: WebFetch returns only footer content from YouTube URLs; zero view/like counts obtained. Video titles and approximate upload dates obtained from search result snippets only. No transcripts available. Coverage estimated at ~40%.
- **Hacker News timing**: The highest-engagement HN threads (816 pts, 738 pts) are from October 2025 — outside the last 30 days. April 2026 HN items on this topic had 1-2 points, suggesting peak community discussion predates this window. The topic may have become "settled" in the HN community.
- **Bluesky**: No Bluesky-specific posts found. The topic appears to live predominantly on X/Twitter, HN, YouTube, and GitHub — Bluesky coverage is negligible or absent.
- **ToxicSkills dates**: Snyk's research is from Feb 5, 2026 (~77 days ago) — outside last 30 days window. Ongoing coverage and response articles extend into March 2026.
- **ClawHub**: References to ClawHub as a skills platform appear in security research but no direct ClawHub URLs were confirmed operational or indexed.
- **Approximate coverage**: Web and GitHub ~85% | HN ~70% | YouTube ~40% | Reddit ~15% | All other platforms ~0%

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — @simonw (Simon Willison) on Hacker News ([link](https://news.ycombinator.com/item?id=45607117))

> "There was no standards committee, no joint announcement, and no formal specification. And yet today, a skill definition written for Claude can be adapted for GPT-4o or Gemini in minutes." — MindStudio, March 29, 2026 ([link](https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google))

> "When you install a skill, you are handing an AI agent instructions that it will follow implicitly." — SpecWeave, Feb 21, 2026 ([link](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/))

> "MCP connects Claude to data; Skills teach Claude what to do with that data." — claude.com/blog/skills-explained ([link](https://claude.com/blog/skills-explained))

> "Skills are the SOP for your agent — a general agent where anything you can achieve by typing commands into a computer is something that can now be automated." — Simon Willison, Oct 16, 2025 ([link](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "Once you have a few dozen Skills, a handful of MCP servers, and CLAUDE.md files scattered across projects, managing them through ~/.claude.json and manual file editing gets old fast." — IO0oI on HN, Show HN: Ensemble ([link](https://news.ycombinator.com/item?id=46922223))

> "documentation written for AI assistants solving your immediate needs generates stronger incentive structures than documentation for hypothetical future human readers" — @7thpower on HN ([link](https://news.ycombinator.com/item?id=45619537))

> "Agent Skills Are the New npm" — buildmvpfast.com ([link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026))

> "Projects say 'here's what you need to know.' Skills say 'here's how to do things.'" — Anthropic, claude.com ([link](https://claude.com/blog/skills-explained))

> "534 (13.4%) contained critical-level issues, 76 were confirmed malicious" — Snyk ToxicSkills study, Feb 2026 ([link](https://app.daily.dev/posts/snyk-finds-prompt-injection-in-36-1467-malicious-payloads-in-a-toxicskills-study-of-agent-skills-s-0bdgmynfg))
