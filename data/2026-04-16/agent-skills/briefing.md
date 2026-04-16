# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-04-16
**Query type:** GENERAL
**Sources:** Hacker News, Web, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | ~referenced | ~4,200 weekly contributors r/ClaudeCode | No direct threads surfaced; referenced via aggregated sources |
| Hacker News | 9 stories | 99 points (3 stories fully counted), 36 comments | Skills, MCP, plugin tooling discussions |
| YouTube | ~25 videos referenced | 853K+ views (top viral demo) | Via ranking roundup article |
| Web | 45+ pages | — | Dev blogs, official docs, news, GitHub repos |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: From Anthropic Internal to Cross-Industry Bedrock

The most structurally significant development of the past 30 days is the maturation of the SKILL.md standard from Anthropic's internal format into a Linux Foundation–governed open standard. Anthropic published the original engineering post on October 16, 2025 ("Equipping agents for the real world with Agent Skills") and released the spec as a formal open standard on December 18, 2025. The spec was donated to the newly formed **Agentic AI Foundation (AAIF)**, a Linux Foundation–backed alliance, making it vendor-neutral governance.

The SKILL.md format is technically elegant: a directory-based structure centered on a single Markdown file with YAML frontmatter (`name`, `description`), supporting three tiers of progressive disclosure — metadata loads at agent startup, full content loads only when relevant, and supplementary files load on demand. An experimental `allowed-tools` field enables sandboxed script execution (Python, Bash) without loading code into the context window. This design lets agents carry unbounded skill libraries without context budget pressure.

**Adoption breadth is remarkable:** OpenAI adopted the same format for Codex CLI and ChatGPT (testing a "Skills Editor" for exporting Custom GPTs to the open format), Microsoft integrated it into VS Code as "Golden Skills", and Salesforce and Atlassian positioned it as a path away from vendor lock-in. Claude Code introduced skills as markdown files; GitHub Copilot adopted them; OpenAI Codex, Cursor, JetBrains Junie, and 30+ other tools followed.

Sources: [Anthropic engineering blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [Agent Skills open standard announcement](https://markets.financialcontent.com/wral/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability) · [Official Anthropic skills repo](https://github.com/anthropics/skills) · [Agent Skills API docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Claude Code skills docs](https://code.claude.com/docs/en/skills) · [What are Skills? (Help Center)](https://support.claude.com/en/articles/12512176-what-are-skills) · [First Principles Deep Dive](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/)

Cross-platform discussion: Hacker News, Web

---

### 2. Marketplace Explosion: Six Ecosystems in 28 Days (February 2026)

February 2026 saw an unprecedented wave of agent marketplace launches — six major ecosystems in 28 days, none of them interoperating:

1. **OpenAI Frontier** (Feb 5): Treats AI agents like employees with onboarding, shared business context, identity governance, and performance feedback. Early customers: HP, Intuit, Oracle, State Farm, Thermo Fisher, Uber. Formalized Frontier Alliances with McKinsey, BCG, Accenture, and Capgemini on Feb 23.

2. **Anthropic Cowork & Plugins for Enterprise** (Feb 24): Private marketplace for enterprise admins; 13 enterprise plugins across HR, investment banking, engineering, and design; 12 new MCP connectors (Google Workspace, DocuSign, FactSet, S&P Global). Kate Jensen, Head of Americas, acknowledged the reset candidly: *"2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature."*

3. **Perplexity Computer** (Feb 27): Multi-model orchestrator coordinating 19 AI models — Claude Opus 4.6 for reasoning/coding, Gemini for research, GPT-5.2 for long-context, Grok for speed. $200/month Perplexity Max tier. Sub-agents run in isolated compute environments.

4. **Superhuman Agent Store** (Feb 23): Partner agents from Box, Gamma, and Wayground. Email-focused distribution.

5. **Google Cloud AI Agent Marketplace** (expanded): Validated agents from ecosystem partners with Cloud Marketplace billing integration.

6. **Oracle AI Agent Marketplace**: Targets Fusion Apps users; agent templates from Infosys, IBM Consulting, KPMG, Box, and Stripe.

Then on **March 6, 2026**, Anthropic launched the **Claude Marketplace** — an enterprise app store where customers with Anthropic spending commitments can apply portions toward third-party tools. Initial 6 partners: Snowflake, GitLab, Harvey AI, Rogo, Replit, and Lovable Labs. Critically: Anthropic takes no commission. A companion **Claude Partner Network** (announced March 12) commits $100M to ecosystem support with a 5x scale-up in partner-facing headcount and a Claude Certified Architect exam.

The core frustration across all six: **none of them interoperate**. A skill built for Anthropic's Cowork is invisible to OpenAI Frontier.

Sources: [Six marketplaces in 28 days](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days) · [Claude Marketplace launch (SiliconAngle)](https://siliconangle.com/2026/03/06/anthropic-launches-claude-marketplace-third-party-cloud-services/) · [VentureBeat on Claude Marketplace](https://venturebeat.com/technology/anthropic-launches-claude-marketplace-giving-enterprises-access-to-claude) · [Claude Marketplace page](https://claude.com/platform/marketplace) · [Claude Partner Network $100M](https://openclawai.io/blog/claude-partner-network-100m-enterprise-channel/) · [Enterprise marketplace review](https://aitoolbriefing.com/blog/claude-marketplace-enterprise-review-2026/) · [Anthropic vs OpenAI vs Google agent strategies](https://www.mindstudio.ai/blog/anthropic-vs-openai-vs-google-agent-strategy)

Cross-platform: Web, Hacker News

---

### 3. The Community Skill Ecosystem: Scale and Fragmentation

The open SKILL.md standard has spawned a sprawling community marketplace ecosystem, with platforms competing on scale, discovery UX, and trust:

- **SkillsMP** (skillsmp.com): Claims the largest catalog — 800,000+ skills with intelligent filtering by occupation, author, and popularity. Smart search, quality indicators.
- **LobeHub Skills** (lobehub.com/skills): 169,739 skills indexed; emphasis on trust and packaging.
- **agentskill.sh**: 110,000+ skills across 20+ AI tools including Claude Code, Cursor, Copilot, Windsurf, and Zed.
- **skills.sh** (Vercel): Launched January 2026. 44k+ skills directory with two-layer security scanning, `/learn` installer, and `npx skills` CLI supporting 43+ agents. Installation: `npx skills add vercel-labs/agent-skills`.
- **agentskills.io**: The "npm or pip" of agent capabilities. Grew from 0 to 100+ community skills in weeks after Hermes Agent's March 12 public launch.
- **MCP.so**: 20,067 MCP Servers collected (third-party aggregator).
- **MCP Market** (mcpmarket.com): Connects Claude and Cursor to tools like Figma, Databricks, Storybook, and Ghidra. 318 MCPs built specifically for Claude.
- **Claude Marketplaces** (claudemarketplaces.com): Largest directory of Claude Code extensions, sorted by installs and GitHub stars.
- **Awesome Claude Code** (GitHub, hesreallyhim): 38,700+ stars — community curated skills, hooks, slash-commands, orchestrators.
- **CCPI marketplace** (jeremylongshore): 340 plugins + 1,367 agent skills with CCPI package manager (`pnpm add -g @intentsolutionsio/ccpi`).
- **OpenClaw ClawHub**: 13,729 community-built skills (AgentSkills-compatible).
- **VoltAgent awesome-agent-skills**: 1,000+ skills from official dev teams and community; **awesome-openclaw-skills**: 5,400+ OpenClaw skills.

On the community dynamics front, **Hermes Agent**'s rapid ecosystem growth offers a case study: it shipped 70+ bundled skills at launch, agentskills.io crossed 100 community contributions within weeks, driven by low barriers (YAML manifest only, no proprietary SDK), conditional activation preventing prompt bloat, and built-in sandbox safety. Community skill patterns: CLI tool wrappers (ffmpeg, pandoc), personal service integrations (Notion, Home Assistant), domain-specific helpers, model-specific features.

Sources: [SkillsMP](https://skillsmp.com) · [SkillsMP review](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) · [LobeHub Skills](https://lobehub.com/skills) · [agentskills.io](https://agentskills.io/home) · [skills.sh](https://skills.sh/) · [Vercel skills changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [vercel-labs/skills GitHub](https://github.com/vercel-labs/skills) · [Hermes ecosystem growth](https://hermesagents.net/blog/skills-and-agentskills.io/) · [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) · [CCPI marketplace](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [MCP.so](https://mcp.so/) · [mcpmarket.com](https://mcpmarket.com/) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [KDnuggets top 5 marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) · [SkillsLLM](https://skillsllm.com) · [anthropic/skills](https://github.com/anthropics/skills) · [skillmatic-ai/awesome-agent-skills](https://github.com/skillmatic-ai/awesome-agent-skills) · [VoltAgent awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) · [VoltAgent openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills)

Cross-platform: Hacker News, Web

---

### 4. Claude Code Extension Architecture: Skills vs. MCP vs. Plugins vs. Hooks

The dominant discussion topic across developer communities in April 2026 is the taxonomy confusion of Claude Code's extension stack. A recurring pattern: developers learn the four layers separately and struggle to understand when to use which.

The **canonical mental model** that's emerged in tutorials and blog posts:
- **Skills** = reusable markdown instructions (`.claude/skills/` or `.claude/commands/`); teach Claude *how* to think; no external processes; activate automatically when context is relevant. "Skills specialize the model."
- **MCP servers** = external executables exposing tools via Model Context Protocol; teach Claude *what it can reach* (databases, APIs, browsers, filesystems); persistent connections. "MCP connects it to live systems."
- **Plugins** = bundles packaging skills + MCP connectors + slash commands + sub-agents into a single installable unit; the newest layer, shipped with Claude Cowork on January 30, 2026. "Plugins are the product."
- **Hooks** = shell commands that execute at lifecycle events (pre-commit, pre-tool-use, etc.) in `.claude/settings.json`; always-on automation.

Claude Code now has four full extension types, with **Agent Teams** (February 5, 2026, alongside Opus 4.6) adding a fifth: multiple Claude instances working in parallel via git-based coordination, each claiming tasks from a shared list and merging changes continuously.

The Hacker News community has pushed back on some of the framing: mergesort characterized Skills as "the killer feature because they are a very composable tool," while fooqux dismissed "emergent behavior" framing as clickbait: "I didn't see any emergent behavior, just combining of skills (which I'll admit looks useful)."

Practical guidance from power users: keep Claude.md under 200 lines, use hierarchical files in nested directories, run 2-3 MCP servers max (MCP context can burn 30-40K tokens before work begins), and name skills in kebab-case (a common silent failure: `Review-Code` never triggers; `review-code` does).

Sources: [Claude Code Extensions guide (Morph)](https://www.morphllm.com/claude-code-extensions) · [Understanding the full stack (alexop.dev)](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [Skills vs MCP vs Plugins complete guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [DEV.to comparison guide](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) · [Claude Code plugins doc](https://code.claude.com/docs/en/plugins) · [MCP doc](https://code.claude.com/docs/en/mcp) · [Sub-agents doc](https://code.claude.com/docs/en/sub-agents) · [Agent Teams workflow guide](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md) · [5 agentic workflow patterns (MindStudio)](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns) · [Skill chaining guide (MindStudio)](https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows) · [HN: Skills Combine (92pts/33cmt)](https://news.ycombinator.com/item?id=46531794) · [HN: CLAUDE.md complexity](https://news.ycombinator.com/item?id=46396930) · [Claude Cowork guide](https://findskill.ai/blog/claude-cowork-guide/) · [DEV.to: production structure guide](https://dev.to/lizechengnet/how-to-structure-claude-code-for-production-mcp-servers-subagents-and-claudemd-2026-guide-4gjn)

Cross-platform: Hacker News, Web, Reddit (via aggregated reports)

---

### 5. April 2026: Rapid Release Cadence and Claude Managed Agents

Claude Code is in an unusually aggressive development sprint. Between mid-March and mid-April 2026, Anthropic shipped **v2.1.69 through v2.1.101 — over 30 releases in 5 weeks**:

- **April 1**: NO_FLICKER rendering engine — 74% reduction in rendering cycles
- **April 2**: Bedrock wizard for enterprise cloud setup
- **April 8**: **Claude Managed Agents** GA — fully managed agent harness at **$0.08/hour + token costs**, with secure sandboxing, built-in tools, state persistence, and SSE streaming
- **April 9**: Vertex AI wizard, Monitor tool, PID sandbox for Linux process isolation
- **April 10**: Team onboarding workflows, OS certificate authority trust
- **Write tool**: 60% faster via improved diff calculation

Claude Managed Agents is a significant architectural shift — Anthropic is now offering a hosted agent runtime, separating developers from the complexity of managing Claude Code's local process model. The HN community flagged this: "SOTA right now is the Claude Agent SDK. Package it up with some company-specific skills..." (moomooskycow).

April also brought infrastructure advances from adjacent players: Visa's Intelligent Commerce Connect (April 8) opened payment rails for autonomous agents; Microsoft's Agent Governance Toolkit (April 2) addresses all 10 OWASP agentic risks at sub-millisecond enforcement (p99 < 0.1ms).

Sources: [AI Agent News April 2026 (fazm.ai)](https://fazm.ai/blog/ai-agent-news-april-2026-claude-code-openclaw) · [Claude Code news April 2026](https://blog.mean.ceo/claude-code-news-april-2026/) · [Claude Managed Agents announcement](https://claude.com/blog/claude-managed-agents) · [Claude Code release notes (Releasebot)](https://releasebot.io/updates/anthropic/claude-code) · [Claude Code changelog](https://code.claude.com/docs/en/changelog) · [HN: Best hosted agent 2026](https://news.ycombinator.com/item?id=46917293)

Cross-platform: Hacker News, Web

---

### 6. Security: Supply Chain Risk Has Arrived for Agent Skills

The security picture for agent skills and MCP has deteriorated sharply in early 2026:

- **CVE-2025-59536**: Remote code execution via poisoned Hook in `.claude/settings.json`. Attackers inject a malicious Hook that runs at lifecycle events — a direct consequence of the Hooks feature executing arbitrary shell commands.
- **March 31, 2026**: Anthropic accidentally exposed 512,000 lines of Claude Code source via npm v2.1.88 (a 59.8 MB JavaScript source map). The security community noted this as a significant OPSEC failure for a company handling agentic workflows.
- **Antiy CERT**: Found 1,184 malicious skills across ClawHub (OpenClaw's community registry).
- **Trend Micro**: 492 MCP servers exposed to the internet with zero authentication.
- **BlueRock Security**: 36.7% of MCP servers vulnerable to server-side request forgery (SSRF).
- **State-sponsored actors** (Salt Typhoon documented): Conducting supply chain compromises injecting malicious logic into agent frameworks.
- **Pentagon**: Designated Anthropic a "supply chain risk" — first time an American company has received this classification.

The community response has been tooling: **SkillRisk.org** (free AI agent skill security scanner), **Agnix** (linting agent configs for 156 validation rules across 11 platforms, catching issues like wrong naming conventions silently breaking skills), and **claude-security-audit** skill on MCP Market. Enterprise guides from Harmonic Security, Backslash, and Straiker have emerged.

Sources: [AI Agent Security Risks 2026](https://blog.cyberdesserts.com/ai-agent-security-risks/) · [SkillRisk scanner](https://skillrisk.org/) · [Claude Code source leak (Straiker)](https://www.straiker.ai/blog/claude-code-source-leak-with-great-agency-comes-great-responsibility) · [HN: Agnix linter](https://news.ycombinator.com/item?id=46983879) · [Claude Code Security docs](https://code.claude.com/docs/en/security) · [Claude Code security best practices (Backslash)](https://www.backslash.security/blog/claude-code-security-best-practices) · [Securing Claude Cowork (Harmonic)](https://www.harmonic.security/resources/securing-claude-cowork-a-security-practitioners-guide) · [MCP governance enterprise security (Obot)](https://obot.ai/blog/claude-code-mcp-governance-enterprise-security/) · [MCP gateway registry (agentic-community)](https://github.com/agentic-community/mcp-gateway-registry)

Cross-platform: Hacker News, Web

---

### 7. MCP Registry Infrastructure: Toward Governed Tool Discovery

The Model Context Protocol registry layer is maturing. The official **MCP Registry** (registry.modelcontextprotocol.io) launched as the canonical catalog in September 2025, aiming to be the primary source of truth for publicly available MCP servers. But the ecosystem has fragmented across 12+ independent directories.

Key infrastructure developments:
- **GitHub MCP Registry**: The fastest way to discover servers; deeply integrated with GitHub's developer workflow.
- **MACH Alliance MCP Registry**: Enterprise-focused, aligned with composable architecture principles.
- **Enterprise MCP Gateway**: Centralized registries with OAuth, dynamic tool discovery, and Keycloak/Entra integration for governed access.
- **MCP Tool Search in Claude Code**: Lazy loading reduces context usage by up to 95%, allowing running many MCP servers without context budget concerns.
- **Pinterest Engineering** (March 2026): Detailed case study of building an internal MCP ecosystem at scale — multi-team, multi-service, with standardized discovery.

The dominant enterprise complaint: MCP servers are powerful but ungoverned. Trend Micro's finding (492 internet-exposed, zero-auth MCP servers) has accelerated adoption of centralized registries with authentication.

Sources: [MCP Registry announcement](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/) · [GitHub MCP Registry](https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/) · [MACH Alliance MCP Registry](https://machalliance.org/mach-alliance-mcp-registry/) · [Best MCP Registries 2026 (TrueFoundry)](https://www.truefoundry.com/blog/best-mcp-registries) · [Enterprise MCP registry guide (InfoWorld)](https://www.infoworld.com/article/4145014/how-to-build-an-enterprise-grade-mcp-registry.html) · [Pinterest MCP ecosystem](https://medium.com/pinterest-engineering/building-an-mcp-ecosystem-at-pinterest-d881eb4c16f1) · [Where to Find MCP Servers 2026](https://automationswitch.com/ai-workflows/where-to-find-mcp-servers-2026) · [50+ best MCP servers](https://claudefa.st/blog/tools/mcp-extensions/best-addons) · [MCP servers (mcpservers.org)](https://mcpservers.org/) · [Claude MCP marketplace](https://claudemarketplaces.com/mcp)

Cross-platform: Web, Hacker News

---

### 8. Real-World Usage Patterns: Power Users and Daily Workflows

The most grounded signal comes from practitioners publishing setup guides and workflow reports after months of sustained use.

**okhlopkov.com** (4-month daily use report): Three core MCPs in production — Coolify for deployment automation, Telegram for async messaging and voice-note ingestion, and a Codex MCP for dual-model code review. Three custom skills: `ton-analyst` (Dune SQL for TON blockchain), `ton-profiler` (wallet relationship graphs), and `crosspost` (publishes to Telegram, Ghost, Twitter in three languages). Total cost: $100/month Claude Max. Daily workflow: "I record a voice note in Telegram describing what I need. My server agent picks it up, reads the transcription, and starts working." Estimated savings: ~2 hours/day on analytical work.

**mergesort** on HN (workshop instructor): Skills are the killer feature because of composability. Advocates routing between skills via a "router skill" that describes how to use other skills together. Many users never touch any of this; "there are absolutely a lot of people who just download Claude Code or Cursor or Codex and dive right in."

**Reddit r/ClaudeCode community** (aggregated): 4,200+ weekly contributors. Key frustrations: Pro plan ($20/month) exhausted after ~12 heavy prompts; MCP context consumption (30-40K tokens before work begins); long-session degradation. Best practices crystallized: CLAUDE.md under 200 lines, hierarchical directory structure.

Sources: [4 months daily use report](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) · [HN: Skills Combine](https://news.ycombinator.com/item?id=46531794) · [HN: CLAUDE.md complexity](https://news.ycombinator.com/item?id=46396930) · [Claude Code Reddit aggregated](https://www.morphllm.com/claude-code-reddit) · [Claude Code 2026 daily OS (Medium)](https://medium.com/@richardhightower/claude-code-2026-the-daily-operating-system-top-developers-actually-use-d393a2a5186d) · [Survival guide (LinkedIn)](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) · [Advanced workflow guide (DEV.to)](https://dev.to/jangwook_kim_e31e7291ad98/claude-code-advanced-workflow-subagents-commands-multi-session-50hl) · [Sankalp's Claude Code 2.0 guide](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/)

Cross-platform: Hacker News, Web, Reddit

---

## Cross-Source Patterns

**Pattern 1: Skills as the composability lever**
Appearing on: Hacker News, Web (multiple dev blogs), Reddit (via aggregation)
The community has converged on Skills (SKILL.md) as the highest-leverage extension point — composable, portable, zero-dependency. "Skills are the killer feature because they are a very composable tool." (mergesort, HN) / "Agent skills are the practical answer to prompt fatigue." (multiple blog posts) / "Skills specialize the model; MCP connects it to live systems." (pervasive framing across 10+ articles)

**Pattern 2: Marketplace fragmentation as the central unsolved problem**
Appearing on: Web (agentpmt.com deep analysis), Hacker News (implicit in "interoperability" discussions), LinkedIn
Six enterprise marketplaces launched in 28 days, none interoperating. The AAIF/Linux Foundation governance layer for SKILL.md is explicitly designed to solve this, but enterprise platforms (Frontier, Cowork, Google Cloud, Oracle) have not committed to SKILL.md portability. The tension between open standard and walled gardens is live.

**Pattern 3: Security lag behind capability**
Appearing on: Web (cyberdesserts, Straiker, Backslash), Hacker News (Agnix discussion)
Agent skills and MCP adoption is outpacing security tooling. Core quotes: "I kept losing time to the same class of bug: AI tool configs that are almost right but silently wrong." (anotherCodder, HN) / "If you don't fully understand what an MCP server does, don't enable it." (security guides) / Pentagon supply chain designation signals policy-level concern.

**Pattern 4: Monetization/discovery gap for skill creators**
Appearing on: Hacker News (Agent37 Show HN), Web (multiple marketplace reviews)
Selling individual skills is structurally hard: customers must download Claude Code, configure MCP servers, trust unknown authors. Agent37 built shareable-link monetization to reduce friction. The gap between "I built a useful skill" and "I can sell it" remains wide.

**Pattern 5: Context overhead as the dominant MCP complaint**
Appearing on: Reddit (r/ClaudeCode, via aggregation), Web (morphllm.com, multiple setup guides)
MCP servers are widely praised but practically constrained by context budget. The 30-40K token burn before any work begins is a frequently cited frustration. Claude Code's MCP Tool Search (lazy loading, up to 95% context reduction) is the direct response and has reduced this complaint in recent months.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| mergesort | You've got your CLAUDE.md, Skills, Agents, MCP, slash commands... | N/A | N/A | "Skills are the killer feature because they are a very composable tool" | [link](https://news.ycombinator.com/item?id=46396930) |
| (community) | Claude Code Emergent Behavior: When Skills Combine | 92 | 33 | "I didn't see any emergent behavior, just combining of skills...Calling this emergent is click bait." — fooqux | [link](https://news.ycombinator.com/item?id=46531794) |
| (community) | Agent Skills – Open Trusted Catalog of AI Agent Skills: Claude,OpenAI,Vercel,GH | N/A | N/A | Aggregates skills from Anthropic, OpenAI, GitHub, Vercel into one auto-updating JSON catalog | [link](https://news.ycombinator.com/item?id=46692865) |
| (community) | Show HN: Agent37 – Monetize your Claude skills with shareable links | N/A | N/A | Selling skills requires customers to "download Claude Code, set up the tool, configure MCP servers" | [link](https://news.ycombinator.com/item?id=46422134) |
| anotherCodder | Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks) | 1 | 1 | "I kept losing time to the same class of bug: AI tool configs that are almost right but silently wrong." | [link](https://news.ycombinator.com/item?id=46983879) |
| moomooskycow | Ask HN: Best option for hosted agent in 2026? | 3 | 2 | "SOTA right now is the Claude Agent SDK. Package it up with some company-specific skills..." | [link](https://news.ycombinator.com/item?id=46917293) |
| (community) | Show HN: OPC Skills – 9 AI agent skills for solopreneurs (Claude Code, Cursor) | N/A | N/A | Solopreneur-focused skills bundle | [link](https://news.ycombinator.com/item?id=46730857) |
| (community) | Show HN: Claude Code skill that uses Codex as MCP server for code review | N/A | N/A | Dual-model review: Claude submits plans to Codex for independent feedback | [link](https://news.ycombinator.com/item?id=46934203) |
| (community) | Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP | N/A | N/A | Instruction-based, 314 lines, no persistent MCP server | [link](https://news.ycombinator.com/item?id=45642911) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Original SKILL.md design spec; progressive disclosure architecture; Oct 2025 publication |
| Agent Skills open standard (WRAL/TokenRing) | [link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability) | Dec 2025 open standard release; AAIF/Linux Foundation governance; OpenAI, Microsoft adoption |
| Six Marketplaces in 28 Days (agentpmt.com) | [link](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days) | Full breakdown of Feb 2026 wave: Anthropic, OpenAI, Perplexity, Superhuman, Google, Oracle |
| Claude Marketplace launch (SiliconAngle) | [link](https://siliconangle.com/2026/03/06/anthropic-launches-claude-marketplace-third-party-cloud-services/) | March 6 enterprise marketplace; 6 partners; no-commission model |
| VentureBeat on Claude Marketplace | [link](https://venturebeat.com/technology/anthropic-launches-claude-marketplace-giving-enterprises-access-to-claude) | Enterprise narrative; enterprise procurement simplification angle |
| Claude Partner Network $100M (OpenClawAI) | [link](https://openclawai.io/blog/claude-partner-network-100m-enterprise-channel/) | $100M commitment; 5x team scale-up; Certified Architect exam |
| Hermes / agentskills.io growth (hermesagents.net) | [link](https://hermesagents.net/blog/skills-and-agentskills.io/) | Community ecosystem growth case study; 70+ bundled skills at launch |
| 4-month daily use report (okhlopkov.com) | [link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | Concrete production setup: MCPs, skills, hooks, cost analysis |
| AI Agent News April 2026 (fazm.ai) | [link](https://fazm.ai/blog/ai-agent-news-april-2026-claude-code-openclaw) | April release cadence; Claude Managed Agents $0.08/hr; OpenClaw Dreaming release |
| AI Agent Security Risks 2026 (cyberdesserts) | [link](https://blog.cyberdesserts.com/ai-agent-security-risks/) | CVE-2025-59536, malicious skills, SSRF, Pentagon supply chain designation |
| Claude Code source leak (Straiker) | [link](https://www.straiker.ai/blog/claude-code-source-leak-with-great-agency-comes-great-responsibility) | March 31 npm v2.1.88 source exposure; 512K lines |
| Vercel skills changelog | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh launch Jan 2026; npx skills CLI; 43+ agent support |
| vercel-labs/skills GitHub | [link](https://github.com/vercel-labs/skills) | Open agent skills tool; official Vercel implementation |
| Awesome Claude Code (hesreallyhim) | [link](https://github.com/hesreallyhim/awesome-claude-code) | 38,700+ star community catalog; skills, hooks, slash-commands |
| CCPI Marketplace (jeremylongshore) | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 340 plugins + 1,367 skills; CCPI package manager |
| anthropics/skills | [link](https://github.com/anthropics/skills) | Official Anthropic public skills repo |
| skillmatic-ai/awesome-agent-skills | [link](https://github.com/skillmatic-ai/awesome-agent-skills) | Definitive cross-platform agent skills resource |
| VoltAgent/awesome-agent-skills | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ skills from official dev teams and community |
| VoltAgent/awesome-openclaw-skills | [link](https://github.com/VoltAgent/awesome-openclaw-skills) | 5,400+ OpenClaw skills |
| Claude Code full stack (alexop.dev) | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | MCP vs Skills vs Subagents vs Hooks technical comparison |
| Skills vs MCP complete guide (morphllm.com) | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Canonical developer decision guide |
| DEV.to: Skills vs MCP (William Wang) | [link](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Installation guides and best-of lists |
| Claude Code Reddit aggregated (morphllm) | [link](https://www.morphllm.com/claude-code-reddit) | Community sentiment; 4,200+ weekly contributors; key complaints |
| MCP Registry announcement | [link](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/) | Official MCP Registry preview |
| GitHub MCP Registry | [link](https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/) | GitHub's MCP server discovery layer |
| Pinterest MCP ecosystem (Medium) | [link](https://medium.com/pinterest-engineering/building-an-mcp-ecosystem-at-pinterest-d881eb4c16f1) | Enterprise-scale internal MCP deployment case study |
| Best MCP Registries 2026 (TrueFoundry) | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Registry landscape comparison |
| Medium: Skills marketplace walkthrough (Mark Chen) | [link](https://medium.com/@markchen69/claude-code-has-a-skills-marketplace-now-a-beginner-friendly-walkthrough-8adeb67cdc89) | Beginner-friendly skills marketplace guide |
| Medium: 10 must-have skills (unicodeveloper) | [link](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | Cross-agent skills picks for Mar 2026 |
| Agent skills cheat codes (Medium/Jonathan Fulton) | [link](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | Apr 2026 practical guide |
| Skills.sh ecosystem (johnoct.com) | [link](https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/) | Vercel skills.sh deep-dive launch analysis |
| KDnuggets top 5 marketplaces | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Marketplace comparison for data professionals |
| AI Agent Skills Marketplace overview (paperclipped.de) | [link](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/) | Plugin ecosystem framing |
| Agent Skills complete guide (explainx.ai) | [link](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | 2026 guide for Claude Code, Cursor & MCP |
| SkillsMP review (SmartScope) | [link](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) | SkillsMP 66,500+ skills review |
| Claude Code survival guide (LinkedIn/Rob Foster) | [link](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) | Practitioner synthesis |
| OpenClaw vs Claude Code vs Managed Agents (MindStudio) | [link](https://www.mindstudio.ai/blog/openclaw-vs-claude-code-channels-vs-managed-agents-2026) | Platform choice guide |
| Claude Marketplace AI Wiki | [link](https://aiwiki.ai/wiki/claude_marketplace) | Reference entry |
| Popular AI Tools: Skills/Plugins/CLIs 2026 | [link](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | Category overview |
| Composio: top Claude plugins | [link](https://composio.dev/content/top-claude-code-plugins) | 10 top plugins list |
| Claude Code improvements (every concept, sabrina.dev) | [link](https://www.sabrina.dev/p/every-claude-code-concept-explained-beginners) | Beginner explanation |
| Claude Code in Action (Anthropic SkillJar) | [link](https://anthropic.skilljar.com/claude-code-in-action) | Official training |
| Agent Skills intro (Anthropic SkillJar) | [link](https://anthropic.skilljar.com/introduction-to-agent-skills) | Official training |
| DevOps.com: Claude introduces agent skills | [link](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) | Industry press coverage |
| SkillRisk.org | [link](https://skillrisk.org/) | Free security scanner for agent skills |
| MACH Alliance MCP Registry | [link](https://machalliance.org/mach-alliance-mcp-registry/) | Enterprise composable architecture registry |
| Claude Marketplace partners (Techzine) | [link](https://www.techzine.eu/news/applications/139359/anthropic-launches-claude-powered-app-marketplace-without-taking-a-cut/) | No-commission model analysis |
| OpenClaw skills (DigitalOcean) | [link](https://www.digitalocean.com/resources/articles/what-are-openclaw-skills) | OpenClaw skills developer guide |
| Securing Claude Cowork (Harmonic) | [link](https://www.harmonic.security/resources/securing-claude-cowork-a-security-practitioners-guide) | Security practitioner guide |
| MCP governance (Obot) | [link](https://obot.ai/blog/claude-code-mcp-governance-enterprise-security/) | Enterprise MCP security framing |
| Claude Code security (Backslash) | [link](https://www.backslash.security/blog/claude-code-security-best-practices) | Security best practices |
| claude-code-mcp (steipete/GitHub) | [link](https://github.com/steipete/claude-code-mcp) | Claude Code as one-shot MCP server (agent-in-agent) |
| Multi-agent orchestration (wshobson/GitHub) | [link](https://github.com/wshobson/agents) | Multi-agent automation for Claude Code |
| ComposioHQ/awesome-claude-plugins | [link](https://github.com/ComposioHQ/awesome-claude-plugins) | Curated Claude plugin registry |
| Kamal claude-plugins | [link](https://github.com/Kamalnrf/claude-plugins) | Lightweight registry CLI |
| 25 YouTube videos ranked (rentierdigital/Medium) | [link](https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840) | Video learning guide |
| Claude code Reddit survey (aitooldiscovery) | [link](https://www.aitooldiscovery.com/guides/claude-code-reddit) | Community sentiment aggregation |
| Where to find MCP servers 2026 | [link](https://automationswitch.com/ai-workflows/where-to-find-mcp-servers-2026) | Discovery guide |
| 50+ best MCP servers | [link](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | Curated list |
| MCP servers (mcpservers.org) | [link](https://mcpservers.org/) | Community awesome list |

---

## Stats Block

```
├─ 🟠 Reddit: ~referenced │ 4,200+ weekly contributors r/ClaudeCode │ no direct threads surfaced
├─ 🔵 X: 0 posts │ not captured
├─ 🔴 YouTube: ~25 videos referenced │ 853K+ top views │ via ranking roundup
├─ 🟢 HN: 9 stories │ 99 points (3 counted) │ 36 comments (3 counted)
├─ 🟣 TikTok: 0 videos │ not captured directly
├─ 🩷 Instagram: 0 reels │ not captured
├─ 🦋 Bluesky: 0 posts │ not captured
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 55+ pages
└─ 🗣️ Top voices: mergesort, anotherCodder, moomooskycow (HN) │ r/ClaudeCode, r/ClaudeAI
```

---

## Data Gaps

- **Reddit**: No direct thread URLs surfaced — site: searches returned empty or were blocked. Community data aggregated from secondhand sources (morphllm.com, aitooldiscovery.com). Estimated Reddit coverage: ~30% (sentiment captured, zero thread-level engagement data).
- **X/Twitter**: Excluded by research design; no data captured.
- **YouTube**: No direct video metadata (views/likes/transcript). Referenced through ranking roundup article (853K+ for top demo); channel names (Net Ninja, Edmund Yong, Nate Herk) identified but not confirmed current view counts.
- **TikTok**: Excluded by research design.
- **Bluesky**: No relevant posts found. May exist; search did not surface.
- **Polymarket**: No prediction markets found for agent skills/MCP topics.
- **HN engagement**: Points/comment counts unavailable for 6 of 9 stories due to HTTP 429 rate limiting on direct HN fetches.
- **Skill catalog counts**: SkillsMP reported both 425,000+ and 800,000+ in different search results — likely reflects rapid growth between source publication dates; treat as directional.
- **Approximate overall coverage**: ~65% — strong on Web/HN signal, weak on social (Reddit, YouTube, X).

---

## Key Quotes

> "Skills are the killer feature because they are a very composable tool." — mergesort on HN ([link](https://news.ycombinator.com/item?id=46396930))

> "I didn't see any emergent behavior, just combining of skills (which I'll admit looks useful). Calling this emergent is click bait." — fooqux on HN ([link](https://news.ycombinator.com/item?id=46531794))

> "I kept losing time to the same class of bug: AI tool configs that are almost right but silently wrong." — anotherCodder (Agnix creator) on HN ([link](https://news.ycombinator.com/item?id=46983879))

> "SOTA right now is the Claude Agent SDK. Package it up with some company-specific skills..." — moomooskycow on HN ([link](https://news.ycombinator.com/item?id=46917293))

> "2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature." — Kate Jensen, Anthropic Head of Americas ([link](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days))

> "I record a voice note in Telegram describing what I need. My server agent picks it up, reads the transcription, and starts working." — okhlopkov.com, 4-month daily use ([link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/))

> "We are finally moving from agents that are 'smarter' to agents that are 'more useful.'" — Lead researcher at AAIF launch ([link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability))

> "Skills specialize the model; MCP connects it to live systems." — Pervasive developer community framing ([link](https://www.morphllm.com/claude-code-extensions))

> "You can make a router skill that describes how to use the other skills together." — kingkongjaffa on HN ([link](https://news.ycombinator.com/item?id=46531794))

> "Claude Code is the best coding tool I've ever used, for the 45 minutes a day I can actually use it." — r/ClaudeCode community, via aggregation ([link](https://www.morphllm.com/claude-code-reddit))
