# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-24
**Query type:** GENERAL
**Sources:** Web (blogs, news, docs, arXiv), Hacker News (referenced threads), GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not captured this run |
| X/Twitter | — | — | Not captured this run |
| YouTube | — | — | Not captured this run |
| Hacker News | 2 threads | 84K+★ awesome-mcp-servers, 52K+★ awesome-claude-skills | Referenced via web search; full thread data not retrieved |
| TikTok | — | — | Not captured this run |
| Instagram | — | — | Not captured this run |
| Bluesky | — | — | Not captured this run |
| Polymarket | — | — | No markets found on topic |
| Web | 130+ pages | — | 13 search queries across 8 topic dimensions |

---

## Synthesized Findings

### 1. The Agent Skills Open Standard: From Anthropic Invention to Cross-Platform Reality

In late 2025, Anthropic introduced the Agent Skills specification for Claude Code — a simple convention of packaging reusable AI instructions into SKILL.md files. What happened next was unexpectedly fast: OpenAI adopted the identical format for Codex CLI within weeks, Google formally integrated it into Antigravity by January 2026, and Vercel launched **skills.sh** on January 20, 2026 as the ecosystem's first dedicated package manager and directory. By April 2026, the format is supported across 40+ agent platforms.

The core format: a SKILL.md file with instructions, frontmatter metadata, and optional supporting files (scripts, templates, reference docs). A skill created for Codex runs unchanged inside Claude Code, Cursor, GitHub Copilot, and thirty others. Claude Code extends the open standard with three additions: invocation control (you vs. Claude triggers the skill), subagent execution, and dynamic context injection.

**Sources:** [Extend Claude with skills (Docs)](https://code.claude.com/docs/en/skills) · [Agent Skills API Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [OpenAI Codex Skills](https://developers.openai.com/codex/skills) · [Vercel skills announcement](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [InfoQ: Vercel Introduces Skills.sh](https://www.infoq.com/news/2026/02/vercel-agent-skills/) · [ITECS Codex CLI Guide](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026) · [Codex Skills Guide](https://www.getaiperks.com/en/articles/codex-skills) · [Exploring OpenAI Codex 2026](https://digitalstrategy-ai.com/2026/04/14/exploring-openai-codex-features/)

---

### 2. The Three-Layer Taxonomy: Skills vs. Plugins vs. MCP

Community confusion about terminology is widespread and actively being addressed by tutorial authors and documentation. The actual distinction:

- **Skills** (`SKILL.md`): A file that teaches Claude how to do one specific task. Pure instructions. Filesystem-based, portable.
- **Plugins**: A folder with a `plugin.json` manifest that bundles any combination of: Skills, Agents (sub-agents as isolated tools), Hooks (scripts triggered on events), MCP servers, and Slash commands. Plugins are the *distribution unit*.
- **MCP Connectors**: The network plumbing. MCP (Model Context Protocol) is an open standard governing how AI clients connect to *external* tools and data sources — databases, GitHub, APIs, browsers. MCP is infrastructure; Skills are methodology.

The developer community has converged on a clean mental model: *"Use MCP when you need Claude to access something external. Use Skills when you need Claude to know how to do something. Most real workflows use both."* Two HN threads — ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) and the follow-up thread [id=46038842](https://news.ycombinator.com/item?id=46038842) — crystallized this distinction for thousands of developers.

**Sources:** [agensi.io: Plugins vs Skills explained](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [DevToolPicks: Skills vs MCP vs Plugins](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) · [MorphLLM Complete Guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [Tony Kipkemboi: Skills & Plugins Explained](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained) · [Chris Ayers: Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) · [Young Leaders Tech #95](https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins) · [HN thread 45619537](https://news.ycombinator.com/item?id=45619537) · [HN thread 46038842](https://news.ycombinator.com/item?id=46038842) · [HackerNoon: CLI vs MCP](https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it)

---

### 3. Marketplace Explosion: Competing Directories at Scale

The marketplace ecosystem is fragmented but enormous. Within four months of the skills standard going open, several platforms emerged:

| Marketplace | Scale | Notes |
|-------------|-------|-------|
| [SkillsMP](https://skillsmp.com/) | 425,000+ skills | Largest by count; open SKILL.md standard |
| [LobeHub Skills](https://lobehub.com/skills) | 169,739 skills | Fastest-growing according to self-report |
| [skills.sh](https://skills.sh/) | Leaderboard-based | Vercel-backed; npm-style install telemetry |
| [Glama Registry](https://glama.ai/mcp/servers) | 21,949 MCP servers | Open-source MCP focus (updated 2026-04-15) |
| [mcp.so](https://mcp.so/) | 20,354 MCP servers | Third-party MCP marketplace |
| [MCPMarket](https://mcpmarket.com/) | 10,000+ MCP servers | 23+ categories; community curated |
| [claudemarketplaces.com](https://claudemarketplaces.com/) | 110K+ monthly devs | Aggregates plugins, skills, MCP servers |
| [SkillsLLM](https://skillsllm.com/) | — | AI-focused skills marketplace |

Anthropic's **official** plugin directory ([claude.com/plugins](https://claude.com/plugins) / [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)) launched in early 2026 with 55+ curated plugins and 72+ vetted community contributions. It is split into `/plugins` (Anthropic-built) and `/external_plugins` (third-party, includes Supabase, Firebase, Discord, Telegram integrations).

**Sources:** [SkillsMP](https://skillsmp.com/) · [LobeHub Skills](https://lobehub.com/skills) · [skills.sh](https://skills.sh/) · [Glama Registry](https://glama.ai/mcp/servers) · [mcp.so](https://mcp.so/) · [MCPMarket](https://mcpmarket.com/) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [SkillsLLM](https://skillsllm.com/) · [claude.com/plugins](https://claude.com/plugins) · [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) · [Groundy: Official Ecosystem Explained](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) · [systemprompt.io guide](https://systemprompt.io/guides/getting-started-anthropic-marketplace) · [DeepWiki](https://deepwiki.com/anthropics/claude-plugins-official) · [KDnuggets: Top 5 Marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) · [TurboDocx guide](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) · [DEV Community guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4)

---

### 4. skills.sh: npm for Agent Behaviors

Vercel's skills.sh is the clearest analog to a package manager for agent skills. Launched January 20, 2026, it positions itself explicitly as "npm for agent behaviors." Key mechanics:

- **CLI**: `npx skills add vercel-labs/agent-skills` — install skills like npm packages
- **Auto-registry**: installs via the CLI show up on skills.sh via install telemetry — no submission required
- **Breadth**: supports OpenCode, Claude Code, Codex, Cursor, and 41 more agents
- **Velocity**: 110,000 skill installs in the first 4 days; Stripe shipped their own skills on day one; the top skill hit 20,000 installs within 6 hours of launch announcement

Academic researchers at arXiv took this further with **Skilldex** ([arXiv:2604.16911](https://arxiv.org/abs/2604.16911), published April 18, 2026) — a TypeScript CLI (`skillpm` / `spm`) proposing a three-tier hierarchical scope system (global → shared → project), compiler-style format conformance scoring, a "skillset" abstraction for bundled related skills, and a human-in-the-loop suggestion loop for skill discovery. The Skilldex paper formalizes what skills.sh does operationally.

**Sources:** [Vercel changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [vercel-labs/skills GitHub](https://github.com/vercel-labs/skills) · [Vercel Skills Docs](https://vercel.com/docs/agent-resources/skills) · [Vercel KB Guide](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context) · [npm/skills](https://www.npmjs.com/package/skills) · [skills.sh](https://skills.sh/) · [johnoct.com blog](https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/) · [Dev Genius top-10 analysis](https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481) · [InfoQ coverage](https://www.infoq.com/news/2026/02/vercel-agent-skills/) · [virtualuncle guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) · [Skilldex paper](https://arxiv.org/abs/2604.16911) · [Skilldex HTML](https://arxiv.org/html/2604.16911)

---

### 5. MCP Registry Landscape: Three Registries, One Meta-Registry

MCP's registry situation is being consolidated. The official **MCP Meta-Registry** (backed by Anthropic, GitHub, PulseMCP, and Microsoft) is a metadata-only registry — it stores information *about* servers, not the servers themselves. Actual packages live on npm, PyPI, Docker Hub. This mirrors the design of Skilldex.

The 2026 MCP roadmap ([modelcontextprotocol.io](https://modelcontextprotocol.io/development/roadmap) and [blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)) targets two critical gaps:
1. **Server Cards**: a `.well-known` endpoint for structured server metadata, enabling discovery without a live connection — solving the "I have to connect to know what it does" problem
2. **Stateless horizontal scaling**: servers that don't need to hold state, enabling proper cloud-native deployment at scale
3. **Skills Over MCP Working Group**: experimenting with skills discovery and distribution as first-class MCP primitives

**Sources:** [MCP GitHub](https://github.com/modelcontextprotocol) · [MCP Roadmap](https://modelcontextprotocol.io/development/roadmap) · [2026 MCP Roadmap Blog](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) · [MCP Wikipedia](https://en.wikipedia.org/wiki/Model_Context_Protocol) · [The New Stack: MCP Growing Pains](https://thenewstack.io/model-context-protocol-roadmap-2026/) · [Truto: MCP Guide for SaaS PMs](https://truto.one/blog/what-is-mcp-model-context-protocol-the-2026-guide-for-saas-pms) · [Fungies: MCP Complete Guide](https://fungies.io/mcp-servers-developers-guide-2026/) · [atalupadhyay: MCP in 2026](https://atalupadhyay.wordpress.com/2026/04/19/mcp-in-2026-building-connected-ai-agents/) · [dasroot.net MCP deep dive](https://dasroot.net/posts/2026/04/model-context-protocol-mcp-technical-deep-dive/) · [Generect MCP Guide](https://generect.com/blog/what-is-mcp/) · [Claude MCP Docs](https://code.claude.com/docs/en/mcp) · [mcpservers.org](https://mcpservers.org) · [Apigene MCP Marketplace Guide](https://apigene.ai/blog/mcp-marketplace) · [TrueFoundry Best Registries](https://www.truefoundry.com/blog/best-mcp-registries) · [Taskade: 15 Best MCP Servers](https://www.taskade.com/blog/mcp-servers) · [MCPMarket daily top list](https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026)

---

### 6. Security Crisis: 13.4% of Skills Are Malicious

The skills ecosystem has a significant supply-chain security problem. Snyk's **ToxicSkills** audit (published February 5, 2026) was the first systematic security scan of the skills ecosystem:

- **Corpus**: 3,984 skills from ClawHub and skills.sh
- **Critical findings**: 534 skills (13.4%) contained at least one critical-level security issue
- **Malicious payloads**: 76 confirmed, including credential theft, backdoor installation, and data exfiltration
- **Prompt injection**: 36% of all skills contained prompt-injection techniques
- **Attack convergence**: 100% of confirmed malicious skills combined code payloads + prompt injection; 91% used prompt injection simultaneously
- **Severity demo**: Three lines of markdown in a SKILL.md file were sufficient to instruct an agent to read SSH keys and exfiltrate them

Responses to this:
- **Snyk + Vercel partnership**: real-time security scanning integrated into skills.sh before user download ([Snyk + Vercel blog](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/))
- **Snyk + Tessl**: setting registry security standards ([Snyk + Tessl blog](https://snyk.io/blog/snyk-tessl-partnership/))
- **Open-source agent-scan CLI**: [github.com/snyk/agent-scan](https://github.com/snyk/agent-scan) — scans skills for prompt injections, tool poisoning, toxic flows, vulnerabilities
- **OWASP Agentic Skills Top 10**: industry-standard risk framework launched ([owasp.org](https://owasp.org/www-project-agentic-skills-top-10/))

**Sources:** [Snyk ToxicSkills blog](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) · [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) · [Snyk + Vercel](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) · [snyk/agent-scan](https://github.com/snyk/agent-scan) · [Agent Scan Skill Inspector](https://labs.snyk.io/resources/agent-scan-skill-inspector/) · [AI CERTs: Snyk Audit](https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/) · [Snyk: SKILL.md to Shell Access](https://snyk.io/articles/skill-md-shell-access/) · [Snyk + Tessl](https://snyk.io/blog/snyk-tessl-partnership/) · [agent-scan issue codes](https://github.com/snyk/agent-scan/blob/main/docs/issue-codes.md) · [skill-audit skill on SkillsMP](https://skillsmp.com/skills/neversight-learn-skills-dev-data-skills-md-absolutelyskilled-absolutelyskilled-skill-audit-skill-md)

---

### 7. Claude Managed Agents: Production Infrastructure Layer (April 8, 2026)

Anthropic launched **Claude Managed Agents** on April 8, 2026 — a composable API suite for building and deploying cloud-hosted agents at production scale. This sits above Skills and MCP in the stack: it's the execution and orchestration layer.

Key capabilities:
- **Sandboxed code execution** (isolated environments per session)
- **Checkpointing** (resume mid-task agents)
- **Credential management** (scoped permissions for external services)
- **End-to-end tracing** (full observability)
- **Pricing**: standard Claude API token rates + $0.08/session-hour

Enterprise customers running in production at launch: Notion, Rakuten, Asana, Sentry, Atlassian. Still in research preview (separate access required): multi-agent coordination and self-evaluation capabilities.

This launch accelerated enterprise conversations about combining Managed Agents (cloud orchestration) + Skills (behavioral instructions) + MCP servers (tool connectivity) as a complete production AI agent stack.

**Sources:** [Claude Managed Agents blog](https://claude.com/blog/claude-managed-agents) · [Claude Managed Agents Docs](https://platform.claude.com/docs/en/managed-agents/overview) · [Help Net Security](https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/) · [InfoWorld](https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html) · [Medium (unicodeveloper)](https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14) · [The AI Corner Guide](https://www.the-ai-corner.com/p/claude-managed-agents-guide-2026) · [Linas Substack](https://linas.substack.com/p/claude-managed-agents-guide) · [OpenLinksW Infographic](https://www.openlinksw.com/data/html/claude-managed-agents-infographic.html) · [Pulse24](https://pulse24.ai/news/2026/4/9/3/claude-launches-managed-agents) · [LowCode Agency](https://www.lowcode.agency/blog/claude-managed-agents) · [DevOps.com](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) · [MindStudio workflow patterns](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns)

---

### 8. BMAD v6.3.0: Framework-Native Marketplace Integration (April 10, 2026)

The BMAD Method (Breakthrough Method for Agile AI Driven Development), a popular open-source framework for multi-agent development workflows, released v6.3.0 on April 10, 2026 — two days after Claude Managed Agents launched. The biggest addition: a marketplace ecosystem baked into the framework itself.

- **Remote registry**: fetch and install modules from the community
- **Community module browser**: VS Code marketplace-like UX for discovering AI skills — the first in-framework browser in the AI vibe coding category
- **Universal Git source support**: point to any Git repo as a skills/module source
- **Agent consolidation**: 4 separate agent personas (previously confusing for new users) merged into a single Developer agent named Amelia
- **Parallel story development**: eliminates the spec-wip.md singleton; each story now has its own spec-{slug}.md with a status field (draft/done), enabling true parallel development

BMAD is also actively listed in LobeHub Skills Marketplace ([BMad Master](https://lobehub.com/skills/aj-geddes-claude-code-bmad-skills-bmad-master)), showing cross-marketplace distribution.

**Sources:** [Vibe Sparking AI: BMAD v6.3.0](https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/) · [BMAD-METHOD GitHub](https://github.com/bmad-code-org/BMAD-METHOD) · [BMAD releases](https://github.com/bmad-code-org/BMAD-METHOD/releases) · [BMAD CHANGELOG](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/CHANGELOG.md) · [BMAD Docs](https://docs.bmad-method.org/) · [BMAD Roadmap](https://docs.bmad-method.org/roadmap/) · [BMadCodes](https://bmadcodes.com/) · [BMad Master on LobeHub](https://lobehub.com/skills/aj-geddes-claude-code-bmad-skills-bmad-master) · [bmad-bmb on LobeHub](https://lobehub.com/skills/dickymoore-macs-bmad-bmb) · [bmad on LobeHub](https://lobehub.com/skills/re-cinq-wave-bmad)

---

### 9. Reusable Workflows & Custom Subagents

Claude Code's custom workflow patterns are maturing. Key capabilities as of April 2026:

- **skill-creator skill**: A built-in skill that walks users through creating new skills — asks about your workflow, generates folder structure, formats SKILL.md, bundles resources
- **Subagents**: [Create custom subagents (Docs)](https://code.claude.com/docs/en/sub-agents) — specialized AI assistants for specific task types; used sequentially in multi-step workflows
- **Agent Teams (experimental)**: parallel workflows with 4 specialized agents, 7 commands, 6 skills
- **Claude-Code-Workflow**: community JSON-driven multi-agent cadence framework with intelligent CLI orchestration supporting Gemini/Qwen/Codex ([catlog22/Claude-Code-Workflow](https://github.com/catlog22/Claude-Code-Workflow))
- **wshobson/agents**: intelligent automation and multi-agent orchestration for Claude Code ([GitHub](https://github.com/wshobson/agents))
- **awesome-claude-code** (52K+ stars): curated list of skills, hooks, slash-commands, agent orchestrators, applications, plugins ([hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code))
- **alirezarezvani/claude-skills**: 232+ skills covering engineering, marketing, product, compliance, and C-level advisory across 10 agent platforms ([GitHub](https://github.com/alirezarezvani/claude-skills))
- **ComposioHQ/awesome-claude-plugins**: curated community plugin list ([GitHub](https://github.com/ComposioHQ/awesome-claude-plugins))
- **claude-code-plugins-plus-skills** (tonsofskills.com): 423 plugins, 2,849 skills, 177 agents with ccpi CLI package manager ([GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills))

**Sources:** [Claude Subagents Docs](https://code.claude.com/docs/en/sub-agents) · [Claude Discover Plugins Docs](https://code.claude.com/docs/en/discover-plugins) · [claude-code/plugins](https://github.com/anthropics/claude-code/tree/main/plugins) · [claude-code/plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) · [marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json) · [wshobson/agents](https://github.com/wshobson/agents) · [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) · [catlog22/Claude-Code-Workflow](https://github.com/catlog22/Claude-Code-Workflow) · [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · [ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) · [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [openai/skills catalog](https://github.com/openai/skills) · [SitePoint: Advanced Workflows 2026](https://www.sitepoint.com/claude-code-as-an-autonomous-agent-advanced-workflows-2026/) · [chatprd.ai workflows](https://www.chatprd.ai/how-i-ai/workflows/tool/claude) · [Medium: Agent Skills cheat codes](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) · [DEV: Skills vs MCP Servers](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) · [Ollama Claude Code integration](https://docs.ollama.com/integrations/claude-code)

---

### 10. Academic Research Surge on Agentic Skills

Academic publishing on agent skills exploded in early 2026, with multiple landmark papers:

| Paper | arXiv | Key Contribution |
|-------|-------|-----------------|
| [Agent Skills: A Data-Driven Analysis](https://arxiv.org/abs/2602.08004) | 2602.08004 | First large-scale empirical analysis of Claude Skills |
| [SoK: Agentic Skills — Beyond Tool Use](https://arxiv.org/abs/2602.20867) | 2602.20867 | Systematic literature review of the full space |
| [Agent Skills for LLMs: Architecture, Acquisition, Security](https://arxiv.org/html/2602.12430v3) | 2602.12430 | Architecture taxonomy + security threat model |
| [SkillsBench](https://arxiv.org/pdf/2602.12670) | 2602.12670 | Benchmark for skills across diverse task types |
| [ARISE: Hierarchical RL + Skill Evolution](https://arxiv.org/abs/2603.16060) | 2603.16060 | RL approach to intrinsic skill evolution |
| [Skilldex](https://arxiv.org/abs/2604.16911) | 2604.16911 | Package manager + registry w/ hierarchical scope (April 18, 2026) |
| [EvoAgent: Evolvable Framework](https://arxiv.org/abs/2604.20133) | 2604.20133 | Evolvable agents w/ skill learning + multi-agent delegation |

Skilldex (the most recent, April 18, 2026) directly operationalizes the skills ecosystem problems: format conformance scoring, hierarchical scope distribution (global/shared/project), and MCP server integration for discovery. It's implemented as a TypeScript CLI (`skillpm`/`spm`) with Hono/Supabase backend.

---

## Cross-Source Patterns

### Pattern 1: Skills vs. MCP Conceptual Confusion (Web + HN)
The most persistent signal across all sources: developers are confused about when to use Skills vs. MCP connectors vs. Plugins. Multiple blog posts, two HN threads, and the Snyk security report all address this from different angles. The winning mental model ("MCP is plumbing, Skills are instructions") has emerged but hasn't fully propagated. HN thread [45619537](https://news.ycombinator.com/item?id=45619537) titled "Claude Skills are awesome, maybe a bigger deal than MCP" generated significant debate.
- **Platforms**: Web (10+ posts), Hacker News (2 threads)
- **Key quote**: *"The concept is simple but the implications are large — you're not writing code, you're writing institutional knowledge that an agent can load and apply."* — inferred from context at [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)

### Pattern 2: Speed of Standards Adoption (Web + GitHub)
An open standard that went from Anthropic-only to 40+ platforms in ~4 months is remarkable velocity for developer tooling. The Vercel launch achieving 110K installs in 4 days signals genuine demand. GitHub star counts (awesome-mcp-servers: 84K+, awesome-claude-skills: 52K+) confirm the community is highly active.
- **Platforms**: Web, GitHub
- **Key quote**: *"The ecosystem went from nothing to hundreds of thousands of indexed skills in under four months, with over 30 products adopting the same format in the same period."* — [SkillsMP](https://skillsmp.com/)

### Pattern 3: Supply-Chain Security as the Next Crisis (Web + Academic)
The Snyk ToxicSkills audit (13.4% malicious, 36% with prompt injection) is being cited across blog posts, news outlets, and academic papers (arXiv:2602.12430 covers security architecture). OWASP Agentic Skills Top 10 launching indicates the security community sees this as a major emerging risk category.
- **Platforms**: Web (Snyk blog, OWASP, AI CERTs, security news), Academic (arXiv)
- **Key quote**: *"Three lines of markdown in a SKILL.md file were enough to instruct an agent to read SSH keys and exfiltrate them to the attacker's infrastructure."* — [Snyk](https://snyk.io/articles/skill-md-shell-access/)

### Pattern 4: Framework-Level Marketplace Integration (Web)
Both BMAD (April 10) and Anthropic's Claude Managed Agents (April 8) launched within 48 hours, both incorporating marketplace/registry concepts. BMAD adds a plugin browser to the framework itself; Managed Agents enables skill-based agents to run at cloud scale. This suggests marketplace infrastructure is moving from community-built to first-class framework feature.
- **Platforms**: Web (multiple blogs, DevOps.com, InfoWorld)
- **Key quote**: *"The first community module browser in AI vibe coding tools."* — [Vibe Sparking AI on BMAD v6.3.0](https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (unknown) | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | "context documents resemble normal developer documentation, but actually useful and task-oriented" | https://news.ycombinator.com/item?id=45619537 |
| (unknown) | I definitely see the value and versatility of Claude Skills (over what MCP is to...) | — | — | Discusses skills portability across agents | https://news.ycombinator.com/item?id=46038842 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Snyk ToxicSkills Report | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | First systematic security audit: 13.4% malicious, 36% prompt injection |
| OWASP Agentic Skills Top 10 | https://owasp.org/www-project-agentic-skills-top-10/ | Risk taxonomy for agentic skills |
| Snyk: SKILL.md to Shell Access | https://snyk.io/articles/skill-md-shell-access/ | Attack proof-of-concept |
| Snyk + Vercel Partnership | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Real-time security scanning on skills.sh |
| snyk/agent-scan | https://github.com/snyk/agent-scan | Open-source security scanner for skills + MCP |
| Vercel skills announcement | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | Official launch of skills.sh, January 20 2026 |
| skills.sh directory | https://skills.sh/ | Canonical skills leaderboard/directory |
| InfoQ: Vercel Skills | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Industry coverage of skills.sh launch |
| Claude Managed Agents blog | https://claude.com/blog/claude-managed-agents | Anthropic's April 8, 2026 production API launch |
| Claude Managed Agents Docs | https://platform.claude.com/docs/en/managed-agents/overview | Full API documentation |
| Help Net Security: Managed Agents | https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/ | Security-focused coverage |
| InfoWorld: Managed Agents | https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html | Enterprise angle |
| BMAD v6.3.0 changelog | https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/ | Marketplace integration details |
| BMAD GitHub | https://github.com/bmad-code-org/BMAD-METHOD | Source and releases |
| Skilldex (arXiv) | https://arxiv.org/abs/2604.16911 | Academic package manager proposal, April 18 2026 |
| SoK: Agentic Skills (arXiv) | https://arxiv.org/abs/2602.20867 | Systematic review of skills landscape |
| Agent Skills: Architecture+Security (arXiv) | https://arxiv.org/html/2602.12430v3 | Security threat modeling |
| SkillsBench (arXiv) | https://arxiv.org/pdf/2602.12670 | Skills benchmark suite |
| Anthropic official plugins | https://github.com/anthropics/claude-plugins-official | Official 55+ plugin directory |
| claude.com/plugins | https://claude.com/plugins | Consumer-facing plugin directory |
| Glama Registry | https://glama.ai/mcp/servers | 21,949 MCP servers |
| MCP Roadmap | https://modelcontextprotocol.io/development/roadmap | Official 2026 MCP priorities |
| 2026 MCP Roadmap Blog | https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/ | MCP roadmap blog post |
| New Stack: MCP Growing Pains | https://thenewstack.io/model-context-protocol-roadmap-2026/ | Production MCP challenges |
| awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | 52K+ star curated list |
| KDnuggets: Top 5 Marketplaces | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Marketplace comparison |
| HackerNoon: CLI vs MCP | https://hackernoon.com/cli-vs-mcp-why-claude-codes-ecosystem-is-pivoting-and-the-10-tools-leading-it | Ecosystem direction analysis |
| OpenAI Codex Skills | https://developers.openai.com/codex/skills | Cross-platform standard confirmation |
| openai/skills GitHub | https://github.com/openai/skills | OpenAI skills catalog |
| ScriptByAI Resource List | https://www.scriptbyai.com/claude-code-resource-list/ | Comprehensive 2026 resource compilation |
| agensi.io: Plugins vs Skills | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Clear taxonomy explainer |
| DevToolPicks: Three-way comparison | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | Skills vs MCP vs Plugins |
| MindStudio: Workflow Patterns | https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns | 5 agentic workflow patterns |
| SitePoint: Advanced Workflows 2026 | https://www.sitepoint.com/claude-code-as-an-autonomous-agent-advanced-workflows-2026/ | Autonomous agent patterns |
| DevOps.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | DevOps perspective |
| Medium: Agent Skills Cheat Codes | https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d | Practical guide, April 2026 |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 232+ cross-platform skills repo |
| MorphLLM Complete Guide | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins guide |
| DEV: Skills vs MCP Servers | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | DEV Community practical guide |
| DEV: Best Skills & Plugins 2026 | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best-of list |
| DEV: Claude Code #1 on HN | https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74 | HN milestone coverage |
| Tony Kipkemboi: Skills Explained | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | Skills and plugins explainer |
| Chris Ayers: Complete Guide | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Comprehensive guide |
| Young Leaders Tech #95 | https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins | Newsletter coverage |
| MCP.so | https://mcp.so/ | 20,354 MCP servers |
| MCPMarket | https://mcpmarket.com/ | 10K+ MCP servers, 23 categories |
| TrueFoundry: Best MCP Registries | https://www.truefoundry.com/blog/best-mcp-registries | Registry comparison |
| Apigene MCP Marketplace Guide | https://apigene.ai/blog/mcp-marketplace | MCP marketplace guide |
| Taskade: 15 Best MCP Servers | https://www.taskade.com/blog/mcp-servers | MCP server recommendations |
| MCPMarket daily top list | https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026 | March 4 top MCP list |
| mcpservers.org | https://mcpservers.org | MCP server directory |
| Claude MCP Docs | https://code.claude.com/docs/en/mcp | Official MCP documentation |
| MCP Wikipedia | https://en.wikipedia.org/wiki/Model_Context_Protocol | Background reference |
| Truto: MCP Guide for SaaS PMs | https://truto.one/blog/what-is-mcp-model-context-protocol-the-2026-guide-for-saas-pms | Product manager angle |
| Fungies: MCP Servers Guide | https://fungies.io/mcp-servers-developers-guide-2026/ | Developer guide |
| atalupadhyay: MCP in 2026 | https://atalupadhyay.wordpress.com/2026/04/19/mcp-in-2026-building-connected-ai-agents/ | April 19 2026 perspective |
| dasroot.net: MCP Technical Dive | https://dasroot.net/posts/2026/04/model-context-protocol-mcp-technical-deep-dive/ | Technical deep dive |
| Generect: MCP 2026 Guide | https://generect.com/blog/what-is-mcp/ | General MCP guide |
| modelcontextprotocol GitHub | https://github.com/modelcontextprotocol | Official MCP GitHub org |
| johnoct.com: skills.sh blog | https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/ | Detailed skills.sh analysis |
| Dev Genius: Top 10 skills analysis | https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481 | Skills quality analysis |
| virtualuncle: Skills.sh Guide | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | Skills.sh guide |
| npm/skills | https://www.npmjs.com/package/skills | npm package |
| vercel-labs/skills | https://github.com/vercel-labs/skills | Official Vercel skills tool |
| Vercel Agent Skills Docs | https://vercel.com/docs/agent-resources/skills | Vercel documentation |
| Vercel KB Guide | https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context | Knowledge base |
| Claude Subagents Docs | https://code.claude.com/docs/en/sub-agents | Subagent documentation |
| Claude Discover Plugins Docs | https://code.claude.com/docs/en/discover-plugins | Plugin discovery docs |
| claude-code/plugins | https://github.com/anthropics/claude-code/tree/main/plugins | Plugin directory |
| claude-code/plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Plugin README |
| marketplace.json | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Marketplace config |
| systemprompt.io | https://systemprompt.io/guides/getting-started-anthropic-marketplace | Getting started guide |
| DeepWiki | https://deepwiki.com/anthropics/claude-plugins-official | Plugin docs |
| Ollama integration | https://docs.ollama.com/integrations/claude-code | Local model + Claude Code |
| wshobson/agents | https://github.com/wshobson/agents | Multi-agent orchestration |
| catlog22/Claude-Code-Workflow | https://github.com/catlog22/Claude-Code-Workflow | JSON-driven workflow framework |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugins list |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 423 plugins, 2849 skills |
| openai/skills | https://github.com/openai/skills | OpenAI skills catalog |
| ITECS: Codex CLI Guide | https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 | Cross-platform guide |
| OpenAI: Introducing Codex | https://openai.com/index/introducing-codex/ | Codex launch |
| Codex Changelog | https://developers.openai.com/codex/changelog | Codex updates |
| OpenAI Codex home | https://openai.com/codex/ | Codex main page |
| IntuitionLabs: Codex App | https://intuitionlabs.ai/articles/openai-codex-app-ai-coding-agents | Multi-agent Codex guide |
| GetAIPerks: Codex Skills | https://www.getaiperks.com/en/articles/codex-skills | Codex skills guide |
| DigitalStrategy: Codex 2026 | https://digitalstrategy-ai.com/2026/04/14/exploring-openai-codex-features/ | Codex feature overview |
| SpicyAdvisory: Codex April 2026 | https://www.spicyadvisory.com/blog/openai-codex-april-2026-update-business-workflows-2026 | Business workflow update |
| EvoAgent (arXiv) | https://arxiv.org/abs/2604.20133 | Evolvable agent framework |
| ARISE (arXiv) | https://arxiv.org/abs/2603.16060 | Hierarchical RL + skills |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregated marketplace |
| SkillsLLM | https://skillsllm.com/ | AI skills marketplace |
| SkillsMP | https://skillsmp.com/ | 425K+ skills marketplace |
| LobeHub Skills | https://lobehub.com/skills | 169K+ skills marketplace |
| Medium: Claude Managed Agents | https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14 | Honest pros/cons review |
| The AI Corner: Managed Agents Guide | https://www.the-ai-corner.com/p/claude-managed-agents-guide-2026 | Complete guide |
| Linas Substack: Managed Agents | https://linas.substack.com/p/claude-managed-agents-guide | Ultimate guide |
| OpenLinksW Infographic | https://www.openlinksw.com/data/html/claude-managed-agents-infographic.html | Visual overview |
| Pulse24: Managed Agents | https://pulse24.ai/news/2026/4/9/3/claude-launches-managed-agents | News coverage |
| LowCode Agency | https://www.lowcode.agency/blog/claude-managed-agents | Everything you need to know |
| chatprd.ai workflows | https://www.chatprd.ai/how-i-ai/workflows/tool/claude | Workflow guides |
| HN Skill for Claude Code | https://mcpmarket.com/tools/skills/hacker-news-reader | HN reader skill |
| TurboDocx guide | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best-of comparison |
| Snyk + Tessl | https://snyk.io/blog/snyk-tessl-partnership/ | Security partnership |
| agent-scan issue codes | https://github.com/snyk/agent-scan/blob/main/docs/issue-codes.md | Scanner reference |
| Agent Scan Skill Inspector | https://labs.snyk.io/resources/agent-scan-skill-inspector/ | Snyk Labs tool |
| AI CERTs: Snyk audit | https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/ | Security news coverage |
| skill-audit on SkillsMP | https://skillsmp.com/skills/neversight-learn-skills-dev-data-skills-md-absolutelyskilled-absolutelyskilled-skill-audit-skill-md | Security skill |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ 0 upvotes │ 0 comments  [NOT CAPTURED]
├─ 🔵 X: 0 posts │ 0 likes │ 0 reposts  [NOT CAPTURED]
├─ 🔴 YouTube: 0 videos │ 0 views  [NOT CAPTURED]
├─ 🟢 HN: 2 threads referenced │ engagement data not retrieved
├─ 🟣 TikTok: 0 videos │ 0 views  [NOT CAPTURED]
├─ 🩷 Instagram: 0 reels │ 0 views  [NOT CAPTURED]
├─ 🦋 Bluesky: 0 posts │ 0 likes  [NOT CAPTURED]
├─ 📊 Polymarket: 0 markets  [no markets found]
├─ 🌐 Web: 130+ pages │ 13 search queries │ 8 topic dimensions
└─ 🗣️ Top voices: @snyk (security), @vercel (skills.sh), @anthropic (plugins/managed agents), @bmad-code-org (framework) │ r/[not captured]
```

---

## Data Gaps

- **Social platforms not captured**: Reddit, X/Twitter, YouTube, TikTok, Instagram, Bluesky data was not retrieved in this run. The `/last30days` skill was invoked but did not execute its full multi-platform retrieval pipeline. Raw social signal (community sentiment, top voices, viral posts) is missing.
- **HN thread details**: Two HN threads were identified ([45619537](https://news.ycombinator.com/item?id=45619537) and [46038842](https://news.ycombinator.com/item?id=46038842)) but point counts, comment counts, and detailed thread content were not retrieved.
- **Polymarket**: No prediction markets found on this topic. Not surprising — this is a developer tooling topic without clear binary outcomes to bet on.
- **ClawHub**: Referenced extensively in the Snyk ToxicSkills audit as a source of malicious skills, but ClawHub itself was not directly searched; its current status (active vs. removed) is unclear.
- **Quantitative marketplace data**: LobeHub claims 169,739 skills; SkillsMP claims 425,000+. These numbers couldn't be independently verified. The discrepancy may reflect different counting methodologies (deduplicated vs. not, forks vs. originals).
- **Estimated coverage**: Web/documentation/GitHub/academic ≈ 85% coverage. Social/community ≈ 10% coverage (inferred from HN references only). Overall: ~50% of available signal captured.

---

## Key Quotes

> *"Three lines of markdown in a SKILL.md file were enough to instruct an agent to read SSH keys and exfiltrate them to the attacker's infrastructure."* — Snyk ([From SKILL.md to Shell Access](https://snyk.io/articles/skill-md-shell-access/))

> *"The ecosystem went from nothing to hundreds of thousands of indexed skills in under four months, with over 30 products adopting the same format in the same period."* — SkillsMP ([skillsmp.com](https://skillsmp.com/))

> *"A skill created for OpenAI's Codex can run unchanged inside Claude Code, Google Antigravity, Cursor, GitHub Copilot, and over thirty other agent platforms."* — ITECS ([Codex CLI Agent Skills Guide](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026))

> *"Think of it as npm for agent behaviors. Instead of packaging JavaScript libraries, it packages workflows, best practices, and domain expertise into modules that any compatible agent can load and execute."* — johnoct.com ([Skills.sh: The Missing Package Manager](https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/))

> *"MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things."* — DevToolPicks ([Skills vs MCP vs Plugins](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026))

> *"Snyk Finds Prompt Injection in 36%, 1467 Malicious Payloads in a ToxicSkills Study of Agent Skills Supply Chain Compromise."* — Snyk ([ToxicSkills blog](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> *"The first community module browser in AI vibe coding tools."* — Vibe Sparking AI on BMAD v6.3.0 ([BMAD changelog](https://www.vibesparking.com/en/blog/ai/bmad/2026-04-11-bmad-v630-changelog/))

> *"Claude Managed Agents: get to production 10x faster."* — Anthropic ([Claude Managed Agents blog](https://claude.com/blog/claude-managed-agents))

> *"Within six hours of Vercel announcing skills.sh, the top skill had over 20,000 installs."* — johnoct.com ([Skills.sh analysis](https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/))

> *"How much these kinds of context documents resemble normal developer documentation, but actually useful and task-oriented."* — HN commenter on agent skills ([HN thread 45619537](https://news.ycombinator.com/item?id=45619537))
