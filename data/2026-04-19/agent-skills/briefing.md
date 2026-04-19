# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-19
**Query type:** GENERAL
**Sources:** Web, Hacker News, Reddit, YouTube, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 1 community | 4,200+ weekly contributors (r/ClaudeCode) | Indirect; community size cited by third-party guides |
| Hacker News | 12 threads | N/A (not scraped directly) | Titles and URLs surfaced via site: search |
| YouTube | 5 videos | N/A (not scraped directly) | Tutorial-focused; titles sourced from search |
| Web | 75+ pages | — | Primary data source via WebSearch |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: Claude Code's Extension Format Goes Cross-Platform

The cornerstone of the 2026 agent-skill ecosystem is SKILL.md — a simple file format developed by Anthropic that encapsulates agent instructions as portable, filesystem-based packages. Every skill consists of a YAML frontmatter block (defining when to auto-activate) followed by markdown instructions Claude follows when the skill fires. Unlike slash commands that require explicit invocation, skills activate *automatically* when Claude detects relevant conversation context.

What makes this a macro-trend: the format was adopted as a cross-industry open standard. As of early 2026, SKILL.md works without modification on **Claude Code, OpenAI Codex CLI, Google Gemini CLI, GitHub Copilot, Cursor, Windsurf, Goose, Roo Code, and Trae**. Anthropic's official skills repo lives at [github.com/anthropics/skills](https://github.com/anthropics/skills); OpenAI, Vercel, Microsoft, and GitHub each publish their own skill catalogs in parallel repos.

The community infrastructure built around this standard is mature: [skills.sh](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) serves as the primary distribution hub, [SkillsMP](https://skillsmp.com) is the cross-platform marketplace (Claude, Codex, ChatGPT), and [agentskills.io](https://agentskills.io/home) aggregates the full catalog via daily-updated JSON. [Vercel Labs' `find-skills`](https://github.com/vercel-labs/skills) (`npx skills`) has accumulated 579,000+ installs as the top skill by total installs as of March 2026.

Official documentation: [Claude Code skills docs](https://code.claude.com/docs/en/skills), [Claude API Agent Skills overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview).

*Platforms: Web, Hacker News*

---

### 2. Plugin Marketplaces: A Maturing Ecosystem with Hundreds of Community Catalogs

Claude Code plugins bundle multiple skills, MCP servers, and slash commands into a single installable unit. Launched in public beta October 2025 and now stable, the plugin system supports `/plugin install`, `/plugin enable/disable`, and `/plugin marketplace` commands.

The community marketplace landscape in April 2026:

- **[tonsofskills.com](https://tonsofskills.com/)**: 423 plugins, 2,849 skills, 177 agents; open-source (MIT); installable via the CCPI npm package (`pnpm add -g @intentsolutionsio/ccpi`). GitHub: [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills). Also has a [marketplace comparisons page](https://tonsofskills.com/compare-marketplaces/).
- **[claudemarketplaces.com](https://claudemarketplaces.com/)**: Largest directory of Claude Code extensions sorted by installs and GitHub stars; 4,200+ skills cited.
- **[ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins)**: Curated list; [Composio blog top 10](https://composio.dev/content/top-claude-code-plugins).
- **[quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins)**: Automated adoption metrics tracking.
- **[VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)**: 1,000+ cross-platform skills (Claude Code, Codex, Gemini CLI, Cursor, and more).
- **[hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)**: Curated list including skills, hooks, slash-commands, orchestrators.
- **[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)**: 232+ skills for 8+ coding agents.
- **[levnikolaevich/claude-code-skills](https://github.com/levnikolaevich/claude-code-skills)**: Plugin suite with bundled MCP servers (hex-line, hex-graph, hex-ssh).

Notable plugins highlighted in reviews ([Firecrawl](https://www.firecrawl.dev/blog/best-claude-code-plugins), [Mejba.me](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026), [self.md](https://self.md/guides/best-claude-code-plugins/)): **Claude-Mem** (long-term memory), **Superpowers** (structured lifecycle planning), **Local-Review** (parallel diff code reviews), **Plannotator** (planning mode clarity). The Universal SEO skill is cited as a showcase with 19 sub-skills, 12 subagents, and 3 extensions.

Official plugin README: [anthropics/claude-code plugins](https://github.com/anthropics/claude-code/blob/main/plugins/README.md).

*Platforms: Web, Hacker News*

---

### 3. MCP at 97 Million Installs: From Anthropic Experiment to Industry Infrastructure

The Model Context Protocol crossed **97 million installs on March 25, 2026** — the fastest adoption curve for any AI infrastructure standard in history. By this date, every major AI provider (OpenAI, Google DeepMind, Microsoft, Meta) ships MCP-compatible tooling, and the protocol has become the *default* mechanism for connecting AI agents to external tools, APIs, and data sources.

Scale: 5,800+ community and enterprise MCP servers; 10,000+ active in production; MCPBundles maintains [10,000+ tools across 700+ providers](https://www.mcpbundles.com/blog/best-mcp-servers). Chrome now ships a [built-in MCP server (native MCP v2)](https://www.computeleap.com/blog/chrome-built-in-mcp-server-native-mcp-v2-2026/).

Directories and marketplaces: [MCP Market](https://mcpmarket.com/), [Awesome MCP Servers](https://mcpservers.org/), [AgentPatch](https://agentpatch.ai/blog/best-mcp-servers-2026/), [Builder.io top servers](https://www.builder.io/blog/best-mcp-servers-2026), [StackGen platform engineers](https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026), [Databar.ai sales teams](https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026).

**MCP joins the Linux Foundation.** In December 2025, Anthropic donated MCP to the newly formed [Agentic AI Foundation (AAIF)](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) under the Linux Foundation. Co-founders: Anthropic, Block (goose), OpenAI (AGENTS.md). Supporters include Google, Microsoft, AWS, Cloudflare, Bloomberg. MCP now has vendor-neutral governance while maintaining technical autonomy. Covered by [TechCrunch](https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/), [The New Stack](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/), [GitHub Blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/), [OpenAI](https://openai.com/index/agentic-ai-foundation/), [Block](https://block.xyz/inside/block-anthropic-and-openai-launch-the-agentic-ai-foundation), [Linux Foundation](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation).

**MCP tool search in Claude Code** (April 2026): Anthropic added native tool search to Claude Code. [Tessl coverage](https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/). **MCP Gateway** pattern also emerging: intermediary proxy providing centralized auth, authorization, auditing, and traffic management. Enterprise-ready implementation: [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry). Microsoft's [Using MCP Tools guide](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools). MCP gateways overview: [ByteBridge/Medium](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a). Year-in-review: [Pento "A Year of MCP"](https://www.pento.ai/blog/a-year-of-mcp-2025-review).

*Platforms: Web*

---

### 4. AWS Agent Registry and Enterprise Agent Governance

AWS launched the **Agent Registry** (preview) in early April 2026 as part of Bedrock AgentCore — a single place to discover, share, and reuse AI agents, tools, and agent skills across an enterprise. Available in 5 compute regions. The registry stores metadata for agents, tools, MCP servers, skills, and associated resources, with hybrid search (keyword + semantic) enabling discovery by intent ("payment processing" surfaces tools tagged "billing" or "invoicing").

Queryable via AgentCore Console, APIs, or any MCP-compatible client including Kiro and Claude Code.

The Register's headline: ["Agents shouldn't be secret, so we built a registry"](https://www.theregister.com/2026/04/09/aws_ai_agent_registry). Full coverage: [AWS Blog](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/), [AWS ML Blog (scale post)](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/), [InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/), [TechBriefly](https://techbriefly.com/2026/04/14/aws-launches-agent-registry-to-manage-enterprise-ai-agents/), [Dataconomy](https://dataconomy.com/2026/04/14/aws-launches-agent-registry-to-centralize-ai-agent-governance/), [Hawkdive](https://www.hawkdive.com/aws-weekly-update-claude-mythos-in-bedrock-agent-registry-launch-and-more/).

Also this week: **Anthropic launched Claude Managed Agents** in public beta (April 8, 2026) — a composable API handling sandboxing, state, permissions, and orchestration for cloud-hosted AI agents. Claude Code April updates include `/tui` fullscreen rendering, mobile push notifications, cleaner plugin/doctor workflows, and smarter MCP session management. [Releasebot Claude Code release notes](https://releasebot.io/updates/anthropic/claude-code), [Anthropic release notes](https://releasebot.io/updates/anthropic).

*Platforms: Web*

---

### 5. Security Crisis: Prompt Injection, Malicious Skills, and the MCP Design Flaw

Two overlapping security stories dominated the last 30 days:

**ToxicSkills (Snyk, February 2026):** The first comprehensive security audit of the agent skills supply chain, scanning 3,984 skills from ClawHub and skills.sh:
- 13.4% (534 skills) contain critical-level security issues
- 36% of all skills contain prompt-injection techniques (1,467 malicious payloads found)
- 100% of confirmed malicious skills combine malicious code + prompt injection
- Attack vector: 3 lines of SKILL.md markdown can instruct an agent to exfiltrate SSH keys

Snyk responded with [agent-scan](https://github.com/snyk/agent-scan) (hybrid LLM judges + deterministic rules), [Skill Inspector](https://labs.snyk.io/resources/agent-scan-skill-inspector/), partnerships with [Vercel](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) and [Tessl](https://snyk.io/blog/snyk-tessl-partnership/) to secure registries. OWASP published the [Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/). Detailed attack writeup: ["From SKILL.md to Shell Access in Three Lines of Markdown"](https://snyk.io/articles/skill-md-shell-access/). ToxicSkills full report: [snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/).

**MCP STDIO Design Flaw (OX Security, April 16, 2026):** OX Security identified a "critical, systemic vulnerability" in MCP's STDIO transport mechanism enabling Arbitrary Command Execution (RCE). Scope: ~150 million downloads, 7,000 publicly accessible servers, up to 200,000 vulnerable instances. 10 high/critical CVEs already issued for individual tools using MCP.

Anthropic declined to modify protocol architecture, calling the behavior "expected." One week after initial report, Anthropic quietly updated security policy advising STDIO adapters "should be used with caution." Researchers: "This change didn't fix anything."

Coverage: [The Register (primary)](https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/), [OX Security research blog](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/), [TechRadar ("This is not a traditional coding error")](https://www.techradar.com/pro/security/this-is-not-a-traditional-coding-error-experts-flag-potentially-critical-security-issues-at-the-heart-of-anthropics-mcp-exposes-150-million-downloads-and-thousands-of-servers-to-complete-takeover), [CyberKendra (RCE details)](https://www.cyberkendra.com/2026/04/anthropics-mcp-design-flaw-enables.html), [Computing.co.uk](https://www.computing.co.uk/news/2026/security/flaw-in-anthropic-s-mcp-putting-200k-servers-at-risk), [Register Forums](https://forums.theregister.com/forum/all/2026/04/16/anthropic_mcp_design_flaw/), [programming.dev discussion](https://programming.dev/post/48949824).

Community discussion with no paywalls: [TheHelper thread](https://www.thehelper.net/threads/anthropic-wont-own-mcp-design-flaw-putting-200k-servers-at-risk.200905/).

*Platforms: Web*

---

### 6. Workflow Patterns: Agent Teams, Routines, and Custom Subagents

Claude Code's agentic workflow capabilities expanded significantly in 2026:

**Agent Skills** ([platform.claude.com/docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)): Reusable instruction sets providing domain-specific expertise. Build once, runs across Claude web app, Claude Code, and the API.

**Custom Subagents** ([code.claude.com/docs/en/sub-agents](https://code.claude.com/docs/en/sub-agents)): Each subagent gets its own context window, custom system prompt, specific tool access, and independent permissions.

**Agent Teams (new 2026)**: Multiple Claude instances working in parallel via git-based coordination — agents claim tasks, merge changes continuously, and resolve conflicts automatically. Guide: [FlorianBruniaux/claude-code-ultimate-guide](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md). Show HN for related tooling: [Real-time dashboard for Claude Code agent teams](https://news.ycombinator.com/item?id=47602986).

**Claude Code Routines**: Named, reusable instruction sets that chain multiple steps. [DEV.to explainer](https://dev.to/onsen/claude-code-routines-automate-dev-workflows-4ijn).

**Workflow Patterns** ([MindStudio](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns)): Sequential, orchestrator, split-and-merge parallel patterns all supported.

Notable community repos: [wshobson/agents](https://github.com/wshobson/agents) (multi-agent orchestration), [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code). DevOps.com coverage of agent skills launch: [devops.com](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/). Practice guide: [smart-webtech.com](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/).

Developer tutorials: [chatprd.ai workflows](https://www.chatprd.ai/how-i-ai/workflows/tool/claude), [Sabrina.dev concept explainer](https://www.sabrina.dev/p/every-claude-code-concept-explained-beginners).

*Platforms: Web, Hacker News, YouTube*

---

### 7. Tutorial Explosion and Developer Education

High tutorial demand reflects a rapidly expanding but complex ecosystem. Top YouTube content as of April 2026:
- ["The Simple Guide to Claude Code: MCP vs. Skills vs. Sub-Agents"](https://www.youtube.com/watch?v=IsJh8IGtErI) (5 days ago)
- ["The Ultimate Claude Code Guide | MCP, Skills & More"](https://www.youtube.com/watch?v=uogzSxOw4LU) (6 days ago)
- ["Claude MCP Tutorial: Give Claude Superpowers in 30 Seconds"](https://www.youtube.com/watch?v=Lxznc91wlTk)
- ["The ONLY Claude Code Tutorial You'll Ever Need in 2026"](https://www.youtube.com/watch?v=LlFgLsffbBs)
- ["FULL Claude Code Tutorial for Beginners in 2026!"](https://www.youtube.com/watch?v=qYqIhX9hTQk)
- [Claude Code Tutorial playlist](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)

The primary conceptual confusion driving tutorial demand: **MCP vs. Skills vs. Sub-Agents vs. Plugins**. Written explainer: [DEV.to: Claude Code Skills vs MCP Servers](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k). Also: [Medium/@unicodeveloper: 10 Must-Have Skills for Claude](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051), [Firecrawl best skills guide](https://www.firecrawl.dev/blog/best-claude-code-skills), [calmops.com AI Agent Skills Guide 2026](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/).

HN notable: ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) reflects community framing of skills as the more impactful innovation. Claude Code hit #1 on HN; [DEV.to write-up](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74).

*Platforms: YouTube, Hacker News, Web*

---

### 8. The Claude Code Source Leak and KAIROS Revelation

On March 31, 2026, Anthropic accidentally published the full Claude Code source to the public npm registry — 512,000 lines across 1,906 TypeScript files. [Alex Kim's blog analysis](https://alex000kim.com/posts/2026-03-31-claude-code-source-leak/) and [Hacker News coverage](https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html) surfaced references to an unreleased autonomous agent mode called **KAIROS**, which includes a **"/dream skill" for nightly memory distillation**. [DEV.to: "The Great Claude Code Leak of 2026: Accident, Incompetence, or the Best PR Stunt in AI History?"](https://dev.to/varshithvhegde/the-great-claude-code-leak-of-2026-accident-incompetence-or-the-best-pr-stunt-in-ai-history-3igm)

Separately, Claude Code was used by Anthropic researcher Nicholas Carlini to identify a remotely exploitable heap buffer overflow in the Linux kernel's NFS driver — undiscovered for 23 years. [InfoQ coverage](https://www.infoq.com/news/2026/04/claude-code-linux-vulnerability/).

*Platforms: Web, Reddit (r/ClaudeCode per community aggregator)*

---

### 9. Developer Tooling for the Skill Ecosystem

Beyond the marketplaces themselves, a meta-layer of developer tooling has emerged:

- **Agnix** (Show HN: [news.ycombinator.com/item?id=46983879](https://news.ycombinator.com/item?id=46983879)): Linter for AI agent configs — validates CLAUDE.md, skills, MCP, hooks
- **agent-scan** ([github.com/snyk/agent-scan](https://github.com/snyk/agent-scan)): Security scanner for AI agents, MCP servers, agent skills
- **skill-audit skill** ([SkillsMP listing](https://skillsmp.com/skills/neversight-learn-skills-dev-data-skills-md-absolutelyskilled-absolutelyskilled-skill-audit-skill-md)): An agent skill that audits other skills
- **Real-time Claude Code agent team dashboard** (Show HN: [news.ycombinator.com/item?id=47602986](https://news.ycombinator.com/item?id=47602986))
- **last30days skill** ([github.com/mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)): Research skill itself indexable in the ecosystem
- **Composio YouTube MCP Integration** ([composio.dev](https://composio.dev/toolkits/youtube/framework/claude-code)): YouTube as a Claude Code tool

Naming convention gotcha flagged in HN discussions: skills require kebab-case naming; Claude Code silently ignores improperly named skills. HN thread: [item?id=46396930](https://news.ycombinator.com/item?id=46396930).

*Platforms: Hacker News, Web*

---

### 10. Microsoft, OpenAI, and Cross-Platform Convergence

The agent skills open standard extends beyond Claude Code:

- **OpenAI Codex**: [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills) — Codex's agent skills page; plugins use distributed registry pattern with multiple marketplace.json targets
- **Microsoft .NET Skills**: [devblogs.microsoft.com/dotnet](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) — Extending coding agents with .NET skills
- **Microsoft Agent Skills (DeepWiki)**: [deepwiki.com/microsoft/agent-skills/4-plugins](https://deepwiki.com/microsoft/agent-skills/4-plugins)
- **Microsoft Learn MCP Tools**: [learn.microsoft.com](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools)

HN thread: ["Claude Code Skills and Plugins as an Open Source Project"](https://news.ycombinator.com/item?id=47321892), ["Agent Skills – Open Trusted Catalog of AI Agent Skills: Claude, OpenAI, Vercel, GH"](https://news.ycombinator.com/item?id=46692865).

Inference.sh published an overview of the convergence: ["Agent Skills: The Open Standard for AI Capabilities"](https://inference.sh/blog/skills/agent-skills-overview). The industry narrative: move from monolithic agents with hard-coded capabilities to composable agents assembling from portable skill packages.

*Platforms: Web, Hacker News*

---

## Cross-Source Patterns

### Pattern 1: The "SKILL.md as universal plugin format" narrative
- **Signal**: SKILL.md being adopted by all major AI coding agent platforms
- **Platforms**: Web (multiple), Hacker News, YouTube tutorials
- **Key quotes**: "A skill you write or install works across all of these tools without modification" (inference.sh); "Claude Skills are awesome, maybe a bigger deal than MCP" (HN thread title)

### Pattern 2: Security as the ecosystem's biggest unsolved problem
- **Signal**: Two concurrent security stories — malicious skills supply chain + MCP architectural flaw
- **Platforms**: Web (The Register, OX Security, Snyk, TechRadar, Computing, CyberKendra), Hacker News discussion threads
- **Key quotes**: "13.4% of all skills contain critical-level security issues" (Snyk ToxicSkills); "This is not a traditional coding error" (TechRadar on MCP flaw); "This change didn't fix anything" (OX Security researchers on Anthropic's response)

### Pattern 3: Enterprise registries emerging to govern agent sprawl
- **Signal**: AWS Agent Registry + MCP tool search in Claude Code + MCPBundles 10K+ tools + Anthropic Claude Managed Agents, all in April 2026
- **Platforms**: Web (AWS Blog, The Register, InfoQ, Dataconomy)
- **Key quotes**: "Agents shouldn't be secret, so we built a registry" (AWS/The Register); "Claude Managed Agents: composable API handling sandboxing, state, permissions, and orchestration" (Anthropic)

### Pattern 4: Developer confusion driving tutorial volume
- **Signal**: Multiple "MCP vs. Skills vs. Sub-Agents vs. Plugins" explainer videos published in the same week
- **Platforms**: YouTube, Web (DEV.to, Sabrina.dev), Hacker News
- **Key quotes**: "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..." (HN thread title)

---

## Per-Platform Tables

### Hacker News

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (unknown) | Claude Skills | — | — | — | https://news.ycombinator.com/item?id=45607117 |
| (unknown) | Customize Claude Code with plugins | — | — | Plugin install/enable/disable/marketplace commands | https://news.ycombinator.com/item?id=45530150 |
| (unknown) | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | "Maybe a bigger deal than MCP" | https://news.ycombinator.com/item?id=45619537 |
| (unknown) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | — | — | https://news.ycombinator.com/item?id=43410866 |
| (unknown) | You've got your CLAUDE.md, Skills, Agents, MCP, slash commands... | — | — | Complexity fragmentation discussion | https://news.ycombinator.com/item?id=46396930 |
| (unknown) | Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks) | — | — | Kebab-case naming validation | https://news.ycombinator.com/item?id=46983879 |
| (unknown) | Remote MCP Support in Claude Code | — | — | — | https://news.ycombinator.com/item?id=44312363 |
| (unknown) | Show HN: Real-time dashboard for Claude Code agent teams | — | — | — | https://news.ycombinator.com/item?id=47602986 |
| (unknown) | Agent Skills – Open Trusted Catalog of AI Agent Skills: Claude,OpenAI,Vercel,GH | — | — | Cross-platform catalog auto-updates daily | https://news.ycombinator.com/item?id=46692865 |
| (unknown) | Claude Code Skills and Plugins as an Open Source Project | — | — | — | https://news.ycombinator.com/item?id=47321892 |
| (unknown) | How I'm Productive with Claude Code | — | — | — | https://news.ycombinator.com/item?id=47494890 |
| (unknown) | How to code Claude Code in 200 lines of code | — | — | — | https://news.ycombinator.com/item?id=46545620 |

### YouTube

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The ONLY Claude Code Tutorial You'll Ever Need in 2026 | — | — | No | https://www.youtube.com/watch?v=LlFgLsffbBs |
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| (unknown) | FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step) | — | — | No | https://www.youtube.com/watch?v=qYqIhX9hTQk |
| (unknown) | The Simple Guide to Claude Code: MCP vs. Skills vs. Sub-Agents | — | — | No | https://www.youtube.com/watch?v=IsJh8IGtErI |
| (unknown) | Claude MCP Tutorial: Give Claude Superpowers in 30 Seconds | — | — | No | https://www.youtube.com/watch?v=Lxznc91wlTk |
| (unknown) | Claude Code Tutorial playlist | — | — | No | https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs | https://code.claude.com/docs/en/skills | Official skills specification |
| Claude API Docs | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Agent Skills API overview |
| Claude Code Sub-Agents Docs | https://code.claude.com/docs/en/sub-agents | Custom subagent creation |
| anthropics/skills (GitHub) | https://github.com/anthropics/skills | Official Anthropic skills repository |
| anthropics/claude-code plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Official plugin system documentation |
| tonsofskills.com | https://tonsofskills.com/ | 423 plugins, 2,849 skills marketplace |
| tonsofskills compare | https://tonsofskills.com/compare-marketplaces/ | Marketplace comparison guide |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | CCPI CLI package manager + tonsofskills source |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Largest Claude plugin directory |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| quemsah/awesome-claude-plugins | https://github.com/quemsah/awesome-claude-plugins | Automated adoption metrics |
| VoltAgent/awesome-agent-skills | https://github.com/VoltAgent/awesome-agent-skills | 1,000+ cross-platform skills |
| hesreallyhim/awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | Skills, hooks, commands, orchestrators |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 232+ multi-platform skills |
| levnikolaevich/claude-code-skills | https://github.com/levnikolaevich/claude-code-skills | Plugin suite + bundled MCP servers |
| SkillsMP | https://skillsmp.com | Cross-platform skills marketplace |
| Vercel Labs/skills | https://github.com/vercel-labs/skills | `npx skills`; 579K+ installs |
| agentskills.io | https://agentskills.io/home | Cross-platform skills catalog |
| skills.sh guide | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | skills.sh distribution hub guide |
| inference.sh open standard blog | https://inference.sh/blog/skills/agent-skills-overview | "Agent Skills: The Open Standard" |
| calmops.com skills guide | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | Complete guide to agent skills 2026 |
| MCP Market | https://mcpmarket.com/ | Primary MCP server directory |
| MCPBundles | https://www.mcpbundles.com/blog/best-mcp-servers | 10,000+ tools, 700+ providers |
| Awesome MCP Servers | https://mcpservers.org/ | Community curated MCP list |
| AgentPatch | https://agentpatch.ai/blog/best-mcp-servers-2026/ | Bundled MCP marketplace |
| MCPBundles March list | https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026 | Top MCP servers March 4 2026 |
| Builder.io MCP | https://www.builder.io/blog/best-mcp-servers-2026 | Best MCP servers for developers |
| StackGen platform engineers | https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026 | Platform engineers MCP guide |
| Databar.ai sales MCP | https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 | Sales team MCP guide |
| ByteBridge MCP gateways | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | MCP Gateway overview |
| MCP gateway registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP gateway implementation |
| Microsoft Learn MCP | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Microsoft MCP tools guide |
| Anthropic MCP AAIF | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | Anthropic donating MCP to AAIF |
| MCP joins AAIF blog | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | MCP foundation blog post |
| Linux Foundation AAIF | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | Linux Foundation announcement |
| OpenAI AAIF | https://openai.com/index/agentic-ai-foundation/ | OpenAI co-founds AAIF |
| Block AAIF | https://block.xyz/inside/block-anthropic-and-openai-launch-the-agentic-ai-foundation | Block co-founds AAIF |
| TechCrunch AAIF | https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/ | TechCrunch AAIF coverage |
| The New Stack AAIF | https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/ | The New Stack AAIF coverage |
| GitHub Blog MCP Linux Foundation | https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/ | GitHub developer perspective |
| Solo.io AAIF | https://www.solo.io/blog/aaif-announcement-agentgateway | AAIF + AgentGateway |
| Vucense MCP 97M | https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/ | MCP 97M installs report |
| AffiliateBooster MCP 97M | https://www.affiliatebooster.com/anthropic-mcp-protocol-97-million-installs/ | MCP 97M installs coverage |
| Artur Markus MCP 97M | https://www.arturmarkus.com/anthropics-model-context-protocol-hits-97-million-installs-on-march-25-mcp-transitions-from-experimental-to-foundation-layer-for-agentic-ai/ | MCP transition to foundation layer |
| ByteIota MCP 97M | https://byteiota.com/model-context-protocol-hits-97m-installs-standard-wins/ | "The Standard Wins" |
| Effloow MCP ecosystem | https://effloow.com/articles/mcp-ecosystem-growth-100-million-installs-2026 | MCP ecosystem growth narrative |
| Chrome MCP server | https://www.computeleap.com/blog/chrome-built-in-mcp-server-native-mcp-v2-2026/ | Chrome built-in MCP v2 |
| Pento year of MCP | https://www.pento.ai/blog/a-year-of-mcp-2025-review | A Year of MCP retrospective |
| Dotun Opasina MCP | https://www.dotunopasina.com/datascience/the-standard-is-set-now-what-do-you-build | "The Standard Is Set" |
| AINetizens MCP | https://ainetizens.com/anthropic-mcp-model-context-protocol-explained-2026/ | MCP Explained 2026 |
| Tessl MCP tool search | https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/ | MCP tool search in Claude Code |
| Releasebot Claude Code | https://releasebot.io/updates/anthropic/claude-code | Claude Code April 2026 release notes |
| Releasebot Anthropic | https://releasebot.io/updates/anthropic | Anthropic April 2026 release notes |
| AWS Blog Agent Registry | https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | AWS weekly roundup April 13 |
| AWS ML Blog registry scale | https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/ | AWS Agent Registry deep-dive |
| The Register AWS registry | https://www.theregister.com/2026/04/09/aws_ai_agent_registry | "Agents shouldn't be secret" |
| InfoQ AWS registry | https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ | Agent sprawl governance |
| TechBriefly AWS registry | https://techbriefly.com/2026/04/14/aws-launches-agent-registry-to-manage-enterprise-ai-agents/ | TechBriefly coverage |
| Dataconomy AWS registry | https://dataconomy.com/2026/04/14/aws-launches-agent-registry-to-centralize-ai-agent-governance/ | Governance angle |
| Hawkdive AWS | https://www.hawkdive.com/aws-weekly-update-claude-mythos-in-bedrock-agent-registry-launch-and-more/ | Weekly roundup |
| NasGuy AWS | https://www.thenasguy.com/2026/04/13/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | NasGuy roundup |
| Noise AWS | https://noise.getoto.net/2026/04/13/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | Noise roundup |
| The Register MCP flaw | https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ | MCP design flaw primary report |
| Register Forums MCP | https://forums.theregister.com/forum/all/2026/04/16/anthropic_mcp_design_flaw/ | Community discussion |
| OX Security MCP flaw | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | OX Security research |
| TechRadar MCP flaw | https://www.techradar.com/pro/security/this-is-not-a-traditional-coding-error-experts-flag-potentially-critical-security-issues-at-the-heart-of-anthropics-mcp-exposes-150-million-downloads-and-thousands-of-servers-to-complete-takeover | "Not a traditional coding error" |
| CyberKendra MCP RCE | https://www.cyberkendra.com/2026/04/anthropics-mcp-design-flaw-enables.html | RCE details |
| Computing.co.uk MCP flaw | https://www.computing.co.uk/news/2026/security/flaw-in-anthropic-s-mcp-putting-200k-servers-at-risk | Computing coverage |
| TheHelper MCP flaw | https://www.thehelper.net/threads/anthropic-wont-own-mcp-design-flaw-putting-200k-servers-at-risk.200905/ | Community thread |
| programming.dev MCP | https://programming.dev/post/48949824 | Developer community discussion |
| Asanify AI news Apr 18 | https://asanify.com/blog/news/agentic-ai-enterprise-workforce-april-18-2026/ | AI news digest April 18 |
| Snyk ToxicSkills | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | ToxicSkills full research report |
| Snyk Vercel partnership | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Securing the skill ecosystem |
| Snyk Tessl partnership | https://snyk.io/blog/snyk-tessl-partnership/ | Securing skills registry |
| OWASP Agentic Skills Top 10 | https://owasp.org/www-project-agentic-skills-top-10/ | OWASP security framework |
| Snyk agent-scan GitHub | https://github.com/snyk/agent-scan | Security scanner tool |
| Snyk SKILL.md shell access | https://snyk.io/articles/skill-md-shell-access/ | 3-line attack vector writeup |
| Snyk Skill Inspector | https://labs.snyk.io/resources/agent-scan-skill-inspector/ | Skill Inspector launch |
| Snyk Agent Security intro | https://snyk.io/blog/introducing-agent-security/ | Agent Security product launch |
| skill-audit SkillsMP | https://skillsmp.com/skills/neversight-learn-skills-dev-data-skills-md-absolutelyskilled-absolutelyskilled-skill-audit-skill-md | Meta-skill auditing other skills |
| wshobson/agents | https://github.com/wshobson/agents | Multi-agent orchestration repo |
| FlorianBruniaux agent-teams | https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md | Agent teams guide |
| DevOps.com agent skills | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | DevOps.com coverage |
| MindStudio workflow patterns | https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns | 5 agentic workflow patterns |
| DEV.to routines | https://dev.to/onsen/claude-code-routines-automate-dev-workflows-4ijn | Claude Code Routines explainer |
| smart-webtech workflows | https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/ | Workflows best practices 2026 |
| chatprd.ai workflows | https://www.chatprd.ai/how-i-ai/workflows/tool/claude | Claude AI Workflows guide |
| Sabrina.dev concepts | https://www.sabrina.dev/p/every-claude-code-concept-explained-beginners | All Claude Code concepts explained |
| DEV.to skills vs MCP | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP comparison |
| Firecrawl best skills | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code Skills 2026 |
| Firecrawl best plugins | https://www.firecrawl.dev/blog/best-claude-code-plugins | Best Claude Code Plugins 2026 |
| Mejba.me top 10 | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills, plugins, CLIs |
| self.md plugins guide | https://self.md/guides/best-claude-code-plugins/ | Best plugins guide |
| Composio top plugins | https://composio.dev/content/top-claude-code-plugins | Top 10 plugins (Composio) |
| Composio YouTube MCP | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP integration |
| Medium unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills |
| calmops.com guide | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI Agent Skills Guide 2026 |
| OpenAI Codex skills | https://developers.openai.com/codex/skills | OpenAI Codex skills page |
| DeepWiki Microsoft skills | https://deepwiki.com/microsoft/agent-skills/4-plugins | Microsoft agent skills plugins |
| Microsoft .NET blog skills | https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ | .NET agent skills extension |
| AITooldiscovery Reddit guide | https://www.aitooldiscovery.com/guides/claude-code-reddit | Claude Code Reddit community overview |
| DEV.to Claude Code #1 HN | https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74 | Claude Code hits #1 HN |
| Alex Kim source leak | https://alex000kim.com/posts/2026-03-31-claude-code-source-leak/ | Source leak analysis |
| HackerNews source leak | https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html | Source leak news |
| DEV.to source leak | https://dev.to/varshithvhegde/the-great-claude-code-leak-of-2026-accident-incompetence-or-the-best-pr-stunt-in-ai-history-3igm | "The Great Claude Code Leak" |
| InfoQ Linux kernel vuln | https://www.infoq.com/news/2026/04/claude-code-linux-vulnerability/ | Claude Code finds kernel vulnerability |
| last30days skill GitHub | https://github.com/mvanhorn/last30days-skill | Research skill (meta) |
| HN mirror Blode | https://hn.matthewblode.com/item/43307809 | HN: Using Claude Code first impressions |
| youtube-transcript-mcp | https://github.com/hancengiz/youtube-transcript-mcp/blob/main/CLAUDE_CODE_AGENT_GUIDE.md | YouTube transcript MCP agent guide |

---

## Stats Block

```
├─ 🟠 Reddit: 1 community │ 4,200+ weekly contributors (r/ClaudeCode) │ engagement not scraped directly
├─ 🔵 X: not crawled
├─ 🔴 YouTube: 6 videos │ views/likes not scraped │ 0 with transcripts
├─ 🟢 HN: 12 threads │ points/comments not scraped │ titles and URLs confirmed
├─ 🟣 TikTok: not crawled
├─ 🩷 Instagram: not crawled
├─ 🦋 Bluesky: not crawled
├─ 📊 Polymarket: not crawled
├─ 🌐 Web: 90+ pages
└─ 🗣️ Top voices: Snyk (security research), OX Security (MCP flaw), AWS (Agent Registry), Anthropic (AAIF/MCP/Claude Managed Agents) │ r/ClaudeCode, HN
```

---

## Data Gaps

- **X/Twitter, TikTok, Instagram, Bluesky, Polymarket**: Not crawled in this run. The /last30days skill pipeline did not successfully retrieve social-platform data for these sources. Likely high-volume discussion on X given the MCP flaw story and Claude Code source leak both broke during this period.
- **Reddit**: Indirect coverage only (community size cited in third-party articles). r/ClaudeCode, r/ClaudeAI, r/AIAssistants almost certainly have active threads on the MCP STDIO flaw and KAIROS leak.
- **Hacker News**: Thread titles and URLs captured via `site:` search, but vote counts, comment counts, and direct quotes from comments are missing. Actual top-voted comments on "Claude Skills are awesome, maybe a bigger deal than MCP" and "Show HN: Agnix" would be high-value additions.
- **YouTube**: Video metadata (view counts, like counts, channel names, publish dates) not retrieved. Transcripts not obtained for any of the 6 identified videos.
- **Engagement metrics**: Across all platforms, engagement data is absent or approximate. This briefing is heavy on content/URL coverage but light on relative signal weighting.
- **Estimated coverage**: Web content ~85%; social platforms ~10% (Reddit via proxy only); quantitative metrics ~5%.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — HN thread title ([link](https://news.ycombinator.com/item?id=45619537))

> "13.4% of all skills contain at least one critical-level security issue including malware distribution, prompt injection attacks, and exposed secrets." — Snyk ToxicSkills Research ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "This is not a traditional coding error" — TechRadar on the MCP architectural flaw ([link](https://www.techradar.com/pro/security/this-is-not-a-traditional-coding-error-experts-flag-potentially-critical-security-issues-at-the-heart-of-anthropics-mcp-exposes-150-million-downloads-and-thousands-of-servers-to-complete-takeover))

> "This change didn't fix anything" — OX Security researchers on Anthropic's updated STDIO security policy ([link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/))

> "Agents shouldn't be secret, so we built a registry" — AWS, via The Register ([link](https://www.theregister.com/2026/04/09/aws_ai_agent_registry))

> "A skill you write or install works across all of these tools without modification" — inference.sh on the SKILL.md cross-platform standard ([link](https://inference.sh/blog/skills/agent-skills-overview))

> "From SKILL.md to shell access in three lines of markdown" — Snyk attack demonstration title ([link](https://snyk.io/articles/skill-md-shell-access/))

> "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..." — HN community, on Claude Code complexity fragmentation ([link](https://news.ycombinator.com/item?id=46396930))

> "MCP has become one of the fastest-growing and widely-adopted open-source projects in AI: Over 97 million monthly SDK downloads, 10,000 active servers" — Anthropic/Linux Foundation announcement ([link](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation))

> "The leaked code revealed references to an unreleased autonomous agent mode called KAIROS that includes a /dream skill for nightly memory distillation." — Coverage of the Claude Code npm leak ([link](https://alex000kim.com/posts/2026-03-31-claude-code-source-leak/))
