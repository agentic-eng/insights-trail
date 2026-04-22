# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-22
**Query type:** GENERAL
**Sources:** Reddit, Hacker News, YouTube, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | ~15 threads (aggregated) | 4,200+ weekly contributors on r/ClaudeCode | Via morphllm.com/claude-code-reddit aggregation; no direct thread URLs indexed |
| Hacker News | 11 stories | Not quantified | Mix of Show HN projects, Ask HN management, official announcements |
| YouTube | 2 videos | Not quantified | 1 April 2026 skills/plugins roundup + 1 beginners tutorial |
| Web | 60+ pages | — | Blogs, official docs, news, GitHub repos, marketplace directories |

---

## Synthesized Findings

### 1. The Plugin/Skill Architecture: Three-Layer Model Now Dominant

The Claude Code extension ecosystem has converged on a three-layer model that the community uses consistently to explain the landscape:

- **Skills** — procedural knowledge encoded in Markdown + YAML metadata + optional scripts. 30–50 tokens each, loaded on-demand. "They feel a lot closer to the spirit of LLMs—throw in some text and let the model figure it out." ([Simon Willison](https://simonwillison.net/2025/Oct/16/claude-skills/))
- **MCP Servers** — the "plumbing" connecting Claude to external tools, APIs, databases. Can use 50k+ tokens; access to GitHub, filesystems, dev tools, project management systems.
- **Plugins** — installable bundles that package Skills + MCP Connectors + slash commands + sub-agents into a single distributable unit. "If Skills are individual recipe cards and MCP is the kitchen plumbing, a Plugin is the full kitchen, stocked and ready to cook." ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

This architecture was formalized when Anthropic shipped plugins on **January 30, 2026**, and the official Plugin Marketplace launched in **February 2026**. The official marketplace reached 101 plugins by March 2026. Anthropic's [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) repo splits into `/plugins` (Anthropic-built) and `/external_plugins` (vetted third-party: Supabase, Firebase, Discord, Telegram, and LSP-based Code Intelligence Plugins for 12 languages).

Official documentation:
- [Extend Claude with skills](https://code.claude.com/docs/en/skills)
- [Discover and install prebuilt plugins](https://code.claude.com/docs/en/discover-plugins)
- [Agent Skills overview (API Docs)](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [anthropics/skills repo](https://github.com/anthropics/skills)
- [anthropics/claude-code plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md)

Discussed on: Reddit (r/ClaudeCode), HN ([item?id=45607117](https://news.ycombinator.com/item?id=45607117)), Web extensively.

---

### 2. GitHub's `gh skill` Command: The Cross-Agent Standard Moment

On **April 16, 2026**, GitHub shipped `gh skill` in public preview (requires CLI v2.90.0+), establishing a unified CLI for discovering, installing, managing, and publishing agent skills across all major AI coding agents. ([GitHub Changelog](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/))

The command works across GitHub Copilot, Claude Code, Cursor, Codex, and Gemini CLI — all using the open **Agent Skills specification** with the SKILL.md format. This format originated at Anthropic and was released as an open standard, subsequently adopted by OpenAI, Microsoft, and the broader ecosystem.

Key capabilities:
- `gh skill install <repo>/<skill> --agent claude-code --scope user`
- `gh skill preview <skill>` — inspect before installing (security recommendation)
- `--pin` flag — lock to specific tag or commit SHA for reproducible environments
- Issue [#13215](https://github.com/cli/cli/issues/13215): active discussion making `gh skill` automation-ready for agent session lifecycle integration
- Issue [#13208](https://github.com/cli/cli/issues/13208): adding opencode as a supported agent

Security caveat from GitHub: "Skills are not verified by GitHub and may contain prompt injections, hidden instructions, or malicious scripts." ([CLI manual](https://cli.github.com/manual/gh_skill))

Analysis:
- [Groundy: gh skill — One Standard to Rule Claude Code, Copilot, Cursor, and Gemini](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor/)
- [azukiazusa.dev: You Can Now Distribute Agent Skills with the gh Command](https://azukiazusa.dev/en/blog/gh-agent-skill-management/)
- [VS Code Agent Skills docs](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) — 1,000+ cross-agent skills

Discussed on: HN (multiple threads), Web.

---

### 3. The Marketplace Explosion — Scale and Fragmentation

The agent skills marketplace landscape has exploded to extraordinary scale, with significant fragmentation:

| Platform | Scale | Notes |
|----------|-------|-------|
| [Skills.sh](https://skills.sh/) | 90,000+ skills | Vercel's official directory; launched Jan 20, 2026; leaderboard shows actual install counts; supports 19 AI agents |
| SkillsMP | ~30,000 entries | Mixes skills, agents, prompts, MCP servers |
| [ClawHub](https://clawhub.ai/) | ~5,400+ tracked | OpenClaw marketplace; hit by malware campaign Jan 2026 |
| [SkillHub](https://www.skillhub.club) | ~7,000 skills | Most developer-curated per community consensus |
| [tonsofskills.com](https://tonsofskills.com/) | 2,849 skills + 423 plugins + 177 agents | Open-source; ccpi CLI package manager; GitHub: [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) |
| [claudemarketplaces.com](https://claudemarketplaces.com/) | 150+ skills | Community-curated, ratings + install counts |
| [Smithery](https://smithery.ai/) | 2,000–7,000 MCP servers | "Docker Hub for MCP"; [smithery-ai/cli](https://github.com/smithery-ai/cli) |
| Anthropic official | 101 plugins | [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) |
| [LobeHub](https://lobehub.com/skills) | Not quantified | Multi-agent: Claude, Codex, ChatGPT |

Total across Skills.sh, SkillsMP, ClawHub: **490,000+ skills** as of March 2026. 105,000+ developers visit Claude Code marketplaces monthly.

Community analysis noting fragmentation and recommendation differences:
- [Claude Skills Marketplace Comparison 2026: 6 Platforms Side-by-Side](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison)
- [KDnuggets: Top 5 Agent Skill Marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)
- [buildtolaunch Substack: Best Claude Code Plugins (2026): 10 Tested, 4 Worth Keeping](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review)
- [Scott Spence: Organising Claude Code Skills Into Plugin Marketplaces](https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces)
- [TurboDocx: Best Claude Code Plugins, Skills & MCP Servers (2026)](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers)
- [virtualuncle: Agent Skills Marketplace: Skills.sh Guide (2026)](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)

Discussed on: Reddit (r/ClaudeCode), HN, Web.

---

### 4. Enterprise Registry Infrastructure: AWS, Kong, ToolHive

April 2026 saw major enterprise-grade registry infrastructure announcements:

**AWS Agent Registry** (preview, ~April 9–13, 2026):
Available through Amazon Bedrock AgentCore — a private, governed catalog and discovery layer for agents, tools, skills, and MCP servers within an organization. ([AWS announcement](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/))
- Hybrid search: keyword + semantic matching (search "payment processing" → surfaces "billing" or "invoicing" tagged tools)
- Access via: Console UI, APIs (AWS CLI/SDK), or as an MCP server from IDE
- Approval workflow before resources become discoverable
- Available in 5 regions (Oregon, Tokyo, Sydney, Ireland, N. Virginia)
- Roadmap: auto-indexing on deploy, cross-registry federation
- The Register headline: "AWS: Agents shouldn't be secret, so we built a registry" ([theregister.com](https://www.theregister.com/2026/04/09/aws_ai_agent_registry))
- [InfoQ coverage](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | [AWS ML Blog](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/) | [AWS Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html)

**ToolHive / Stacklok** (April 6, 2026): Added agent skills support across CLI and Registry Server ([docs.stacklok.com](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates))
- Full lifecycle: create → publish → install across supported AI clients
- Install from ToolHive Registry Server, OCI registries, or Git repos
- Registry server is open-source, implements official MCP Registry API spec, multi-tenant auth + audit logging
- [toolhive-registry-server](https://github.com/stacklok/toolhive-registry-server)

**Kong MCP Registry**: In Kong Konnect — dynamic, programmatic tool discovery moving from rigid configs to flexible API-driven approach. ([konghq.com/products/mcp-registry](https://konghq.com/products/mcp-registry)) | [Engineering blog](https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery)

**Official MCP Registry**: [registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io) — primary source of truth for publicly available MCP servers. ([MCP blog announcement Sep 2025](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/))

**Community enterprise registry**: [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) — enterprise-ready with OAuth, dynamic tool discovery, Keycloak/Entra integration.

**InfoWorld**: [How to build an enterprise-grade MCP registry](https://www.infoworld.com/article/4145014/how-to-build-an-enterprise-grade-mcp-registry.html)
**TrueFoundry**: [Best MCP Registries in 2026: Compared for Developers and Enterprises](https://www.truefoundry.com/blog/best-mcp-registries)
**MACH Alliance**: [MACH Alliance MCP Registry](https://machalliance.org/mach-alliance-mcp-registry)

Discussed on: HN, Web.

---

### 5. Security Crisis: ToxicSkills, ClawHub Breach, OWASP Response

The most alarming development in the last 30 days (anchored in February 2026 but rippling through April) is the security crisis in agent skills supply chains:

**Snyk ToxicSkills Study** (published Feb 5, 2026 — [snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)):
- Scanned 3,984 skills from ClawHub and skills.sh
- **36.82% (1,467 skills)** carry security issues of any severity
- **13.4% (534 skills)** contain at least one critical-level flaw
- 76 malicious payloads confirmed via manual review: credential theft, backdoor installation, data exfiltration
- 91% of confirmed malicious skills combine prompt injection + traditional malware techniques
- Attack categories: password-protected ZIPs with obfuscated install scripts, base64-encoded commands exfiltrating AWS credentials, instructions disabling agent safety mechanisms
- "Lethal Trifecta": skills are especially dangerous when simultaneously having (1) access to private data (SSH keys, API credentials), (2) exposure to untrusted content, and (3) ability to communicate externally

**ClawHub Malware Campaign** (late January 2026):
- 335 malicious skills sharing a single command-and-control IP
- 5 of the top 7 most-downloaded skills at peak infection were confirmed malware
- Entry barrier: SKILL.md + a GitHub account one week old, no code signing, no security review, no sandbox
- Coverage: [cybersecuritywaala.com: 71 Malicious Claude Skills Found](https://cybersecuritywaala.com/blog/71-malicious-claude-skills-found/) | [aicerts.ai](https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/) | [skillshield.dev](https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/) | [specweave blog](https://github.com/anton-abyzov/specweave/blob/develop/docs-site/blog/2026-02-21-toxicskills-why-your-ai-agent-skills-need-verification.md)

**Community/Industry Response:**
- [OWASP Agentic Skills Top 10 (AST10)](https://owasp.org/www-project-agentic-skills-top-10/) — new OWASP project specifically for skills supply chain threats; [GitHub repo](https://github.com/OWASP/www-project-agentic-skills-top-10)
- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — 100+ expert contributors
- [Microsoft Agent Governance Toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/) (April 2, 2026) — open-source runtime security
- [skillcop PoC](https://github.com/cfitzgerald-pd/skillcop) — proof of concept protecting Claude Code against malicious skills
- GitHub CLI's `gh skill preview` recommendation before any install
- Palo Alto Networks: [OWASP Agentic AI Security](https://www.paloaltonetworks.com/blog/cloud-security/owasp-agentic-ai-security/)
- [aikido.dev: OWASP Top 10 Agentic Applications full guide](https://www.aikido.dev/blog/owasp-top-10-agentic-applications)

Discussed on: Web (major security publications, GitHub), HN.

---

### 6. Remote MCP and Cross-Tool Connectivity

Remote MCP support for Claude Code was announced November 3, 2025 ([Anthropic blog](https://claude.com/blog/claude-code-remote-mcp)), with continued community discussion and tooling building through April 2026:

- Native OAuth support — authenticate once, credentials handled automatically, no API keys to manage
- Vendors handle updates, scaling, availability — "just add the vendor's URL to Claude Code"
- Claude Code accesses both tools and resources from MCP servers
- HN thread [item?id=44312363](https://news.ycombinator.com/item?id=44312363) — "Remote MCP Support in Claude Code"

Community tooling built around MCP management:
- [HN: Show HN: Agents – Sync MCP Configs Across Claude, Cursor, Codex Automatically](https://news.ycombinator.com/item?id=46926648)
- [HN: Ask HN: How do you manage multiple MCP servers in Claude Code?](https://news.ycombinator.com/item?id=45114196) — managing 40+ tool thresholds
- [HN: Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex](https://news.ycombinator.com/item?id=45374908)
- [HN: Show HN: UI and MCP server for analyzing Claude Code history](https://news.ycombinator.com/item?id=46500801)
- [HN: 24 Simultaneous Claude Code agents on local hardware](https://news.ycombinator.com/item?id=47099597)
- [HN: Show HN: Browser MCP – Automate your browser using Cursor, Claude, VS Code](https://news.ycombinator.com/item?id=43613194)
- [HN: Show HN: Seite static site generator with MCP server and Claude Code integration](https://news.ycombinator.com/item?id=47151427)

Further reading:
- [The New Stack: Claude Code Gets Remote MCP Support](https://thenewstack.io/anthropics-claude-code-gets-support-for-remote-mcp-servers/)
- [Remote MCP servers docs](https://platform.claude.com/docs/en/agents-and-tools/remote-mcp-servers)
- [InfoQ: Claude Code Gains Remote MCP Support](https://www.infoq.com/news/2025/06/anthropic-claude-remote-mcp/)
- [support.claude.com: Custom connectors with remote MCP](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)

Discussed on: HN, Web.

---

### 7. Developer Sentiment and Usage Patterns

Community sentiment on r/ClaudeCode (4,200+ weekly contributors — triple r/Codex's 1,200) is directionally positive with nuance. Source: [morphllm.com/claude-code-reddit](https://www.morphllm.com/claude-code-reddit).

**Praised:**
- 67% blind test win rate; 77.2% SWE-bench score
- Multi-file refactoring capabilities
- MCP ecosystem breadth
- Skills for project-specific workflows (SEO audit, deployment checklists)

**Complaints:**
- Usage limits on Pro plan
- Context window consumption from MCP servers (40-tool threshold frequently hit)
- Performance degradation in long sessions

**Usage patterns from community:**
- Most developers need: 2–3 MCP servers (GitHub, Filesystem, one domain-specific) + a few custom Skills
- Custom skills show bigger ROI than generic ones
- "Developers who invest time learning Claude Code's patterns (CLAUDE.md, subagents, hooks, slash commands) report significant productivity gains, while developers who treat it like autocomplete get frustrated and leave."
- MCP is "the killer feature for developers building custom workflows"

Community guides and discussions:
- [morphllm.com: Claude Code Extensions: MCP, Skills, Agents & Hooks Guide 2026](https://www.morphllm.com/claude-code-extensions)
- [DEV Community: Claude Code Skills vs MCP Servers — What to Use, How to Install](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k)
- [devtoolpicks.com: Claude Skills vs MCP Connectors vs Plugins](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)
- [DEV Community: Best Claude Code Skills & Plugins 2026 Guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4)
- [agensi.io: Claude Code Plugins vs Skills — What's the Difference?](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained)
- [Medium: Agent Skills: The Cheat Codes for Claude Code](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) (Jonathan Fulton, April 2026)
- [Medium: 10 Must-Have Skills for Claude (and Any Coding Agent) in 2026](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) (March 2026)
- [Composio: Top 10 Claude Code Skills Every Builder Should Know](https://composio.dev/content/top-claude-skills)
- [alexop.dev: Understanding Claude Code's Full Stack](https://alexop.dev/posts/understanding-claude-code-full-stack/)
- [Muneeb Ahmad (Medium): Claude Code Extensions Explained: Skills, MCP, Hooks, Subagents, Agent Teams & Plugins](https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff)
- [MindStudio: Claude Code Skills vs Plugins — Which Should You Build?](https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference)
- [Claude Code vs Codex 2026 — 500+ Reddit Developers](https://dev.to/_46ea277e677b888e0cd13/claude-code-vs-codex-2026-what-500-reddit-developers-really-think-31pb)

Discussed on: Reddit (r/ClaudeCode), Web.

---

### 8. Simon Willison's Seminal Analysis (October 2025 — Still Widely Referenced)

Simon Willison's [October 16, 2025 post](https://simonwillison.net/2025/Oct/16/claude-skills/) — "Claude Skills are awesome, maybe a bigger deal than MCP" — continues to be the most widely cited technical framing of the skills landscape. Key arguments:

- Skills are superior to MCP in philosophical alignment with LLMs: "They feel a lot closer to the spirit of LLMs—throw in some text and let the model figure it out."
- MCP is "a whole protocol specification, covering hosts, clients, servers, resources, prompts, tools, sampling, roots, elicitation and three different transports." Skills are just Markdown.
- "Claude Code is, with hindsight, poorly named. It's not purely a coding tool: it's a tool for general computer automation. Anything you can achieve by typing commands into a computer is something that can now be automated by Claude Code."
- 2025 was genuinely the year of agents — "tools in a loop" as the working definition.

HN discussion of the original post: [item?id=45607117](https://news.ycombinator.com/item?id=45607117)
Technical comparison: [IntuitionLabs: Claude Skills vs. MCP](https://intuitionlabs.ai/articles/claude-skills-vs-mcp)

---

### 9. Community GitHub Repositories and Discovery Tools

Active open-source curation and tooling:
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) — 1,000+ cross-agent skills (Claude Code, Codex, Gemini CLI, Cursor)
- [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) — 5,400+ OpenClaw skills, filtered and categorized
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) — curated list of Claude Skills
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) — 232+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8 more agents
- [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) — 423 plugins, 2,849 skills, 177 agents; ccpi CLI package manager at [tonsofskills.com](https://tonsofskills.com/)
- [quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) — automated collection of Claude Code plugin adoption metrics via n8n workflows
- [github/awesome-copilot/skills](https://github.com/github/awesome-copilot/blob/main/docs/README.skills.md) — GitHub's curated cross-agent skills list
- [agentskills GitHub org](https://github.com/agentskills) — umbrella org for Agent Skills specification

Other discovery resources:
- [claudecodeplugins.io](https://claudecodeplugins.io/) — Claude Code Skills Hub
- [aitmpl.com](https://www.aitmpl.com/) — 1,000+ Agents, Commands, Skills & MCP Integrations
- [awesomeclaude.ai](https://awesomeclaude.ai) — Claude AI Resources Directory
- [scriptbyai.com/claude-code-resource-list](https://www.scriptbyai.com/claude-code-resource-list/) — Ultimate Claude Code Resource List 2026
- [mejba.me: Top 10 Claude Code Skills, Plugins & CLIs for 2026](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026)
- [openaitoolshub.org: Skills vs Plugins](https://www.openaitoolshub.org/en/blog/claude-code-skills-vs-plugins)
- [agensi.io: Plugin Marketplace Guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide)
- [systemprompt.io: Getting Started with Anthropic Marketplace](https://systemprompt.io/guides/getting-started-anthropic-marketplace)
- [groundy.com: Anthropic's Official Plugin Ecosystem Explained](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/)
- [termdock.com: Agent Skills Guide 2026](https://www.termdock.com/en/blog/agent-skills-guide)
- [aitooldiscovery.com: Claude Code Reddit](https://www.aitooldiscovery.com/guides/claude-code-reddit)
- [releasebot.io: Claude Code April 2026 Release Notes](https://releasebot.io/updates/anthropic/claude-code)

---

## Cross-Source Patterns

### Pattern 1: Security-as-an-Afterthought Is Now a Crisis
**Platforms:** Web (Snyk, OWASP, cybersecurity pubs), HN, Reddit

The skills ecosystem grew faster than trust infrastructure. Low publishing barriers (just a SKILL.md + week-old GitHub account), no code signing, no sandboxing. The ClawHub breach and ToxicSkills study both landed in January–February 2026, and the community response (OWASP AST10, Microsoft Agent Governance Toolkit, `gh skill preview`) shows this became a genuine concern — not a theoretical one.

Key quotes:
> "The barrier to publishing a new agent skill on ClawHub is a SKILL.md Markdown file and a GitHub account that's one week old, with no code signing, no security review, and no sandbox by default." — Snyk ToxicSkills report ([snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "91% of confirmed malicious skills combine prompt injection with traditional malware techniques." — Snyk ToxicSkills ([snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

### Pattern 2: Cross-Agent Portability Is Winning
**Platforms:** HN, Web (GitHub blog, multiple analysis posts), Reddit

The SKILL.md format originated at Anthropic but is now an open standard. `gh skill` supports Claude Code, Copilot, Cursor, Codex, and Gemini CLI in one command. Skills.sh supports 19 agents. The community is converging on agent-agnostic distribution.

Key quote:
> "Agent skills are portable sets of instructions, scripts, and resources that teach AI agents how to perform specific tasks. They follow the open Agent Skills specification, and work across multiple agent hosts." — GitHub CLI changelog ([github.blog](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/))

### Pattern 3: Enterprise Registry Infrastructure Is Finally Catching Up
**Platforms:** Web (AWS, Kong, ToolHive, InfoQ), HN

April 2026 was notable for enterprise-grade registry infrastructure arriving in preview: AWS Agent Registry, Kong MCP Registry, ToolHive's skills lifecycle management, and the open official MCP Registry. The "agent sprawl" problem — organizations not knowing what agents/tools they have — is now being actively solved.

Key quote:
> "AWS: Agents shouldn't be secret, so we built a registry" — The Register ([theregister.com](https://www.theregister.com/2026/04/09/aws_ai_agent_registry))

### Pattern 4: Skills > MCP for Developer Ergonomics; MCP Wins for Power
**Platforms:** Reddit, HN, Web (Simon Willison, morphllm, agensi, devtoolpicks)

Consistent across sources: skills are easier to write and reason about, MCP is more powerful for external connectivity. Most developers use 2–3 MCP servers + a handful of custom skills. Heavy MCP usage (40+ tools) creates context window and performance issues.

Key quote:
> "Skills are Markdown with a tiny bit of YAML metadata and some optional scripts...They feel a lot closer to the spirit of LLMs—throw in some text and let the model figure it out." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

### Pattern 5: Ecosystem Scale Is Outrunning Discoverability
**Platforms:** Web, Reddit, HN

490,000+ skills across three platforms, with 6 different marketplaces serving different audiences (developer-curated vs raw volume vs security-focused). The community is actively building comparison guides. Skills.sh's install-count leaderboard is emerging as a trust signal.

---

## Per-Platform Tables

### Hacker News

| Story | Title | URL | Notes |
|-------|-------|-----|-------|
| Remote MCP Support in Claude Code | Remote MCP Support in Claude Code | [HN](https://news.ycombinator.com/item?id=44312363) | Official announcement thread |
| Claude Skills | Claude Skills (Simon Willison) | [HN](https://news.ycombinator.com/item?id=45607117) | Major discussion on Skills vs MCP |
| Ask HN: MCP management | Ask HN: How do you manage multiple MCP servers in Claude Code? | [HN](https://news.ycombinator.com/item?id=45114196) | 40-tool threshold problem |
| Show HN: Agents sync | Show HN: Agents – Sync MCP Configs Across Claude, Cursor, Codex Automatically | [HN](https://news.ycombinator.com/item?id=46926648) | MCP config management tooling |
| Show HN: Browser MCP | Show HN: Browser MCP – Automate your browser using Cursor, Claude, VS Code | [HN](https://news.ycombinator.com/item?id=43613194) | Browser automation via MCP |
| Show HN: Codemcp | Show HN: Codemcp – Claude Code for Claude Pro subscribers – ditch API bills | [HN](https://news.ycombinator.com/item?id=43356016) | Pro plan workaround |
| Show HN: Roundtable MCP | Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex | [HN](https://news.ycombinator.com/item?id=45374908) | Multi-agent orchestration via MCP |
| Show HN: MCP history UI | Show HN: UI and MCP server for analyzing Claude Code history. No more lost ideas | [HN](https://news.ycombinator.com/item?id=46500801) | Session history + search |
| 24 simultaneous agents | 24 Simultaneous Claude Code agents on local hardware | [HN](https://news.ycombinator.com/item?id=47099597) | Multi-agent local deployment |
| Hacking AI assistant | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | [HN](https://news.ycombinator.com/item?id=43410866) | MCP DIY exploration |
| Show HN: Seite | Show HN: Seite static site generator with MCP server and Claude Code integration | [HN](https://news.ycombinator.com/item?id=47151427) | MCP-enabled static site generator |

---

### YouTube

| Channel | Title | URL | Notes |
|---------|-------|-----|-------|
| Not specified | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | [YouTube](https://www.youtube.com/watch?v=KjEFy5wjFQg) | April 2026, current ecosystem roundup |
| Not specified | Claude Code Tutorial for Beginners | [YouTube](https://www.youtube.com/watch?v=kwE-uSEakYU) | Covers CLAUDE.md, skills, agent usage |

---

### Web (Selected Key Sources)

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Simon Willison (blog) | [simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/) | Seminal "Skills > MCP" framing; still most-cited analysis |
| Snyk (ToxicSkills) | [snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | 36.82% skills have security issues; 534 critical; 76 malicious payloads |
| GitHub Changelog | [github.blog](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) | `gh skill` launched April 16, 2026; cross-agent standard |
| Anthropic blog | [claude.com/blog](https://claude.com/blog/claude-code-remote-mcp) | Remote MCP support announcement |
| Anthropic docs: skills | [code.claude.com](https://code.claude.com/docs/en/skills) | Official skills documentation |
| Anthropic docs: plugins | [code.claude.com](https://code.claude.com/docs/en/discover-plugins) | Official plugin marketplace docs |
| anthropics/claude-plugins-official | [GitHub](https://github.com/anthropics/claude-plugins-official) | Official Anthropic-managed plugin directory |
| anthropics/skills | [GitHub](https://github.com/anthropics/skills) | Public Agent Skills repository |
| AWS (Agent Registry) | [aws.amazon.com](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | Enterprise agent/tool/skill registry in preview |
| The Register | [theregister.com](https://www.theregister.com/2026/04/09/aws_ai_agent_registry) | "Agents shouldn't be secret" — AWS registry framing |
| ToolHive / Stacklok | [docs.stacklok.com](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) | Skills lifecycle management added April 6, 2026 |
| Kong (MCP Registry) | [konghq.com](https://konghq.com/products/mcp-registry) | Dynamic enterprise tool discovery |
| OWASP AST10 | [owasp.org](https://owasp.org/www-project-agentic-skills-top-10/) | New skills-specific security project |
| OWASP Top 10 Agentic | [genai.owasp.org](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) | Top 10 for Agentic Applications 2026 |
| Microsoft OSS Blog | [opensource.microsoft.com](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/) | Agent Governance Toolkit, April 2, 2026 |
| morphllm.com | [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Comprehensive Skills vs MCP vs Plugins guide |
| morphllm.com (Reddit) | [morphllm.com](https://www.morphllm.com/claude-code-reddit) | Aggregated Reddit developer sentiment |
| ClawHub | [clawhub.ai](https://clawhub.ai/) | OpenClaw skills marketplace; security incident Jan 2026 |
| Skills.sh | [skills.sh](https://skills.sh/) | 90,000+ skills; Vercel-launched Jan 20, 2026; install-count leaderboard |
| Smithery | [smithery.ai](https://smithery.ai/) | 2,000–7,000 MCP servers; Docker Hub analogue |
| tonsofskills.com | [tonsofskills.com](https://tonsofskills.com/) | 2,849 skills + 423 plugins + 177 agents; ccpi CLI |
| claudemarketplaces.com | [claudemarketplaces.com](https://claudemarketplaces.com/) | Community-curated directory with ratings |
| SkillHub | [skillhub.club](https://www.skillhub.club) | 7,000 skills; most developer-curated |
| Groundy (gh skill) | [groundy.com](https://groundy.com/articles/github-clis-gh-skill-command-one-standard-to-rule-claude-code-copilot-cursor/) | gh skill = one standard for all agents |
| InfoQ (AWS registry) | [infoq.com](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | AWS registry launch analysis |
| InfoQ (remote MCP) | [infoq.com](https://www.infoq.com/news/2025/06/anthropic-claude-remote-mcp/) | Remote MCP technical explainer |
| The New Stack | [thenewstack.io](https://thenewstack.io/anthropics-claude-code-gets-support-for-remote-mcp-servers/) | Remote MCP news coverage |
| cybersecuritywaala | [cybersecuritywaala.com](https://cybersecuritywaala.com/blog/71-malicious-claude-skills-found/) | 71 Malicious Claude Skills Found |
| skillshield.dev | [skillshield.dev](https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/) | ToxicSkills implications for OpenClaw users |
| skillcop PoC | [GitHub](https://github.com/cfitzgerald-pd/skillcop) | Proof of concept: defense against malicious skills |
| specweave blog | [GitHub](https://github.com/anton-abyzov/specweave/blob/develop/docs-site/blog/2026-02-21-toxicskills-why-your-ai-agent-skills-need-verification.md) | ToxicSkills verification analysis |
| aicerts.ai | [aicerts.ai](https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/) | Snyk audit news |
| buildtolaunch (Substack) | [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) | 10 Tested Plugins — 4 Worth Keeping |
| Scott Spence (blog) | [scottspence.com](https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces) | Organizing skills into marketplaces |
| devtoolpicks.com | [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Skills vs MCP Connectors vs Plugins |
| DEV Community | [dev.to](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Skills vs MCP Servers practical guide |
| DEV Community | [dev.to](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best Claude Code Skills & Plugins Guide |
| Medium (Jonathan Fulton) | [medium.com](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | "Agent Skills: The Cheat Codes for Claude Code" |
| Medium (unicodeveloper) | [medium.com](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 Must-Have Skills for Claude (March 2026) |
| Medium (Muneeb Ahmad) | [medium.com](https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff) | Claude Code Extensions deep dive |
| alexop.dev | [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Full Stack: MCP, Skills, Subagents, Hooks |
| agensi.io | [agensi.io](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Plugins vs Skills explainer |
| agensi.io (marketplace) | [agensi.io](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Plugin Marketplace Complete Guide |
| turbodocx.com | [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best Plugins, Skills & MCP Servers roundup |
| openaitoolshub.org | [openaitoolshub.org](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison) | 6 marketplaces compared side-by-side |
| KDnuggets | [kdnuggets.com](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 Agent Skill Marketplaces |
| MindStudio | [mindstudio.ai](https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference) | Skills vs Plugins for builders |
| IntuitionLabs | [intuitionlabs.ai](https://intuitionlabs.ai/articles/claude-skills-vs-mcp) | Technical comparison: Skills vs MCP |
| TrueFoundry | [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries) | Best MCP Registries compared |
| InfoWorld | [infoworld.com](https://www.infoworld.com/article/4145014/how-to-build-an-enterprise-grade-mcp-registry.html) | How to build an enterprise-grade MCP registry |
| MCP Registry Blog | [blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/) | Official MCP Registry preview (Sep 2025) |
| Kong (engineering) | [konghq.com](https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery) | Kong MCP Registry engineering details |
| MACH Alliance | [machalliance.org](https://machalliance.org/mach-alliance-mcp-registry) | MACH Alliance MCP Registry |
| GitHub MCP Registry | [github.blog](https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/) | GitHub's MCP discovery layer |
| agentic-community | [GitHub](https://github.com/agentic-community/mcp-gateway-registry) | Enterprise MCP Gateway & Registry |
| VoltAgent/awesome-agent-skills | [GitHub](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ cross-agent skills |
| VoltAgent/awesome-openclaw-skills | [GitHub](https://github.com/VoltAgent/awesome-openclaw-skills) | 5,400+ OpenClaw skills |
| ComposioHQ/awesome-claude-skills | [GitHub](https://github.com/ComposioHQ/awesome-claude-skills) | Curated Claude skills list |
| alirezarezvani/claude-skills | [GitHub](https://github.com/alirezarezvani/claude-skills) | 232+ multi-agent skills |
| jeremylongshore repo | [GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 423 plugins, 2,849 skills, 177 agents |
| quemsah/awesome-claude-plugins | [GitHub](https://github.com/quemsah/awesome-claude-plugins) | Plugin adoption metrics via n8n |
| github/awesome-copilot | [GitHub](https://github.com/github/awesome-copilot/blob/main/docs/README.skills.md) | Copilot skills list |
| agentskills org | [GitHub](https://github.com/agentskills) | Agent Skills specification org |
| toolhive-registry-server | [GitHub](https://github.com/stacklok/toolhive-registry-server) | Open-source MCP Registry API server |
| smithery-ai/cli | [GitHub](https://github.com/smithery-ai/cli) | Smithery CLI for MCP + skills |
| kenhuangus AST10 | [GitHub](https://github.com/kenhuangus/agentic-skills-top-10) | Agentic Skills Top 10 reference |
| OWASP AST10 repo | [GitHub](https://github.com/OWASP/www-project-agentic-skills-top-10) | OWASP AST10 project |
| skillcop | [GitHub](https://github.com/cfitzgerald-pd/skillcop) | Malicious skills defense PoC |
| Palo Alto OWASP | [paloaltonetworks.com](https://www.paloaltonetworks.com/blog/cloud-security/owasp-agentic-ai-security/) | OWASP agentic security analysis |
| aikido.dev | [aikido.dev](https://www.aikido.dev/blog/owasp-top-10-agentic-applications) | OWASP Top 10 Agentic full guide |
| auth0 | [auth0.com](https://auth0.com/blog/owasp-top-10-agentic-applications-lessons/) | OWASP agentic lessons |
| Practical DevSecOps | [practical-devsecops.com](https://www.practical-devsecops.com/owasp-top-10-agentic-applications/) | OWASP agentic practical guide |
| DeepTeam | [trydeepteam.com](https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications) | OWASP agentic framework docs |
| morphllm.com/comparisons | [morphllm.com](https://www.morphllm.com/comparisons/opencode-vs-claude-code) | OpenCode vs Claude Code comparison |
| Snyk (cybersecurity skills) | [snyk.io](https://snyk.io/articles/top-claude-skills-cybersecurity-hacking-vulnerability-scanning/) | Top 9 Claude Skills for Cybersecurity |
| Snyk (UI/UX skills) | [snyk.io](https://snyk.io/articles/top-claude-skills-ui-ux-engineers/) | Top 8 Claude Skills for UI/UX |
| Andrew Baker blog | [andrewbaker.ninja](https://andrewbaker.ninja/2026/03/30/claude-code-remote-control-computer-use-2026-guide/) | Claude Code Remote Control Guide |
| claudefa.st | [claudefa.st](https://claudefa.st/blog/guide/development/claude-code-channels) | Claude Code Channels guide |
| oreateai.com | [oreateai.com](https://www.oreateai.com/blog/claude-code-gets-smarter-unlocking-your-development-ecosystem-with-remote-mcp-support/4b448b134eccc5688a1b00b64c539d3a) | Remote MCP explainer |
| Joe Njenga (Medium) | [medium.com](https://medium.com/@joe.njenga/claude-code-remote-mcp-now-supported-heres-how-it-works-fe54305c78cf) | Remote MCP how it works |
| support.claude.com | [support.claude.com](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp) | Custom connectors with remote MCP |
| platform.claude.com (skills) | [platform.claude.com](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | Agent Skills API documentation |
| platform.claude.com (MCP) | [platform.claude.com](https://platform.claude.com/docs/en/agents-and-tools/remote-mcp-servers) | Remote MCP servers documentation |
| releasebot.io | [releasebot.io](https://releasebot.io/updates/anthropic/claude-code) | Claude Code April 2026 release notes |
| releasebot.io (Anthropic) | [releasebot.io](https://releasebot.io/updates/anthropic) | Anthropic release notes tracker |
| claudecodeplugins.io | [claudecodeplugins.io](https://claudecodeplugins.io/) | Plugin & skills discovery hub |
| aitmpl.com | [aitmpl.com](https://www.aitmpl.com/) | Templates, agents, commands, skills |
| LobeHub | [lobehub.com/skills](https://lobehub.com/skills) | Multi-agent skills marketplace |
| termdock.com | [termdock.com](https://www.termdock.com/en/blog/agent-skills-guide) | Agent Skills Guide 2026 |
| virtualuncle.com | [virtualuncle.com](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Skills.sh guide |
| scriptbyai.com | [scriptbyai.com](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate Claude Code Resource List |
| awesomeclaude.ai | [awesomeclaude.ai](https://awesomeclaude.ai) | Claude AI Resources Directory |
| mejba.me | [mejba.me](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 Skills, Plugins & CLIs 2026 |
| aitooldiscovery.com | [aitooldiscovery.com](https://www.aitooldiscovery.com/guides/claude-code-reddit) | Reddit developer sentiment aggregation |
| claudecodeplugins.io | [claudecodeplugins.io](https://claudecodeplugins.io/) | Skills Hub |
| DataCamp | [datacamp.com](https://www.datacamp.com/blog/best-clawhub-skills) | Best ClawHub Skills guide |
| systemprompt.io | [systemprompt.io](https://systemprompt.io/guides/getting-started-anthropic-marketplace) | Getting Started with Anthropic Marketplace |
| claudemarketplaces.com (Anthropic) | [claudemarketplaces.com](https://claudemarketplaces.com/plugins/anthropics-claude-code) | Anthropic official plugins listing |
| azukiazusa.dev | [azukiazusa.dev](https://azukiazusa.dev/en/blog/gh-agent-skill-management/) | gh skill distribution blog |
| GitHub CLI manual | [cli.github.com](https://cli.github.com/manual/gh_skill) | gh skill command reference |
| GitHub CLI issue #13215 | [GitHub](https://github.com/cli/cli/issues/13215) | gh skill automation-ready feature request |
| GitHub CLI issue #13208 | [GitHub](https://github.com/cli/cli/issues/13208) | opencode support in gh skill |
| VS Code docs | [code.visualstudio.com](https://code.visualstudio.com/docs/copilot/customization/agent-skills) | Agent Skills in VS Code |
| Composio (skills) | [composio.dev](https://composio.dev/content/top-claude-skills) | Top 10 Claude Code Skills |
| morphllm.com/extensions | [morphllm.com](https://www.morphllm.com/claude-code-extensions) | Extensions guide |
| morphllm.com/plugins | [morphllm.com](https://www.morphllm.com/claude-code-plugins) | Plugins guide |
| morphllm.com/opencode | [morphllm.com](https://www.morphllm.com/comparisons/opencode-vs-claude-code) | OpenCode vs Claude Code |
| DEV (Codex comparison) | [dev.to](https://dev.to/_46ea277e677b888e0cd13/claude-code-vs-codex-2026-what-500-reddit-developers-really-think-31pb) | 500+ Reddit devs: Claude Code vs Codex |
| AWS ML Blog | [aws.amazon.com](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/) | AWS Agent Registry ML blog |
| AWS weekly roundup | [aws.amazon.com](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/) | AWS weekly roundup April 13, 2026 |
| AWS Bedrock docs | [docs.aws.amazon.com](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html) | AWS Agent Registry documentation |
| dev.classmethod.jp | [dev.classmethod.jp](https://dev.classmethod.jp/en/articles/aws-agent-registry-preview/) | AWS Agent Registry summary (Japanese dev community) |
| AgentKit/Inngest | [agentkit.inngest.com](https://agentkit.inngest.com/integrations/smithery) | Smithery integration in AgentKit |
| ToolHive skills guide | [docs.stacklok.com](https://docs.stacklok.com/toolhive/guides-cli/skills-management) | ToolHive skill management |
| ToolHive run MCP | [docs.stacklok.com](https://docs.stacklok.com/toolhive/guides-cli/run-mcp-servers) | ToolHive MCP server management |
| Smithery on ToolHive | [smithery.ai](https://smithery.ai/server/@StacklokLabs/toolhive) | ToolHive listed on Smithery |
| openaitoolshub skills guide | [openaitoolshub.org](https://www.openaitoolshub.org/en/blog/claude-code-skills-vs-plugins) | Skills vs Plugins guide |
| devtoolpicks.com | [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Three-way comparison |

---

## Stats Block

```
├─ 🟠 Reddit: ~15 threads │ engagement not quantified │ r/ClaudeCode (4,200+ weekly contributors)
├─ 🔵 X: 0 posts │ excluded from search
├─ 🔴 YouTube: 2 videos │ views not quantified
├─ 🟢 HN: 11 stories │ points/comments not quantified
├─ 🟣 TikTok: 0 videos │ no results
├─ 🩷 Instagram: 0 reels │ no results
├─ 🦋 Bluesky: 0 posts │ no results
├─ 📊 Polymarket: 0 markets │ no on-topic markets found
├─ 🌐 Web: 90+ pages │ blogs, official docs, GitHub repos, news
└─ 🗣️ Top voices: @simonw (simonwillison.net), @snyk_research │ r/ClaudeCode, r/ClaudeAI
```

---

## Data Gaps

- **Reddit thread URLs**: Site-specific Reddit searches returned no indexed results. Reddit sentiment summarized via third-party aggregators (morphllm.com/claude-code-reddit, aitooldiscovery.com). No direct upvote/comment counts available.
- **X/Twitter**: Excluded per research protocol.
- **TikTok**: No on-topic content found. The topic appears primarily text/code developer-focused, not video-short-form.
- **Instagram**: No on-topic content found. Same reason as TikTok.
- **Bluesky**: No on-topic posts surfaced despite search. Likely some activity but not indexed at depth.
- **Polymarket**: No prediction markets found on agent skills ecosystem topics.
- **YouTube engagement data**: Video URLs found but no view/like counts retrieved.
- **HN engagement data**: Stories identified but points/comment counts not retrieved from individual pages.
- **Smithery server count**: Two sources give conflicting numbers (2,000 vs 7,000) — likely different measurement dates or methodology.
- **Approximate coverage**: Reddit ~60% (sentiment only, no threads), HN ~85%, YouTube ~50%, Web ~90%. Overall topic coverage estimated at 80%.
- **Noise**: High volume of "best X in 2026" SEO content with low original information density. Filtered toward primary sources, official docs, and security research.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — Simon Willison on simonwillison.net ([link](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "Skills are Markdown with a tiny bit of YAML metadata and some optional scripts in whatever you can make executable in the environment. They feel a lot closer to the spirit of LLMs—throw in some text and let the model figure it out." — Simon Willison ([link](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "The barrier to publishing a new agent skill on ClawHub is a SKILL.md Markdown file and a GitHub account that's one week old, with no code signing, no security review, and no sandbox by default." — Snyk ToxicSkills report ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "91% of confirmed malicious skills combine prompt injection with traditional malware techniques." — Snyk ToxicSkills ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "AWS: Agents shouldn't be secret, so we built a registry" — The Register ([link](https://www.theregister.com/2026/04/09/aws_ai_agent_registry))

> "Skills are not verified by GitHub and may contain prompt injections, hidden instructions, or malicious scripts." — GitHub CLI documentation ([link](https://cli.github.com/manual/gh_skill))

> "If Skills are individual recipe cards and MCP is the kitchen plumbing, a Plugin is the full kitchen, stocked and ready to cook." — morphllm.com ([link](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "Developers who invest time learning Claude Code's patterns (CLAUDE.md, subagents, hooks, slash commands) report significant productivity gains, while developers who treat it like autocomplete get frustrated and leave." — morphllm.com aggregating r/ClaudeCode ([link](https://www.morphllm.com/claude-code-reddit))

> "Claude Code is, with hindsight, poorly named. It's not purely a coding tool: it's a tool for general computer automation. Anything you can achieve by typing commands into a computer is something that can now be automated by Claude Code." — Simon Willison ([link](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "Agent skills are portable sets of instructions, scripts, and resources that teach AI agents how to perform specific tasks. They follow the open Agent Skills specification, and work across multiple agent hosts including GitHub Copilot, Claude Code, Cursor, Codex, and Gemini CLI." — GitHub CLI Changelog ([link](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/))
