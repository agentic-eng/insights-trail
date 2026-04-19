# Agent Skills & Plugin Ecosystems — Raw Research Output
**Date:** 2026-04-19
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## WEB SEARCH RESULTS

### Query 1: "Claude Code skills plugins extensions 2026"

**Links:**
- https://code.claude.com/docs/en/skills — Extend Claude with skills (official docs)
- https://github.com/quemsah/awesome-claude-plugins — Automated collection of Claude Code plugin adoption metrics
- https://github.com/ComposioHQ/awesome-claude-plugins — Curated list of plugins for Claude Code (custom commands, agents, hooks, MCP servers)
- https://claudemarketplaces.com/ — Claude Code Plugins marketplace directory
- https://self.md/guides/best-claude-code-plugins/ — Best Claude Code plugins 2026 guide
- https://composio.dev/content/top-claude-code-plugins — 10 top Claude Code plugins (Composio)
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 423 plugins, 2,849 skills, 177 agents; marketplace at tonsofskills.com with ccpi CLI
- https://github.com/anthropics/claude-code/blob/main/plugins/README.md — Official Anthropic Claude Code plugins README
- https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 — Top 10 Claude Code Skills, Plugins & CLIs for 2026
- https://www.firecrawl.dev/blog/best-claude-code-plugins — Top 10 Claude Code Plugins to Try in 2026 (Firecrawl)

**Key findings:**
- Claude Code plugins launched in public beta October 2025, now stable
- A plugin bundles multiple skills, MCP servers, or commands as one installable unit
- 4,200+ skills and 2,500+ marketplaces cited by claudemarketplaces.com
- Notable plugins: Claude-Mem (long-term memory), Superpowers (structured lifecycle planning), Local-Review (parallel local diff code reviews), Plannotator
- Universal SEO skill with 19 sub-skills, 12 subagents, 3 extensions cited as showcase example
- Types of extensions: Skills (auto-activating), Subagents (specialized AI agents), MCP Servers (external service connectors)

---

### Query 2: "MCP servers tools agent marketplace 2026"

**Links:**
- https://mcpmarket.com/ — Discover Top MCP Servers | MCP Market
- https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools — Using MCP Tools (Microsoft Learn)
- https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a — MCP Gateways in 2026 (ByteBridge/Medium)
- https://agentpatch.ai/blog/best-mcp-servers-2026/ — Best MCP Servers in 2026 (AgentPatch)
- https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 — Best MCP Servers for Sales Teams (Databar.ai)
- https://mcpservers.org/ — Awesome MCP Servers community list
- https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026 — Top 10 MCP Servers for Platform Engineers (StackGen)
- https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026 — Top MCP Servers list March 4 2026
- https://www.builder.io/blog/best-mcp-servers-2026 — Best MCP Servers for Developers 2026 (Builder.io)
- https://www.mcpbundles.com/blog/best-mcp-servers — Best MCP Servers 2026 Definitive List (MCPBundles)

**Key findings:**
- MCP Market is primary directory for MCP servers and clients
- MCPBundles maintains 10,000+ tools across 700+ providers for production SaaS integrations
- MCP Gateway pattern emerging: intermediary proxy sitting between AI agents and MCP servers providing centralized auth, authorization, auditing, traffic management
- Enterprise adoption from Microsoft, AWS, HashiCorp validating MCP as production-ready
- AgentPatch bundles common tools (web search, YouTube transcripts, image generation, Google Maps, email, news)

---

### Query 3: "Claude Code custom workflows reusable agent capabilities 2026"

**Links:**
- https://code.claude.com/docs/en/sub-agents — Create custom subagents (official docs)
- https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview — Agent Skills API docs
- https://github.com/wshobson/agents — Intelligent automation and multi-agent orchestration for Claude Code
- https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ — Claude Introduces Agent Skills for Custom AI Workflows (DevOps.com)
- https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md — Agent teams workflow guide
- https://github.com/hesreallyhim/awesome-claude-code — Curated list of skills, hooks, slash-commands, agent orchestrators, applications
- https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/ — Claude Code Workflows and Best Practices 2026
- https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns — 5 Claude Code Agentic Workflow Patterns (MindStudio)
- https://dev.to/onsen/claude-code-routines-automate-dev-workflows-4ijn — Claude Code Routines: Automate Dev Workflows
- https://www.chatprd.ai/how-i-ai/workflows/tool/claude — Claude AI Workflows guide

**Key findings:**
- Skills are reusable, filesystem-based resources providing domain-specific expertise
- Skills work across Claude web app, Claude Code, and API — build once, use everywhere
- Agent teams (new in 2026): multiple Claude instances working in parallel with git-based coordination
- Claude Code Routines: named, reusable instruction sets chaining multiple steps
- Workflow patterns: sequential, orchestrator, split-and-merge parallel
- Each subagent runs in its own context window with custom system prompt and specific tool access

---

### Query 4: "agent skill discovery distribution plugin ecosystem 2026"

**Links:**
- https://developers.openai.com/codex/skills — Agent Skills (OpenAI Codex)
- https://deepwiki.com/microsoft/agent-skills/4-plugins — Microsoft Agent Skills plugins (DeepWiki)
- https://github.com/VoltAgent/awesome-agent-skills — 1000+ agent skills compatible with Claude Code, Codex, Gemini CLI, Cursor, more
- https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ — Extend your coding agent with .NET Skills (Microsoft)
- https://skillsmp.com — Agent Skills Marketplace for Claude, Codex & ChatGPT Skills
- https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ — AI Agent Skills Complete Guide 2026 (Calmops)
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — Agent Skills Marketplace: Skills.sh Guide
- https://github.com/vercel-labs/skills — Open agent skills tool by Vercel Labs (npx skills)
- https://inference.sh/blog/skills/agent-skills-overview — Agent Skills: The Open Standard for AI Capabilities
- https://agentskills.io/home — AgentSkills.io home

**Key findings:**
- SKILL.md is the open standard — adopted by Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, GitHub Copilot
- skills.sh is primary distribution hub; lists compatibility with 10+ agent platforms
- "find-skills" by Vercel Labs: 579,000+ installs as of March 2026 (top skill by total installs)
- Plugin marketplace uses distributed registry pattern with multiple marketplace.json targets
- Snyk scanned 3,984 skills in February 2026: 13.4% contained critical-level security issues, 36% had prompt injection techniques
- Industry shift toward composable agents assembling abilities from portable skill packages

---

### Query 5: "MCP tool registry agent tools Claude Anthropic April 2026"

**Links:**
- https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/ — Anthropic brings MCP tool search to Claude Code (Tessl)
- https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ — AWS Weekly Roundup April 13, 2026 (AWS Blog)
- https://releasebot.io/updates/anthropic/claude-code — Claude Code Release Notes April 2026
- https://releasebot.io/updates/anthropic — Anthropic Release Notes April 2026
- https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ — Anthropic won't own MCP design flaw (The Register)
- https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/ — MCP Hits 97 Million Installs (Vucense)
- https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation — Anthropic donating MCP to AAIF
- https://github.com/agentic-community/mcp-gateway-registry — Enterprise-ready MCP Gateway & Registry

**Key findings:**
- MCP crossed 97 million installs March 25, 2026 — fastest adoption for any AI infrastructure standard
- Claude Code adds MCP tool search capability (April 2026)
- Claude Managed Agents launched public beta April 8, 2026 (composable API: sandboxing, state, permissions, orchestration)
- Claude Code April updates: /tui fullscreen rendering, mobile push notifications, better plugin/doctor workflows
- AWS Agent Registry launched preview April 9, 2026 — central repo for discovering/sharing/reusing AI agents, tools, MCP servers, skills
- MCP design flaw reported April 16: up to 200,000 servers at risk of RCE via STDIO transport; Anthropic declined to modify protocol architecture

---

### Query 6: "Claude Code plugin system SKILL.md open standard skills.sh 2026"

**Links:**
- https://code.claude.com/docs/en/skills — Official skills documentation
- https://github.com/levnikolaevich/claude-code-skills — Plugin suite + bundled MCP servers for Claude Code
- https://skillsmp.com — SkillsMP marketplace
- https://github.com/alirezarezvani/claude-skills — 232+ Claude Code skills & agent plugins for 8+ coding agents
- https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 — 10 Must-Have Skills for Claude (Medium/@unicodeveloper)
- https://www.firecrawl.dev/blog/best-claude-code-skills — Best Claude Code Skills to Try in 2026 (Firecrawl)
- https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview — Agent Skills API overview
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — tonsofskills.com / ccpi package manager
- https://github.com/anthropics/skills — Anthropic's official skills public repository
- https://self.md/guides/best-claude-code-plugins/ — self.md plugin guide

**Key findings:**
- Every skill needs SKILL.md with YAML frontmatter (trigger conditions) + markdown instructions
- Skills auto-activate based on conversation context (vs. slash commands requiring explicit trigger)
- Official Anthropic skills repo at github.com/anthropics/skills
- Cross-platform: SKILL.md works on Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, GitHub Copilot without modification
- skills.sh reference cited from February 2026

---

### Query 7: "Anthropic MCP 97 million installs protocol standard 2026"

**Links:**
- https://www.affiliatebooster.com/anthropic-mcp-protocol-97-million-installs/ — MCP Protocol Crosses 97 Million Installs (AffiliatBooster)
- https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/ — (repeated)
- https://www.arturmarkus.com/anthropics-model-context-protocol-hits-97-million-installs-on-march-25-mcp-transitions-from-experimental-to-foundation-layer-for-agentic-ai/ — MCP Transitions from Experimental to Foundation Layer
- https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ — (repeated)
- https://www.dotunopasina.com/datascience/the-standard-is-set-now-what-do-you-build — The Standard Is Set (Dotun Opasina)
- https://ainetizens.com/anthropic-mcp-model-context-protocol-explained-2026/ — MCP Explained 2026 (AINetizens)
- https://byteiota.com/model-context-protocol-hits-97m-installs-standard-wins/ — Model Context Protocol Hits 97M Installs (ByteIota)
- https://effloow.com/articles/mcp-ecosystem-growth-100-million-installs-2026 — MCP Ecosystem in 2026: From Experiment to 97 Million Installs (Effloow)
- https://www.computeleap.com/blog/chrome-built-in-mcp-server-native-mcp-v2-2026/ — Chrome's Built-In MCP Server (ComputeLeap)
- https://www.pento.ai/blog/a-year-of-mcp-2025-review — A Year of MCP: From Internal Experiment to Industry Standard (Pento)

**Key findings:**
- MCP crossed 97M installs March 25, 2026; described as fastest adoption for any AI infra standard
- 5,800+ community and enterprise MCP servers; 10,000+ active in production
- Every major AI provider (OpenAI, Google DeepMind, Microsoft, Meta) ships MCP-compatible tooling
- Chrome now has a built-in MCP server (native MCP v2)
- Pento's retrospective: "A Year of MCP" documents the trajectory from internal experiment to standard

---

### Query 8: "agent skills security audit snyk prompt injection 2026"

**Links:**
- https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ — ToxicSkills: Malicious AI Agent Skills (Snyk)
- https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ — Snyk and Vercel Securing Agent Skill Ecosystem
- https://owasp.org/www-project-agentic-skills-top-10/ — OWASP Agentic Skills Top 10
- https://github.com/snyk/agent-scan — Snyk agent-scan: Security scanner for AI agents, MCP servers, skills
- https://snyk.io/articles/skill-md-shell-access/ — From SKILL.md to Shell Access in Three Lines of Markdown (Snyk)
- https://labs.snyk.io/resources/agent-scan-skill-inspector/ — Introducing Agent Scan - Skill Inspector (Snyk Labs)
- https://snyk.io/blog/snyk-tessl-securing-agent-skills-registry/ — Snyk and Tessl Securing Agent Skills Registry
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — (repeated)
- https://skillsmp.com/skills/neversight-learn-skills-dev-data-skills-md-absolutelyskilled-absolutelyskilled-skill-audit-skill-md — skill-audit Agent Skill (SkillsMP)
- https://snyk.io/blog/introducing-agent-security/ — Introducing Agent Security (Snyk)

**Key findings:**
- Snyk ToxicSkills research (Feb 5, 2026): scanned 3,984 skills from ClawHub and skills.sh
- 13.4% of all skills (534 of 3,984) contain critical-level security issues
- 36% of skills contain prompt-injection techniques (1,467 malicious payloads found)
- 100% of confirmed malicious skills use malicious code + prompt injection combined
- Attack vector: 3 lines of SKILL.md markdown can instruct agent to exfiltrate SSH keys
- Snyk agent-scan uses LLM-based judges + deterministic rules (hybrid scanning)
- OWASP published Agentic Skills Top 10 list in response
- Snyk partnerships: with Vercel (securing registry) and Tessl (securing skills registry)

---

### Query 9: "Anthropic MCP design flaw 200K servers risk April 2026"

**Links:**
- https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ — The Register (primary report)
- https://forums.theregister.com/forum/all/2026/04/16/anthropic_mcp_design_flaw/ — The Register Forums discussion
- https://www.thehelper.net/threads/anthropic-wont-own-mcp-design-flaw-putting-200k-servers-at-risk.200905/ — TheHelper discussion thread
- https://www.computing.co.uk/news/2026/security/flaw-in-anthropic-s-mcp-putting-200k-servers-at-risk — Computing.co.uk report
- https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ — OX Security research: "The Mother of All AI Supply Chains"
- https://programming.dev/post/48949824 — programming.dev discussion
- https://www.cyberkendra.com/2026/04/anthropics-mcp-design-flaw-enables.html — CyberKendra: MCP Design Flaw Enables RCE
- https://www.techradar.com/pro/security/this-is-not-a-traditional-coding-error-experts-flag-potentially-critical-security-issues-at-the-heart-of-anthropics-mcp-exposes-150-million-downloads-and-thousands-of-servers-to-complete-takeover — TechRadar: "This is not a traditional coding error"
- https://asanify.com/blog/news/agentic-ai-enterprise-workforce-april-18-2026/ — AI News Digest April 18 (Asanify)

**Key findings:**
- OX Security identified "critical, systemic vulnerability" in MCP's STDIO transport mechanism
- Arbitrary Command Execution possible on any system running vulnerable MCP implementation
- Scope: ~150 million downloads, 7,000 publicly accessible servers, up to 200,000 vulnerable instances
- 10 high/critical CVEs issued for individual tools and agents using MCP
- Anthropic declined to modify protocol architecture, citing behavior as "expected"
- After initial report, Anthropic quietly released updated security policy saying STDIO adapters "should be used with caution"
- Researchers: "This change didn't fix anything"
- TechRadar: "This is not a traditional coding error"

---

### Query 10: "tonsofskills.com ccpi CLI package manager"

**Links:**
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — Primary repo (423 plugins, 2,849 skills, 177 agents)
- https://tonsofskills.com/ — Claude Code Skills Hub | Plugins & Agent Skills
- https://tonsofskills.com/compare-marketplaces/ — Claude Code Plugin Marketplaces Compared
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md — README
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/CONTRIBUTING.md — Contributing guide

**Key findings:**
- CCPI install: `pnpm add -g @intentsolutionsio/ccpi`
- Can also use `/plugin install pluginname@claude-code-plugins-plus` directly in Claude Code
- 100% free and open source (MIT license)
- CI pipeline validation for structure, metadata, and security on contributions
- Marketplace is searchable web UI with quality validation, structured metadata, dedicated plugin pages

---

### Query 11: "Anthropic donating MCP to Agentic AI Foundation"

**Links:**
- https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation — Official Anthropic announcement
- https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ — MCP Blog: MCP joins Agentic AI Foundation
- https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/ — The New Stack coverage
- https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/ — TechCrunch: Linux Foundation effort
- https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation — Linux Foundation announcement
- https://openai.com/index/agentic-ai-foundation/ — OpenAI co-founds AAIF
- https://erp.today/anthropic-set-to-donate-mcp-to-new-linux-foundation-agentic-ai-foundation/ — ERP Today
- https://www.solo.io/blog/aaif-announcement-agentgateway — Solo.io: AAIF and AgentGateway
- https://block.xyz/inside/block-anthropic-and-openai-launch-the-agentic-ai-foundation — Block announcement
- https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/ — GitHub Blog

**Key findings:**
- Agentic AI Foundation (AAIF) announced December 9, 2025 under Linux Foundation
- Founding projects: MCP (Anthropic), goose (Block), AGENTS.md (OpenAI)
- Co-founders: Anthropic, Block, OpenAI; supporters: Google, Microsoft, AWS, Cloudflare, Bloomberg
- MCP gets vendor-neutral governance; individual projects maintain technical autonomy
- GitHub Blog: "What this means for developers building the next era of AI tools and agents"

---

### Query 12: Hacker News discussions

**Links:**
- https://news.ycombinator.com/item?id=45607117 — "Claude Skills"
- https://news.ycombinator.com/item?id=45530150 — "Customize Claude Code with plugins"
- https://news.ycombinator.com/item?id=45619537 — "Claude Skills are awesome, maybe a bigger deal than MCP"
- https://news.ycombinator.com/item?id=43410866 — "Hacking Your Own AI Coding Assistant with Claude Pro and MCP"
- https://news.ycombinator.com/item?id=46396930 — "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands..."
- https://news.ycombinator.com/item?id=46983879 — "Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks)"
- https://news.ycombinator.com/item?id=44312363 — "Remote MCP Support in Claude Code"
- https://news.ycombinator.com/item?id=47602986 — "Show HN: Real-time dashboard for Claude Code agent teams"
- https://news.ycombinator.com/item?id=46692865 — "Agent Skills – Open Trusted Catalog of AI Agent Skills"
- https://news.ycombinator.com/item?id=47321892 — "Claude Code Skills and Plugins as an Open Source Project"
- https://news.ycombinator.com/item?id=47494890 — "How I'm Productive with Claude Code"
- https://news.ycombinator.com/item?id=46545620 — "How to code Claude Code in 200 lines of code"

**Key findings:**
- HN community discussion that "Claude Skills are awesome, maybe a bigger deal than MCP" went viral
- Agnix (Show HN): linting tool for AI agent configs (CLAUDE.md, skills, MCP, hooks)
- Discussion about Claude Code complexity: "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..."
- Agent Skills cataloging effort: Anthropic, OpenAI, GitHub, Vercel all publish skills in separate repos; project aggregating all into one JSON catalog
- Plugin system: `/plugin install`, `/plugin enable/disable`, `/plugin marketplace` commands noted
- Kebab-case naming convention required for skills; Claude Code silently ignores improperly named skills

---

### Query 13: AWS Agent Registry (April 2026)

**Links:**
- https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ — AWS Blog roundup
- https://techbriefly.com/2026/04/14/aws-launches-agent-registry-to-manage-enterprise-ai-agents/ — TechBriefly coverage
- https://www.theregister.com/2026/04/09/aws_ai_agent_registry — The Register: "Agents shouldn't be secret, so we built a registry"
- https://www.thenasguy.com/2026/04/13/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ — The NAS Guy roundup
- https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/ — AWS ML Blog: "The future of managing agents at scale"
- https://www.hawkdive.com/aws-weekly-update-claude-mythos-in-bedrock-agent-registry-launch-and-more/ — Hawkdive roundup
- https://dataconomy.com/2026/04/14/aws-launches-agent-registry-to-centralize-ai-agent-governance/ — Dataconomy: "Centralize AI Agent Governance"
- https://noise.getoto.net/2026/04/13/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ — Noise roundup
- https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ — InfoQ: "AWS Launches Agent Registry in Preview to Govern AI Agent Sprawl"

**Key findings:**
- AWS Agent Registry (preview) announced early April 2026 as part of Bedrock AgentCore
- Single place to discover, share, and reuse AI agents, tools, and agent skills across enterprise
- Available across 5 compute regions
- Stores metadata for agents, tools, MCP servers, agent skills, associated resources
- Hybrid search (keyword + semantic) for discovery
- Queryable via AgentCore Console, APIs, or MCP-compatible clients (Kiro, Claude Code)
- The Register headline: "Agents shouldn't be secret, so we built a registry"

---

### Query 14: Community Discussions / Reddit

**Links:**
- https://www.infoq.com/news/2026/04/claude-code-linux-vulnerability/ — InfoQ: Claude Code Found Remotely Exploitable Linux Kernel Vulnerability
- https://alex000kim.com/posts/2026-03-31-claude-code-source-leak/ — Alex Kim's blog: Claude Code Source Leak
- https://www.aitooldiscovery.com/guides/claude-code-reddit — Claude Code Reddit guide
- https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74 — DEV.to: Claude Code hits #1 on HN
- https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html — Hacker News: Source code leak via npm
- https://github.com/mvanhorn/last30days-skill — last30days agent skill (GitHub)
- https://dev.to/varshithvhegde/the-great-claude-code-leak-of-2026-accident-incompetence-or-the-best-pr-stunt-in-ai-history-3igm — DEV.to: Great Claude Code Leak of 2026
- https://news.ycombinator.com/item?id=47494890 — HN: How I'm Productive with Claude Code
- https://hn.matthewblode.com/item/43307809 — HN mirror: I've been using Claude Code for a couple of days

**Key findings:**
- r/ClaudeCode: 4,200+ weekly contributors (vs. r/Codex: 1,200)
- March 31, 2026: Anthropic accidentally shipped Claude Code source code to public npm — 512,000 lines, 1,906 TypeScript files
- Leaked code revealed unreleased KAIROS autonomous agent mode with "/dream skill for nightly memory distillation"
- Claude Code used to find remotely exploitable heap buffer overflow in Linux kernel NFS driver (23 years undiscovered)
- Claude Code hit #1 on HN; community sentiment: "becoming the default way a new generation of builders creates software"

---

### Query 15: YouTube Videos

**Links:**
- https://www.youtube.com/watch?v=LlFgLsffbBs — "The ONLY Claude Code Tutorial You'll Ever Need in 2026"
- https://www.youtube.com/watch?v=uogzSxOw4LU — "The Ultimate Claude Code Guide | MCP, Skills & More"
- https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY — Claude Code Tutorial playlist
- https://composio.dev/toolkits/youtube/framework/claude-code — Youtube MCP Integration with Claude Code
- https://www.youtube.com/watch?v=qYqIhX9hTQk — "FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step)"
- https://www.youtube.com/watch?v=IsJh8IGtErI — "The Simple Guide to Claude Code: MCP vs. Skills vs. Sub-Agents"
- https://www.youtube.com/watch?v=Lxznc91wlTk — "Claude MCP Tutorial: Give Claude Superpowers in 30 Seconds"
- https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k — DEV.to: Claude Code Skills vs MCP Servers

**Key findings:**
- Multiple tutorial videos explaining the Claude Code extension system in 2026
- Primary confusion point for developers: MCP vs Skills vs Sub-Agents vs Plugins
- "The Simple Guide to Claude Code: MCP vs. Skills vs. Sub-Agents" (5 days ago at time of search)
- "The Ultimate Claude Code Guide | MCP, Skills & More" (6 days ago)
- High tutorial demand suggests ecosystem rapidly expanding but with complexity/learning curve

---

## SUMMARY STATISTICS (Web-derived)

- MCP installs: 97 million (March 25, 2026)
- Active MCP servers: 10,000+ in production; 5,800+ community/enterprise
- tonsofskills.com: 423 plugins, 2,849 skills, 177 agents
- VoltAgent/awesome-agent-skills: 1,000+ skills across platforms
- alirezarezvani/claude-skills: 232+ skills for 8+ coding agents
- Snyk audit scope: 3,984 skills scanned
- Critical security issues found: 13.4% of all skills
- Prompt injection found: 36% of skills
- MCP flaw exposure: up to 200,000 servers, ~150 million downloads
- find-skills (Vercel Labs): 579,000+ installs
- r/ClaudeCode: 4,200+ weekly contributors
- AWS Agent Registry: available in 5 compute regions
