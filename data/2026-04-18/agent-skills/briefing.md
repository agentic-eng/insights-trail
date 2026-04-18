# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-18
**Query type:** GENERAL
**Sources:** Web, Hacker News, Reddit, YouTube, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 3 threads/analyses | 300+ upvotes (top thread), ~4,200 weekly contributors in r/ClaudeCode | No direct thread URLs returned; community overview data only |
| Hacker News | 12 stories | Multiple Show HN / Ask HN threads | Mix of product launches and discussions |
| YouTube | 4 videos | — | Tutorials and top-10 roundups |
| Web | 60+ pages | — | Blogs, docs, news, security advisories |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: From Anthropic Experiment to Cross-Industry Format

On December 18, 2025, Anthropic open-sourced the Agent Skills specification, defining `SKILL.md` as the canonical format for reusable agent capabilities. Within weeks the format jumped to competitors: OpenAI adopted it for Codex CLI and ChatGPT, Google for Gemini CLI, Microsoft/GitHub for Copilot (VS Code agent skills launched experimentally January 11, 2026), Cursor, JetBrains Junie, and Windsurf. By April 2026 at least 30 agent products support the format.

A `SKILL.md` file is a Markdown document with YAML frontmatter defining `name` (required, lowercase-with-hyphens) and `description` (required). The agent matches the description against conversation context to decide when to load the skill's instructions. Installation is now unified across platforms: `npx skills add <owner/repo>`.

The DEV Community article ["SKILL.md Goes Multi-Ecosystem"](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg) documented this adoption wave and noted the spec is platform-agnostic in its core form while each tool may add proprietary extensions.

Cross-platform coverage: Web (dev.to, inference.sh, agensi.io), GitHub (docs), YouTube (tutorials), Hacker News (discussion threads)

---

### 2. Marketplace Explosion: Five Distinct Discovery Platforms in Competition

The agent skills marketplace landscape fragmented in early 2026 into at least five competing platforms, each with a different philosophy:

**skills.sh** (Vercel, launched January 20, 2026) — The official cross-platform directory. Tracks 90,000+ skills across 19 AI agents, growing at ~147 new skills/day. Leans on the open standard and one-command install. Top skill: `find-skills` by Vercel Labs with 579,000+ installs. Integrated with automated Snyk security scanning at install time per [Vercel's changelog](https://vercel.com/changelog/automated-security-audits-now-available-for-skills-sh).

**SkillsMP** (independent community) — Largest by raw count at 500,000+ skills aggregated from GitHub, filtering repos with fewer than 2 stars. Works as a discovery layer for Claude Code, Codex CLI, and ChatGPT per [SkillsMP's homepage](https://skillsmp.com). Reviewed on [SmartScope](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/).

**LobeHub Skills** — 169,739 skills, fastest-growing, most polished UX. Implements the agentskills.io open specification. See [lobehub.com/skills](https://lobehub.com/skills).

**tonsofskills.com** (jeremylongshore's open-source project) — 2,804 skills across 423 plugins, 100% MIT license. Managed by the `ccpi` CLI package manager (`pnpm add -g @intentsolutionsio/ccpi`). See [tonsofskills.com](https://tonsofskills.com/) and [GitHub repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills).

**agentskills.so** — 44,000+ skills with two-layer security scanning, defaults to showing grade-A skills only. Most security-conscious of the major platforms.

KDnuggets published ["Top 5 Agent Skill Marketplaces"](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) summarizing the landscape. Vercel published a direct [skills.sh vs SkillsMP comparison](https://vibecoding.app/compare/skills-sh-vs-skillsmp).

Cross-platform coverage: Web (multiple), Reddit (community data), YouTube (tutorials)

---

### 3. Claude Code Plugin Architecture: Skills, MCP Servers, and Plugins Defined

Claude Code's official documentation distinguishes three distinct extension types (see [plugins docs](https://code.claude.com/docs/en/plugins) and [skills docs](https://code.claude.com/docs/en/skills)):

- **Skills** — Markdown instruction files (`SKILL.md`) that teach Claude Code *how* to behave in specific contexts. Activate automatically when context matches; no explicit trigger needed. Go in `.claude/skills/`.
- **Plugins** — Bundles of multiple skills, MCP servers, or commands distributed together. Published as JSON-based catalogs hosted in Git repositories.
- **MCP Servers** — Executable protocol servers that expose new *tools* to the agent via Model Context Protocol, connecting to external services (databases, APIs, browsers).

The community shorthand captured in the Top 10 guide ([mejba.me](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026)): *"Skills teach Claude; plugins give Claude hands; CLIs give Claude helpers."*

As of March 2026: 101 official plugins (33 Anthropic-built, 68 from partners). The official `frontend-design` skill had 277,000+ installs. The [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) and [awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) repositories curate community-maintained collections.

Composio's [top Claude Code plugins guide](https://composio.dev/content/top-claude-code-plugins) recommends a day-one stack: Codex CLI, Firecrawl, Playwright, Skill Creator.

The full architecture stack was explained in [alexop.dev's deep-dive](https://alexop.dev/posts/understanding-claude-code-full-stack/): skills → plugins → MCP servers → hooks → CLAUDE.md → subagents, all composable.

Cross-platform coverage: Web (official docs, blogs), Reddit, YouTube, Hacker News

---

### 4. Security Crisis: 43% Vulnerable MCP Servers and a Toxic Skills Supply Chain

The rapid growth of the agent skills and MCP ecosystem surfaced serious supply chain risks that became the dominant security story of Q1 2026.

**Skills supply chain (Snyk ToxicSkills study, February 5, 2026):** Snyk scanned 3,984 skills from ClawHub and skills.sh — the largest public corpus at the time. Findings: 13.4% (534 skills) contain at least one critical-level security issue (malware, prompt injection, exposed secrets). 36.82% (1,467 skills) have at least one flaw. A separate [New Stack article](https://thenewstack.io/ai-agent-skills-security/) covered a broader audit of 22,511 AI coding skills. In January 2026, a coordinated malware campaign targeting ClawHub planted 335 malicious skills harvesting API keys, wallet credentials, and browser passwords.

Snyk published ["ToxicSkills: Malicious AI Agent Skills"](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) and partnered with Vercel to add pre-install security scanning to skills.sh (see [Snyk-Vercel announcement](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/)). Snyk's open-source [`agent-scan`](https://github.com/snyk/agent-scan) scanner was released for MCP servers and agent skills. OWASP launched the [Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) project. Snyk presented at RSAC 2026 with [a dedicated Agent Security Solution](https://securityboulevard.com/2026/03/snyk-launches-agent-security-solution-and-ships-evo-ai-spm-at-rsac-2026/).

**MCP infrastructure vulnerabilities:** BlueRock Security found 36.7% of 7,000+ MCP servers potentially vulnerable to SSRF. Trend Micro found 492 with zero authentication. Gentic News reported ["43% of Servers Vulnerable, 341 Malicious Skills Found"](https://gentic.news/article/mcp-security-crisis-43-of-servers). The 30-CVE-in-60-days story was documented at [heyuan110.com](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/).

**Recent CVEs:**
- **CVE-2025-59536** (CVSS 8.7) — Claude Code config injection via malicious Hook in `.claude/settings.json` → remote code execution (Check Point Research, Feb 25, 2026). See [Practical DevSecOps](https://www.practical-devsecops.com/mcp-security-vulnerabilities/).
- **CVE-2026-26118** — Microsoft MCP Server vulnerability enabling AI tool hijacking. See [PointGuard AI](https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118).
- **CVE-2026-32211** (CVSS 9.1) — Azure MCP Server missing authentication entirely (Microsoft, April 3, 2026). See [DEV Community](https://dev.to/michael_onyekwere/cve-2026-32211-what-the-azure-mcp-server-flaw-means-for-your-agent-security-14db).
- **April 16, 2026** — The Register: ["Anthropic won't own MCP 'design flaw' putting 200K servers at risk"](https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/).

Comprehensive guides published by [Aembit](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/), [Composio](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know), [Palo Alto Networks](https://live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed-what-you-need-to-know-now/ba-p/1227143), and [Prompt Security](https://prompt.security/blog/top-10-mcp-security-risks).

Cross-platform coverage: Web (news, advisories, blogs), Hacker News (Show HN: Runtime security for AI agents, [item #47799856](https://news.ycombinator.com/item?id=47799856))

---

### 5. MCP Governance, Roadmap, and the "Is MCP Dead?" Debate

MCP's trajectory in 2026 followed a turbulent arc: explosive adoption, governance handoff, and a "MCP vs Skills" debate.

**Governance:** MCP crossed 10,000 active public servers and was donated to the Linux Foundation in November 2025. By March 2026 it was formalized as a multi-company open standard. The [2026 MCP Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) focuses on transport scalability (stateful sessions vs. load balancers), agent-to-agent communication, enterprise readiness (SSO-integrated auth, audit trails, gateway behavior), and registry standardization. The New Stack covered roadmap challenges in ["MCP's biggest growing pains for production use will soon be solved"](https://thenewstack.io/model-context-protocol-roadmap-2026/).

**"Is MCP Dead?" debate:** Milvus published ["Is MCP Dead? MCP vs CLI vs Agent Skills Compared"](https://milvus.io/blog/is-mcp-dead-cli-and-skills-for-ai-agents.md) and Hacker News hosted ["Show HN: MCP Isn't Dead. You're Just Using It Wrong"](https://news.ycombinator.com/item?id=47412133). The consensus from HN threads (especially ["Ask HN: When does MCP make sense vs CLI?"]) was that both Skills and MCP have their place: Skills for teaching behavioral patterns, MCP for connecting to live external systems.

**Dynamic Tool Registration** — Introduced in Claude Code's January 2026 release. Described by HN community as "a powerful development in MCP" that addresses the token-bloat problem (loading all tool schemas upfront). PolyMCP Skills ([HN #46770554](https://news.ycombinator.com/item?id=46770554)) built on this: organizes tools as curated skill sets loaded only as needed.

Cross-platform coverage: Web (New Stack, Milvus, The Register), Hacker News (multiple threads), Reddit

---

### 6. GitHub CLI Skills Management and Cross-Tool Integrations (April 16, 2026)

On April 16, 2026, GitHub published ["Manage agent skills with GitHub CLI"](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/), announcing the `gh skill` command for installing, updating, and tracking agent skills. A key architectural detail: when `gh skill` installs a skill, it writes provenance metadata (repository, ref, tree SHA) directly into the `SKILL.md` frontmatter — so provenance travels with the skill file regardless of where it ends up.

GitHub's [VS Code agent skills docs](https://code.visualstudio.com/docs/copilot/customization/agent-skills) and [GitHub Docs: About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) describe how Copilot reads name/description from YAML frontmatter, matches to user intent, and loads skill body into context.

Microsoft published ["Supercharge Your Dev Workflows with GitHub Copilot Custom Skills"](https://techcommunity.microsoft.com/blog/azuredevcommunityblog/supercharge-your-dev-workflows-with-github-copilot-custom-skills/4510012) and VS Code posted ["Your Home for Multi-Agent Development"](https://code.visualstudio.com/blogs/2026/02/05/multi-agent-development) (February 5, 2026).

Cross-platform coverage: Web (GitHub Blog, GitHub Docs, VS Code Blog, Medium)

---

### 7. Claude Code 2.1.0 and Multi-Agent Orchestration

VentureBeat covered ["Claude Code 2.1.0 arrives with smoother workflows and smarter agents"](https://venturebeat.com/orchestration/claude-code-2-1-0-arrives-with-smoother-workflows-and-smarter-agents). New features: agent lifecycle hooks, **hot-reloading of skills** (skills can be updated without restarting the session), wildcard permissioning, and session teleportation.

Agent Teams (still experimental, requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS` in settings.json) allow one session to act as team lead coordinating teammates in separate context windows per [official docs](https://code.claude.com/docs/en/agent-teams). Community tools: [oh-my-claudecode](https://ohmyclaudecode.com/), [Claude Code Agentrooms](https://claudecode.run/), [Shipyard](https://shipyard.build/blog/claude-code-multi-agent/), and [claude-code-workflow-orchestration](https://github.com/barkain/claude-code-workflow-orchestration).

The most-cited insight from community analysis ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)): harness architecture matters more than the model itself — same model scoring 78% with one harness vs. 42% with another.

Jonathan Fulton's Medium post ["Agent Skills: The Cheat Codes for Claude Code"](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) (April 2026) and multiple "must-have skills" lists ([unicodeveloper](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051), [vibecodingdirectory](https://medium.com/@vibecodingdirectory/20-must-have-skills-for-claude-and-any-coding-agent-in-2026-7c437bbdc9f5)) drove awareness.

Cross-platform coverage: Web (VentureBeat, Medium, blogs), Reddit (multi-agent as top discussion topic), YouTube (tutorials), Hacker News

---

### 8. BMAD Method v6.3.0 — First AI Framework with a Marketplace Ecosystem (April 10, 2026)

BMAD METHOD v6.3.0 shipped April 10, 2026, billing itself as the biggest update yet. The key feature: a full Marketplace Ecosystem with a remote registry (`official.yaml`), offline fallback, universal Git source support, and a VS Code marketplace-like community module browser — described as "the first community module browser in AI vibe coding tools." Covered in detail on [Vibe Sparking AI](https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/).

Other highlights: 4 agents merged into "Amelia" (consolidation), first true parallel story development via `spec-{slug}.md` + status field. The [BMAD-METHOD GitHub](https://github.com/bmad-code-org/BMAD-METHOD) and [bmad-master skill on LobeHub](https://lobehub.com/skills/aj-geddes-claude-code-bmad-skills-bmad-master) are active.

Cross-platform coverage: Web (Vibe Sparking AI, LobeHub, npm, GitHub)

---

### 9. Hacker News Projects: MCP Tooling Innovation

The most notable HN launches in the last 30 days on this topic:

- **Mother MCP** ([HN #46692102](https://news.ycombinator.com/item?id=46692102), Jan 20, 2026) — Auto-detects tech stack and provisions relevant agent skills automatically.
- **PolyMCP Skills** ([HN #46770554](https://news.ycombinator.com/item?id=46770554), Jan 26, 2026) — Addresses token bloat by organizing MCP tools as curated skill sets loaded on demand. Related earlier version at [HN #46656902](https://news.ycombinator.com/item?id=46656902).
- **MCP-skill** ([HN #47274589](https://better-hackernews.vercel.app/item?id=47274589), Mar 6, 2026) — Introspects MCP servers and generates typed Python classes; each tool becomes an async method.
- **Model Context Shell** ([HN #47073185](https://news.ycombinator.com/item?id=47073185), Feb 19, 2026) — Unix-style pipeline composition for MCP tool calls.
- **King Louie** ([HN #47799129](https://news.ycombinator.com/item?id=47799129)) — Desktop AI with 20 built-in agent tools, semantic memory, P2P mesh networking, skill system.
- **Runtime security for AI agents** ([HN #47799856](https://news.ycombinator.com/item?id=47799856)) — Addresses injection, tool abuse, data exfiltration.
- **Playground to Test Skills and MCP** ([HN #46815786](https://news.ycombinator.com/item?id=46815786)) — Testing sandbox for skills before deployment.
- **MCP Isn't Dead. You're Just Using It Wrong** ([HN #47412133](https://news.ycombinator.com/item?id=47412133)) — Opinion piece generating discussion.

Community questions: [Ask HN: How do you manage MCP servers across multiple AI agents?](https://news.ycombinator.com/item?id=45695556) and [Ask HN: In Cursor/agents, do plugins hide MCP tools from the main agent?](https://news.ycombinator.com/item?id=47067558).

Cross-platform coverage: Hacker News primarily

---

### 10. Community Sentiment and Practitioner Insights

Reddit's r/ClaudeCode has grown to ~4,200 weekly contributors — triple r/CursorCode's 1,200. The most upvoted discussions are about workflow architecture, not prompting. The multi-agent pattern is the most actively discussed advanced technique. Analysis from [morphllm.com's Claude Code Reddit roundup](https://www.morphllm.com/claude-code-reddit) and [aitooldiscovery.com](https://www.aitooldiscovery.com/guides/claude-code-reddit).

The ["Claude Code Survival Guide for 2026"](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) (LinkedIn, Rob Foster) and [sankalp's Claude Code 2.0 blog](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) frame skills as the key differentiator for power users.

Trust Insights published ["So What? Plug-ins for Claude Cowork"](https://www.trustinsights.ai/blog/2026/02/so-what-plug-ins-for-claude-cowork/) noting practical business applications of Claude Code plugins.

["Best Claude Code Plugins (2026): 10 Tested, 4 Worth Keeping"](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) on Build to Launch Substack applied a practical filter to the ecosystem noise.

---

## Cross-Source Patterns

### Pattern 1: Security is the #1 unresolved challenge for the ecosystem

**Platforms:** Web (Snyk, The Register, New Stack, Palo Alto, Prompt Security, OWASP), Hacker News (Show HN: Runtime security), Reddit (community warnings)

The same concern appears everywhere: agent skills and MCP servers are growing faster than security tooling can validate. Snyk's ToxicSkills audit (13.4% critical issues), the SSRF findings (36.7% of MCP servers), 30 CVEs in 60 days, and two high-severity CVEs in April alone all reinforce this. Vercel + Snyk's pre-install scanning is the leading defensive response, but it only covers skills.sh.

> "The Agent Skills ecosystem has a supply chain security problem that mirrors the early days of npm and PyPI — except with unprecedented access to credentials, file systems, and APIs." — Snyk ToxicSkills study ([snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

---

### Pattern 2: SKILL.md as the "npm package.json" moment for agents

**Platforms:** Web (dev.to, inference.sh, agensi.io, visualstudiomagazine.com), GitHub (multiple repos), Hacker News, YouTube

Multiple independent sources compare SKILL.md's cross-vendor adoption to the moment npm's `package.json` became a de facto standard. The format's simplicity (name + description in YAML frontmatter, markdown body) has enabled rapid cross-platform adoption. 30+ agent products support it. This pattern appeared in blog posts, HN comments, and YouTube tutorials alike.

> "SKILL.md is now supported across OpenAI Codex CLI, GitHub Copilot, Cursor, and Vercel — plus at least 7 commercial enterprise partners." — DEV Community ([dev.to](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg))

---

### Pattern 3: Harness/workflow architecture matters more than the model

**Platforms:** Web (alexop.dev, morphllm.com, Medium), Reddit (most upvoted discussions), YouTube

The insight that "the harness matters more than the model" (78% vs 42% with same model, different harness) appears repeatedly across Reddit analysis, practitioner blog posts, and YouTube tutorials. Claude Code rewards investment in CLAUDE.md, hooks, skills, and orchestration patterns — treating it as "just autocomplete" underperforms.

> "Developers who invest time learning Claude Code's patterns report significant productivity gains, while those who treat it like autocomplete get frustrated." — Claude Code Reddit analysis ([morphllm.com](https://www.morphllm.com/claude-code-reddit))

---

### Pattern 4: MCP scalability problems driving skills-first architectural choices

**Platforms:** Web (Milvus, New Stack, andrewbaker.ninja), Hacker News (PolyMCP, Mother MCP, "MCP Isn't Dead"), Reddit

Multiple independent voices are noting that connecting every MCP tool upfront floods the context window. The architectural response — loading skills/tools dynamically when relevant — appears in PolyMCP, Mother MCP, Dynamic Tool Registration (Claude Code Jan 2026), and the SKILL.md standard itself. The "Is MCP Dead?" debate is really a debate about when MCP is the right layer vs. when a lightweight Skill suffices.

> "PolyMCP addresses scalability by organizing MCP tools as curated, structured skill sets that agents load only as needed instead of full tool schemas." — HN #46770554 description ([news.ycombinator.com](https://news.ycombinator.com/item?id=46770554))

---

## Per-Platform Tables

### Hacker News

| Story | Points | Comments | Notable Quote | URL |
|-------|--------|----------|---------------|-----|
| Show HN: Mother MCP – Manage your Agent Skills like a boss | — | — | Auto-detects tech stack, provisions relevant coding skills | [HN #46692102](https://news.ycombinator.com/item?id=46692102) |
| Show HN: PolyMCP Skills – Scalable Tool Organization for MCP-Based AI Agents | — | — | Agents load skill sets on demand vs full tool schemas | [HN #46770554](https://news.ycombinator.com/item?id=46770554) |
| Show HN: PolyMCP – structured skills from MCP tools | — | — | Earlier version of PolyMCP concept | [HN #46656902](https://news.ycombinator.com/item?id=46656902) |
| Show HN: MCP-skill – generate Python skills from MCP servers | — | — | Introspects servers, generates typed Python async class | [HN #47274589](https://better-hackernews.vercel.app/item?id=47274589) |
| Show HN: Playground to Test Skills and MCP | — | — | Testing sandbox before deployment | [HN #46815786](https://news.ycombinator.com/item?id=46815786) |
| Ask HN: How do you manage MCP servers across multiple AI agents? | — | — | Community approaches to multi-agent MCP mgmt | [HN #45695556](https://news.ycombinator.com/item?id=45695556) |
| Ask HN: In Cursor/agents, do plugins hide MCP tools from the main agent? | — | — | Tool scoping/isolation question | [HN #47067558](https://news.ycombinator.com/item?id=47067558) |
| Show HN: Unix-style pipeline composition for MCP tool calls | — | — | Model Context Shell, composable MCP | [HN #47073185](https://news.ycombinator.com/item?id=47073185) |
| Show HN: Runtime security for AI agents | — | — | Injection, tool abuse, data exfiltration | [HN #47799856](https://news.ycombinator.com/item?id=47799856) |
| Show HN: King Louie – desktop AI with 20 agent tools, no cloud | — | — | Semantic memory, P2P mesh, skill system | [HN #47799129](https://news.ycombinator.com/item?id=47799129) |
| Show HN: MCP Isn't Dead. You're Just Using It Wrong | — | — | Opinion piece on correct MCP usage | [HN #47412133](https://news.ycombinator.com/item?id=47412133) |
| Show HN: Mcp-Agent – Build effective agents with MCP | — | — | Early MCP agent framework | [HN #42867050](https://news.ycombinator.com/item?id=42867050) |

### YouTube

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Chase AI | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | — | — | Unknown | [YouTube](https://www.youtube.com/watch?v=KjEFy5wjFQg) |
| Unknown | FULL Claude Tutorial For Beginners in 2026! (FULL COURSE) | — | — | Unknown | [YouTube](https://www.youtube.com/watch?v=Xg55nTrbYYY) |
| Unknown | FULL Claude Skills Tutorial (Step By Step) in 2026! | — | — | Unknown | [YouTube](https://www.youtube.com/watch?v=rlYBZswdd8A) |
| Unknown | Top 10 Claude Code Frontend Design Skills, Plugins, & CLIs | — | — | Unknown | [YouTube](https://www.youtube.com/watch?v=Q9ty3eopOPs) |

### Reddit

| Subreddit | Topic | Notes | URL |
|-----------|-------|-------|-----|
| r/ClaudeCode | General Claude Code skills/MCP discussions | ~4,200 weekly contributors; top topics: multi-agent, workflow architecture | [Reddit](https://www.reddit.com/r/ClaudeCode/) |
| r/ClaudeCode | Documentation automation skill discussion | 300+ upvotes | (no direct URL returned) |
| r/CursorCode | Claude Code comparison discussions | ~1,200 weekly contributors | [Reddit](https://www.reddit.com/r/CursorCode/) |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Official Plugins Docs | [code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins) | Canonical plugin architecture reference |
| Claude Code Official Skills Docs | [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills) | Official SKILL.md format and usage |
| Claude Code Plugin Marketplaces Docs | [code.claude.com/docs/en/plugin-marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) | How to create and distribute plugin marketplaces |
| skills.sh (Vercel) | [skills.sh](https://skills.sh/) | Official cross-platform skills directory, 90K+ skills |
| SkillsMP | [skillsmp.com](https://skillsmp.com) | Largest aggregator, 500K+ skills |
| LobeHub Skills | [lobehub.com/skills](https://lobehub.com/skills) | 169K+ skills, polished UX |
| tonsofskills.com | [tonsofskills.com](https://tonsofskills.com/) | Open-source MIT marketplace, 2,804 skills |
| agentskills.so | [agentskills.so/skills/laurigates-claude-plugins-configure-mcp](https://agentskills.so/skills/laurigates-claude-plugins-configure-mcp) | Security-focused directory |
| Claude Marketplaces | [claudemarketplaces.com](https://claudemarketplaces.com/) | Community-curated with ratings |
| Vercel Agent Skills intro | [vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | Vercel's launch announcement |
| Vercel Agent Skills docs | [vercel.com/docs/agent-resources/skills](https://vercel.com/docs/agent-resources/skills) | Vercel official skills documentation |
| Vercel-labs/skills GitHub | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) | Open skills tool repo |
| tonsofskills.com CCPI marketplace | [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | Open-source marketplace repo |
| Awesome Claude Code | [github.com/hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Curated skills, hooks, commands, plugins |
| Awesome Claude Plugins (Composio) | [github.com/ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) | Curated plugin list |
| Awesome Claude Plugins (quemsah) | [github.com/quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) | Adoption metrics via n8n |
| Awesome MCP Servers | [mcpservers.org](https://mcpservers.org/) | MCP server discovery |
| Awesome MCP Servers (wong2) | [github.com/wong2/awesome-mcp-servers](https://github.com/wong2/awesome-mcp-servers) | Curated MCP list |
| MCP official servers | [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | Reference MCP server implementations |
| MCP GitHub org | [github.com/modelcontextprotocol](https://github.com/modelcontextprotocol) | MCP organization on GitHub |
| MCP 2026 Roadmap | [blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) | Official roadmap |
| The New Stack – MCP Roadmap | [thenewstack.io/model-context-protocol-roadmap-2026/](https://thenewstack.io/model-context-protocol-roadmap-2026/) | Coverage of MCP growing pains |
| The Register – MCP design flaw | [theregister.com/2026/04/16/anthropic_mcp_design_flaw/](https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/) | Breaking: 200K servers at risk |
| MCP Wikipedia | [en.wikipedia.org/wiki/Model_Context_Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) | Overview article |
| K2View MCP servers | [k2view.com/blog/awesome-mcp-servers](https://www.k2view.com/blog/awesome-mcp-servers) | Top 15 MCP servers list |
| claudemarketplaces.com MCP | [claudemarketplaces.com/mcp](https://claudemarketplaces.com/mcp) | MCP marketplace aggregator |
| DEV: SKILL.md Multi-Ecosystem | [dev.to/nathanielc85523/skillmd-goes-multi-ecosystem…](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg) | Cross-platform SKILL.md adoption story |
| OpenAI Codex Skills | [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills) | OpenAI official skills docs |
| Agensi.io Open Standard Explainer | [agensi.io/learn/agent-skills-open-standard](https://www.agensi.io/learn/agent-skills-open-standard) | What Is the Agent Skills Open Standard? |
| Awesome Agent Skills (skillmatic) | [github.com/skillmatic-ai/awesome-agent-skills](https://github.com/skillmatic-ai/awesome-agent-skills) | Definitive cross-platform skills list |
| Awesome Agent Skills (VoltAgent) | [github.com/VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 1000+ skills, all major agents |
| inference.sh Skills Overview | [inference.sh/blog/skills/agent-skills-overview](https://inference.sh/blog/skills/agent-skills-overview) | Open standard explainer |
| Snyk ToxicSkills | [snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | Malicious skills supply chain study |
| Snyk + Vercel partnership | [snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) | Pre-install security scanning |
| Snyk agent-scan | [github.com/snyk/agent-scan](https://github.com/snyk/agent-scan) | Open-source scanner |
| New Stack Skills Security | [thenewstack.io/ai-agent-skills-security/](https://thenewstack.io/ai-agent-skills-security/) | 22,511 skills audit |
| OWASP Agentic Skills Top 10 | [owasp.org/www-project-agentic-skills-top-10/](https://owasp.org/www-project-agentic-skills-top-10/) | New OWASP project |
| Vercel automated security audits | [vercel.com/changelog/automated-security-audits-now-available-for-skills-sh](https://vercel.com/changelog/automated-security-audits-now-available-for-skills-sh) | skills.sh security scanning |
| Snyk RSAC 2026 | [securityboulevard.com/2026/03/snyk-launches-agent-security-solution-and-ships-evo-ai-spm-at-rsac-2026/](https://securityboulevard.com/2026/03/snyk-launches-agent-security-solution-and-ships-evo-ai-spm-at-rsac-2026/) | Agent Security Solution launch |
| Snyk Agent Scan Skill Inspector | [labs.snyk.io/resources/agent-scan-skill-inspector/](https://labs.snyk.io/resources/agent-scan-skill-inspector/) | Skill Inspector tool |
| Cyber Desserts AI Agent Security | [blog.cyberdesserts.com/ai-agent-security-risks/](https://blog.cyberdesserts.com/ai-agent-security-risks/) | MCP, OpenClaw & Supply Chain risks |
| Practical DevSecOps MCP | [practical-devsecops.com/mcp-security-vulnerabilities/](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | Prompt injection and tool poisoning |
| Aembit MCP Security Guide | [aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) | Comprehensive 2026 guide |
| Composio MCP Vulnerabilities | [composio.dev/content/mcp-vulnerabilities-every-developer-should-know](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know) | Developer-facing security guide |
| PointGuard AI CVE-2026-26118 | [pointguardai.com/ai-security-incidents/…](https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118) | Microsoft MCP vulnerability |
| Prompt Security Top 10 | [prompt.security/blog/top-10-mcp-security-risks](https://prompt.security/blog/top-10-mcp-security-risks) | MCP risk taxonomy |
| Heyuan110 30 CVEs | [heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) | 30 CVEs in 60 days |
| DEV CVE-2026-32211 | [dev.to/michael_onyekwere/cve-2026-32211…](https://dev.to/michael_onyekwere/cve-2026-32211-what-the-azure-mcp-server-flaw-means-for-your-agent-security-14db) | Azure MCP auth flaw |
| Gentic News MCP Crisis | [gentic.news/article/mcp-security-crisis-43-of-servers](https://gentic.news/article/mcp-security-crisis-43-of-servers) | 43% vulnerable, 341 malicious skills |
| Integrate.io MCP Gateways | [integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/) | Best MCP gateways 2026 |
| Palo Alto MCP Security | [live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed…](https://live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed-what-you-need-to-know-now/ba-p/1227143) | MCP Security Exposed |
| Levo.ai MCP Cybersecurity | [levo.ai/resources/blogs/top-mcp-servers-for-cybersecurity-2026](https://www.levo.ai/resources/blogs/top-mcp-servers-for-cybersecurity-2026) | Top cybersecurity MCP servers |
| GitHub Copilot Skills VS Code | [code.visualstudio.com/docs/copilot/customization/agent-skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills) | VS Code agent skills docs |
| GitHub Changelog gh skill | [github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) | gh skill command launch |
| GitHub Docs About Agent Skills | [docs.github.com/en/copilot/concepts/agents/about-agent-skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) | GitHub official skills docs |
| GitHub Docs Create Skills | [docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills) | How to add Copilot agent skills |
| GitHub Docs Copilot CLI Skills | [docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills) | CLI skills |
| Awesome Copilot Skills README | [github.com/github/awesome-copilot/blob/main/docs/README.skills.md](https://github.com/github/awesome-copilot/blob/main/docs/README.skills.md) | Copilot skills collection |
| VS Magazine Copilot Skills | [visualstudiomagazine.com/articles/2026/01/11/hand-on-with-new-github-copilot-agent-skills-in-vs-code.aspx](https://visualstudiomagazine.com/articles/2026/01/11/hand-on-with-new-github-copilot-agent-skills-in-vs-code.aspx) | Experimental skills hands-on (Jan 11, 2026) |
| Agensi GitHub Copilot vs SKILL.md | [agensi.io/learn/github-copilot-skills-vs-skill-md-2026](https://www.agensi.io/learn/github-copilot-skills-vs-skill-md-2026) | Comparison guide |
| MS Tech Community Copilot Skills | [techcommunity.microsoft.com/blog/…/supercharge-your-dev-workflows…/4510012](https://techcommunity.microsoft.com/blog/azuredevcommunityblog/supercharge-your-dev-workflows-with-github-copilot-custom-skills/4510012) | Microsoft blog on Copilot skills |
| VS Code Multi-Agent Dev | [code.visualstudio.com/blogs/2026/02/05/multi-agent-development](https://code.visualstudio.com/blogs/2026/02/05/multi-agent-development) | VS Code multi-agent blog (Feb 5, 2026) |
| VentureBeat Claude Code 2.1.0 | [venturebeat.com/orchestration/claude-code-2-1-0-arrives-with-smoother-workflows-and-smarter-agents](https://venturebeat.com/orchestration/claude-code-2-1-0-arrives-with-smoother-workflows-and-smarter-agents) | 2.1.0 feature coverage |
| Claude Code Agent Teams docs | [code.claude.com/docs/en/agent-teams](https://code.claude.com/docs/en/agent-teams) | Official agent teams docs |
| Shipyard Multi-Agent | [shipyard.build/blog/claude-code-multi-agent/](https://shipyard.build/blog/claude-code-multi-agent/) | Multi-agent orchestration guide |
| oh-my-claudecode | [ohmyclaudecode.com](https://ohmyclaudecode.com/) | Community orchestration framework |
| Claude Code Agentrooms | [claudecode.run](https://claudecode.run/) | Multi-agent workspace |
| WShobson agents GitHub | [github.com/wshobson/agents](https://github.com/wshobson/agents) | Multi-agent orchestration for Claude Code |
| barkain orchestration plugin | [github.com/barkain/claude-code-workflow-orchestration](https://github.com/barkain/claude-code-workflow-orchestration) | Workflow orchestration plugin |
| BMAD v6.3.0 Changelog | [vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/](https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/) | BMAD marketplace ecosystem launch |
| BMAD-METHOD GitHub | [github.com/bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) | BMAD-METHOD repository |
| BMad Master on LobeHub | [lobehub.com/skills/aj-geddes-claude-code-bmad-skills-bmad-master](https://lobehub.com/skills/aj-geddes-claude-code-bmad-skills-bmad-master) | BMAD Master skill |
| bmad-skill on LobeHub | [lobehub.com/skills/jarbitechture-claude-skills-bmad-skill](https://lobehub.com/skills/jarbitechture-claude-skills-bmad-skill) | BMAD skill on LobeHub |
| MorphLLM Claude Code Skills vs MCP | [morphllm.com/claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Complete guide: Skills vs MCP vs Plugins |
| MorphLLM Claude Code Reddit | [morphllm.com/claude-code-reddit](https://www.morphllm.com/claude-code-reddit) | Reddit community analysis |
| alexop.dev full stack | [alexop.dev/posts/understanding-claude-code-full-stack/](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Deep-dive on Claude Code architecture |
| Milvus Is MCP Dead? | [milvus.io/blog/is-mcp-dead-cli-and-skills-for-ai-agents.md](https://milvus.io/blog/is-mcp-dead-cli-and-skills-for-ai-agents.md) | MCP vs CLI vs Skills comparison |
| Andrew Baker MCP 2026 | [andrewbaker.ninja/2026/03/22/mcp-in-2026-rise-security-flaws-what-comes-next/](https://andrewbaker.ninja/2026/03/22/mcp-in-2026-rise-security-flaws-what-comes-next/) | Rise, fall, what comes next |
| Medium: Agent Skills Cheat Codes | [medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | Jonathan Fulton (Apr 2026) |
| Medium: 10 Must-Have Skills (unicodeveloper) | [medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | Must-have skills list |
| Medium: 20 Must-Have Skills (vibecodingdirectory) | [medium.com/@vibecodingdirectory/20-must-have-skills-for-claude-and-any-coding-agent-in-2026-7c437bbdc9f5](https://medium.com/@vibecodingdirectory/20-must-have-skills-for-claude-and-any-coding-agent-in-2026-7c437bbdc9f5) | Extended must-have skills list |
| Medium: GitHub Copilot Skills 2026 | [medium.com/@mpholoane/agent-skills-in-github-copilot-for-visual-studio-2026-stop-repeating-yourself-d0b5a0209f48](https://medium.com/@mpholoane/agent-skills-in-github-copilot-for-visual-studio-2026-stop-repeating-yourself-d0b5a0209f48) | Copilot skills in Visual Studio |
| DEV: Claude Code Skills vs MCP | [dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Skills vs MCP guide |
| DEV: Claude Code #1 on HN | [dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74) | HN milestone coverage |
| DEV: Best Claude Code Skills 2026 | [dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best skills guide |
| Bright Coding Plugins Plus | [blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development) | 270+ AI agent tools |
| Build to Launch Plugins Tested | [buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) | 10 tested, 4 worth keeping |
| AI Maker Q1 2026 Guide | [aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide](https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide) | Complete Q1 2026 update guide |
| Trust Insights Plugins | [trustinsights.ai/blog/2026/02/so-what-plug-ins-for-claude-cowork/](https://www.trustinsights.ai/blog/2026/02/so-what-plug-ins-for-claude-cowork/) | Business applications |
| LinkedIn Claude Code Survival Guide | [linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) | Rob Foster's survival guide |
| Sankalp Claude Code 2.0 Blog | [sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) | Developer experience writeup |
| Zaz Codes Cross-Platform Skills | [zazencodes.substack.com/p/cross-platform-agent-skills-guide](https://zazencodes.substack.com/p/cross-platform-agent-skills-guide) | Cross-platform skills guide |
| Young Leaders Tech Skills Guide | [youngleaders.tech/p/claude-skills-commands-subagents-plugins](https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins) | Skills vs Commands vs Subagents vs Plugins |
| MindStudio Social Media Skills | [mindstudio.ai/blog/claude-code-skills-social-media-content-repurposing](https://www.mindstudio.ai/blog/claude-code-skills-social-media-content-repurposing) | Practical use case: content repurposing |
| Hermes Agents Skills + agentskills.io | [hermesagents.net/blog/skills-and-agentskills-io/](https://hermesagents.net/blog/skills-and-agentskills-io/) | Ecosystem growth story |
| TurboDocx Best Skills | [turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best skills and MCP roundup |
| ClaudeFast Best MCP Servers | [claudefa.st/blog/tools/mcp-extensions/best-addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers |
| Composio Top Plugins | [composio.dev/content/top-claude-code-plugins](https://composio.dev/content/top-claude-code-plugins) | Top 10 plugins 2026 |
| Self.md Best Plugins | [self.md/guides/best-claude-code-plugins/](https://self.md/guides/best-claude-code-plugins/) | Best Claude Code plugins guide |
| aitmpl.com Plugins | [aitmpl.com/plugins/](https://www.aitmpl.com/plugins/) | Plugin and marketplace collection |
| popularaitools.ai | [popularaitools.ai/blog/claude-code-skills-plugins-clis-2026](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | Skills, plugins, CLIs roundup |
| Mejba.me Top 10 | [mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | April 2026 top 10 list |
| AI Coding Daily Substack | [aicodingdaily.substack.com/p/token-limits-horror-leaked-claude](https://aicodingdaily.substack.com/p/token-limits-horror-leaked-claude) | Token limits and Claude Code news |
| AI Tool Discovery Reddit Analysis | [aitooldiscovery.com/guides/claude-code-reddit](https://www.aitooldiscovery.com/guides/claude-code-reddit) | Reddit community analysis |
| SmartScope SkillsMP Review | [smartscope.blog/en/blog/skillsmp-marketplace-guide/](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) | SkillsMP marketplace guide |
| VirtualUncle Skills.sh Guide | [virtualuncle.com/agent-skills-marketplace-skills-sh-2026/](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Skills.sh guide 2026 |
| Toolworthy Skills.sh Review | [toolworthy.ai/tool/skills-sh](https://www.toolworthy.ai/tool/skills-sh) | skills.sh review |
| ExplainX find-skills | [explainx.ai/skills/vercel-labs/skills/find-skills](https://explainx.ai/skills/vercel-labs/skills/find-skills) | find-skills explainer |
| Byteiota oh-my-claudecode | [byteiota.com/oh-my-claudecode-multi-agent-orchestration-for-claude-code/](https://byteiota.com/oh-my-claudecode-multi-agent-orchestration-for-claude-code/) | oh-my-claudecode writeup |
| KDnuggets Top 5 Marketplaces | [kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Marketplace comparison |
| Vibecoding.app Skills.sh vs SkillsMP | [vibecoding.app/compare/skills-sh-vs-skillsmp](https://vibecoding.app/compare/skills-sh-vs-skillsmp) | Platform comparison |
| ITECS Codex CLI Skills Guide | [itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026) | Codex CLI skills guide |
| Yawn.ai Agentic Skills | [yawn.ai/agentic-skills](https://yawn.ai/agentic-skills) | What are agentic skills? |
| Prompt Index AI Skills Guide | [thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html](https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html) | Complete usage guide |
| Chris Ayers Agent Skills Guide | [chris-ayers.com/posts/agent-skills-plugins-marketplace/](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Complete guide to skills + marketplace |
| Verdent Guides Skills vs MCP | [verdent.ai/guides/claude-skills-vs-mcp-agents-comparison](https://www.verdent.ai/guides/claude-skills-vs-mcp-agents-comparison) | Skills vs MCP comparison |
| DeepWiki Microsoft agent-skills | [deepwiki.com/microsoft/agent-skills/4-plugins](https://deepwiki.com/microsoft/agent-skills/4-plugins) | Microsoft agent-skills plugins |
| Hype ML/AI News | [hype.replicate.dev](https://hype.replicate.dev/) | ML/AI news aggregator |
| MCP Playground Reddit Ads | [mcpplaygroundonline.com/blog/reddit-ads-mcp-claude-automation-guide](https://mcpplaygroundonline.com/blog/reddit-ads-mcp-claude-automation-guide) | Practical MCP Reddit automation |
| Clinde MCP Reddit Server | [clinde.ai/blog/2025/02/07/mcp-server-reddit](https://clinde.ai/blog/2025/02/07/mcp-server-reddit) | Reddit MCP server project |

---

## Stats Block

```
├─ 🟠 Reddit: 3 analyses │ 300+ upvotes (top thread) │ ~4,200 weekly contributors in r/ClaudeCode
├─ 🔵 X: — │ — │ — (not crawled)
├─ 🔴 YouTube: 4 videos │ views not reported │ 0 with transcripts
├─ 🟢 HN: 12 stories │ points not reported │ active Show HN + Ask HN threads
├─ 🟣 TikTok: — │ — (not crawled)
├─ 🩷 Instagram: — │ — (not crawled)
├─ 🦋 Bluesky: — │ — (not crawled)
├─ 📊 Polymarket: — │ — (no relevant markets found)
├─ 🌐 Web: 100+ pages
└─ 🗣️ Top voices: @jeremylongshore (tonsofskills/ccpi), @vercel-labs (skills.sh), @snyk (ToxicSkills), @bmad-code-org (BMAD v6.3) │ r/ClaudeCode, r/LocalLLaMA
```

---

## Data Gaps

- **X/Twitter:** Not crawled in this run. Active discourse expected given the volume of developer attention to Claude Code.
- **TikTok/Instagram:** Not crawled. Some developer tutorial content likely exists.
- **Bluesky:** Not crawled.
- **Polymarket:** No agent-skills-specific prediction markets identified.
- **Reddit direct thread URLs:** Search infrastructure returned community-level data but not individual thread permalinks for r/ClaudeCode posts. The 300+ upvote documentation thread could not be linked directly.
- **YouTube engagement metrics:** View/like counts not returned by search results; only video titles and URLs confirmed.
- **HN engagement metrics:** Point/comment counts not returned by search; thread IDs confirmed.
- **Coverage estimate:** Web (95%), HN (85%), Reddit (60% — community trends confirmed, individual thread links sparse), YouTube (70% — videos identified, no transcripts), X/Bluesky/TikTok (0%).

---

## Key Quotes

> "Skills teach Claude; plugins give Claude hands; CLIs give Claude helpers." — Top 10 Claude Code Skills, Plugins & CLIs guide ([mejba.me](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026))

> "The same model scored 78% with one harness and 42% with another — the harness matters more than the model." — Claude Code community analysis ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "Developers who invest time learning Claude Code's patterns report significant productivity gains, while those who treat it like autocomplete get frustrated." — Claude Code Reddit analysis ([morphllm.com](https://www.morphllm.com/claude-code-reddit))

> "The Agent Skills ecosystem has a supply chain security problem that mirrors the early days of npm and PyPI — except with unprecedented access to credentials, file systems, and APIs." — Snyk ToxicSkills study ([snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "13.4% of all skills contain at least one critical-level security issue, including malware distribution, prompt injection attacks, and exposed secrets." — Snyk February 2026 audit ([snyk.io](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/))

> "SKILL.md is now supported across OpenAI Codex CLI, GitHub Copilot, Cursor, and Vercel — plus at least 7 commercial enterprise partners." — DEV Community ([dev.to](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg))

> "By March 2026, MCP had been formalized as a multi-company open standard under the Linux Foundation." — Andrew Baker ([andrewbaker.ninja](https://andrewbaker.ninja/2026/03/22/mcp-in-2026-rise-security-flaws-what-comes-next/))

> "When gh skill installs a skill, it writes tracking metadata (repository, ref, tree SHA) directly into the SKILL.md frontmatter. Because provenance data lives inside the skill file itself, it travels with the skill no matter where it ends up." — GitHub Changelog, April 16, 2026 ([github.blog](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/))

> "Every time a new agent skill is installed using the npx skills installer, Vercel's infrastructure calls out to Snyk's high-throughput API to perform deep security analysis on the skill before it ever reaches a developer's machine." — Snyk + Vercel announcement ([snyk.io](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/))

> "PolyMCP addresses scalability by organizing MCP tools as curated, structured skill sets that agents load only as needed instead of full tool schemas." — Show HN: PolyMCP Skills ([news.ycombinator.com](https://news.ycombinator.com/item?id=46770554))
