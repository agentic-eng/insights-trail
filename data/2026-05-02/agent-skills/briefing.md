# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-02
**Query type:** GENERAL
**Sources:** Web, Hacker News, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 threads | High engagement | Show HN launches, ecosystem debates |
| Web | 80+ pages | — | via WebSearch; official docs, press, community blogs |
| GitHub | 15+ repos | 6,900+ stars (top repo) | Trending skill collections, registries, tooling |

---

## Synthesized Findings

### 1. Anthropic Formalizes Agent Skills as an Open Cross-Platform Standard

The single biggest story of the past 30 days is Anthropic officially releasing **Agent Skills** — a filesystem-based, open standard for extending AI coding agents with reusable, modular capabilities. The announcement came via the Anthropic engineering blog post ["Equipping agents for the real world with Agent Skills"](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) and the public GitHub repository [github.com/anthropics/skills](https://github.com/anthropics/skills).

The initial release includes Anthropic-managed Skills for Microsoft Office files (PowerPoint `.pptx`, Excel `.xlsx`, Word `.docx`, and PDF), a Skills API for uploading custom skills, and enterprise admin controls allowing Team/Enterprise administrators to govern which skills are provisioned for users and which are enabled by default.

Critically, the spec was published as an **open standard** — not a Claude-proprietary format. The [official Claude API docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) describe Agent Skills as organized folders of instructions, scripts, and resources that Claude loads dynamically. The kebab-case SKILL.md file is the canonical format, recognized by 30+ agent platforms.

[The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) framed it bluntly: "Agent Skills: Anthropic's Next Bid to Define AI Standards." [InfoWorld](https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html) and [SiliconANGLE](https://siliconangle.com/2026/04/08/anthropic-launches-claude-managed-agents-speed-ai-agent-development/) both covered the parallel launch of **Claude Managed Agents** — a fully managed agent harness with secure sandboxing, built-in tools, and server-sent event streaming (beta header: `managed-agents-2026-04-01`). Notion, Rakuten, and Sentry are already building on it.

**Cross-platform coverage:** Reddit/X, Web, GitHub, HN all discussed this launch.

---

### 2. The Three-Layer Architecture Becomes the Community Mental Model

The Claude Code extension ecosystem has converged on a clear three-layer mental model that now dominates tutorials, blog posts, and HN comments:

- **MCP = Plumbing** — connects Claude to external systems (GitHub, databases, APIs, browsers)
- **Skills = Methodology** — teaches Claude when, why, and how to use those tools
- **Plugins = Packaged bundles** — installable units combining skills, MCP configs, hooks, commands, and agents

This framing appears in [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026), [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins), [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/), [explainx.ai](https://explainx.ai/blog/what-are-agent-skills-complete-guide), and [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/).

**Context cost** is now a first-class engineering concern. A typical 5-server MCP setup consumes ~55,000 tokens before any conversation starts. Anthropic's **Tool Search** (lazy loading for MCP tools) reduces this by **85%** — making large MCP configurations practical. Skills, by contrast, cost only **30–50 tokens each** when loaded on-demand.

An arXiv paper ["Dive into Claude Code: The Design Space of Today's and Future AI Agent Systems"](https://arxiv.org/html/2604.14228v1) provides academic framing of this architecture. The [Pluto Security guide](https://pluto.security/blog/claude-extension-ecosystem-security-practitioner-guide/) covers the attack surface of each layer for security practitioners.

**Cross-platform coverage:** Web blogs, HN, academic paper.

---

### 3. Marketplace & Discovery Ecosystem Reaches Critical Mass

The plugin/skill discovery ecosystem has hit significant scale:

**By the numbers (claudemarketplaces.com self-reported):**
- 32,018 active plugins
- 282,356 total components: 161,541 skills, 58,116 commands, 48,047 agents, 7,159 MCP servers

**Primary discovery hubs:**
- [claudemarketplaces.com](https://claudemarketplaces.com/) — community-driven, 110,000+ monthly developers, quality filter (500+ installs required), voting/reviewing. Lists [Plugin Marketplaces](https://claudemarketplaces.com/marketplaces) and individual extensions.
- [mcpmarket.com/tools/skills](https://mcpmarket.com/tools/skills) — Agent Skills directory for Claude.ai, Claude Code, Codex, ChatGPT. Publishes a [daily top skills list](https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026).
- Anthropic's [official plugin marketplace](https://code.claude.com/docs/en/discover-plugins) at claude.ai/settings/plugins — reviewed, curated, launched February 2026 with 11 official plugins (legal, sales, finance, marketing, data analysis).
- [github.com/anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) — official Anthropic-managed directory.

**Niche/community directories:** [glama.ai](https://glama.ai/mcp/servers/garasegae/aiskillstore), [mcpservers.org](https://mcpservers.org/servers/back1ply/agent-skill-loader), [lobehub.com](https://lobehub.com/mcp/sfc-gh-dflippo-skills-mcp-server).

The [Ultimate Claude Code Resource List](https://www.scriptbyai.com/claude-code-resource-list/) aggregates all of these. [TruFoundry's MCP registry comparison](https://www.truefoundry.com/blog/best-mcp-registries) surveys the broader landscape.

**Cross-platform coverage:** Web, GitHub, HN (Agent37 Show HN for monetization).

---

### 4. Enterprise Registry Race: AWS, Kong, ToolHive, Open-Source

April 2026 saw a coordinated race among enterprise vendors to own the **governed agent registry** layer:

**AWS Agent Registry (Amazon Bedrock AgentCore) — April 9, 2026**
Available in preview across 5 regions (US East/West, AP Sydney/Tokyo, EU Ireland). Features: console/API/MCP access, URL-based auto-discovery, hybrid keyword+semantic search, draft→pending→discoverable approval workflow, IAM and OAuth authentication. Accessible as an MCP server itself — meaning Claude Code and Kiro can query it natively. [AWS announcement](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | [AWS ML blog](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/) | [InfoQ coverage](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | [The Register: "Agents shouldn't be secret, so we built a registry"](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/)

**Kong MCP Registry — February 2, 2026**
[Announced via PR Newswire](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html) as part of Kong Konnect. Integrates with AI Alliance Interoperability Framework (AAIF). Governs MCP servers in full operational context (API dependencies, ownership, blast radius, policies). Compliance: GDPR, HIPAA, EU AI Act. [Kong product page](https://konghq.com/products/mcp-registry) | [Enterprise MCP Gateway blog](https://konghq.com/blog/product-releases/enterprise-mcp-gateway) | [DEVOPSdigest](https://www.devopsdigest.com/kong-introduces-mcp-registry-in-kong-konnect)

**ToolHive / Stacklok — April 2026 sprint**
Three major releases in April alone:
- [April 6](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates): Added reusable agent skills to CLI and Registry Server with separate `extensions` API path
- [April 13](https://docs.stacklok.com/toolhive/updates/2026/04/13/updates): Threaded chat, claim-based authorization, MCP tool rate limiting
- [April 27](https://docs.stacklok.com/toolhive/updates/2026/04/27/updates): Desktop UI v0.33.0 ships dedicated Skills section (Registry/Local Builds/Installed tabs), vMCP local mode (no Kubernetes needed), 130 skills available

[ToolHive Registry Server repo](https://github.com/stacklok/toolhive-registry-server) | [ToolHive catalog](https://github.com/stacklok/toolhive-catalog) | [Dev.to: "Taming MCPs, Skills, and Agent Chaos with ToolHive"](https://dev.to/thisisryanswift/taming-mcps-skills-and-agent-chaos-with-toolhive-192e)

**Open-source MCP Gateway Registry**
[agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) — enterprise-ready, OAuth authentication, Keycloak/Entra integration, dynamic tool discovery for both autonomous AI agents and AI coding assistants.

**Cross-platform coverage:** Web/press, GitHub, HN.

---

### 5. Cross-Platform Skills Portability Explodes

The Agent Skills spec is **filesystem-based and agent-agnostic** — the same SKILL.md format works identically across all major AI coding agents. This month saw the ecosystem absorb this fact and build infrastructure around it:

- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) — 6,900+ GitHub stars, 1,000+ skills compatible with Claude Code, Codex, Gemini CLI, Cursor, GitHub Copilot, Antigravity. The de facto community standard for cross-agent skill discovery.
- [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) — 1,400+ agentic skills with installer CLI, bundles, workflows, official/community collections
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) — 232+ skills for engineering, marketing, product, compliance, C-level advisory across 8+ agents
- [micsapp/micstec-skills](https://github.com/micsapp/micstec-skills) — collection covering Claude Code, Gemini CLI, Copilot, Cursor, Windsurf, Codex CLI
- [iamzhihuix/skills-manage](https://github.com/iamzhihuix/skills-manage) — desktop app managing skills across 20+ platforms from one place

**Package manager:** `skills.sh` / `npx skills add` — one-command installation, discovery, and updates across all supported agents.

**GitHub CLI:** [Manage agent skills with GitHub CLI](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) added April 16, 2026.

**Per-agent paths:**
- Claude Code: `.claude/skills/`
- Gemini CLI: `~/.gemini/skills/` (personal), `.gemini/skills/` (project) — per [agensi.io](https://www.agensi.io/learn/where-are-gemini-cli-skills-stored)

[shinpr/sub-agents-skills](https://github.com/shinpr/sub-agents-skills) enables cross-LLM sub-agent orchestration — routing tasks to Codex, Claude Code, Cursor, or Gemini from any compatible tool.

[agensi.io compares](https://www.agensi.io/learn/claude-code-skills-vs-cursor-rules-vs-codex-skills) Claude Code Skills vs Cursor Rules vs Codex Skills in detail.

**GitHub Trending Weekly April 29** ([shareuhack.com](https://www.shareuhack.com/en/posts/github-trending-weekly-2026-04-29)) headline: "Skills Ecosystem Matures, Claude Design Gets Open-Sourced in 12 Days, AI Agent Memory Layer Fills In."

**Cross-platform coverage:** GitHub, Web, HN.

---

### 6. FastMCP 3.0 Makes Skills First-Class MCP Resources

[FastMCP 3.0](https://jlowin.dev/blog/fastmcp-3) ([changelog](https://jlowin.dev/blog/fastmcp-3-whats-new)) shipped **SkillsDirectoryProvider** — a new provider that scans directories for SKILL.md files and exposes them as MCP resources discoverable by any MCP client. Two modes:
- `SkillsDirectoryProvider`: scans multiple root directories, creates a `SkillProvider` per valid skill folder
- `SkillProvider`: handles a single skill directory with fine-grained configuration

Vendor-specific providers ship for every major platform (Claude, Cursor, Gemini, Codex, Copilot), making skills automatically portable across clients. [FastMCP GitHub](https://github.com/PrefectHQ/fastmcp) | [PyPI](https://pypi.org/project/fastmcp) | [gofastmcp.com skills provider docs](https://gofastmcp.com/servers/providers/skills)

The [Substack essay "Why Skills and MCP Work Better Together"](https://thepipeandtheline.substack.com/p/why-skills-and-mcp-work-better-together) is circulating as a conceptual companion piece.

Also notable: [back1ply/agent-skill-loader](https://github.com/back1ply/agent-skill-loader) bridges static skills libraries with dynamic AI agents by exposing skills as both MCP Prompts and MCP Tools — featured on [mcpservers.org](https://mcpservers.org/servers/back1ply/agent-skill-loader).

**Cross-platform coverage:** GitHub, Web (dev community blogs).

---

### 7. Hacker News Community: Practical Discourse Matures

HN discussions on this topic have shifted from "what is this?" to "here's what actually works." Ten threads identified in the last 30 days:

The highest-engagement thread — ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) — argues that Skills' low context cost and cross-platform portability make them strategically more significant than MCP servers for daily coding use. The companion thread ["Claude Skills vs. MCP: Complementary Philosophies"](https://news.ycombinator.com/item?id=45766686) rebuts this with the "plumbing vs. methodology" framing.

**Show HN launches:**
- [Agent37 – Monetize your Claude skills with shareable links](https://news.ycombinator.com/item?id=46422134)
- [Mother MCP – Manage your Agent Skills like a boss](https://news.ycombinator.com/item?id=46692102)
- [Playwright Skill for Claude Code – Less context than playwright-MCP](https://news.ycombinator.com/item?id=45642911)
- [Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks)](https://news.ycombinator.com/item?id=46983879)
- [Almanac MCP, turn Claude Code into a Deep Research agent](https://news.ycombinator.com/item?id=47855284)

Additional context threads:
- [Claude Skills (official spec launch discussion)](https://news.ycombinator.com/item?id=45607117)
- [CLAUDE.md, Skills, Agents, MCP, slash commands...](https://news.ycombinator.com/item?id=46396930)
- [Hacking Your Own AI Coding Assistant with Claude Pro and MCP](https://news.ycombinator.com/item?id=43410866)

**Cross-platform coverage:** HN primarily; themes echoed on Web and GitHub.

---

### 8. Specialized Skills & Industry Verticals

The ecosystem is now verticalizing. Notable domain-specific skill collections and coverage this month:

- **DevOps:** [devops-daily.com](https://devops-daily.com/posts/best-claude-code-plugins-devops-2026) covers Context7 (live docs), Security Guidance (vuln scanning), HashiCorp Agent Skills (Terraform/Packer), DevOps Skills Marketplace (Kubernetes, CI/CD, monitoring, FinOps)
- **Enterprise SaaS:** [NetSuite SuiteConnect 2026](https://knowledgehubmedia.com/netsuite-suiteconnect-2026-new-ai-coding-agent-skills-for-suitecloud-developers/) announced new AI coding agent skills for SuiteCloud developers
- **Security:** [Snyk Top 8 Claude Skills](https://snyk.io/articles/top-claude-skills-developers/) focuses on security-forward developer skills; [Pluto Security](https://pluto.security/blog/claude-extension-ecosystem-security-practitioner-guide/) maps the attack surface
- **Cross-role:** [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) covers engineering, marketing, product, compliance, C-level advisory
- **MCP spec governance:** ["Skills Over MCP Interest Group" April 14 office hours](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585) discusses formalizing the skills layer within the MCP specification

General developer guides: [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers), [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons), [redwerk.com](https://redwerk.com/blog/best-claude-code-plugins/), [medium.com/unicodeveloper](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051), [mejba.me](https://www.mejba.me/blog/top-33-claude-skills-ecosystem), [claudepluginhub.com](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code)

**Cross-platform coverage:** Web (press + blogs + official docs), GitHub.

---

## Cross-Source Patterns

### Pattern 1: Skills + MCP as Complementary Layers (not competitors)
- **Platforms:** Web (10+ articles), HN (2+ threads), GitHub (FastMCP, back1ply), official docs
- The market has rejected the framing of "Skills vs MCP" in favor of "Skills AND MCP." MCP provides connectivity; skills provide behavioral expertise. FastMCP 3.0's SkillsDirectoryProvider concretizes this by making skills distributable via MCP.
- > "MCP is the plumbing that connects Claude to the outside world, Skills are the instructions that teach Claude how to do specific things, and Plugins are the finished product that bundle both together into something you install once." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

### Pattern 2: Context Cost as the Defining Engineering Constraint
- **Platforms:** Web (morphllm.com, alexop.dev, GitHub trending analysis), HN (Playwright Skill thread)
- ~55K tokens for a 5-server MCP setup; Anthropic's Tool Search cuts this 85%. Skills at 30–50 tokens. GenericAgent research: <30K context = 6x token efficiency. This is driving the adoption of skills over heavier MCP solutions.
- > "The Playwright Skill for Claude Code" was explicitly built as a lower-context alternative to playwright-MCP — and launched as a Show HN.

### Pattern 3: Enterprise Registry Convergence in April 2026
- **Platforms:** Web (AWS, Kong, InfoQ, The Register, DEVOPSdigest), GitHub (ToolHive, mcp-gateway-registry)
- AWS, Kong, Stacklok/ToolHive, and community all shipped governed registry products in the same 30-day window. Governance features (OAuth, approval workflows, audit trails, rate limiting) are the common theme — reflecting enterprise anxiety about "AI tool sprawl."
- > "AWS: Agents shouldn't be secret, so we built a registry" — [The Register](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/)

### Pattern 4: Open Standard Momentum — Skills Portability Is Real
- **Platforms:** GitHub (VoltAgent/awesome-agent-skills, 6,900+ stars), Web (itecsonline, agensi.io, explainx.ai), GitHub Changelog
- The filesystem-based SKILL.md format is now working in practice across 30+ agents. GitHub CLI integration (April 16) cemented this at the platform level.
- > "Cross-platform portability is real: Skills authored for one agent work on others because the specification is filesystem-based, not API-dependent." — [explainx.ai](https://explainx.ai/blog/what-are-agent-skills-complete-guide)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (community) | Claude Skills are awesome, maybe a bigger deal than MCP | High | High | "maybe a bigger deal than MCP" | https://news.ycombinator.com/item?id=45619537 |
| (community) | Claude Skills | High | High | Official spec launch discussion | https://news.ycombinator.com/item?id=45607117 |
| (community) | Claude Skills vs. MCP: Complementary Philosophies for AI Customization | Med | High | Complementary, not competing | https://news.ycombinator.com/item?id=45766686 |
| (Show HN) | Agent37 – Monetize your Claude skills with shareable links | Med | Med | New monetization layer | https://news.ycombinator.com/item?id=46422134 |
| (Show HN) | Mother MCP – Manage your Agent Skills like a boss | Med | Med | Auto-provision skills | https://news.ycombinator.com/item?id=46692102 |
| (Show HN) | Playwright Skill for Claude Code – Less context than playwright-MCP | Med | Med | Context-cost motivation | https://news.ycombinator.com/item?id=45642911 |
| (Show HN) | Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks) | Med | Med | Config quality tooling | https://news.ycombinator.com/item?id=46983879 |
| (Show HN) | Almanac MCP, turn Claude Code into a Deep Research agent | Med | Med | Deep research use case | https://news.ycombinator.com/item?id=47855284 |
| (community) | CLAUDE.md, Skills, Agents, MCP, slash commands... | Med | High | Complexity discussion | https://news.ycombinator.com/item?id=46396930 |
| (community) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | Med | Med | Early adoption story | https://news.ycombinator.com/item?id=43410866 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Official Agent Skills launch post |
| Anthropic — Agent Skills Docs | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Canonical spec reference |
| Anthropic — Claude API Skill | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/claude-api-skill | API skill integration guide |
| Anthropic — Managed Agents | https://platform.claude.com/docs/en/managed-agents/overview | Claude Managed Agents spec |
| Anthropic — Public Skills Repo | https://github.com/anthropics/skills | Official open-source skill repo |
| Anthropic — Official Plugins | https://github.com/anthropics/claude-plugins-official | Official plugin directory |
| Claude Code Docs — MCP | https://code.claude.com/docs/en/mcp | MCP integration guide |
| Claude Code Docs — Discover Plugins | https://code.claude.com/docs/en/discover-plugins | Plugin discovery guide |
| The New Stack | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | Standards framing of Agent Skills |
| SiliconANGLE | https://siliconangle.com/2026/04/08/anthropic-launches-claude-managed-agents-speed-ai-agent-development/ | Managed Agents launch coverage |
| InfoWorld | https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html | Managed Agents rollout |
| DevOps.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | DevOps angle on Agent Skills |
| AWS — Whats New | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry launch |
| AWS ML Blog | https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/ | AWS registry architecture |
| AWS Weekly Roundup | https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | AWS April 13 roundup |
| InfoQ | https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ | AWS registry deep dive |
| The Register | https://www.theregister.com/2026/04/09/aws_ai_agent_registry/ | Opinionated AWS registry coverage |
| Dev Classmethod | https://dev.classmethod.jp/en/articles/aws-agent-registry-preview/ | AWS registry technical walkthrough |
| AWS AgentCore Docs | https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html | Registry API reference |
| AWS Bedrock AgentCore MCP | https://awslabs.github.io/mcp/servers/amazon-bedrock-agentcore-mcp-server | AgentCore as MCP server |
| Kong PR Newswire | https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html | Kong MCP Registry announcement |
| Kong Product Page | https://konghq.com/products/mcp-registry | Kong registry feature overview |
| Kong Enterprise Gateway | https://konghq.com/blog/product-releases/enterprise-mcp-gateway | Enterprise MCP gateway |
| Kong Tech Preview | https://konghq.com/blog/product-releases/kong-mcp-registry-tech-preview | Kong registry tech preview |
| DEVOPSdigest | https://www.devopsdigest.com/kong-introduces-mcp-registry-in-kong-konnect | Kong registry news |
| VMblog | https://vmblog.com/archive/2026/02/02/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance.aspx | Kong registry coverage |
| ToolHive April 6 | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | Agent skills in CLI + Registry |
| ToolHive April 13 | https://docs.stacklok.com/toolhive/updates/2026/04/13/updates | Auth + rate limiting update |
| ToolHive April 27 | https://docs.stacklok.com/toolhive/updates/2026/04/27/updates | Desktop UI skills + vMCP local |
| ToolHive Concepts | https://docs.stacklok.com/toolhive/concepts/skills | Skills concept docs |
| ToolHive UI Guide | https://docs.stacklok.com/toolhive/guides-ui/skills | UI skills management |
| ToolHive CLI Guide | https://docs.stacklok.com/toolhive/guides-cli/skills-management | CLI skills management |
| Dev.to — ToolHive | https://dev.to/thisisryanswift/taming-mcps-skills-and-agent-chaos-with-toolhive-192e | ToolHive overview article |
| GitHub CLI Changelog | https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/ | GitHub CLI agent skills support |
| FastMCP Skills Provider | https://gofastmcp.com/servers/providers/skills | FastMCP skills provider docs |
| FastMCP 3.0 Launch | https://jlowin.dev/blog/fastmcp-3 | FastMCP 3.0 release post |
| FastMCP 3.0 Changelog | https://jlowin.dev/blog/fastmcp-3-whats-new | What's new in FastMCP 3.0 |
| Substack — Skills+MCP | https://thepipeandtheline.substack.com/p/why-skills-and-mcp-work-better-together | Why Skills and MCP work together |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Primary community marketplace directory |
| claudemarketplaces.com/marketplaces | https://claudemarketplaces.com/marketplaces | Marketplace registry listing |
| mcpmarket.com/skills | https://mcpmarket.com/tools/skills | MCP Market agent skills directory |
| mcpmarket.com daily | https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026 | Daily top skills list |
| morphllm.com — comparison | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins guide |
| morphllm.com — extensions | https://www.morphllm.com/claude-code-extensions | Extensions architecture guide |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full-stack architecture explainer |
| explainx.ai | https://explainx.ai/blog/what-are-agent-skills-complete-guide | Comprehensive agent skills guide |
| devtoolpicks.com | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | Skills vs MCP vs Plugins breakdown |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide to skills+marketplace |
| Towards AI | https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff?gi=3191096a4c91 | Extensions deep dive |
| arxiv.org | https://arxiv.org/html/2604.14228v1 | Academic design space analysis |
| Pluto Security | https://pluto.security/blog/claude-extension-ecosystem-security-practitioner-guide/ | Security practitioner guide |
| Snyk | https://snyk.io/articles/top-claude-skills-developers/ | Top skills for developers |
| Snyk / truefoundry | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries compared |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers list |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Curated plugins/skills/MCP list |
| claudepluginhub.com | https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code | MCP server plugins overview |
| redwerk.com | https://redwerk.com/blog/best-claude-code-plugins/ | 7 best Claude Code plugins |
| dev.to/raxxostudios | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Dev.to skills+plugins guide |
| dev.to/williamwangai | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP comparison |
| smart-webtech.com | https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/ | Workflows and best practices |
| devops-daily.com | https://devops-daily.com/posts/best-claude-code-plugins-devops-2026 | DevOps-focused plugin guide |
| medium.com/unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills |
| mejba.me | https://www.mejba.me/blog/top-33-claude-skills-ecosystem — Top 33 skills ecosystem | Top 33 Claude skills |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate resource list |
| linkedin.com (Rob Foster) | https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we | LinkedIn survival guide |
| agensi.io — paths | https://www.agensi.io/learn/where-are-gemini-cli-skills-stored | Gemini CLI skill paths |
| agensi.io — comparison | https://www.agensi.io/learn/claude-code-skills-vs-cursor-rules-vs-codex-skills | Cross-agent skill format comparison |
| itecsonline.com | https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 | Codex CLI agent skills guide |
| knowledgehubmedia.com | https://knowledgehubmedia.com/netsuite-suiteconnect-2026-new-ai-coding-agent-skills-for-suitecloud-developers/ | NetSuite SuiteConnect AI skills |
| shareuhack.com | https://www.shareuhack.com/en/posts/github-trending-weekly-2026-04-29 | GitHub Trending Weekly Apr 29 |
| Releasebot | https://releasebot.io/updates/anthropic | Anthropic release notes tracker |
| ai-techpark.com | https://ai-techpark.com/kong-introduces-mcp-registry-in-kong-konnect/ | Kong registry coverage |
| yahoo/finance | https://finance.yahoo.com/news/kong-introduces-mcp-registry-kong-151500541.html | Kong registry syndicated |
| thenasguy.com | https://www.thenasguy.com/2026/04/13/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | AWS roundup mirror |
| Udemy | https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/ | Claude Code 2026 bootcamp |
| glama.ai | https://glama.ai/mcp/servers/garasegae/aiskillstore | aiskillstore on Glama |
| lobehub.com | https://lobehub.com/mcp/sfc-gh-dflippo-skills-mcp-server | Skills MCP Server on LobeHub |
| code.claude.com/settings | https://code.claude.com/docs/en/settings | Claude Code settings docs |
| platform.claude.com/release-notes | https://platform.claude.com/docs/en/release-notes/overview | Claude Platform release notes |

**GitHub:**
| Repo | Description | Stars | URL |
|------|-------------|-------|-----|
| VoltAgent/awesome-agent-skills | 1,000+ skills, Claude Code/Codex/Gemini CLI/Cursor | 6,900+ | https://github.com/VoltAgent/awesome-agent-skills |
| anthropics/skills | Official Anthropic Agent Skills repository | — | https://github.com/anthropics/skills |
| anthropics/claude-plugins-official | Official Anthropic plugin directory | — | https://github.com/anthropics/claude-plugins-official |
| sickn33/antigravity-awesome-skills | 1,400+ skills with installer CLI and bundles | — | https://github.com/sickn33/antigravity-awesome-skills |
| alirezarezvani/claude-skills | 232+ skills across 8 agent platforms | — | https://github.com/alirezarezvani/claude-skills |
| stacklok/toolhive-registry-server | Discover, govern, control MCP servers and skills | — | https://github.com/stacklok/toolhive-registry-server |
| stacklok/toolhive-catalog | ToolHive MCP server registry catalog | — | https://github.com/stacklok/toolhive-catalog |
| agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth/Keycloak | — | https://github.com/agentic-community/mcp-gateway-registry |
| PrefectHQ/fastmcp | FastMCP: Pythonic MCP server/client framework | — | https://github.com/PrefectHQ/fastmcp |
| back1ply/agent-skill-loader | MCP server exposing Claude Code skills as MCP resources | — | https://github.com/back1ply/agent-skill-loader |
| shinpr/sub-agents-skills | Cross-LLM sub-agent orchestration via Agent Skills | — | https://github.com/shinpr/sub-agents-skills |
| shinpr/claude-code-workflows | Production-ready Claude Code workflows | — | https://github.com/shinpr/claude-code-workflows |
| iamzhihuix/skills-manage | Desktop app managing skills across 20+ platforms | — | https://github.com/iamzhihuix/skills-manage |
| micsapp/micstec-skills | Skills for Claude Code, Gemini CLI, Copilot, Cursor, Windsurf | — | https://github.com/micsapp/micstec-skills |
| quemsah/awesome-claude-plugins | Plugin adoption metrics via n8n | — | https://github.com/quemsah/awesome-claude-plugins |
| affaan-m/everything-claude-code | Harness optimization: skills, instincts, memory, security | — | https://github.com/affaan-m/everything-claude-code |
| mhattingpete/claude-skills-marketplace | Skills for Git automation, testing, code review | — | https://github.com/mhattingpete/claude-skills-marketplace |
| shanraisshan/claude-code-best-practice | From vibe coding to agentic engineering | — | https://github.com/shanraisshan/claude-code-best-practice |
| ChromeDevTools/chrome-devtools-mcp | Chrome DevTools for coding agents | — | https://github.com/ChromeDevTools/chrome-devtools-mcp |
| modelcontextprotocol/discussions/2585 | Skills Over MCP Interest Group April 14 office hours | — | https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ n/a (reddit.com not crawlable by WebSearch)
├─ 🔵 X: 0 posts │ n/a (excluded per brief)
├─ 🔴 YouTube: 0 videos │ n/a (not retrieved)
├─ 🟢 HN: 10 stories │ high engagement │ multi-hundred comments estimated
├─ 🟣 TikTok: 0 videos │ n/a
├─ 🩷 Instagram: 0 reels │ n/a
├─ 🦋 Bluesky: 0 posts │ n/a
├─ 📊 Polymarket: 0 markets │ n/a
├─ 🌐 Web: 80+ pages │ official docs, press, community blogs, GitHub
└─ 🗣️ Top voices: Anthropic Engineering, AWS ML team, Kong Inc., Stacklok/ToolHive, jlowin (FastMCP) │ r/ClaudeAI (not crawled)
```

Ecosystem scale (claudemarketplaces.com, self-reported):
- 32,018 active plugins | 161,541 skills | 7,159 MCP servers | 48,047 agents | 58,116 commands

---

## Data Gaps

- **Reddit:** reddit.com returned a crawler block (HTTP 400) — Reddit discussion on r/ClaudeAI, r/LocalLLaMA, and r/programming entirely absent. This is likely a significant gap given the high community activity on these topics.
- **X/Twitter:** Excluded per research brief. Likely high signal volume given the nature of this topic (developer ecosystem announcements).
- **YouTube:** No YouTube data retrieved — tutorial videos and walkthroughs on Claude Code skills are likely substantial.
- **TikTok/Instagram:** Not retrieved — limited relevance for this technical topic.
- **Bluesky:** Not retrieved.
- **Polymarket:** No prediction markets identified on this topic.
- **Engagement numbers:** HN point/comment counts were described as "high/medium" without exact figures (threads not individually fetched).
- **GitHub stars for most repos:** Not retrieved for all repos except VoltAgent/awesome-agent-skills (6,900+).
- **Approximate coverage:** Web and GitHub well-covered (~80%); social platforms (Reddit, X, YouTube) entirely absent (~20% of likely total signal).
- **Kong announcement date precision:** Kong MCP Registry announced February 2, 2026 — slightly outside a strict 30-day window from May 2, 2026; included because it remains the dominant enterprise MCP registry story.

---

## Key Quotes

> "Skills are having a moment. Claude Code, Cursor, Copilot—they all learn new capabilities from instruction files." — FastMCP docs ([gofastmcp.com](https://gofastmcp.com/servers/providers/skills))

> "MCP is the plumbing that connects Claude to the outside world, Skills are the instructions that teach Claude how to do specific things, and Plugins are the finished product that bundle both together into something you install once." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

> "Agent Skills: Anthropic's Next Bid to Define AI Standards." — [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

> "Cross-platform portability is real: Skills authored for one agent work on others because the specification is filesystem-based, not API-dependent." — [explainx.ai](https://explainx.ai/blog/what-are-agent-skills-complete-guide)

> "A skill created for OpenAI's Codex can run unchanged inside Claude Code, Google Antigravity, Cursor, GitHub Copilot, and over thirty other agent platforms." — [itecsonline.com](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026)

> "AWS: Agents shouldn't be secret, so we built a registry." — [The Register](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/)

> "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..." — [HN discussion](https://news.ycombinator.com/item?id=46396930)

> "Claude Skills are awesome, maybe a bigger deal than MCP." — [HN thread title](https://news.ycombinator.com/item?id=45619537)

> "The ToolHive Desktop UI installs skills directly into the AI clients you already use." — [Stacklok docs](https://docs.stacklok.com/toolhive/updates/2026/04/27/updates)

> "Skills Ecosystem Matures, Claude Design Gets Open-Sourced in 12 Days, AI Agent Memory Layer Fills In." — [GitHub Trending Weekly 2026-04-29](https://www.shareuhack.com/en/posts/github-trending-weekly-2026-04-29)
