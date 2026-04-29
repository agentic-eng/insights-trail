# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-29
**Query type:** GENERAL
**Sources:** Web, Hacker News, X/Twitter, YouTube, TikTok, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 9 stories | 626 points, 174 comments | Mix of Show HN launches and technical discussions |
| X/Twitter | 1 post | N/A | @WesRothMoney on MCP Tool Search rollout |
| YouTube | 2 videos | N/A | Claude Code MCP/skills tutorials |
| TikTok | 2 videos | N/A | Claude MCP tutorials going viral |
| Web | 42 pages | — | via WebSearch + WebFetch |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: Anthropic's Play for Cross-Platform Dominance

In December 2025, Anthropic released the Agent Skills specification as an open standard — a minimal, portable file format for bundling procedural AI instructions. A skill is a folder containing a `SKILL.md` file with metadata (name, description) plus optional scripts and templates. The format is intentionally simple: Markdown plus frontmatter.

The adoption velocity was remarkable. Within 48 hours of the December 18, 2025 announcement, Microsoft integrated SKILL.md into VS Code and OpenAI added it to both ChatGPT and Codex CLI. By March 2026, 32 tools — including Google's Gemini CLI, JetBrains' Junie, AWS Kiro, and Block's Goose — all read the same SKILL.md files from the same directory structure. This cross-platform interoperability is unprecedented in the AI tooling space.

Institutional governance followed quickly. The Linux Foundation announced the Agentic AI Foundation (AAIF) with Anthropic, OpenAI, and Block as founding members; by February 2026, AAIF had grown to 146 member organizations. The April 2026 MCP Dev Summit North America in NYC drew approximately 1,200 attendees.

The April 14, 2026 Skills Over MCP Interest Group office hours (discussion #2585 on GitHub) reveals active in-progress standardization work. Peter Alexander (Anthropic) confirmed prototyping of a skills extension to MCP (a "Skills Extension Proposal" / SEP); Pedro Rodrigues (Supabase) flagged the core discovery challenge: *"Agents don't know what they don't know."* The current design has hosts fetch `index.json` on startup and decide how to surface skills.

**Platforms:** Web, HN, GitHub
**Key URLs:**
- Spec: https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md
- VentureBeat launch: https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard
- Interoperability guide: https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
- Office hours notes: https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585
- AI Business coverage: https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude

---

### 2. The Extension Taxonomy: Skills vs. MCP vs. Plugins vs. Hooks

A consistent theme across all sources is that developers confuse — and conflate — the four Claude Code extension mechanisms. The emerging consensus taxonomy:

- **Skills** (SKILL.md / .claude/commands/): Procedural knowledge files that teach Claude *how* to perform tasks. They inject 30-50 tokens per skill into context via progressive loading. Best for: coding standards, commit conventions, testing patterns, team workflows. Zero external dependencies.

- **MCP Servers**: Standalone programs exposing tools, resources, and prompts over a standardized JSON-RPC protocol. They provide *external connectivity* to GitHub, databases, APIs, browsers. Expensive at scale — a five-server setup can consume ~55,000 tokens before any conversation starts (now mitigated by Tool Search).

- **Plugins**: Distributable bundles combining skills, MCP configs, slash commands, subagents, and hooks. Plugins launched January 30, 2026 in research preview; went GA on Cowork April 9, 2026. The official `claude-plugins-official` repo has 101 curated plugins.

- **Hooks**: Event-driven JSON handlers triggering shell commands on lifecycle events (tool use, session changes, file modifications). Deterministic automation layer.

> *"A skill is a cheat sheet, a plugin is a toolkit, and an MCP server is a bridge to another application."* — dev.to/raxxostudios

> *"Skills teach Claude how to perform tasks...MCP connects Claude to external tools and data sources. Skills are for procedural knowledge; MCP is for external connectivity."* — morphllm.com

> *"Claude Code is a framework for orchestrating AI agents, and most people use one or two features without seeing how they stack together."* — alexop.dev

**Platforms:** Web, HN
**Key URLs:**
- Full taxonomy: https://www.morphllm.com/claude-code-skills-mcp-plugins
- Architecture explainer: https://alexop.dev/posts/understanding-claude-code-full-stack/
- Skills vs MCP comparison: https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k
- Official plugins docs: https://code.claude.com/docs/en/plugins
- Official plugin marketplace: https://github.com/anthropics/claude-plugins-official

---

### 3. The Marketplace Explosion: 500K+ Skills, Competing Registries

The skills ecosystem has grown from zero to massive scale in under 18 months:

| Platform | Skills | Notes |
|----------|--------|-------|
| SkillsMP | 900,000+ | Independent community; aggregates from GitHub; 425K browseable |
| LobeHub Skills | 169,739 | Quality checks + community feedback |
| agentskill.sh | 110,000+ | 20+ AI tools; security scores on listings |
| skills.sh | 87,000+ | Vercel-backed; public leaderboard |
| ClawHub (OpenClaw) | 20,000+ | 5,400 in curated awesome-openclaw-skills list |
| tonsofskills.com | 2,849 + 423 plugins | ccpi CLI package manager; 2.1k GitHub stars |
| claudemarketplaces.com | 2,500+ marketplaces | 110,000+ monthly visitors |
| Official Anthropic | 101 plugins | claude-plugins-official; curated, high-quality |

The top skill on skills.sh, Vercel's "find-skills," has 579,000+ installs. New skills publish at 147/day on average. The `microsoft/skills` repo (2.2k stars) provides 132 skills across Python, TypeScript, .NET, Java, and Rust with 1,158 test scenarios — emphasizing quality: *"Loading all skills causes context rot: diluted attention, wasted tokens, conflated patterns."*

The `jeremylongshore/claude-code-plugins-plus-skills` repo (2.1k stars) offers 423 plugins, 2,849 skills, and 177 agents with a CLI package manager (`ccpi`) and web marketplace at tonsofskills.com, including 106 SaaS-specific skill packs.

**Platforms:** Web, GitHub
**Key URLs:**
- SkillsMP: https://skillsmp.com/
- skills.sh leaderboard: https://skills.sh/
- agentskill.sh: https://agentskill.sh/ (via https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)
- KDnuggets top 5: https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
- SkillsMP review: https://smartscope.blog/en/blog/skillsmp-marketplace-guide/
- tonsofskills.com repo: https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- Microsoft skills: https://github.com/microsoft/skills
- ClawHub: https://github.com/openclaw/clawhub
- VoltAgent awesome skills: https://github.com/VoltAgent/awesome-agent-skills
- Daily top skills (April 16): https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026
- Marketplace directory: https://claudemarketplaces.com/

---

### 4. MCP at Scale: Context Bloat Crisis and the Tool Search Solution

MCP has grown explosively — 10,000+ active public servers, 97 million monthly SDK downloads — but that scale revealed a structural problem: loading all MCP tool definitions at session start could consume 77K+ tokens before any work begins.

On January 14, 2026, Anthropic shipped **MCP Tool Search** (lazy loading) as the solution. The mechanism:
- Activates automatically when MCP tools would exceed 10% of context window
- Defers tool definitions with `defer_loading: true`
- Injects a lightweight Tool Search tool instead (~5K tokens)
- Loads 3-5 relevant tools (~3K tokens) per query on-demand via BM25 or regex matching
- Result: 95% reduction in initial context consumption; 195K tokens available vs. 92K before

@WesRothMoney on X: *"Anthropic is rolling out MCP Tool Search for Claude Code, addressing one of the most requested GitHub features: lazy loading for MCP servers. Tool Search now lets Claude Code dynamically fetch tools only when needed. If the tool descriptions exceed 10% of context, they're [deferred]."*

The HN thread on a competing context-reduction server (570 points, 107 comments) shows deep community engagement with this problem. The community debate: does aggressive compression create blind spots? Key technical debate — `re5i5tor` noted that `context-mode cannot intercept MCP tool responses` since they flow via JSON-RPC directly; author (`mksglu`) countered with SQLite FTS5 BM25 ranking in isolated subprocesses.

OpenAI filed a GitHub issue to implement the same pattern in Codex (issue #9266) and VS Code filed one too (issue #288310), confirming Tool Search is becoming a de facto standard.

**Platforms:** Web, HN, X/Twitter, GitHub
**Key URLs:**
- Tool Search explainer: https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search
- X post: https://x.com/WesRothMoney/status/2011785440140149034
- HN context reduction thread: https://news.ycombinator.com/item?id=47193064
- Lazy-load GitHub issue: https://github.com/anthropics/claude-code/issues/11364
- Medium explainer: https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc
- lazy-mcp community proxy: https://github.com/voicetreelab/lazy-mcp
- OpenAI Codex issue: https://github.com/openai/codex/issues/9266
- VS Code issue: https://github.com/microsoft/vscode/issues/288310

---

### 5. Multi-Agent Orchestration: Managing MCP Across Multiple AI Tools

A recurring pain point: developers using Claude Code, Cursor, Codex CLI, and Gemini CLI each have their own config files for MCP servers. Adding a single server requires manually updating 4-6 different configs.

Show HN: "Agents – Sync MCP Configs Across Claude, Cursor, Codex Automatically" ([HN #46926648](https://news.ycombinator.com/item?id=46926648)) addresses this directly with a unified config sync tool.

Show HN: "Roundtable MCP" ([HN #45374908](https://news.ycombinator.com/item?id=45374908)) goes further — it orchestrates Claude Code, Cursor, Gemini, and Codex in parallel via MCP, enabling specialized parallel code reviews: *"Takes 2-5 minutes vs 20+ minutes of manual copy-paste coordination."* Architecture: `Your IDE → MCP Server → Multiple AI CLIs (parallel execution)`.

The "Ask HN: How do you manage multiple MCP servers in Claude Code?" thread ([HN #45114196](https://news.ycombinator.com/item?id=45114196)) reveals a practical community workaround: `__warlord__` advises *"Use subagents with access to dedicated tools"* and *"Build slash commands with high level directives."* Emerging consolidation tools cited: aci.dev, ibm-contextforge, hyprmcp.com.

**Platforms:** HN, Web
**Key URLs:**
- Config sync Show HN: https://news.ycombinator.com/item?id=46926648
- Roundtable MCP Show HN: https://news.ycombinator.com/item?id=45374908
- Multi-MCP management Ask HN: https://news.ycombinator.com/item?id=45114196
- MCP gateway registry: https://github.com/agentic-community/mcp-gateway-registry
- Best-of MCP servers: https://github.com/tolkonepiu/best-of-mcp-servers

---

### 6. Domain-Specific MCP Innovation: Finance, Remote Access, Terminal Control

Three Show HN submissions illustrate MCP innovation at the edges:

**LangAlpha** ([HN #47766370](https://news.ycombinator.com/item?id=47766370), 148 points, 54 comments): Finance-specific Claude Code. Problem: standard MCP financial data calls dump "tens of thousands of tokens into the context window" — data vendor schema definitions alone can consume 50K+ tokens. Solution: auto-generates typed Python modules from MCP schemas instead of embedding tool definitions. Adds persistent research workspaces (memory file + file index) for multi-session investing where *"You update the model when earnings drop, re-run comps when a competitor reports."*

**ht-mcp** ([HN #44310783](https://news.ycombinator.com/item?id=44310783)): A Rust MCP server giving AI coding tools (Claude Code, Cursor) a headless terminal interface — agents see and interact with terminals exactly as humans do.

**Claw** ([HN #47216532](https://news.ycombinator.com/item?id=47216532)): MCP server that deploys a lightweight Go binary over SSH to remote machines, extending agent tools to any server: *"It's an MCP server that deploys a small Go binary over SSH and gives your agent the same tools it already knows (bash, read, write, edit, grep, glob) on any remote machine."* No open ports, daemons, or root access required.

**Platforms:** HN
**Key URLs:**
- LangAlpha HN: https://news.ycombinator.com/item?id=47766370
- ht-mcp HN: https://news.ycombinator.com/item?id=44310783
- Claw HN: https://news.ycombinator.com/item?id=47216532
- Remote MCP in Claude Code: https://news.ycombinator.com/item?id=44312363
- Claude Code history UI MCP: https://news.ycombinator.com/item?id=46500801

---

### 7. Routines and Scheduled Automations: Running Claude When You're Offline

A major capability unlock arrived April 14, 2026: **Routines** in research preview — cloud-hosted automations running on Anthropic's infrastructure, not locally. Key distinction from the February 2026 Scheduled Tasks feature (which required the computer to be on).

Anthropic's framing: *"Developers already use Claude Code to automate the software development cycle, but until now, they've managed cron jobs, infrastructure, and additional tooling like MCP servers themselves. Routines ship with access to your repos and your connectors, so you can package up automations and set them to run on a schedule or trigger."*

Routine triggers: schedule (cron), GitHub events (webhooks), API triggers from user code. Rate limits by tier: Pro=5/day, Max=15/day, Team/Enterprise=25/day.

This shipped alongside a redesigned Claude Code interface featuring parallel sessions, integrated terminal, file editing, HTML/PDF preview, and customizable drag-and-drop layout.

**Platforms:** Web
**Key URLs:**
- 9to5Mac coverage: https://9to5mac.com/2026/04/14/anthropic-adds-repeatable-routines-feature-to-claude-code-heres-how-it-works/
- Cowork plugins blog post: https://claude.com/blog/cowork-plugins
- Enterprise deployment guide: https://systemprompt.io/guides/claude-cowork-plugins-enterprise
- "Claude Code can now do your job overnight": https://thenewstack.io/claude-code-can-now-do-your-job-overnight/
- Full 2026 changelog: https://claudefa.st/blog/guide/changelog
- Complete Q1 2026 update guide: https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide
- FindSkill Cowork guide: https://findskill.ai/blog/claude-cowork-guide/

---

### 8. The Security Crisis: ToxicSkills and the Supply Chain Problem

The rapid proliferation of agent skills has created a new software supply chain security problem. Snyk's **ToxicSkills** research (published February 5, 2026) is the landmark finding:

- **3,984 skills** scanned across ClawHub and skills.sh
- **13.4%** (534) contain at least one critical security issue
- **36.82%** (1,467) have at least one security flaw of any severity
- **76 confirmed malicious payloads** identified via human-in-the-loop review
- **8 malicious skills** remain live on ClawHub as of publication
- **91%** of malicious skills combine prompt injection with traditional malware

The key attack surface: *"Unlike traditional packages that execute in isolated contexts, Agent Skills operate with the full permissions of the AI agent they extend."* And: *"If you've installed one in the past month, there's a 13% chance it contains a critical security flaw and a non-zero chance it's actively exfiltrating your credentials right now."*

60% of risk lives in the instruction layer — the markdown itself, not the scripts. Named threat actors: `zaycv` (40+ programmatically generated malicious skills), `Aslaep123` (crypto credential theft), `pepe276` and `moonshine-100rze` (Unicode obfuscation).

Responses to the crisis:
- **Snyk + Vercel partnership**: "Security Verified" badge system on skills.sh; integrated scanning before install; 90-100% recall, 0% false positive rate on legitimate skills
- **Snyk Agent Scan** (open source): CLI scanner detecting 15+ risk types including prompt injection, tool poisoning, toxic flows, hardcoded secrets
- **OWASP Agentic Skills Top 10**: New security framework specifically for agent skills
- **mcpskills.io**: "Is Your AI Skill Safe?" — community safety check tool
- The dev.to article notes: *"Custom skills outperform generic marketplace options. The biggest ROI comes from project-specific skills encoding team conventions rather than downloading generic community skills."*

**Platforms:** Web, GitHub
**Key URLs:**
- ToxicSkills research: https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/
- Snyk + Vercel partnership: https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/
- Snyk agent-scan repo: https://github.com/snyk/agent-scan
- Agent Scan - Skill Inspector: https://labs.snyk.io/experiments/skill-scan/
- OWASP Agentic Skills Top 10: https://owasp.org/www-project-agentic-skills-top-10/
- MCP Skills safety checker: https://mcpskills.io/
- What ToxicSkills means for OpenClaw users: https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/
- Snyk Evo AI-SPM launch: https://techspective.net/2026/03/24/snyk-launches-evo-ai-spm-to-govern-autonomous-coding-agents/
- SKILL.md shell access threat model: https://snyk.io/articles/skill-md-shell-access/

---

### 9. Ecosystem Architecture: The "Three-Pillar" 2026 Connectivity Stack

A recurring architectural insight from analysts and practitioners: the most capable 2026 agents don't choose one mechanism — they combine all three seamlessly:

1. **Skills** (portable, reusable capability files) — for procedural knowledge
2. **CLI / Computer Use** (local sandbox for file-based tasks)
3. **MCP** (rich semantics for long-running, platform-independent work)

The progressive discovery principle — rather than loading all tools upfront, agents query for relevant tools on-demand — is becoming the design standard for both skills (on-demand frontmatter-driven loading) and MCP (Tool Search).

Key quote from Anand Topu (Medium): *"The most capable 2026 agents will not pick one but they will combine all three seamlessly depending on the task."*

Architectural quote from alexop.dev: *"Claude Code is a framework for orchestrating AI agents, and most people use one or two features without seeing how they stack together."*

Practical recommendation from morphllm.com: *"Most developers need 2-3 MCP servers (GitHub, Filesystem, one domain-specific) + a few custom Skills for their workflow."*

**Platforms:** Web
**Key URLs:**
- Future of MCP (Medium): https://anandtopu.medium.com/the-future-of-mcp-how-agents-get-connected-in-2026-ee24d62c0c43
- Claude Code full stack: https://alexop.dev/posts/understanding-claude-code-full-stack/
- Skills vs MCP vs Plugins: https://www.morphllm.com/claude-code-skills-mcp-plugins
- MCP roadmap: https://www.getknit.dev/blog/the-future-of-mcp-roadmap-enhancements-and-whats-next
- New Stack MCP growing pains: https://thenewstack.io/model-context-protocol-roadmap-2026/
- MCP Wikipedia: https://en.wikipedia.org/wiki/Model_Context_Protocol
- MCP specification: https://modelcontextprotocol.io/specification/2025-11-25
- MCP servers repo: https://github.com/modelcontextprotocol/servers

---

## Cross-Source Patterns

### Pattern 1: Context window is the central constraint across all extension mechanisms
- **Platforms:** HN (multiple threads), X/Twitter, Web, GitHub issues
- Every major 2026 development — MCP Tool Search, skills lazy loading, the 30-50 token skills design, domain-specific MCP compression (LangAlpha) — is a response to context window pressure
- HN 47193064 (570 pts): community debate whether 98% context reduction creates dangerous blind spots
- @WesRothMoney: "dynamically fetch tools only when needed" as the core principle
- Microsoft skills repo warning: "Loading all skills causes context rot: diluted attention, wasted tokens, conflated patterns"

### Pattern 2: Cross-platform interoperability is collapsing the AI tool fragmentation
- **Platforms:** Web, HN, GitHub
- SKILL.md standard: 32 tools in 3 months all reading same format
- MCP config sync tools addressing multi-IDE friction
- OpenAI Codex and VS Code implementing identical lazy-loading patterns
- AAIF growing to 146 members in 2 months

### Pattern 3: Supply chain security is the ecosystem's biggest unsolved problem
- **Platforms:** Web, GitHub
- 13.4% critical security issues in scanned skills (Snyk Feb 2026)
- OWASP created an "Agentic Skills Top 10" — signals the problem is taken seriously
- The attack surface is novel: markdown instructions that operate with full agent permissions
- Community guidance converging on "build your own, don't install random marketplace skills"

### Pattern 4: Finance and enterprise are the highest-value MCP use cases — and the hardest to serve
- **Platforms:** HN, Web
- LangAlpha (148 pts, 54 comments) shows strong interest but also skepticism about AI in finance without rigorous benchmarks
- Context token costs are disproportionately high for structured financial/enterprise data
- Enterprise Claude Marketplace launched March 2026 (Replit, GitLab, Harvey, Snowflake partners)

---

## Per-Platform Tables

### Hacker News

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| mksglu | MCP server that reduces Claude Code context consumption by 98% | 570 | 107 | "only stdout enters context through SQLite FTS5 with BM25 ranking" | https://news.ycombinator.com/item?id=47193064 |
| (various) | Show HN: LangAlpha – what if Claude Code was built for Wall Street? | 148 | 54 | "dumps tens of thousands of tokens into the context window" | https://news.ycombinator.com/item?id=47766370 |
| (various) | Remote MCP Support in Claude Code | N/A | N/A | HTTPS support and API standardization discussed | https://news.ycombinator.com/item?id=44312363 |
| (various) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | N/A | N/A | — | https://news.ycombinator.com/item?id=43410866 |
| (various) | Show HN: Agents – Sync MCP Configs Across Claude, Cursor, Codex | N/A | N/A | "adding a server requires manually updating 4-6 different configs" | https://news.ycombinator.com/item?id=46926648 |
| (various) | Ask HN: How do you manage multiple MCP servers in Claude Code? | 2 | 4 | "Use subagents with access to dedicated tools" | https://news.ycombinator.com/item?id=45114196 |
| (various) | Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex | 2 | 3 | "Takes 2-5 minutes vs 20+ minutes of manual copy-paste coordination" | https://news.ycombinator.com/item?id=45374908 |
| (various) | Show HN: UI and MCP server for analyzing Claude Code history | N/A | N/A | — | https://news.ycombinator.com/item?id=46500801 |
| (various) | Show HN: Claw – Let your AI agent operate any machine as if it were local | 2 | N/A | "no open ports, background daemons, or root access" | https://news.ycombinator.com/item?id=47216532 |

### X/Twitter

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @WesRothMoney | "Anthropic is rolling out MCP Tool Search for Claude Code, addressing one of the most requested GitHub features: lazy loading for MCP servers..." | N/A | N/A | https://x.com/WesRothMoney/status/2011785440140149034 |

### YouTube

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | N/A | N/A | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| (unknown) | My Claude Code System For Viral TikTok Videos | N/A | N/A | No | https://www.youtube.com/watch?v=lw69SOTKRM4 |
| (various) | Claude Code Tutorial playlist | N/A | N/A | No | https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY |

### TikTok

| Creator | Caption Snippet | Views | Likes | URL |
|---------|----------------|-------|-------|-----|
| @rileybrown.ai | "CLAUDE MCP TUTORIAL — Claude is an AI Agent! You can give it access to many tools using MCP (And it will decide which one to use)" | N/A | N/A | https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559 |
| @taki.gpt | "Claude MCP is crazy smart 🧠 It plans, writes, codes like 10 assistants in one! #claude #ai #mcp #aitools #productivityhack #anthropic" | N/A | N/A | https://www.tiktok.com/@taki.gpt/video/7534464076173331718 |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search | MCP Tool Search 95% context reduction, before/after stats |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers for Claude Code in 2026 |
| claudefa.st | https://claudefa.st/blog/guide/changelog | Claude Code full 2026 changelog |
| VentureBeat | https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard | Agent Skills open standard launch announcement |
| VentureBeat | https://venturebeat.com/technology/anthropic-launches-claude-marketplace-giving-enterprises-access-to-claude | Claude Enterprise Marketplace launch (Replit, GitLab, Harvey, Snowflake) |
| 9to5Mac | https://9to5mac.com/2026/04/14/anthropic-adds-repeatable-routines-feature-to-claude-code-heres-how-it-works/ | Routines feature detailed breakdown, tier limits |
| Snyk | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | ToxicSkills: 13.4% critical issues, 76 malicious payloads found |
| Snyk | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Snyk+Vercel partnership for skills.sh security badges |
| Snyk | https://snyk.io/articles/skill-md-shell-access/ | SKILL.md → shell access threat model |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplace comparison |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Best architectural overview of the full extension stack |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins complete guide |
| DEV Community | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Top skills (GSD, Frontend Design, Simplify, Commit) and MCP servers |
| DEV Community | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills by category (Dev, Productivity, Frontend) |
| Medium (Anand Topu) | https://anandtopu.medium.com/the-future-of-mcp-how-agents-get-connected-in-2026-ee24d62c0c43 | Three-pillar connectivity stack analysis |
| Medium (JP Caparas) | https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cu | Lazy loading for MCP tools explainer (January 2026) |
| GitHub Discussion | https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585 | Skills Over MCP Interest Group April 14 office hours notes |
| paperclipped.de | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | Agent Skills open standard interoperability guide |
| paperclipped.de | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | SKILL.md, Skills.sh & SkillsMP developer guide |
| OWASP | https://owasp.org/www-project-agentic-skills-top-10/ | Agentic Skills Top 10 security framework |
| SkillsMP | https://skillsmp.com/ | 900K+ skills marketplace |
| skills.sh | https://skills.sh/ | Vercel-backed skills directory and leaderboard |
| MCPMarket | https://mcpmarket.com/daily/top-mcp-server-list-april-26-2026 | Top MCP servers April 26, 2026 |
| MCPMarket | https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026 | Top agent skills April 16, 2026 |
| MCPMarket | https://mcpmarket.com/tools/skills | Agent Skills Directory for Claude, ChatGPT & Codex |
| OpenClaw | https://github.com/openclaw/clawhub | ClawHub skill registry for OpenClaw |
| skywork.ai | https://skywork.ai/skypage/en/clawhub-openclaw-skill-registry/2038573559848898560 | ClawHub registry guide |
| HackerNoon | https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it | CLI vs MCP ecosystem pivot analysis |
| systemprompt.io | https://systemprompt.io/guides/getting-started-anthropic-marketplace | Anthropic Marketplace plugin install guide |
| systemprompt.io | https://systemprompt.io/guides/claude-cowork-plugins-enterprise | Enterprise Cowork plugins deployment |
| Strapi | https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them | What are Agent Skills and how to use them |
| New Stack | https://thenewstack.io/claude-code-can-now-do-your-job-overnight/ | Routines feature analysis |
| New Stack | https://thenewstack.io/model-context-protocol-roadmap-2026/ | MCP growing pains and 2026 roadmap |
| techspective.net | https://techspective.net/2026/03/24/snyk-launches-evo-ai-spm-to-govern-autonomous-coding-agents/ | Snyk Evo AI-SPM launch for agent governance |
| skillshield.dev | https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/ | ToxicSkills impact for OpenClaw users |
| mcpskills.io | https://mcpskills.io/ | MCP skills safety checker |
| smartscope.blog | https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ | SkillsMP marketplace review |
| buildtolaunch.substack | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | Best Claude Code plugins (10 tested, 4 worth keeping) |
| aimaker.substack | https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide | Complete Q1 2026 Claude update guide |
| the-ai-corner.com | https://www.the-ai-corner.com/p/everything-claude-shipped-2026-complete-guide | Everything Claude shipped in 2026 |
| devops.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | Agent Skills for custom AI workflows |
| aibusiness.com | https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude | Anthropic Skills Open Standard launch |
| Anthropic | https://code.claude.com/docs/en/mcp | Official MCP docs |
| Anthropic | https://code.claude.com/docs/en/plugins | Official plugins docs |
| Anthropic | https://code.claude.com/docs/en/sub-agents | Official subagents docs |
| claude.com | https://claude.com/blog/cowork-plugins | Cowork plugins announcement |
| Composio | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP integration with Claude Code |
| Composio | https://composio.dev/toolkits/twitter/framework/claude-code | Twitter MCP integration |
| releasebot.io | https://releasebot.io/updates/anthropic/claude | Claude April 2026 release notes |
| findskill.ai | https://findskill.ai/blog/claude-cowork-guide/ | Claude Cowork guide 2026 |
| cashandcache.substack | https://cashandcache.substack.com/p/claude-just-had-a-crazy-2026-the | 18 features Claude shipped in 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads directly found (discussed via aggregators/summaries)
├─ 🔵 X: 1 post │ N/A likes │ N/A reposts
├─ 🔴 YouTube: 3 videos │ N/A views
├─ 🟢 HN: 9 stories │ 626 points │ 174 comments
├─ 🟣 TikTok: 2 videos │ N/A views
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 50+ pages
└─ 🗣️ Top voices: @WesRothMoney, @rileybrown.ai, @taki.gpt │ HN: mksglu (MCP context reduction), LangAlpha team
```

---

## Data Gaps

- **Reddit**: No direct Reddit thread results found for this topic — site-specific searches returned no matches; community discussion known to exist in r/ClaudeAI, r/LocalLLaMA, r/vibecoding (referenced in aggregator content) but individual threads not surfaced
- **X/Twitter**: Only one X post found with specific attribution (@WesRothMoney); broader X discussion exists per aggregator summaries (e.g., 226 Claude Code community mentions cited) but individual tweets not retrievable due to auth restrictions
- **YouTube**: Video metadata (views, likes, transcript) not accessible — YouTube pages return only navigation/footer content; video titles and URLs confirmed but stats unknown
- **TikTok**: View counts and like counts not accessible via web scraping; 2 relevant videos confirmed
- **HN engagement stats**: Points/comments retrieved for 3 of 9 HN threads; 6 threads showed minimal engagement (2 points) or returned 429 errors
- **Rate limiting**: Multiple WebFetch calls returned 429 (rate limited) or 403 (blocked) including VentureBeat, HackerNoon, several HN threads
- **Coverage estimate**: ~75% of the web content landscape covered; Reddit and X/Twitter social layers at ~15% coverage; video platform metadata at 0%

---

## Key Quotes

> "If you've installed one in the past month, there's a 13% chance it contains a critical security flaw and a non-zero chance it's actively exfiltrating your credentials right now." — Snyk ToxicSkills research ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Unlike traditional packages that execute in isolated contexts, Agent Skills operate with the full permissions of the AI agent they extend." — Snyk ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Anthropic is rolling out MCP Tool Search for Claude Code, addressing one of the most requested GitHub features: lazy loading for MCP servers. Tool Search now lets Claude Code dynamically fetch tools only when needed." — @WesRothMoney on X ([link](https://x.com/WesRothMoney/status/2011785440140149034))

> "Agents don't know what they don't know." — Pedro Rodrigues (Supabase), Skills Over MCP Interest Group April 14, 2026 ([link](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585))

> "Claude Code is a framework for orchestrating AI agents, and most people use one or two features without seeing how they stack together." — alexop.dev ([link](https://alexop.dev/posts/understanding-claude-code-full-stack/))

> "The most capable 2026 agents will not pick one but they will combine all three seamlessly depending on the task." — Anand Topu, Medium ([link](https://anandtopu.medium.com/the-future-of-mcp-how-agents-get-connected-in-2026-ee24d62c0c43))

> "A skill is a cheat sheet, a plugin is a toolkit, and an MCP server is a bridge to another application." — dev.to/raxxostudios ([link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4))

> "Takes 2-5 minutes vs 20+ minutes of manual copy-paste coordination." — Roundtable MCP creator, HN ([link](https://news.ycombinator.com/item?id=45374908))

> "It's an MCP server that deploys a small Go binary over SSH and gives your agent the same tools it already knows (bash, read, write, edit, grep, glob) on any remote machine." — Claw creator, HN ([link](https://news.ycombinator.com/item?id=47216532))

> "Loading all skills causes context rot: diluted attention, wasted tokens, conflated patterns." — Microsoft skills repo ([link](https://github.com/microsoft/skills))
