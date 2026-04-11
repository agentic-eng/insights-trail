# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-11
**Query type:** GENERAL
**Sources:** X/Twitter, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 19 posts | 837 likes, 289 reposts, 78 replies | High engagement on setup guides and security tools |
| Web | 36 pages | — | via WebSearch; official docs, blog posts, GitHub repos, registries |

---

## Synthesized Findings

### 1. The Terminology War: Skills vs. MCP Servers vs. Plugins vs. Extensions

The Claude Code ecosystem has a terminology problem that community educators are rushing to resolve. Three overlapping terms — Skills, MCP servers, and Plugins — describe distinct things, and the confusion is generating enormous content demand.

**Skills** are markdown-based instruction files (SKILL.md) that define reusable workflows and can be auto-triggered by context or invoked manually as slash commands. They add domain expertise without consuming context. **MCP servers** are standalone programs implementing the open Model Context Protocol, connecting Claude to external tools — GitHub, Figma, databases, Slack — through a standardized JSON interface. **Plugins** are the newest layer (launched October 2025): installable bundles that combine skills, MCP configs, hooks, and agents into a single distributable unit.

The definitive community breakdown, per @Dharmikpawar31 (206 likes, 48 reposts): "CLAUDE.md → your project's memory layer • .claude/ → extensions hub • commands/ → reusable slash commands • skills/ → auto-triggered workflows (SKILL.md) • agents/ → sub-agents (.yml) • plugins/ → packaged setups • .mcp.json → external tool connections." The same breakdown from @dkare1009 (34 likes) went viral weeks earlier: "Weeks ago I shared an Agentic AI project structure. It blew up. But people kept asking: 'Where do Skills go?'"

The official Claude Code docs define three tiers (per code.claude.com/docs): Skills for workflows, MCP servers for tool connectivity, Hooks for deterministic automation, and Plugins as the packaging format for all of the above.

Sources: X (@Dharmikpawar31, @dkare1009), Web (morphllm.com, agentpatch.ai, agentwiki.org, code.claude.com)

### 2. Ecosystem Scale: The Numbers Are Getting Absurd

The growth statistics being cited across sources have become a defining feature of 2026 discourse around Claude Code extensions:

- **110,000 GitHub stars** on the anthropics/claude-code repo (per GitHub issue #41068)
- **1,273+ community skills** cited by bittalks.org as of March 27 — "growing faster than any plugin ecosystem in developer tool history"
- **2,811 skills and 415 plugins** tracked by the community marketplace as of March 2026 (per claudefa.st)
- **2,500+ marketplaces** now available (per claudemarketplaces.com)
- **200,000+ agent skills** claimed by SkillsMP (per @Suryanshti777)
- **89,000+ installs** for the most popular single plugin: feature-dev (per @8020principal and TurboDocx)
- **84K+ GitHub stars** on awesome-mcp-servers; **52K+ stars** on awesome-claude-skills
- **$2.5B ARR in under a year, 29M daily installs** for Claude Code overall (per @stackaible — unverified, treat as community claim)

The ecosystem grew from zero to this scale in roughly a year. For context: Claude Code launched its plugin system in October 2025, and by March 2026 community marketplaces were tracking thousands of entries.

Sources: X (@Suryanshti777, @stackaible, @8020principal), Web (bittalks.org, claudefa.st, claudemarketplaces.com, github.com)

### 3. Top MCP Servers — What Practitioners Are Actually Using

The most frequently cited MCP servers across the ecosystem in March–April 2026:

1. **GitHub MCP** — Repos, PRs, issues, CI/CD management
2. **Figma MCP** — Read designs, extract tokens, generate code from files
3. **Playwright MCP** — Browser automation and E2E testing
4. **Context7** (by Upstash) — Version-specific library documentation injected live into context, replacing stale training data
5. **PostgreSQL/SQLite** — Natural language to SQL
6. **Vercel MCP** — Deploy, check logs
7. **Notion MCP** — Knowledge base access
8. **Google Workspace** — Calendar, Drive, Gmail, Docs, Sheets (per @8020principal)
9. **Slack** — Channels, threads, post messages
10. **Memory Bank** — Persistent context across sessions

Per @mejba_92: "12 extensions (trimmed from 23). 4 MCP servers always connected." This reflects a common practitioner pattern: start broad, trim to a working set of 5–8. Per TurboDocx: "Most working stacks land at five to eight tools total, and more than ten becomes hard to maintain."

**Key optimization:** MCP Tool Search now enables lazy loading, reducing context usage by up to 95% — enabling practitioners to have all servers configured without paying the context cost unless they're needed.

Sources: X (@8020principal, @mejba_92, @NeuroBrowse), Web (claudefa.st, ailog.page, TurboDocx, turbodocx.com, code.claude.com/docs/en/mcp)

### 4. The Plugin Distribution Problem — And Who's Solving It

The ecosystem's discovery and distribution layer is fragmented, and multiple actors are building competing solutions:

**Official channels:**
- Anthropic launched a plugin marketplace with admin controls and the Customize hub for skills, plugins, and connectors (per @buildwithhassan, March 17 recap)
- The official MCP Registry lives at registry.modelcontextprotocol.io
- Official docs at code.claude.com/docs/en/discover-plugins cover marketplace subscription

**Community tools:**
- **claudemarketplaces.com** — aggregates 2,500+ marketplaces; each acts as a subscribable registry
- **TokRepo** — free registry with 500+ skills, MCP servers, and workflows, searchable by category
- **CCPI package manager** (jeremylongshore/claude-code-plugins-plus-skills) — terminal-native with `ccpi search`, `ccpi install`, `ccpi list --installed`; 340 plugins + 1367 skills; MIT licensed
- **SkillsMP** — claims 200,000+ agent skills, billed as "App Store for AI Agents"
- **allagents** (@christso) — "workspace manager for AI coding agent plugins across Claude Code, Copilot, Cursor, Codex, and more"
- **awesome-claude-code-toolkit** (rohitg00) — 135 agents, 35 curated skills + 400,000 via SkillKit, 42 commands, 176+ plugins

**Enterprise layer emerging:**
- AWS launched Agent Registry (preview) via Amazon Bedrock AgentCore — a private, governed catalog for agents, tools, skills, MCP servers within organizations
- Kong launched MCP Server Registry for enterprise governance
- agentic-community/mcp-gateway-registry — enterprise MCP Gateway with OAuth, Keycloak/Entra integration

Per icme.io: "Agents have registries, package managers, skill directories, and protocol-native discovery layers. There is no single front door." The discoverability problem is real: "Research shows agent accuracy collapses past 30 tools when descriptions overlap. Past 100, it's basically random."

Sources: X (@christso, @Suryanshti777, @buildwithhassan), Web (claudemarketplaces.com, registry.modelcontextprotocol.io, AWS, Kong, icme.io, truefoundry.com, medium.com/@aiforhuman)

### 5. Cross-Platform Skills — The Emerging Standard

The most strategically important development: skills are becoming cross-platform. Per bittalks.org: "Skills work across Claude Code, Cursor, Codex CLI, and Gemini CLI — they're becoming cross-platform." The agentwiki.org entry notes: "Skills follow the open Agent Skills standard, which works across multiple AI coding tools."

GitHub Copilot CLI added `~/.agents/skills/` as a personal skill discovery directory "aligned with VS Code extension" (per @GHCopilotCLILog, 115 likes). VS Code 1.110 added "Agent plugins (experimental)" that bundle skills, commands, agents, MCP servers, and hooks together — and "extension hooks from multiple extensions now merge instead of overwriting" (per @GHCopilotCLILog and @_kkoga).

The competitive angle: per @aakashgupta (39 likes): "Anthropic created MCP as an open standard, and Claude Code, Cursor, Windsurf, and dozens of other tools connect to the same servers through the same protocol... So why is OpenAI announcing 'plugins'? Because **the integration layer is the lock-in layer**. MCP democratizes tools but plugins create platform dependency."

OpenAI shipped a first-class plugin system for Codex on March 26-27. Per @botnewsnetwork: "The feature directly answers the main enterprise objection to AI coding agents: you can't roll them out consistently across a team." The competition has arrived.

Sources: X (@aakashgupta, @GHCopilotCLILog, @botnewsnetwork, @_kkoga), Web (bittalks.org, agentwiki.org)

### 6. Security: A New Attack Surface Has Emerged

MCP servers and plugins create a new class of endpoint risk that the security community noticed. The most engaged post this cycle: @AISecHub (188 likes, 40 reposts) shipped **claudit-sec** — "single-command visibility into MCP servers, extensions, plugins, connectors, scheduled tasks, and permissions" for Claude Desktop and Claude Code on macOS.

"Claude Desktop introduces a new class of endpoint risk: AI agents with autonomous execution, persistent scheduled tasks, MCP server integrations, browser-control extensions, and OAuth-authenticated connectors to external services. Most of this configuration lives in JSON files scattered across your filesystem."

The enterprise MCP registry solutions (Kong, AWS AgentCore, agentic-community/mcp-gateway-registry) are in part a response to this — providing governed, auditable access rather than ad-hoc JSON file configuration.

Sources: X (@AISecHub, @4save_info), Web (github.com/agentic-community/mcp-gateway-registry, konghq.com)

### 7. Feature Request: Skill-Driven On-Demand MCP Loading

GitHub issue #41068 on anthropics/claude-code (filed March 30, labeled enhancement/area:mcp/area:skills/area:plugins) requests "Skill-Driven On-Demand MCP & Tool Loading." This represents community pressure to make the skills and MCP layers interact more dynamically — letting a skill declare its own tool dependencies rather than requiring global configuration. The `--plan` flag in Claude Code already enables skills to define query strategies; this feature request would extend that to tool loading.

Context: MCP Tool Search (lazy loading) already reduces context by up to 95%. The feature request pushes further toward per-skill tool isolation.

Sources: Web (github.com/anthropics/claude-code/issues/41068)

### 8. Anthropic's 2026 Launch Velocity

Per @buildwithhassan (March 17 recap): Anthropic launched in rapid succession in early 2026 — Claude Cowork, Cowork rollout to Pro/Team/Enterprise/Windows, scheduled tasks in Cowork, Cowork plugins, plugin marketplace and admin controls, new Customize hub for skills/plugins/connectors, Claude Opus 4.6, Claude Sonnet 4.6, 1M context window, agent teams in Claude Code, Claude Code Security, Claude Code Review, automated preview environments. Per @iwhale (230 likes, 175 reposts, Thai language thread): "Anthropic is releasing at extraordinary speed in 2026."

Code Kit v5.0 was released for Claude Code's new Agent Teams feature as of April 9 (per claudefa.st). Agent Teams allows multiple Claude instances to work in parallel on different subtasks, coordinating through a git-based system where agents claim tasks, merge changes continuously, and resolve conflicts automatically.

April 2026 Claude Code changelog adds: CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE env var (keeps existing cache when git pull fails, useful in offline environments); larger MCP result persistence; disables inline shell execution for skills/commands; plugins can now ship executables in bin/.

Sources: X (@buildwithhassan, @iwhale), Web (releasebot.io, claudefa.st)

---

## Cross-Source Patterns

**Pattern 1: Setup guides going viral**
The single most engaging content type this cycle: definitive Claude Code setup cheatsheets (CLAUDE.md + .claude/ directory structure). @Dharmikpawar31 (206 likes) and @dkare1009 (34 likes) both went viral with nearly identical content. The demand signal is clear: developers know they should be using Skills and MCP servers but don't know how to organize them.
- Platforms: X
- Key quote: "You don't need another Claude Code setup. Just this one." — @Dharmikpawar31

**Pattern 2: Security concerns rising with adoption**
@AISecHub's claudit-sec (188 likes) was the second most engaged post. As MCP servers proliferate — each connecting Claude to external services with OAuth credentials, persistent tasks, and file access — security tooling has become a first-class concern.
- Platforms: X
- Key quote: "Claude Desktop introduces a new class of endpoint risk: AI agents with autonomous execution, persistent scheduled tasks, MCP server integrations, browser-control extensions." — @AISecHub

**Pattern 3: The "integration layer is lock-in" debate**
Anthropic's MCP is an open standard. OpenAI's new Codex plugin system is proprietary. Practitioners are debating whether openness or vertical integration wins. @aakashgupta (39 likes, 17 replies): "So why is OpenAI announcing 'plugins'? Because the integration layer is the lock-in layer."
- Platforms: X, Web (botnewsnetwork, aakashgupta)

**Pattern 4: Skills going cross-platform**
Skills are no longer Claude-specific. GitHub Copilot CLI, VS Code extensions, Cursor, Codex CLI, and Gemini CLI are all building skill-compatible layers. "Write once, works everywhere" is the developer dream — but fragmentation remains.
- Platforms: X (@GHCopilotCLILog), Web (bittalks.org, agentwiki.org)

**Pattern 5: Discovery is still broken at scale**
Multiple registry and marketplace projects exist, but tool discoverability degrades at scale. Past 30 overlapping tools, agent accuracy collapses; past 100, it's basically random. Both the official MCP Registry and community solutions (claudemarketplaces.com, CCPI, TokRepo) are racing to solve this.
- Platforms: Web (icme.io, medium.com/@aiforhuman, truefoundry.com)

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Dharmikpawar31 | "You don't need another Claude Code setup. Just this one. Where do Skills go? How do Hooks work? How do you connect MCP servers?" | 206 | 48 | https://x.com/Dharmikpawar31/status/2037792844916965714 |
| @iwhale | "All Claude updates since early 2026 (Thai language summary): Anthropic releasing at extraordinary speed" | 230 | 175 | https://x.com/iwhale/status/2036362880946413650 |
| @AISecHub | "claudit-sec — single-command visibility into MCP servers, extensions, plugins, connectors, scheduled tasks, and permissions" | 188 | 40 | https://x.com/AISecHub/status/2035937270885142961 |
| @GHCopilotCLILog | "Add ~/.agents/skills/ as personal skill discovery directory aligned with VS Code; hooks from multiple extensions now merge" | 115 | 12 | https://x.com/GHCopilotCLILog/status/2037937811857305685 |
| @aakashgupta | "The integration layer is the lock-in layer. MCP democratizes tools but plugins create platform dependency." | 39 | 5 | https://x.com/aakashgupta/status/2037366003211087873 |
| @dkare1009 | "You won't need any other project structure for Claude Code. Just this one." | 34 | 7 | https://x.com/dkare1009/status/2035906942741151944 |
| @Suryanshti777 | "SkillsMP — marketplace with 200,000+ agent skills designed for Claude Code. Like apps. AI agents can now install capabilities." | 12 | 2 | https://x.com/Suryanshti777/status/2031945821852483852 |
| @gadievron | "We currently provide only Skills and VS Code extensions in the public version, will add support for MCP servers and Claude Code Plugins" | 1 | 0 | https://x.com/gadievron/status/2039004271635509655 |
| @botnewsnetwork | "OpenAI just gave Codex a plugin system. The Claude Code war just got a new front." | 2 | 0 | https://x.com/botnewsnetwork/status/2038089014834852227 |
| @christso | "allagents — workspace manager for AI coding agent plugins across Claude Code, Copilot, Cursor, Codex" | 1 | 0 | https://x.com/christso/status/2035966273482588521 |
| @8020principal | "The Claude mcp/plugin ecosystem grew fast. MCP servers: Slack, GitHub, Google Workspace, Brave Search, PostgreSQL, Memory Bank, Filesystem" | 0 | 0 | https://x.com/8020principal/status/2035492336394961090 |
| @buildwithhassan | "Things Anthropic has launched in 2026: Cowork plugins, plugin marketplace, agent teams, Claude Code Security & Review" | 2 | 0 | https://x.com/buildwithhassan/status/2033952755744731641 |
| @stackaible | "Claude Code — $2.5B ARR in under a year, 29M daily installs" | 1 | 0 | https://x.com/stackaible/status/2032495261352874350 |
| @woon_wong23193 | "cc-update-all: One slash command bulk-updates ALL Claude Code plugins, MCP servers (Cursor/Cline/Roo)" | 3 | 0 | https://x.com/woon_wong23193/status/2034307414334525647 |
| @mejba_92 | "12 extensions (trimmed from 23). 4 MCP servers always connected. Full config files." | 0 | 0 | https://x.com/mejba_92/status/2035852212648501543 |
| @NeuroBrowse | "Claude Desktop—MCP servers connected to Notion, Stripe, Supabase, Canva. Three interfaces. One AI. Different jobs." | 3 | 0 | https://x.com/NeuroBrowse/status/2037289560468521035 |
| @_kkoga | "VS Code 1.110: Agent plugins (experimental) added — skills, commands, agents, MCP servers, hooks bundled. Agent Debug panel added." | 0 | 0 | https://x.com/_kkoga/status/2034630067158950308 |
| @4save_info | "claudit sec — single-command visibility into MCP servers, extensions, plugins, connectors, scheduled tasks, and permissions" | 0 | 0 | https://x.com/4save_info/status/2036016413752820149 |
| @grok | "Claude Code Resource Bible — massive curated list of 50+ tools, GitHub repos, docs, and frameworks" | — | — | https://x.com/grok/status/2041383051519778935 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| bittalks.org | https://bittalks.org/blog/agent-skills-ecosystem-explodes-2026/ | 1,273+ community skills, cross-platform skills (Claude Code, Cursor, Codex CLI, Gemini CLI), skills replacing manual config |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers guide; Code Kit v5.0 for Agent Teams; 2,811 skills + 415 plugins in marketplace |
| claudefa.st | https://claudefa.st/blog/tools | MCP setup in 6 lines of JSON; Agent Teams Code Kit v5.0 |
| github.com | https://github.com/anthropics/claude-code/issues/41068 | Feature request: Skill-Driven On-Demand MCP & Tool Loading; repo has 110K stars |
| agentpatch.ai | https://agentpatch.ai/blog/claude-code-extensions-2026 | Three-tier definition: MCP servers, Skills, Hooks; "extensions push the ceiling higher" |
| ailog.page | https://ailog.page/7-claude-code-extensions-i-tested-these-are-the-ones-i-kept/ | 7 extensions worth installing: GitHub MCP, Figma MCP, Context7, Playwright, Notion MCP |
| agentwiki.org | https://agentwiki.org/claude_code_skills | Open Agent Skills standard; cross-platform definition |
| code.claude.com | https://code.claude.com/docs/en/mcp | Official MCP integration docs |
| code.claude.com | https://code.claude.com/docs/en/plugins | Official plugin creation docs |
| code.claude.com | https://code.claude.com/docs/en/discover-plugins | Official marketplace discovery docs |
| code.claude.com | https://code.claude.com/docs/en/sub-agents | Official subagents docs |
| code.claude.com | https://code.claude.com/docs/en/changelog | Claude Code changelog |
| releasebot.io | https://releasebot.io/updates/anthropic/claude-code | April 2026 updates: PLUGIN_KEEP_MARKETPLACE_ON_FAILURE, larger MCP persistence, plugins can ship executables |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 skills; CCPI package manager; MIT licensed |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 2,500+ marketplaces; registry subscription model |
| aitmpl.com | https://www.aitmpl.com/plugins/ | Plugin discovery; install counts; categories |
| Stacklok ToolHive | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | Agent skills as reusable bundles; full lifecycle management; install from ToolHive Registry, OCI, or Git |
| AWS AgentCore | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | Agent Registry preview: private, governed catalog for agents/tools/skills/MCP servers |
| AWS blog | https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/ | Technical deep-dive on Agent Registry architecture |
| agentic-community/mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth, Keycloak/Entra; dynamic tool discovery |
| Kong Inc. | https://konghq.com/products/mcp-registry | Enterprise MCP Server Registry; governance and auditable access |
| registry.modelcontextprotocol.io | https://registry.modelcontextprotocol.io/ | Official Anthropic/MCP community registry |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Comparison of MCP registries for developers and enterprises |
| icme.io | https://blog.icme.io/getting-found-by-agents-a-builders-guide-to-tool-discovery-in-2026/ | Builder's guide: agents have no single front door; accuracy collapses past 30 overlapping tools |
| medium.com/@aiforhuman | https://medium.com/@aiforhuman/beyond-service-discovery-54040e716327 | MCP registry must evolve; thousands of tools, discoverability at scale unsolved |
| github.com/hesreallyhim | https://github.com/hesreallyhim/awesome-claude-code | Curated skills, hooks, slash-commands, agent orchestrators, plugins |
| github.com/rohitg00 | https://github.com/rohitg00/awesome-claude-code-toolkit | 135 agents, 35 skills + 400K via SkillKit, 176+ plugins, 14 MCP configs |
| github.com/travisvn | https://github.com/travisvn/awesome-claude-skills | 52K+ stars curated skills list |
| github.com/wong2 | https://github.com/wong2/awesome-mcp-servers | 84K+ stars MCP servers list |
| awesomeclaude.ai | https://awesomeclaude.ai/top-mcp-servers | MCP servers ranked by GitHub stars |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full-stack explainer: MCP, Skills, Subagents, Hooks |
| trensee.com | https://www.trensee.com/en/blog/explainer-claude-code-skills-fork-subagents-2026-03-31 | Advanced patterns: Skills, Fork, Subagents |
| claudefa.st (agent teams) | https://claudefa.st/blog/guide/agents/agent-teams | Agent Teams setup guide 2026 |
| medium.com/@unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills for Claude and any coding agent |
| blakecrosley.com | https://blakecrosley.com/guides/claude-code | CLI reference: hooks, MCP, subagents |
| skillsplayground.com | https://skillsplayground.com/guides/claude-code-plugins/ | Complete plugins guide |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins complete guide |
| morphllm.com (extensions) | https://www.morphllm.com/claude-code-extensions | MCP, Skills, Agents & Hooks guide |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills/plugins/CLIs with install instructions |
| dev.to (williamwangai) | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP servers: when to use each |
| dev.to (raxxostudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills & plugins guide |
| self.md | https://self.md/guides/best-claude-code-plugins/ | Community curated plugin list |
| toolradar.com | https://toolradar.com/blog/best-mcp-servers-claude-code | MCP servers by category |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best plugins/skills/MCP servers; feature-dev at 89K installs; MCP lazy loading 95% context reduction |

---

## Stats Block

```
├─ 🔵 X: 19 posts │ 837 likes │ 289 reposts
├─ 🌐 Web: 36 pages — claudefa.st, bittalks.org, agentpatch.ai, ailog.page, AWS, Kong, DEV Community, morphllm.com, GitHub (multiple repos), registry.modelcontextprotocol.io, Stacklok, icme.io, agentwiki.org
└─ 🗣️ Top voices: @Dharmikpawar31 (206 likes), @iwhale (230 likes, 175rt), @AISecHub (188 likes), @GHCopilotCLILog (115 likes), @aakashgupta (39 likes) │ bittalks.org, claudefa.st, icme.io
```

---

## Data Gaps

- **Reddit: 0 results** — All subreddit searches returned 403/402 errors (rate limited or payment required). This is a significant gap; r/ClaudeAI and r/LocalLLaMA likely have high-signal discussions about MCP servers and plugins that are not reflected here.
- **YouTube: 0 results** — yt-dlp is not installed in this environment; YouTube tutorials, walkthroughs, and channel content on skills/MCP setup are absent.
- **Hacker News: 0 results** — No HN items found. HN discussions on MCP protocol design and security implications would be high-signal for this topic.
- **TikTok/Instagram: 0 results** — Not configured.
- **Polymarket: 0 results** — No prediction markets on Claude Code extension ecosystem growth.
- **GitHub: 0 results from live API** — No GitHub token available; star counts and issue data from web search approximations only.
- **X coverage concentration**: Top engagement concentrated in a few viral posts; many long-tail discussions likely missed.
- **Approximate coverage**: ~40–50% (X + Web only, no Reddit/YouTube/HN/GitHub live data).

---

## Key Quotes

> "You don't need another Claude Code setup. Just this one. Everyone kept asking: Where do Skills go? How do Hooks work? How do you connect MCP servers?" — @Dharmikpawar31 on X ([link](https://x.com/Dharmikpawar31/status/2037792844916965714))

> "The integration layer is the lock-in layer. MCP democratizes tools but plugins create platform dependency." — @aakashgupta on X ([link](https://x.com/aakashgupta/status/2037366003211087873))

> "Claude Desktop introduces a new class of endpoint risk: AI agents with autonomous execution, persistent scheduled tasks, MCP server integrations, browser-control extensions, and OAuth-authenticated connectors to external services." — @AISecHub on X ([link](https://x.com/AISecHub/status/2035937270885142961))

> "1,273+ community skills now exist — growing faster than any plugin ecosystem in developer tool history." — bittalks.org ([link](https://bittalks.org/blog/agent-skills-ecosystem-explodes-2026/))

> "MCP servers give agents the raw tools they can call; skills give them the knowledge of when, why, and how to use those tools effectively." — Stacklok ToolHive ([link](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates))

> "Research shows agent accuracy collapses past 30 tools when descriptions overlap. Past 100, it's basically random." — icme.io ([link](https://blog.icme.io/getting-found-by-agents-a-builders-guide-to-tool-discovery-in-2026/))

> "The dream is a converging ecosystem standard where plugin authors write once and it works everywhere." — @christso on X ([link](https://x.com/christso/status/2035966273482588521))

> "Add ~/.agents/skills/ as personal skill discovery directory aligned with VS Code extension. Extension hooks from multiple extensions now merge instead of overwriting." — @GHCopilotCLILog on X ([link](https://x.com/GHCopilotCLILog/status/2037937811857305685))

> "Before: AI tools could generate text or code. Now: AI agents can install capabilities. Just like apps." — @Suryanshti777 on X ([link](https://x.com/Suryanshti777/status/2031945821852483852))

> "Claude Code ships with zero extensions — you need Skills and MCP servers to unlock its full potential." — ailog.page ([link](https://ailog.page/7-claude-code-extensions-i-tested-these-are-the-ones-i-kept/))
