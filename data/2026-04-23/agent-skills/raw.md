# Agent Skills — Raw Research Data
**Date:** 2026-04-23
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## SEARCH QUERY 1: Claude Code skills plugins extensions 2026

### Results
- https://code.claude.com/docs/en/plugins — Official Claude Code plugin documentation
- https://github.com/ComposioHQ/awesome-claude-plugins — Curated list of plugins extending Claude Code via custom commands, agents, hooks, MCP servers
- https://claudemarketplaces.com/ — Claude Code Plugins | Skills, MCP Servers & Marketplace Directory
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 423 plugins, 2,849 skills, 177 agents for Claude Code; open-source marketplace at tonsofskills.com with ccpi CLI package manager
- https://github.com/quemsah/awesome-claude-plugins — Automated collection of Claude Code plugin adoption metrics via n8n workflows
- https://composio.dev/content/top-claude-code-plugins — 10 top Claude Code plugins to consider in 2026
- https://self.md/guides/best-claude-code-plugins/ — Best claude code plugins 2026
- https://www.scriptbyai.com/claude-code-resource-list/ — The Ultimate Claude Code Resource List (2026 Edition)
- https://www.firecrawl.dev/blog/best-claude-code-plugins — Top 10 Claude Code Plugins to Try in 2026
- https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 — Top 10 Claude Code Skills, Plugins & CLIs for 2026

### Key Findings
- As of April 17, 2026: 423 plugins, 2,849 skills, 177 agents across 26 published packages in claude-code-plugins namespace, updated daily by GitHub Actions
- Skills are features Claude automatically uses when needed (e.g., Playwright for browser automation when testing login flow)
- Subagents are specialized AI agents for specific dev tasks (security-auditor, frontend-developer)
- MCP Servers connect Claude to external services (Linear, GitHub, Postgres)
- Popular plugins: Awesome Claude Plugins (registry), Claude-Mem (long-term memory), Superpowers (lifecycle planning), Local-Review (parallel diff reviews), Plannotator (structured plans), Ralph Wiggum Plugin (visual testing), Shipyard (lifecycle + IaC + security), Dev-Browser Plugin (lightweight browsing)
- feature-dev skill: most popular Claude Code plugin with over 89,000 installs
- Claude Code no longer loads full MCP tool schemas at startup; loads tool names only, fetches full schemas on demand via ToolSearch — cuts context overhead by ~95% when running 50+ tools

---

## SEARCH QUERY 2: MCP servers tools agent marketplace 2026

### Results
- https://mcpmarket.com/ — MCP Market: directory of MCP servers and clients
- https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools — Microsoft Learn: Using MCP Tools
- https://mcp.harishgarg.com/use/ai-agent-marketplace-index/mcp-server/with/perplexity — Harishgarg MCP index
- https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a — MCP Gateways in 2026: Top 10 Tools
- https://mcpmarket.com/daily/top-mcp-server-list-april-21-2026 — Top MCP Servers for April 21, 2026
- https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 — Best MCP Servers for Sales Teams in 2026
- https://lobehub.com/mcp — LobeHub MCP Servers Marketplace
- https://agentpatch.ai/blog/mcp-marketplace-agentpatch/ — AgentPatch: The MCP Marketplace for AI Agents
- https://mcpservers.org — Awesome MCP Servers collection
- https://www.taskade.com/blog/mcp-servers — 15 Best MCP Servers for AI Developers in 2026

### Key Findings
- MCP ecosystem April 2026: 500+ servers, 97 million monthly SDK downloads, official client support across every major editor
- Multiple MCP gateway solutions: single governed entry point for tool access; centralizes auth, authorization, auditing, traffic management
- AgentPatch model: browse catalog, pick tools, connect once; handles hosting, reliability, billing
- LobeHub hosts MCP Toolbox for Databases (enterprise database connections)
- Popular MCP servers: Figma, Playwright (browser automation/E2E testing), Vercel (deploy/logs), PostgreSQL (query databases), GitHub (create PRs/review issues)
- MCP Channels: let MCP servers push messages into Claude sessions (still research preview April 2026)
- A typical 5-server setup with 58 tools uses ~55,000 tokens before any conversation starts

---

## SEARCH QUERY 3: Agent skill discovery distribution plugin ecosystem 2026

### Results
- https://developers.openai.com/codex/skills — Agent Skills on OpenAI Codex
- https://deepwiki.com/microsoft/agent-skills/4-plugins — Microsoft agent-skills plugins
- https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution — AI Agent Marketplaces 2026: Discovery and Distribution
- https://github.com/vercel-labs/skills — Vercel open agent skills tool (npx skills)
- https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ — Extend your coding agent with .NET Skills
- https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ — AI Agent Skills Complete Guide 2026: Building Reusable Agent Capabilities
- https://agentskills.io/home — Agent Skills Overview (official open standard site)
- https://inference.sh/blog/skills/agent-skills-overview — Agent Skills: The Open Standard for AI Capabilities
- https://skillsmp.com/ — Agent Skills Marketplace - Claude, Codex & ChatGPT Skills
- https://github.com/VoltAgent/awesome-agent-skills — 1000+ agent skills from official dev teams, compatible with Claude Code, Codex, Gemini CLI, Cursor, and more

### Key Findings (agentskills.io)
35+ platforms adopting Agent Skills standard as of April 2026:
Junie (JetBrains), Gemini CLI, Autohand Code CLI, OpenCode, OpenHands, Mux (Coder), Cursor, Amp, Letta, Firebender, Goose (Block), GitHub Copilot, VS Code, Claude Code, Claude (claude.ai), OpenAI Codex, Piebald, Factory, pi, Databricks Genie Code, Agentman, TRAE (ByteDance), Spring AI, Roo Code, Mistral Vibe, Command Code, Ona, VT Code, Qodo, Laravel Boost, Emdash, Snowflake Cortex Code, Kiro, Workshop, Google AI Edge Gallery, nanobot, fast-agent

Eight marketplaces matter in Q2 2026:
- Anthropic Claude Skills (first-party directory, free distribution)
- OpenAI GPT Store (revenue share on usage)
- MCP Hubs
- Hugging Face Spaces
- Replit Agent Market (direct-sale model)
- LangChain Hub
- Vercel Agent Gallery
- Cloudflare AI Marketplace (bills on inference)

Plugin marketplace distributed registry pattern: 3 marketplace.json files deployed to different locations, symlinks in skills/ for cross-platform discovery.

---

## SEARCH QUERY 4: Claude Code MCP tool registry custom workflows April 2026

### Results
- https://code.claude.com/docs/en/mcp — Official MCP documentation
- https://github.com/hesreallyhim/awesome-claude-code — Curated awesome-claude-code list
- https://releasebot.io/updates/anthropic/claude-code — Claude Code Release Notes April 2026
- https://generect.com/blog/claude-mcp/ — Ultimate Guide to Claude MCP Servers & Setup 2026
- https://scottspence.com/posts/configuring-mcp-tools-in-claude-code — Configuring MCP Tools in Claude Code
- https://dextralabs.com/blog/claude-code-mcp-enterprise-ai-integrations/ — Claude Code MCP Server Setup: Enterprise Integration Guide
- https://www.mindstudio.ai/blog/how-to-use-mcp-servers-with-claude-code — How to Use MCP Servers with Claude Code
- https://markaicode.com/claude-code-mcp-integration/ — Claude Code MCP Integration: Connect to Any External Tool
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — 50+ Best MCP Servers for Claude Code in 2026
- https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop — Getting Started with Local MCP Servers

### Claude Code April 2026 Release Notes (Skills/MCP/Plugins)
**Skills:**
- Model can now discover/invoke built-in slash commands via Skill tool (v2.1.108)
- Skills with `disable-model-invocation: true` now work properly mid-message
- /skills menu gained token-count sorting with `t` toggle (v2.1.111)

**MCP:**
- Faster startup when multiple stdio servers configured (v2.1.116)
- Resources/templates listing deferred to first mention
- /doctor warns on duplicate MCP server config across scopes
- Fixed tool calls hanging when server connections drop (v2.1.110)
- Stalled subagents fail clearly after 10 min instead of hanging silently
- OAuth authServerMetadataUrl config override honored on token refresh (v2.1.97)

**Plugins:**
- Plugin install now installs missing dependencies on already-installed plugins (v2.1.117)
- blockedMarketplaces and strictKnownMarketplaces enforced during install/update/refresh
- /reload-plugins auto-installs missing dependencies from configured marketplaces
- Background monitor support via top-level `monitors` manifest key (v2.1.105)

---

## HACKER NEWS THREADS

### HN 45607117 - "Claude Skills" (816 pts, 427 comments, ~Oct 2025)
URL: https://news.ycombinator.com/item?id=45607117
**Notable comments:**
- **simonw**: "Claude Skills are awesome, maybe a bigger deal than MCP"
- **libraryofbabel**: Skills involve storing instruction files, searching available skills at startup, telling LLM how to invoke them, using bash tools to read skill files when needed
- **pants2**: characterized skills as "a design pattern / prompt engineering trick" rather than requiring formal specification
- **ChadMoran**: "reliably triggering appropriate tool usage remains challenging — the system requires careful context injection rather than deterministic behavior"

### HN 45619537 - "Claude Skills are awesome, maybe a bigger deal than MCP" (738 pts, 370 comments, ~Oct 2025)
URL: https://news.ycombinator.com/item?id=45619537
**Notable comments:**
- **michael1999**: context documents for AI resemble useful developer documentation; three theories: faster feedback loops, AI reduces documentation costs, programmers motivated by personal productivity
- **7thpower**: framed as principal-agent problem — docs written for AI solving your immediate needs generate stronger incentives than docs for hypothetical future human readers
- **emn13**: real breakthrough is targeting current, specific problems rather than predicting future needs
- **simonw**: skills represent formalization of existing markdown-plus-CLI patterns; distinction lies in automated discovery: Claude scans skill folders for YAML metadata, enabling self-directed tool selection without manual user intervention
- **causal**: "Is this really all this is?" — embedding context with markdown files already accomplishes similar objectives
- **tptacek**: actual innovation is tool calling capabilities, not MCP specifically; skills are improved context-management vs MCPs' token-heavy front-loading

### HN 45530150 - "Customize Claude Code with plugins" (48 pts, 9 comments, ~Oct 2025)
URL: https://news.ycombinator.com/item?id=45530150
**Notable comments:**
- **BrutalCoding**: `/plugin marketplace add anthropics/claude-code` SSH auth error; resolved with full HTTPS URL
- **joesaunderson**: launched claudecodemarketplace.com to help plugin creators share work
- **handfuloflight**: claudecodemarketplace.com triggered Chrome security warning
- **jngiam1**, **ananddtyagi**: shared own marketplace repos

### HN 46922223 - "Show HN: Ensemble – macOS App to Manage Claude Code Skills, MCPs, and Claude.md" (1 pt, 1 comment, ~Feb 2026)
URL: https://news.ycombinator.com/item?id=46922223
**Notable quote (IO0oI):** "Once you have a few dozen Skills, a handful of MCP servers, and CLAUDE.md files scattered across projects, managing them through ~/.claude.json and manual file editing gets old fast."
Built with Tauri 2 (Rust backend, React frontend), MIT license.

### HN 47321892 - "Claude Code Skills and Plugins as an Open Source Project" (2 pts, 1 comment, ~March 2026)
URL: https://news.ycombinator.com/item?id=47321892
**Comment (jungard):** "180+ production-ready skills and plugins for Claude Code, OpenAI Codex, Gemini CLI, and OpenClaw — reusable expertise bundles that transform AI coding agents into specialized professionals across engineering, product, marketing, compliance, and more."

### Other HN threads found:
- https://news.ycombinator.com/item?id=47543139 — "Anatomy of the .claude/ folder"
- https://news.ycombinator.com/item?id=43410866 — "Hacking Your Own AI Coding Assistant with Claude Pro and MCP"
- https://news.ycombinator.com/item?id=45642911 — "Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP"
- https://news.ycombinator.com/item?id=46396930 — "CLAUDE.md, Skills, Agents, MCP, slash commands" discussion
- https://news.ycombinator.com/item?id=46531794 — "Claude Code Emergent Behavior: When Skills Combine"

---

## YOUTUBE VIDEOS

- https://www.youtube.com/watch?v=pvxNcQTcIy4 — "Agent Skills or MCP in the era of Claude Code?" (March 10, 2026)
- https://www.youtube.com/watch?v=jzf7DQa2CAc — "How I Use Claude Code With Skills, MCP, Agents & Plugins" (Jan 19, 2026)
- https://www.youtube.com/watch?v=KjEFy5wjFQg — "Top 10 Claude Code Skills, Plugins & CLIs (April 2026)" (~2 weeks ago, in last 30 days)
- https://www.youtube.com/shorts/a8SlmCdJcNM — "Google Stitch MCP Just Made Claude Code 10x Better"
- https://www.youtube.com/watch?v=pBHKTojO1YY — "Better With This Setup (CLAUDE.md + Skills + MCPs)" (March 3, 2026)
- https://www.youtube.com/watch?v=OdtGN27LchE — "Claude Code Skills just Built me an AI Agent Team (2026 Guide)" (Dec 21, 2025)
- https://www.youtube.com/watch?v=6wdvSH61xGw — "Agent Skills vs MCP: What's the difference?" (Jan 4, 2026)
- https://www.youtube.com/watch?v=bFC1QGEQ2E8 — "Claude Skills Explained: 4 Skills to 10x Your Coding Workflow"
- https://www.youtube.com/watch?v=1WImBwiA7RA — "Claude Skills - the SOP for your agent that is bigger than MCP"
- https://www.youtube.com/watch?v=qthyl0GCpDo — "Claude Skills vs MCP: What's the Difference and When to Use Each?" (Nov 20, 2025)

---

## ANTHROPIC OFFICIAL SOURCES

### Anthropic Engineering Blog: "Equipping Agents for the Real World with Agent Skills"
URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
**Published:** October 16, 2025

Key points:
- Skills are directories with SKILL.md (YAML frontmatter: name + description required)
- Progressive disclosure design: Level 1 = skill metadata in system prompt; Level 2 = full SKILL.md when relevant; Level 3+ = additional bundled files
- Context efficiency: Claude triggers skills via Bash tool file reads, avoiding unnecessary context use
- Bundled executable code (Python scripts) for deterministic operations (e.g., PDF form field extraction)
- Guidelines: "Start with evaluation," "structure for scale," "think from Claude's perspective"
- Security: install only from trusted sources; audit unfamiliar skills for code dependencies and external network connections
- Supported across: Claude.ai, Claude Code, Claude Agent SDK, Claude Developer Platform
- Future: planned features for complete lifecycle of creating, discovering, sharing skills; potential MCP integration

### Claude.com Blog: "Skills Explained"
URL: https://claude.com/blog/skills-explained
**Published:** November 13, 2025

Five building blocks comparison:
| Aspect | Skills | Prompts | Projects | Subagents | MCP |
|--------|--------|---------|----------|-----------|-----|
| Provides | Procedural knowledge | Moment-to-moment instructions | Background knowledge | Task delegation | Tool connectivity |
| Persistence | Across conversations | Single conversation | Within project | Across sessions | Continuous connection |
| Best for | Specialized expertise | Quick requests | Centralized context | Specialized tasks | Data access |

Notable quotes:
- "Think of them as specialized training manuals that give Claude expertise in specific domains — from working with Excel spreadsheets to following your organization's brand guidelines."
- "Projects say 'here's what you need to know.' Skills say 'here's how to do things.'"
- "MCP connects Claude to data; Skills teach Claude what to do with that data."
- Progressive disclosure: metadata ~100 tokens; full instructions <5k tokens

### Claude.com Blog: "Building agents that reach production systems with MCP"
URL: https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp

### Agent Skills API Docs
URL: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

### Anthropic Makes Agent Skills Open Standard
URL: https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/
**Date:** December 18, 2025

### GitHub: anthropics/skills — Public repository for Agent Skills
URL: https://github.com/anthropics/skills

---

## OPEN STANDARD COVERAGE

### aibusiness.com: "Anthropic Launches Skills Open Standard for Claude"
URL: https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude

### VentureBeat: "Anthropic launches enterprise 'Agent Skills' and opens the standard"
URL: https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard

### The New Stack: "Agent Skills: Anthropic's Next Bid to Define AI Standards"
URL: https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/

### MindStudio: "What Is Agent Skills as an Open Standard? How Claude, OpenAI, and Google Adopted the Same Format"
URL: https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google
**Date:** March 29, 2026
- No standards committee, no joint announcement, no formal specification — yet Claude skills, ChatGPT function calling, and Gemini FunctionDeclaration are structurally identical
- "There was no standards committee, no joint announcement, and no formal specification. And yet today, a skill definition written for Claude can be adapted for GPT-4o or Gemini in minutes."
- MindStudio's Agent Skills Plugin exposes 120+ typed capabilities

### inference.sh: "Agent Skills: The Open Standard for AI Capabilities"
URL: https://inference.sh/blog/skills/agent-skills-overview
**Last updated:** ~April 13, 2026
- skills.sh: primary distribution platform (npx skills add <owner/repo>)
- Compatible platforms include Claude Code, ChatGPT, Codex CLI, Cursor, GitHub Copilot, Goose, Windsurf, Gemini CLI, Roo Code
- "Skills let anyone package expertise into composable resources that agents can discover and load dynamically."

### Simon Willison: "Claude Skills are awesome, maybe a bigger deal than MCP"
URL: https://simonwillison.net/2025/Oct/16/claude-skills/
**Date:** October 16, 2025
- "Claude can now use Skills to improve how it performs specific tasks"
- "a general agent where anything you can achieve by typing commands into a computer is something that can now be automated"
- Skills avoid MCP's token consumption problem (GitHub MCP consumes tens of thousands of tokens)
- Model-agnostic: functional with Gemini CLI, Codex CLI, and other tools

### DeepWiki: Agent Skills Specification
URL: https://deepwiki.com/anthropics/skills/6.1-agent-skills-specification

### Medium: "Unveiling Agent Skill: Anthropic's Open Standard"
URL: https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71

---

## GITHUB CLI v2.90.0 — `gh skill` (April 16, 2026)

### GitHub Changelog
URL: https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/

### gh skill CLI Manual
URL: https://cli.github.com/manual/gh_skill
URL: https://cli.github.com/manual/gh_skill_install

### Release Notes
URL: https://github.com/cli/cli/releases/tag/v2.90.0
Also: https://github.com/cli/cli/releases/tag/v2.91.0

### Coverage
- https://azukiazusa.dev/en/blog/gh-agent-skill-management/ — "You Can Now Distribute Agent Skills with the `gh` Command"
- https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/ — "gh skill: GitHub CLI Agent Skills Management for Copilot, Claude Code, and Cursor"
- https://app.daily.dev/posts/manage-agent-skills-with-github-cli-cwqtearpx — "Manage agent skills with GitHub CLI"
- https://github.com/anthropics/claude-code/issues/50148 — Feature request for remote skill source integration

**Key features of `gh skill`:**
- Install agent skills from GitHub repo or local directory
- User scope (home dir) or project scope (inside git repo)
- `--pin` flag to lock to specific tag/commit SHA
- Supported agents: GitHub Copilot, Claude Code, Cursor, Codex, Gemini CLI, Antigravity, Amp, Goose, Junie, OpenCode, Windsurf, and more
- Launched April 16, 2026 as public preview (subject to change)

---

## SECURITY: TOXICSKILLS RESEARCH (February 2026)

### Snyk ToxicSkills Study (Feb 5, 2026)
- Scanned 3,984 publicly listed skills across all major registries
- **1,467 skills (36.82%) had at least one security flaw**
- **534 (13.4%) contained critical-level issues**
- **76 confirmed malicious — would steal credentials, install backdoors, or exfiltrate data**
- 8 still live on ClawHub when research published
- Attack vectors: prompt injection + shell payloads, markdown files with full host privileges (filesystem access, terminal execution, network requests, credential visibility)
- Snyk coined term "ToxicSkills" for agent skills that appear harmless in isolation but behave maliciously when executed

### Coverage
- https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/
- https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/
- https://blog.barrack.ai/openclaw-security-vulnerabilities-2026/
- https://github.com/anton-abyzov/specweave/blob/develop/docs-site/blog/2026-02-21-toxicskills-why-your-ai-agent-skills-need-verification.md
- https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/
- https://app.daily.dev/posts/snyk-finds-prompt-injection-in-36-1467-malicious-payloads-in-a-toxicskills-study-of-agent-skills-s-0bdgmynfg
- https://www.penligent.ai/hackinglabs/openclaw-virustotal-clawhub-skill-scanning-turns-the-marketplace-into-a-supply-chain-boundary/
- https://dougseven.com/2026/02/09/trust-without-verification/ — "Trust Without Verification" (Feb 9, 2026)
- https://blog.cyberdesserts.com/openclaw-malicious-skills-security/
- https://snyk.io/articles/top-claude-skills-cybersecurity-hacking-vulnerability-scanning/

### SpecWeave (Feb 21, 2026)
URL: https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/
- "When you install a skill, you are handing an AI agent instructions that it will follow implicitly."
- SpecWeave's two-tier approach achieved 100% detection against real malicious samples: pattern scanning (75% detection rate) + LLM-based semantic analysis
- ClawHub platform had 341+ malicious skills; 5 of top 7 most-downloaded were malware

---

## MARKETPLACES & DISTRIBUTION PLATFORMS

### skills.sh (Vercel)
URL: https://skills.sh/
- Launched January 20, 2026; 20,000 installs within 6 hours
- Security scanning integrated via Snyk partnership
- Tracked over 87,000 unique skills since launch
- Installation: `npx skills add <owner/repo>`
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — Guide
- https://github.com/vercel-labs/skills — Open source repo

### SkillsMP
URL: https://skillsmp.com/
- 66,500+ skills (community-run, NOT affiliated with Anthropic)
- Crawls GitHub for SKILL.md files with AI-powered semantic search
- No official CLI or automatic installer; download ZIP manually
- https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ — Review
- https://mcpmarket.com/server/skillsmp — MCP Market listing

### tonsofskills.com / ccpi
URL: https://tonsofskills.com (via github.com/jeremylongshore/claude-code-plugins-plus-skills)
- 423 plugins, 2,849 skills, 177 agents
- Install: `pnpm add -g @intentsolutionsio/ccpi`
- Commands: `ccpi search`, `ccpi install`

### VoltAgent/awesome-agent-skills
URL: https://github.com/VoltAgent/awesome-agent-skills
- 1000+ curated skills from official dev teams and community
- Compatible with Claude Code, Codex, Gemini CLI, Cursor, and more

### claudemarketplaces.com
URL: https://claudemarketplaces.com/
- Claude Code Plugins, Skills, MCP Servers directory

### agentpatch.ai
URL: https://agentpatch.ai/blog/mcp-marketplace-agentpatch/
- Browse catalog, pick tools, connect once; handles hosting, reliability, billing

### Agent Skills Library
URL: https://mcpservers.org/agent-skills

### MCPMarket daily skills rankings
URL: https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026

### KDNuggets: Top 5 Agent Skill Marketplaces
URL: https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents

---

## COMMUNITY & TOOLING

### GitHub Repos
- https://github.com/hesreallyhim/awesome-claude-code — Curated awesome-claude-code: skills, hooks, slash commands, agent orchestrators, plugins
- https://github.com/levnikolaevich/claude-code-skills — Plugin suite + bundled MCP servers; includes hex-line (hash-verified editing), hex-graph (code knowledge graph), hex-ssh (remote SSH) MCP servers
- https://github.com/xingkongliang/skills-manager — Desktop app to manage, sync, organize AI agent skills across 15+ coding tools
- https://github.com/ykdojo/claude-code-tips — 45 tips including dx plugin, cutting system prompt in half, using Gemini CLI as Claude Code minion

### Blog Articles (Technical)
- https://alexop.dev/posts/understanding-claude-code-full-stack/ — Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks Explained
- https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 — Claude Skills vs MCP Connectors vs Plugins comparison
- https://www.morphllm.com/claude-code-skills-mcp-plugins — Complete Guide 2026
- https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 — Best Claude Code Skills & Plugins (2026 Guide)
- https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained — Claude Code Plugins vs Skills explained
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers — Best Claude Code Plugins, Skills & MCP Servers
- https://buildtolaunch.substack.com/p/claude-code-mcp-vs-plugins-vs-skills — MCP vs Plugins vs Skills decision guide
- https://dev.to/_46ea277e677b888e0cd13/claude-code-vs-codex-2026-what-500-reddit-developers-really-think-31pb — Claude Code vs Codex 2026
- https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026 — "Agent Skills Are the New npm"
- https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution — AI Agent Marketplaces 2026

### Ensemble macOS App
URL: https://news.ycombinator.com/item?id=46922223
- Manages Claude Code Skills, MCPs, and Claude.md
- Built with Tauri 2 (Rust backend, React frontend), MIT license
- Bundling capabilities into workflow presets, one-click deployment, Finder integration

### Reddit community
- r/ClaudeCode: 4,200+ weekly contributors (vs 1,200 for r/Codex)
- 4x more discussion volume than Codex
- https://www.aitooldiscovery.com/guides/claude-code-reddit — Claude Code Reddit: What Developers Actually Use It For in 2026

---

## ADDITIONAL WEB SOURCES

- https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills — Anthropic Engineering
- https://anandbg.com/blog/claude-skills-comprehensive-guide-2026 — Comprehensive guide
- https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ — Complete guide
- https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ — .NET Skills integration
- https://deepwiki.com/microsoft/agent-skills/4-plugins — Microsoft agent-skills architecture
- https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026 — Popular AI Tools guide
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — 50+ Best MCP Servers for Claude Code
- https://www.termdock.com/en/blog/agent-skills-guide — Agent Skills Guide 2026

---

## DATA NOTES
- Reddit direct fetch blocked; community data sourced from third-party summaries
- YouTube video metadata unavailable via WebFetch (only footer returned); titles/dates from search results
- HN threads with high engagement (816 pts, 738 pts) date from October 2025 — before last 30 days window
- Most recent HN items on this topic had 1-2 points, suggesting community may have moved discussion to other channels
- gh skill CLI (April 16, 2026) is the most recent major development within the last 30 days
- ToxicSkills research is from February 2026 (~60 days ago), still actively being discussed
- Bluesky-specific discussions not found; search did not return Bluesky-specific threads
