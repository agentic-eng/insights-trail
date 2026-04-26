# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-26
**Query type:** GENERAL
**Sources:** Hacker News, X/Twitter, YouTube, Reddit (via aggregators), Web, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 8 stories | ~800+ points, 20+ comments | Threads on Skills vs MCP, plugin system, Wombat, Ensemble |
| X/Twitter | 10 posts | Varies (thousands of likes combined) | Official announcements + dev discussions |
| YouTube | 8 videos | Not quantified | Mix of beginner guides and advanced skill tutorials |
| Reddit | ~4,200 weekly contributors to r/ClaudeCode | — | Via aggregator summaries; direct thread data not retrieved |
| GitHub | 10+ repos | 37.5k stars (anthropics/skills), 55k stars (claude-code) | Multiple awesome-lists and marketplaces |
| Web | 40+ pages | — | Blogs, news, official docs, security disclosures |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: A Cross-Industry Consensus Moment

The most significant structural development of the last 30 days is the broad adoption of Anthropic's SKILL.md open standard, originally published December 18, 2025. At its core, a skill is a folder containing a `SKILL.md` file with a name, description, and instructions that tell an agent how to perform a specific task. The Anthropic engineering team described the design philosophy as: *"Building a skill for an agent is like putting together an onboarding guide for a new hire."* ([Anthropic Engineering](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

OpenAI adopted the same SKILL.md format for Codex CLI and ChatGPT in December 2025, creating a rare moment of cross-platform standardization. The official specification lives at [agentskills.io/specification](https://agentskills.io/specification) and is maintained at [github.com/anthropics/skills](https://github.com/anthropics/skills) (37,500 stars). Commercial launch partners include Atlassian, Canva, Cloudflare, Figma, Notion, Ramp, and Sentry.

The [New Stack framed this](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) as "Anthropic's Next Bid to Define AI Standards," noting that having a portable format across Claude Code, Cursor, Codex, Gemini CLI, GitHub Copilot, Windsurf, Goose, and 10+ other tools represents a foundational infrastructure win.

**Platforms discussing this:** HN, X/Twitter, Web (multiple blog/news sources)

---

### 2. The Three-Layer Extension Architecture: Skills vs MCP vs Plugins

The ecosystem has converged on a clear taxonomy, though community confusion persists:

- **Skills**: Markdown files in `~/.claude/skills/YourSkill/SKILL.md` — procedural knowledge for *how to do things*. Activate automatically when Claude detects relevant context. Token-efficient via progressive disclosure (metadata ~100 tokens → full SKILL.md <5k tokens → resources on demand). Best for methodology, workflows, coding patterns.
- **MCP (Model Context Protocol)**: Connect Claude Code to external systems — GitHub, databases, APIs, browsers. A typical five-server setup with 58 tools uses ~55,000 tokens before any conversation starts. Best for *accessing* external state.
- **Plugins**: Distribution bundles combining slash commands, subagents, MCP configs, hooks, and skills into one installable package. Introduced in Claude Code v2.0.12 via `/plugin install`, `/plugin enable/disable`, `/plugin marketplace`.

The canonical guide ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)), the [DEV Community breakdown](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k), and [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) all land on the same conclusion: *most workflows need both MCP for connectivity and Skills for methodology.*

The practical token difference is stark: a Playwright MCP server loads all tool descriptions upfront; a [Playwright Skill](https://news.ycombinator.com/item?id=45642911) achieves the same browser automation with 314 lines of instructions, writes code and executes it, and returns screenshots and console output — with a fraction of the context cost.

**Platforms discussing this:** HN (multiple threads), X/Twitter, Web

---

### 3. Anthropic Addresses the MCP Token Bloat Problem

One of the most-discussed engineering improvements of the period: Anthropic shipped **MCP Tool Search** (dynamic tool loading) for Claude Code. [@WesRothMoney reported](https://x.com/WesRothMoney/status/2011785440140149034): *"Tool Search now lets Claude Code dynamically fetch tools only when needed. If the tool descriptions exceed 10% of context, they're [lazy loaded]."* [@elvis (omarsar0) responded](https://x.com/omarsar0/status/2011589983090688262): *"This is a big deal... Enabling this to reduce all of that context bloat is going to make it more effective and faster to integrate agents with tools."*

[@marcospereeira noted](https://x.com/marcospereeira/status/2021868313848995984) you can force-enable it before the 10% threshold. This feature reduces MCP overhead by ~85% (per [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons)), significantly changing the practical economics of running many MCP servers.

**Platforms discussing this:** X/Twitter, Web

---

### 4. Skills Marketplaces: Explosive Proliferation and Fragmentation

The marketplace landscape has exploded in early 2026:

| Platform | Scale | Notes |
|----------|-------|-------|
| [agentskill.sh](https://agentskill.sh) | 110,000+ skills | 20+ AI tools supported |
| [skills.sh](https://skills.sh) (Vercel) | 87,000+ skills tracked | Launched Jan 20, 2026; 20k installs in 6 hours |
| [LobeHub Skills](https://lobeai.com) | 169,739 skills | Emphasis on trust/discoverability |
| [ClawHub](https://navtools.ai/tool/clawhub-ai) (OpenClaw) | 13,729 skills | As of Feb 28, 2026 |
| [tonsofskills.com](https://tonsofskills.com) | 2,849 skills, 423 plugins, 177 agents | Claude-specific; ccpi CLI package manager |
| [claudemarketplaces.com](https://claudemarketplaces.com) | 150+ skills | Claude-focused community directory |
| [skillsmp.com](https://skillsmp.com) | Supports Claude, Codex, ChatGPT | Cross-platform |
| [Smithery](https://smithery.ai) | 7,000+ MCP servers | "Docker Hub" for MCP |
| [MCPMarket.com](https://mcpmarket.com) | 10,000+ MCP servers | 23+ categories |

Vercel launched [skills.sh](https://skills.sh) on January 20, 2026 with a CLI (`npx skills add <package>`) and reached 20,000 installs in six hours. The Vercel announcement positioned it as "the open agent skills ecosystem" — a vendor-neutral directory and leaderboard. [InfoQ coverage](https://www.infoq.com/news/2026/02/vercel-agent-skills/) noted it supports 17 agent tools. The [full announcement](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) and [source code](https://github.com/vercel-labs/skills) are public.

The fragmentation is significant: [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) identified five competing top-tier marketplaces; [rapidclaw.dev's 2026 guide](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026) split the landscape into enterprise (Salesforce AgentExchange, Google Agentspace, Microsoft Marketplace, AWS) vs. developer platforms.

**Platforms discussing this:** Web (multiple), GitHub

---

### 5. GitHub: Massive Community Curation Ecosystem

The GitHub ecosystem around Claude Code skills is enormous and growing. Key repositories:

| Repo | Description | Stars |
|------|-------------|-------|
| [anthropics/skills](https://github.com/anthropics/skills) | Official Agent Skills | 37,500 |
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Skills, hooks, slash-commands, orchestrators, plugins | High |
| [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) | 1,400+ agentic skills | 35,000 |
| [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ cross-platform skills | High |
| [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 423 plugins, 2,849 skills, 177 agents; tonsofskills.com | Active |
| [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) | 135 agents, 400,000+ skills via SkillKit, 176+ plugins | Comprehensive |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) | 232+ skills for Claude Code, Codex, Gemini CLI, Cursor | 5,200 |
| [ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) | CCHub desktop app + curated list | Active |

The [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) pattern is proliferating — over 10 competing curated lists found in a single search. The [rohitg00 toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) claims access to 400,000+ skills via SkillKit, suggesting aggregation layers are emerging above marketplace layers.

**Platforms discussing this:** GitHub, Web

---

### 6. MCP Governance: Linux Foundation Takes the Wheel

A major institutional development: in December 2025, Anthropic donated MCP to the **Agentic AI Foundation (AAIF)**, a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI. This month (April 2026), AAIF held the **MCP Dev Summit North America** in New York City with approximately 1,200 attendees — the theme was "MCP Is Now Enterprise Infrastructure." ([AAIF blog](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

The [2026 MCP Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) prioritizes: transport scalability, agent communication, governance maturation, and enterprise readiness. The [New Stack analysis](https://thenewstack.io/model-context-protocol-roadmap-2026/) notes that "MCP's biggest growing pains for production use will soon be solved."

Docker's MCP Catalog has been described on Hacker News as "the npm of AI tools" — centralized, sandboxed, any MCP-compatible client can consume. The [Truefoundry registry comparison](https://www.truefoundry.com/blog/best-mcp-registries) evaluated Smithery, Glama, MCPMarket, and Docker Catalog, with Smithery ("7,000 servers") as the closest to Docker Hub.

**Platforms discussing this:** HN, Web

---

### 7. The Security Crisis in Plugin Ecosystems

The rapid expansion of skills and plugin marketplaces has created a significant and under-addressed security problem. April 2026 brought a wave of disclosures:

**Critical RCE in MCP SDK** ([The Hacker News](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html), [Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed)): A design vulnerability in Anthropic's official MCP SDK (Python, TypeScript, Java, Rust) enables arbitrary command execution on systems running vulnerable implementations, affecting 7,000+ publicly accessible servers and software packages with 150M+ downloads.

**Malicious skills in marketplaces** ([cybersecuritywaala.com](https://cybersecuritywaala.com/blog/71-malicious-claude-skills-found/)): 71 malicious Claude Skills found in marketplace; 1,184 malicious skills confirmed across ClawHub; 492 MCP servers exposed to the internet with zero authentication.

**Statistical risk** ([VentureBeat](https://venturebeat.com/security/mcp-stacks-have-a-92-exploit-probability-how-10-plugins-became-enterprise)): Deploying 10 MCP plugins creates a 92% probability of exploitation. A single MCP plugin presents 9% exploit probability.

**Supply chain attack** ([composio.dev](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know)): The `postmark-mcp` npm package was trojanized to silently BCC every outbound email to attacker's domain, exfiltrating internal memos, invoices, and password resets.

The community response has been tooling-focused: [Wombat](https://news.ycombinator.com/item?id=47418076) applies Unix-style rwxd permissions as a proxy between Claude Code and MCP servers (late March 2026). [JFrog blog](https://jfrog.com/blog/agent-skills-new-ai-packages/) argued agent skills should be treated like software packages — scanned, versioned, and managed with dependency hygiene. [Snyk + Vercel announced a partnership](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) to secure the agent skill ecosystem.

**Platforms discussing this:** Web (security/tech press), HN (via Wombat discussion)

---

### 8. Community Sentiment: Enthusiasm Tempered by Complexity

The developer community is highly engaged but divided on the noise-to-signal ratio of the skills ecosystem. From HN thread ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537):

- **michael1999** (738 points): Three theories on why context documents suddenly work — *short feedback loops, friction-reducing tools, personal motivation* ("harness a computer minion")
- **simonw**: Skills represent a "conceptually trivial" but "elegant" solution vs complex MCP server infrastructure
- **7thpower**: "If you are writing them because the AI using them will help you, you have a very strong and immediate incentive."
- Multiple HN commenters questioned novelty — *"is this more than just prompt engineering patterns we've always used?"*

The [Claude Code Plugin System announcement](https://news.ycombinator.com/item?id=45530150) (48 points) surfaced distribution as the critical unsolved problem: a developer built claudecodemarketplace.com because *"plugin maintainers do not want to have to build a marketplace as well as a plugin."*

On Reddit, r/ClaudeCode has 4,200+ weekly contributors. The most upvoted tips focus on workflow architecture (CLAUDE.md, subagents, hooks, slash commands) rather than individual skills, suggesting the ceiling of value may be in orchestration over individual capability packages. Main pain point: $20/month plan runs out after ~12 heavy prompts.

**Platforms discussing this:** HN (direct), Reddit (via aggregator), Web

---

## Cross-Source Patterns

### Pattern 1: "Skills vs MCP" is the defining architectural debate

**Appeared on:** HN, X/Twitter, Web (15+ articles), YouTube
- HN: simonw argued skills are "a bigger deal than MCP"; tptacek countered that tool calls are the real innovation
- X: @omarsar0 celebrated MCP Tool Search as addressing the core problem (context bloat)
- Web: Dozens of comparison articles landed on "use both — MCP for connectivity, Skills for methodology"
- Key tension: MCP requires running live server infrastructure; skills are static markdown that load on demand

### Pattern 2: Security as the ecosystem's biggest unsolved problem

**Appeared on:** Web (security press), HN (Wombat thread), X (implied in developer caution)
- April 2026 RCE disclosure in MCP SDK: covered by The Hacker News, Tom's Hardware, VentureBeat
- 71–1,184 malicious skills found across different marketplaces
- 92% exploit probability with 10 MCP plugins
- Community response: Wombat permissions proxy (HN), Snyk/Vercel partnership (web)
- Quote: *"Agents in 2026 are running with the same access level as the developer who run them"* — Wombat creator

### Pattern 3: Marketplace explosion → fragmentation → tooling for tooling

**Appeared on:** GitHub, Web, X
- Massive proliferation: 150+ skills → 87,000+ → 110,000+ → 169,000+ across competing platforms
- Second-order tooling emerging: Ensemble (macOS app to manage skills/MCPs), CCHub desktop app, ccpi CLI (`pnpm add -g @intentsolutionsio/ccpi`), SkillKit (aggregates 400,000+ skills)
- Distribution becomes first-class problem: "Your Claude Plugin Marketplace Needs More Than a Git Repo" ([DEV Community](https://dev.to/michaeltuszynski/your-claude-plugin-marketplace-needs-more-than-a-git-repo-5631))

### Pattern 4: Cross-platform portability as competitive moat

**Appeared on:** Web, GitHub, X
- SKILL.md adopted by Claude Code AND Codex CLI AND ChatGPT: creates network effects across tools
- skills.sh supports 17 agents; agentskill.sh supports 20+ tools
- Developers increasingly write one skill for all their agents — single SKILL.md works on Cursor, Claude Code, Gemini CLI, Windsurf
- Microsoft joined: "Extend your coding agent with .NET Skills" ([.NET Blog](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/))

---

## Per-Platform Tables

### Hacker News

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (various) | Claude Skills are awesome, maybe a bigger deal than MCP | ~738+ | High | "short feedback loops, friction-reducing tools, personal motivation" — michael1999 | [link](https://news.ycombinator.com/item?id=45619537) |
| (various) | Claude Skills | High | High | "conceptually trivial" but elegant vs MCP infrastructure — simonw | [link](https://news.ycombinator.com/item?id=45607117) |
| (various) | Customize Claude Code with plugins | 48 | 9 | "plugin maintainers do not want to have to build a marketplace as well as a plugin" | [link](https://news.ycombinator.com/item?id=45530150) |
| (various) | Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP | — | — | 314 lines of instructions vs persistent MCP server | [link](https://news.ycombinator.com/item?id=45642911) |
| IO0oI | Show HN: Ensemble – macOS App to Manage Claude Code Skills, MCPs | 1 | 1 | "managing them through ~/.claude.json and manual file editing gets old fast" | [link](https://news.ycombinator.com/item?id=46922223) |
| (various) | Show HN: Wombat, a Unix-style rwxd permissions for MCP tool calls | 2 | 1 | "Agents in 2026 are running with the same access level as the developer who run them" | [link](https://news.ycombinator.com/item?id=47418076) |
| (various) | Remote MCP Support in Claude Code | — | — | — | [link](https://news.ycombinator.com/item?id=44312363) |
| (various) | Anatomy of the .claude/ folder | — | — | — | [link](https://news.ycombinator.com/item?id=47543139) |

### X/Twitter

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | "Today we're introducing Claude Code Plugins in public beta. Plugins allow you to install and share curated collections of slash commands, agents, MCP servers, and hooks…" | High | High | [link](https://x.com/claudeai/status/1976332881409737124) |
| @WesRothMoney | "Anthropic is rolling out MCP Tool Search for Claude Code… Tool Search now lets Claude Code dynamically fetch tools only when needed." | High | High | [link](https://x.com/WesRothMoney/status/2011785440140149034) |
| @trq212 | "We just released Claude Code channels… control your Claude Code session through select MCPs, starting with Telegram and Discord." | High | Medium | [link](https://x.com/trq212/status/2034761016320696565) |
| @Sumanth_077 | "Cipher is built for coding agents. It works with Cursor, Windsurf, Claude Desktop, Claude Code, Gemini CLI, AWS Kiro, VS Code, Roo Code (via MCP)…" | Medium | Medium | [link](https://x.com/Sumanth_077/status/1950549604468129923) |
| @heygurisingh | "10 Open-Source MCP Servers that give Claude superpowers: Most people use Claude with zero plugins. Meanwhile, developers who install these are building 10x faster." | High | High | [link](https://x.com/heygurisingh/status/2039920621153587238) |
| @omarsar0 | "This is a big deal. Claude Code now has dynamic tool loading… Enabling this to reduce all of that context bloat is going to make it more effective…" | High | High | [link](https://x.com/omarsar0/status/2011589983090688262) |
| @marcospereeira | "you can force enable tool search in claude code, which avoids bloating context with MCP tool descriptions" | Medium | Medium | [link](https://x.com/marcospereeira/status/2021868313848995984) |
| @ktknd | "Claude CodeとCodexを組み合わせる公式Pluginが出た！ インストールしたら3つのコマンドが使えるようになる：/codex:review, /codex:adversarial-review…" | Medium | Medium | [link](https://x.com/ktknd/status/2038859928069398552) |
| @pveerina | "Excited to leverage the new MCP apps protocol to bring rich image and video gen into Claude!" | Medium | Low | [link](https://x.com/pveerina/status/2041564650056437867) |
| @adamdotdev | "im running fetch and puppeteer mcp servers with claude code right now `claude mcp add <name> <command>`" | Low | Low | [link](https://x.com/adamdotdev/status/1901015069791604816) |

### YouTube

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Various | FULL Claude Tutorial For Beginners in 2026! (FULL COURSE) | High | — | No data | [link](https://www.youtube.com/watch?v=Xg55nTrbYYY) |
| Various | FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step) | High | — | No data | [link](https://www.youtube.com/watch?v=qYqIhX9hTQk) |
| Various | Full Claude Skills Tutorial for Beginners in 2026! (Become a PRO) | High | — | No data | [link](https://www.youtube.com/watch?v=YkpEX_jlb04) |
| Various | The ONLY Claude Code Tutorial You'll Ever Need in 2026 | High | — | No data | [link](https://www.youtube.com/watch?v=LlFgLsffbBs) |
| Various | Solo necesitas estas 22 Skills de Claude Code en 2026 (Spanish) | Recent | — | No data | [link](https://www.youtube.com/watch?v=dj7uAA2Phqg) |
| Various | The Ultimate Claude Code Guide \| MCP, Skills & More | Medium | — | No data | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| Various | Claude Skills for Designers \| Create Your Own Custom Skills! | Medium | — | No data | [link](https://www.youtube.com/watch?v=WUMIdvphiTQ) |
| Various | Claude Code Skills playlist | — | — | No data | [link](https://www.youtube.com/playlist?list=PLmWCw1CzcFim_hkruZSlABOUOAAQ5JMyo) |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Authoritative SKILL.md design goals, architecture, author quotes |
| Vercel Changelog | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh launch announcement (Jan 20, 2026), 20k installs in 6 hours |
| The New Stack (MCP roadmap) | [link](https://thenewstack.io/model-context-protocol-roadmap-2026/) | 2026 MCP roadmap: transport scalability, enterprise readiness |
| The New Stack (Agent Skills) | [link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Framing SKILL.md as Anthropic's standard-setting bid |
| AAIF Blog | [link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/) | MCP Dev Summit NA April 2026, 1,200 attendees |
| The Hacker News | [link](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) | April 2026 RCE in MCP SDK affecting 7,000+ servers |
| Tom's Hardware | [link](https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed) | 200,000 AI servers at risk from MCP critical flaw |
| VentureBeat | [link](https://venturebeat.com/security/mcp-stacks-have-a-92-exploit-probability-how-10-plugins-became-enterprise) | 92% exploit probability with 10 MCP plugins |
| Cybersecuritywaala | [link](https://cybersecuritywaala.com/blog/71-malicious-claude-skills-found/) | 71 malicious Claude Skills found in marketplace |
| JFrog Blog | [link](https://jfrog.com/blog/agent-skills-new-ai-packages/) | "Agent Skills are the New Packages of AI: It's Time to Manage Them Securely" |
| Snyk Blog | [link](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) | Snyk + Vercel partnership to secure agent skill supply chain |
| InfoQ | [link](https://www.infoq.com/news/2026/02/vercel-agent-skills/) | Vercel skills.sh deep-dive, February 2026 |
| KDnuggets | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 agent skill marketplaces comparison |
| Morphllm.com | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills vs MCP vs Plugins definitive guide |
| DEV Community (raxxo) | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best Claude Code skills and plugins 2026 guide |
| DEV Community (williamwang) | [link](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Skills vs MCP servers comparison |
| DEV Community (michaelt) | [link](https://dev.to/michaeltuszynski/your-claude-plugin-marketplace-needs-more-than-a-git-repo-5631) | "Your Claude Plugin Marketplace Needs More Than a Git Repo" |
| Medium (sean.j.moran) | [link](https://medium.com/@sean.j.moran/effective-claude-code-workflows-in-2026-what-changed-and-what-works-now-c93ebc6f8f50) | What changed in 2026 Claude Code workflows |
| Medium (unicodeveloper) | [link](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 must-have skills for Claude, March 2026 |
| Truefoundry | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Best MCP Registries in 2026: Smithery, Glama, MCPMarket, Docker Catalog |
| AIAgentsdirectory | [link](https://aiagentsdirectory.com/landscape) | AI Agents Landscape & Ecosystem April 2026 interactive map |
| Fungies.io | [link](https://fungies.io/ai-agent-skills-skill-md-guide-2026/) | Complete SKILL.md guide for developers |
| Digital Applied | [link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | AI Agent Marketplaces 2026: Discovery and Distribution |
| Microsoft .NET Blog | [link](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | .NET Skills integration for coding agents |
| Buildtolaunch Substack | [link](https://buildtolaunch.substack.com/p/claude-code-mcp-vs-plugins-vs-skills) | MCP vs Skills vs Plugins decision guide |
| Alexop.dev | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Understanding Claude Code full stack: MCP, Skills, Subagents, Hooks |
| MindStudio | [link](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns) | 5 Claude Code agentic workflow patterns |
| DevOps.com | [link](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) | "Claude Introduces Agent Skills for Custom AI Workflows" |
| LiteLLM Docs | [link](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) | Claude Code Plugin Marketplace via LiteLLM |
| Composio | [link](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know) | MCP vulnerabilities every developer should know |
| Adversa AI | [link](https://adversa.ai/blog/top-mcp-security-resources-february-2026/) | Top MCP security resources, February 2026 |
| Practical DevSecOps | [link](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | MCP Security Vulnerabilities: Prevent Prompt Injection |
| Aembit | [link](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) | Ultimate guide to MCP security vulnerabilities |
| Rapidclaw.dev | [link](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026) | 2026 AI Agent Marketplace guide |
| Sitepoint | [link](https://www.sitepoint.com/claude-code-as-an-autonomous-agent-advanced-workflows-2026/) | Claude Code as autonomous agent: advanced workflows |
| Substack (aimaker) | [link](https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide) | Complete guide to every Claude update in Q1 2026 |
| Claude Code Docs | [link](https://code.claude.com/docs/en/plugins) | Official plugin creation documentation |
| Claude Code Docs (MCP) | [link](https://code.claude.com/docs/en/mcp) | Official MCP documentation |
| Claude Code Docs (discover) | [link](https://code.claude.com/docs/en/discover-plugins) | Official discover/install plugins docs |
| Anthropic News | [link](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously) | Enabling Claude Code to work more autonomously |
| Pipelab | [link](https://pipelab.org/blog/state-of-mcp-security-2026/) | State of MCP Security 2026 |
| Vercel Skills Docs | [link](https://vercel.com/docs/agent-resources/skills) | Vercel's Agent Skills docs |
| skills.sh | [link](https://skills.sh) | Vercel skills directory |
| agentskills.io | [link](https://agentskills.io/home) | Official SKILL.md spec host |
| Turbodocx | [link](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best Claude Code Plugins, Skills & MCP Servers (2026) |
| DEV Community (raxonstudios) | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best Claude Code Skills & Plugins guide |
| Claudefa.st | [link](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ Best MCP Servers for Claude Code |
| Popularaitools | [link](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | Claude Code Skills, Plugins, CLIs 2026 |
| Devtoolpicks | [link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Claude Skills vs MCP vs Plugins decision guide |
| Explainx.ai | [link](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | Complete guide to agent skills |
| Chris Ayers blog | [link](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Agent Skills, Plugins and Marketplace guide |
| Agensi | [link](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Claude Code Plugins vs Skills explained |
| Deepwiki | [link](https://deepwiki.com/anthropics/skills/6.1-agent-skills-specification) | Agent Skills Specification deep-dive |
| mcpservers.org | [link](https://mcpservers.org) | Awesome MCP Servers community directory |
| Intuz | [link](https://www.intuz.com/blog/best-mcp-servers) | Top 10 MCP Servers in 2026 |
| k2view | [link](https://www.k2view.com/blog/awesome-mcp-servers) | Top 15 awesome MCP servers 2026 |
| Claude Skills Tutorials | [link](https://claudeskills.cc/tutorials) | Tutorial hub for Claude Skills |
| Medium ranking | [link](https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840) | Ranking of 25 Claude Code YouTube videos |

---

## Stats Block

```
├─ 🟠 Reddit: ~4,200 weekly r/ClaudeCode contributors │ via aggregators (direct thread data unavailable)
├─ 🔵 X: 10 posts │ thousands of likes combined │ 10+ reposts
├─ 🔴 YouTube: 8 videos │ views data not retrieved │ 0 with transcripts
├─ 🟢 HN: 8 stories │ ~800+ points │ 30+ comments
├─ 🟣 TikTok: 0 videos │ not retrieved
├─ 🩷 Instagram: 0 reels │ not retrieved
├─ 🦋 Bluesky: 0 posts │ not retrieved
├─ 📊 Polymarket: 0 markets │ no active markets on agent skills found
├─ 🌐 Web: 45+ pages
└─ 🗣️ Top voices: @claudeai, @WesRothMoney, @omarsar0 │ r/ClaudeCode (4.2k/wk), HN/simonw
```

---

## Data Gaps

- **Reddit**: No direct Reddit thread URLs retrieved — all Reddit data came via third-party aggregator summaries (morphllm.com, aitooldiscovery.com, dev.to). Specific post titles, scores, and URLs not available. Approximate coverage: 30%.
- **TikTok**: Not queried; likely active given the tutorial video content pattern. Gap: ~0% coverage.
- **Instagram**: Not queried. Gap: ~0% coverage.
- **Bluesky**: No results returned; either limited activity on this topic or search indexing gap. Gap: ~0% coverage.
- **Polymarket**: No prediction markets found for agent skills/plugin ecosystem topics. Gap: 0% relevant markets.
- **YouTube transcripts**: 8 videos found but no transcripts retrieved — view/like counts not available. Coverage: ~30% (titles and context only).
- **X engagement metrics**: Like/repost counts not specifically retrieved — described qualitatively. Coverage: ~60%.
- **HN comment details**: Full comment thread content retrieved for threads 1-5; threads 6-8 have URL only. Coverage: ~65%.
- **Noise**: Very high volume of SEO-optimized "best skills 2026" content makes it difficult to distinguish genuine practitioner discussion from marketing content. An estimated 40-50% of web results are low-signal listicles.
- **Overall coverage estimate**: ~65-70% of relevant signal captured across available platforms.

---

## Key Quotes

> "Claude is powerful, but real work requires procedural knowledge and organizational context." — Anthropic Engineering Team ([link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

> "Building a skill for an agent is like putting together an onboarding guide for a new hire." — Anthropic Engineering Team ([link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

> "Agents in 2026 are running with the same access level as the developer who run them." — Wombat creator on HN ([link](https://news.ycombinator.com/item?id=47418076))

> "If you are writing them because the AI using them will help you, you have a very strong and immediate incentive." — 7thpower on HN ([link](https://news.ycombinator.com/item?id=45619537))

> "This is a big deal. Claude Code now has dynamic tool loading… Enabling this to reduce all of that context bloat is going to make it more effective and faster to integrate agents with tools." — @omarsar0 on X ([link](https://x.com/omarsar0/status/2011589983090688262))

> "Plugin maintainers do not want to have to build a marketplace as well as a plugin." — Community developer on HN ([link](https://news.ycombinator.com/item?id=45530150))

> "Once you have a few dozen Skills, a handful of MCP servers, and CLAUDE.md files scattered across projects, managing them through ~/.claude.json and manual file editing gets old fast." — IO0oI (Ensemble creator) on HN ([link](https://news.ycombinator.com/item?id=46922223))

> "Most people use Claude with zero plugins. Meanwhile, developers who install these are building 10x faster." — @heygurisingh on X ([link](https://x.com/heygurisingh/status/2039920621153587238))

> "Deploying just ten MCP plugins creates a 92% probability of exploitation." — VentureBeat ([link](https://venturebeat.com/security/mcp-stacks-have-a-92-exploit-probability-how-10-plugins-became-enterprise))
