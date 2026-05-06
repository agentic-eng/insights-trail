# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-06
**Query type:** GENERAL
**Sources:** Hacker News, Web, GitHub, YouTube

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 stories | ~2,230+ points, ~1,370+ comments | Includes 816-pt and 738-pt threads |
| YouTube | 1 video | — | April 2026 top-skills roundup, metadata blocked |
| Web | 60+ pages | — | Docs, blogs, news, security advisories, marketplaces |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: A Cross-Industry Convergence

The defining event of the last 30 days — and of the last five months — is the emergence of SKILL.md as a de facto cross-platform open standard for AI agent capabilities. Anthropic released the Agent Skills specification on **December 18, 2025**, and the adoption velocity has been remarkable: by March 2026, **32 tools** from competing companies read the same SKILL.md files from the same directory structure.

Adopters include Claude Code (Anthropic), Codex CLI and ChatGPT (OpenAI), VS Code and GitHub Copilot (Microsoft), Gemini CLI (Google), Kiro (AWS), Goose (Block), Sourcegraph Amp, JetBrains Junie, ByteDance TRAE, Mistral AI, Snowflake, Databricks, and 18 others. The portability of skills across competing agents is what made a marketplace ecosystem viable — a creator can reach the entire agent ecosystem from one SKILL.md file.

The growth numbers are staggering. A **Bosch Research/CMU study** analyzing 40,285 publicly listed skills found the ecosystem grew **18.5× in just 20 days** — from 2,179 skills on January 16 to over 40,000 by February 5, 2026. By May 2026, LobeHub alone indexes **169,739 skills**, while skills.sh (Vercel) tracks 87,000+.

The institutional home for this ecosystem was established on **December 9, 2025**, when the Linux Foundation announced the **Agentic AI Foundation (AAIF)** with Anthropic, OpenAI, and Block as co-founders. Anthropic donated MCP; OpenAI donated AGENTS.md. By April 2026, AAIF had grown to **170+ member organizations** and appointed Mazin Gilbert as its first permanent Executive Director.

**Platforms discussing:** Hacker News, Web (InfoQ, TechCrunch, IntuitionLabs, Paperclipped, agensi.io, firecrawl.dev)

**Sources:** https://www.agensi.io/learn/agent-skills-open-standard | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | https://openai.com/index/agentic-ai-foundation/ | https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/ | https://aaif.io/ | https://www.infoq.com/news/2025/12/agentic-ai-foundation/

---

### 2. Claude Code's Extension Architecture: Skills, Plugins, MCP, Hooks, Agent Teams

Claude Code now has a layered extension ecosystem that evolved rapidly over 18 months:

| Extension Type | Launched | Description |
|---|---|---|
| MCP (Model Context Protocol) | Nov 2024 | Client-server JSON-RPC; connects Claude to external tools and databases |
| Subagents | Jul 2025 | Spawn child Claude instances for parallel tasks |
| Hooks | Sep 2025 | Shell scripts triggered by Claude Code lifecycle events |
| Skills | Oct 2025 | SKILL.md files with YAML frontmatter; lazy-loaded procedural context |
| Plugins | Oct 2025 | Bundled distribution format: skills + hooks + MCP configs |
| Agent Teams | Feb 2026 | Multi-Claude squads that communicate directly, self-assign from shared task lists |

The canonical architecture is: **Skills are the content, Plugins are the distribution format.** A plugin bundles one or more skills with optional hooks, agents, and MCP server configurations, then distributes through a marketplace. Installation is as simple as `/plugin install`.

A key technical differentiator of skills over always-on MCP: skills are **lazy-loaded**, consuming only 30–50 tokens per skill until needed. Claude's MCP Tool Search feature extends this to MCP servers, reducing context usage by **up to 95%** compared to always-loaded configurations.

**Sources:** https://code.claude.com/docs/en/skills | https://code.claude.com/docs/en/plugins | https://code.claude.com/docs/en/agent-sdk/mcp | https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff?gi=d76373efe7aa | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | https://www.morphllm.com/claude-code-skills-mcp-plugins | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

---

### 3. The Marketplace Explosion: From One Registry to Eight in Five Months

The agent skills marketplace ecosystem grew from essentially one registry in December 2025 to at least eight major platforms by Q2 2026. Key platforms:

- **skills.sh** (Vercel, launched Jan 20, 2026): CLI-first, `npx skills add <package>`, leaderboard-driven discovery. 87,000+ skills, 19 agent platforms supported. Top skill: find-skills with 579,000+ installs. ([Vercel changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem))
- **LobeHub Skills**: 169,739 skills indexed, trust/discoverability/packaging focus. ([lobehub.com/skills](https://lobehub.com/skills))
- **claudemarketplaces.com**: 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces listed, 120,000+ monthly visitors. ([claudemarketplaces.com](https://claudemarketplaces.com/))
- **SkillsMP**: Cross-platform marketplace for Claude, Codex, ChatGPT skills. ([skillsmp.com](https://skillsmp.com/))
- **ClawHub**: 20,000+ skills registered.
- **agentskillshub.dev**: Security-focused marketplace with 45+ vulnerability patterns scanned per skill. ([agentskillshub.dev](https://agentskillshub.dev/))
- **Agensi**: Individual SKILL.md skills with security scanning + MCP-based live access. ([agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))
- **claudeskills.info**: Browse and download free skills. ([claudeskills.info/skills/](https://claudeskills.info/skills/))

The official Anthropic marketplace (built into Claude Code) contained **101 plugins as of March 2026**, including 33 Anthropic-built plugins covering language servers, dev workflow, setup tools, output styles, and messaging. The official repo `anthropics/skills` has **129k GitHub stars** and 15.2k forks.

**Sources:** https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | https://github.com/vercel-labs/skills | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481 | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | https://awesome-skills.com/

---

### 4. GitHub CLI Integration and the Toolchain Maturation Signal

On **April 16, 2026**, GitHub released `gh skill` as part of CLI v2.90.0 — the most significant signal that agent skills have entered mainstream developer tooling. The command provides discover/install/manage/publish for skills across Claude Code, GitHub Copilot, Cursor, Codex, and Gemini CLI.

The `gh skill` announcement emphasized **supply chain integrity** prominently: skills use content-addressed git tree SHAs for change detection, version pinning via git tags, and portable provenance data in frontmatter. The announcement explicitly warns: "Skills are installed at your own discretion. They are not verified by GitHub and may contain prompt injections, hidden instructions, or malicious scripts."

Community GitHub activity confirms mainstream adoption: `anthropics/skills` has 129k stars; "5 of the 10 trending GitHub repos are Claude tools"; VoltAgent's `awesome-agent-skills` (1,000+ curated skills) is heavily starred; multiple community-driven curation projects (`awesome-claude-plugins`, `glebis/claude-skills`, `alirezarezvani/claude-skills`) are active.

**Sources:** https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/ | https://github.com/anthropics/skills | https://github.com/VoltAgent/awesome-agent-skills | https://github.com/quemsah/awesome-claude-plugins | https://github.com/alirezarezvani/claude-skills | https://github.com/glebis/claude-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | https://github.com/mvanhorn/last30days-skill | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | https://www.ngjoo.com/en/trending/

---

### 5. Critical Security Crisis: MCP Architecture Flaws and Supply Chain Attacks

The most alarming development of April–May 2026 is a series of critical security disclosures targeting the MCP and Claude Code plugin ecosystems.

**The OX Security "Mother of All AI Supply Chains" disclosure (April 2026):** Researchers discovered an architectural flaw baked into Anthropic's official MCP SDKs across Python, TypeScript, Java, and Rust — unsafe STDIO defaults enabling Arbitrary Command Execution. The blast radius: **150M+ downloads**, **7,000+ exposed servers**, ~**200,000 vulnerable instances**. Commands were successfully executed on 6 live production platforms. Affected tools include LiteLLM, LangChain, IBM LangFlow, Cursor, Windsurf, VS Code, Claude Code, and Gemini-CLI. CVEs issued to 10 projects. Critically, **Anthropic declined to modify the protocol**, calling the behavior "expected."

**The Check Point RCE/exfiltration disclosures (published Feb 2026, patched beforehand):**
- **CVE-2025-59536**: Hooks in `.claude/settings.json` execute shell commands before the trust dialog appears, enabling RCE via malicious repos
- **CVE-2026-21852**: Malicious `ANTHROPIC_BASE_URL` in project settings intercepts API keys before trust confirmation

**Skill marketplace poisoning (ongoing):** Security audits found **12–20% of skills on at least one public marketplace were malicious**. agentskillshub.dev scans for 45+ vulnerability patterns; GitHub itself warns skills "may contain prompt injections."

**Claude Security public beta (May 1, 2026):** Anthropic launched Claude Security, built on Opus 4.7, scanning codebases for vulnerabilities — partly in response to this security environment. Available to Enterprise customers via claude.ai/security.

The HN ".claude/ folder anatomy" thread includes the starkest community advice: "you likely should never install ANY skill that you didn't create yourself."

**Platforms discussing:** Web (The Hacker News, SecurityWeek, Infosecurity Magazine, The Register, OX Security, Check Point, Help Net Security, Practical DevSecOps)

**Sources:** https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ | https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/ | https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/ | https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/ | https://blog.checkpoint.com/research/check-point-researchers-expose-critical-claude-code-flaws/ | https://www.mintmcp.com/blog/claude-code-cve | https://www.helpnetsecurity.com/2026/05/04/anthropic-claude-security-public-beta/ | https://www.infosecurity-magazine.com/news/anthropic-claude-security-for-ai/ | https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/ | https://www.practical-devsecops.com/mcp-security-vulnerabilities/ | https://ctdefense.com/mcp-security-vulnerabilities-risks/ | https://blog.cyberdesserts.com/ai-agent-security-risks/ | https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ | https://mcpmarket.com/tools/skills/security-analysis-vulnerability-scanner | https://github.com/trailofbits/skills | https://cybersecuritynews.com/cve-mcp-server-and-claude/

---

### 6. Community Debate: Productivity vs. Configuration Theater

The highest-engagement HN thread of the period — "Anatomy of the .claude/ folder" (627 points, 265 comments) — captures a sharp skeptical current running counter to the marketplace enthusiasm.

Core tension: elaborate `.claude/` configurations vs. minimal setups. Key arguments from skeptics:
- "Building your AI agent 'toolkit' is becoming the equivalent of the perfect 'productivity' setup" — time spent configuring tools > time using them
- "Plain Claude, ask it to write a plan, review plan, then tell it to execute still works the best"
- Claude doesn't reliably follow instructions as context fills or compaction occurs
- "Most of this stuff will go away within a year, obsoleted by improved models"
- Shared `.claude/` files in teams create consistency and testing challenges

The counterarguments: custom MCPs for niche APIs, accounting workflow automation, debugging tools, and team safety guardrails have genuine value. The key insight from Build to Launch's real-world review: "The best Claude Code stack in 2026 isn't the biggest one. It's the one where every entry pays rent. The best Claude Code users run 2–3 plugins max, and some run zero."

The Ensemble macOS app (MIT, Tauri 2 + React + Rust) emerged to address the organizational chaos of power users managing dozens of skills and MCP servers — a tooling meta-layer that itself signals ecosystem complexity has reached a pain point.

**Sources:** https://news.ycombinator.com/item?id=47543139 | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | https://news.ycombinator.com/item?id=46922223 | https://self.md/guides/best-claude-code-plugins/ | https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p | https://www.scriptbyai.com/claude-code-resource-list/

---

### 7. Skills vs. MCP Debate: Philosophies of Agent Customization

The "Claude Skills vs. MCP: Complementary Philosophies" thread and "Claude Skills are awesome, maybe a bigger deal than MCP" (738 pts, "Claude Skills" 816 pts) show sustained community engagement with the conceptual distinction.

Core technical difference:
- **MCP**: Client-server JSON-RPC; connects to live external systems (databases, APIs, services); upfront context cost; real-time data access
- **Skills**: Filesystem-based SKILL.md; procedural knowledge/workflows; lazy-loaded; no network by default; teaches "how" not "what"

TpTacek (HN): "Tool calls are incredibly interesting. MCP is just one means to that end, not one of the better ones." The Docker analogy gained traction: pseudosavant wrote "It would be like calling Docker/containers just some shell scripts for a kernel feature...conceptually simple, but...novel." The emerging consensus: they're complementary — skills for workflow encoding, MCP for live data access.

The steipete/claude-code-mcp project takes this to an extreme: running Claude Code as an MCP server itself, enabling "an agent in your agent."

**Sources:** https://news.ycombinator.com/item?id=45619537 | https://news.ycombinator.com/item?id=45607117 | https://news.ycombinator.com/item?id=45766686 | https://github.com/steipete/claude-code-mcp | https://www.ksred.com/claude-code-as-an-mcp-server-an-interesting-capability-worth-understanding/ | https://code.claude.com/docs/en/agent-sdk/mcp | https://systemprompt.io/guides/claude-code-mcp-servers-extensions | https://evomap.ai/blog/claude-code-mcp-setup-extensions-guide | https://claudefa.st/blog/tools/mcp-extensions/best-addons | https://claudefa.st/blog/tools/mcp-extensions/custom-integrations | https://claudefa.st/blog/tools/mcp-extensions/cursor-mcp-setup

---

### 8. Security Skills as First-Class Citizens

A notable specialized segment: skills for security research and vulnerability detection, validating the ecosystem's maturation.

- **Trail of Bits** shipped Claude Code skills specifically for security research, vulnerability detection, and audit workflows — with Codex-native skill discovery. ([github.com/trailofbits/skills](https://github.com/trailofbits/skills))
- The **CVE MCP Server** gives Claude access to 27 intelligence tools spanning 21 external APIs across 5 categories: Core Vulnerability Intelligence, Exploit & Attack Intelligence, Advanced Risk, Network Intelligence, Threat Intelligence. ([cybersecuritynews.com](https://cybersecuritynews.com/cve-mcp-server-and-claude/))
- **mcpmarket.com's Security Analysis skill** enables OWASP-pattern deep scans via slash command. ([mcpmarket.com](https://mcpmarket.com/tools/skills/security-analysis-vulnerability-scanner))
- **Claude Security** (public beta May 1): Opus 4.7-powered codebase scanning, integrated with CrowdStrike, Microsoft Security, Palo Alto Networks. ([helpnetsecurity.com](https://www.helpnetsecurity.com/2026/05/04/anthropic-claude-security-public-beta/))

**Sources:** https://github.com/trailofbits/skills | https://cybersecuritynews.com/cve-mcp-server-and-claude/ | https://mcpmarket.com/tools/skills/security-analysis-vulnerability-scanner | https://www.helpnetsecurity.com/2026/05/04/anthropic-claude-security-public-beta/

---

## Cross-Source Patterns

**Pattern 1: Supply chain security is the central unsolved problem**
- Appearing on: Web (The Hacker News, The Register, SecurityWeek, OX Security, Check Point, agensi.io), Hacker News
- 12–20% malicious skills in public marketplaces; architectural RCE flaw affecting 150M+ downloads; GitHub explicitly warning about skill safety; HN power users advising "never install a skill you didn't write yourself"
- Quote: "This is not a traditional coding error...an architectural design decision baked into Anthropic's official MCP SDKs across every supported programming language." — OX Security (https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/)

**Pattern 2: Skills are compelling but reliability is unproven**
- Appearing on: Hacker News (multiple threads), Web (buildtolaunch, self.md, dev.to)
- Skills don't reliably activate without explicit invocation; context compaction can cause Claude to stop following skill instructions; "Plain Claude still works best"
- Quote: "you likely should never install ANY skill that you didn't create yourself" — HN user, Anatomy of .claude/ thread (https://news.ycombinator.com/item?id=47543139)
- Quote: "Most of this stuff will go away within a year, obsoleted by improved models" — HN user (https://news.ycombinator.com/item?id=47543139)

**Pattern 3: The Docker analogy — simple primitives enabling rich ecosystems**
- Appearing on: Hacker News (both major Claude Skills threads), Web
- Multiple commenters independently compared SKILL.md to Docker: conceptually trivial but strategically important as a standardization layer
- Quote: "It would be like calling Docker/containers just some shell scripts for a kernel feature...conceptually simple, but...novel" — pseudosavant, HN (https://news.ycombinator.com/item?id=45607117)
- Quote: "essentially, dynamic context assembling with stuff crossing user boundaries" — ajtejankar, HN (https://news.ycombinator.com/item?id=45607117)

**Pattern 4: Marketplace proliferation → quality/signal/noise problem**
- Appearing on: Web (KDnuggets, agensi.io, agentskillshub.dev), Hacker News
- 8+ major marketplaces in 5 months; 169k+ skills on LobeHub alone; "getting hard to keep up with skills, plugins, marketplaces, connectors"; security audits catching 12–20% malicious content
- Signals the ecosystem maturity problem: discoverability, quality, and verification are the next frontier

**Pattern 5: Skills as "alive documentation" — AI feedback loops creating value**
- Appearing on: Hacker News (45619537, 45607117)
- Michael1999 (HN): "If you wrote some docs, you might never learn if they were any good... Now, you can iterate in minutes" — the economics of LLM feedback loops incentivize documentation creation that was previously unmotivated
- Multiple technical writers cited potential renaissance as "communication clarity becomes the limiting factor"

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| weinzierl | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | "MCP is just one means to that end, not one of the better ones." — TpTacek | https://news.ycombinator.com/item?id=45619537 |
| (unknown) | Claude Skills | 816 | 427 | "essentially, dynamic context assembling with stuff crossing user boundaries" — ajtejankar | https://news.ycombinator.com/item?id=45607117 |
| (unknown) | Anatomy of the .claude/ folder | 627 | 265 | "CLAUDE.md isn't documentation for Claude to read - it's an operating system" | https://news.ycombinator.com/item?id=47543139 |
| (unknown) | Customize Claude Code with plugins | 48 | 9 | "Distribution is going to be key here..." | https://news.ycombinator.com/item?id=45530150 |
| (unknown) | Show HN: Ensemble – macOS App to Manage Claude Code Skills | 1 | 1 | "managing them through ~/.claude.json and manual file editing gets old fast" | https://news.ycombinator.com/item?id=46922223 |
| (unknown) | Show HN: Playwright Skill for Claude Code | — | — | Less context than playwright-MCP | https://news.ycombinator.com/item?id=45642911 |
| (unknown) | Show HN: Real-time dashboard for Claude Code agent teams | — | — | Agent Teams observability | https://news.ycombinator.com/item?id=47602986 |
| (unknown) | Claude Skills vs. MCP: Complementary Philosophies | — | — | Skills + MCP are complementary, not competing | https://news.ycombinator.com/item?id=45766686 |
| (unknown) | Claude Code Emergent Behavior: When Skills Combine | — | — | Skill composition producing unexpected capabilities | https://news.ycombinator.com/item?id=46531794 |
| (unknown) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | — | Custom MCP approaches | https://news.ycombinator.com/item?id=43410866 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Engr Mejba Ahmed | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | — | — | No (metadata blocked) | https://www.youtube.com/watch?v=KjEFy5wjFQg |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | 4,200+ skills, 770+ MCPs, 2,500+ marketplaces directory |
| code.claude.com/docs | https://code.claude.com/docs/en/plugins | Official plugin architecture docs |
| code.claude.com/docs | https://code.claude.com/docs/en/skills | Official skills docs |
| code.claude.com/docs | https://code.claude.com/docs/en/agent-sdk/mcp | Official MCP docs |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Agent Skills API spec |
| code.claude.com/docs | https://code.claude.com/docs/en/plugin-marketplaces | Plugin marketplace creation docs |
| agensi.io | https://www.agensi.io/learn/agent-skills-open-standard | Open standard explainer |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Marketplace comparison |
| agensi.io | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Plugins vs Skills explainer |
| agensi.io | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Marketplace guide |
| agensi.io | https://www.agensi.io/learn/skills-marketplace-ai-agents | New App Store framing |
| vercel.com | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | skills.sh launch (Jan 20, 2026) |
| vercel.com | https://vercel.com/docs/agent-resources/skills | Vercel skills docs |
| github.blog | https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/ | gh skill command (Apr 16, 2026) |
| infoq.com | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Vercel skills ecosystem coverage |
| linuxfoundation.org | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | AAIF announcement |
| anthropic.com | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | Anthropic MCP donation |
| blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | MCP → AAIF |
| aaif.io | https://aaif.io/ | AAIF home |
| techcrunch.com | https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/ | AAIF TechCrunch coverage |
| openai.com | https://openai.com/index/agentic-ai-foundation/ | OpenAI AAIF announcement |
| block.xyz | https://block.xyz/inside/block-anthropic-and-openai-launch-the-agentic-ai-foundation | Block AAIF announcement |
| ox.security | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | MCP systemic vulnerability |
| ox.security | https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ | MCP supply chain CVEs |
| thehackernews.com | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | MCP design flaw coverage |
| theregister.com | https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ | MCP 'design flaw' 200k servers |
| securityweek.com | https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/ | SecurityWeek analysis |
| infosecurity-magazine.com | https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/ | 150M downloads affected |
| research.checkpoint.com | https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/ | CVE-2025-59536 / CVE-2026-21852 |
| blog.checkpoint.com | https://blog.checkpoint.com/research/check-point-researchers-expose-critical-claude-code-flaws/ | Check Point summary |
| mintmcp.com | https://www.mintmcp.com/blog/claude-code-cve | CVE enterprise guidance |
| helpnetsecurity.com | https://www.helpnetsecurity.com/2026/05/04/anthropic-claude-security-public-beta/ | Claude Security beta |
| infosecurity-magazine.com | https://www.infosecurity-magazine.com/news/anthropic-claude-security-for-ai/ | Claude Security feature detail |
| obot.ai | https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/ | MCP leak crisis post-mortem |
| practical-devsecops.com | https://www.practical-devsecops.com/mcp-security-vulnerabilities/ | MCP security prevention guide |
| ctdefense.com | https://ctdefense.com/mcp-security-vulnerabilities-risks/ | MCP security risks |
| aembit.io | https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ | Comprehensive MCP security guide |
| cyberdesserts.com | https://blog.cyberdesserts.com/ai-agent-security-risks/ | AI agent security risks |
| cybersecuritynews.com | https://cybersecuritynews.com/cve-mcp-server-and-claude/ | CVE MCP server capabilities |
| github.com/trailofbits | https://github.com/trailofbits/skills | Trail of Bits security skills |
| mcpmarket.com | https://mcpmarket.com/tools/skills/security-analysis-vulnerability-scanner | OWASP security analysis skill |
| github.com/anthropics | https://github.com/anthropics/skills | Anthropic official skills (129k stars) |
| github.com/anthropics | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Official plugin marketplace JSON |
| github.com/VoltAgent | https://github.com/VoltAgent/awesome-agent-skills | 1000+ curated cross-platform skills |
| github.com/vercel-labs | https://github.com/vercel-labs/skills | Vercel skills CLI |
| github.com/vercel-labs | https://github.com/vercel-labs/agent-skills | Vercel official agent skills |
| github.com/steipete | https://github.com/steipete/claude-code-mcp | Claude Code as MCP server |
| github.com/jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2810 skills |
| github.com/quemsah | https://github.com/quemsah/awesome-claude-plugins | Plugin adoption metrics via n8n |
| github.com/alirezarezvani | https://github.com/alirezarezvani/claude-skills | 232+ Claude Code skills |
| github.com/glebis | https://github.com/glebis/claude-skills | Community skills collection |
| github.com/mvanhorn | https://github.com/mvanhorn/last30days-skill | last30days skill (#1 trending) |
| lobehub.com | https://lobehub.com/skills | LobeHub 169k+ skills |
| skillsmp.com | https://skillsmp.com/ | Cross-platform skills marketplace |
| agentskillshub.dev | https://agentskillshub.dev/ | Secure marketplace |
| claudeskills.info | https://claudeskills.info/skills/ | Free skills browsing |
| awesome-skills.com | https://awesome-skills.com/ | Curated skills list |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins guide |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Claude Code tools |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP servers |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/custom-integrations | Custom MCP integrations |
| claudefa.st | https://claudefa.st/blog/tools/skills/best-claude-code-skills | Best Claude Code skills |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/cursor-mcp-setup | Cursor MCP setup |
| systemprompt.io | https://systemprompt.io/guides/claude-code-mcp-servers-extensions | MCP setup guide |
| evomap.ai | https://evomap.ai/blog/claude-code-mcp-setup-extensions-guide | MCP extensions guide |
| ksred.com | https://www.ksred.com/claude-code-as-an-mcp-server-an-interesting-capability-worth-understanding/ | Claude Code as MCP server |
| kdnuggets.com | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 marketplaces |
| towardsai.net | https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff?gi=d76373efe7aa | Extensions architecture overview |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete agent skills guide |
| tonykipkemboi.com | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | Agent skills explained |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 guide |
| dev.to | https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p | Practical skills guide |
| buildtolaunch.substack.com | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | 10 tested, 4 worth keeping |
| self.md | https://self.md/guides/best-claude-code-plugins/ | Best plugins guide |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate resource list |
| medium.com | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills |
| firecrawl.dev | https://www.firecrawl.dev/blog/agent-skills | How SKILL.md files work |
| paperclipped.de | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | 32 tools interoperability |
| thepromptindex.com | https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html | Complete SKILL.md guide |
| itecsonline.com | https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 | Codex CLI skills guide |
| aidesigner.ai | https://www.aidesigner.ai/blog/claude-code-skills | Claude Code skills guide |
| intuitionlabs.ai | https://intuitionlabs.ai/articles/agentic-ai-foundation-open-standards | AAIF open standards guide |
| solo.io | https://www.solo.io/blog/aaif-announcement-agentgateway | AAIF + enterprise security |
| blog.devgenius.io | https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481 | Vercel registry top-10 analysis |
| virtualuncle.com | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | skills.sh guide |
| docs.litellm.ai | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | LiteLLM plugin marketplace tutorial |
| claudepluginhub.com | https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills | alirezarezvani skills marketplace |
| ngjoo.com | https://www.ngjoo.com/en/trending/ | GitHub trending tracker |

---

## Stats Block

```
├─ 🟢 HN: 10 stories │ ~2,230+ points │ ~1,370+ comments
├─ 🔴 YouTube: 1 video │ views N/A (metadata blocked)
├─ 🌐 Web: 65+ pages
└─ 🗣️ Top voices: simonw (Simon Willison), pseudosavant, ajtejankar, TpTacek, Michael1999 │ r/ no Reddit data
```

---

## Data Gaps

- **Reddit**: No Reddit data retrieved — a significant gap given the r/ClaudeAI, r/LocalLLaMA, and r/programming communities are likely discussing these topics actively. Estimated coverage: 0%.
- **X/Twitter**: Excluded per research protocol. Missing developer discourse and real-time reactions to security disclosures.
- **TikTok / Instagram / Bluesky**: No data retrieved. Agent skills ecosystem has minimal presence on short-form video/social platforms in this data pull.
- **Polymarket**: No prediction markets found for this topic cluster.
- **YouTube engagement metrics**: The KjEFy5wjFQg video returned only footer HTML — no view/like counts extractable.
- **HN thread points for items 4, 7–10**: The five lower-engagement HN items didn't have points/comments extracted in fetches; exact numbers unknown.
- **LobeHub engagement**: Skills count (169,739) confirmed but per-skill engagement data not collected.
- **Marketplace security audit sourcing**: The "12–20% malicious skills" stat appears on multiple sources but original audit paper not verified.
- **Approximate overall coverage**: ~70% of web/HN discourse captured; ~0% of social/Reddit/X; ~50% of GitHub ecosystem activity.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — simonw (Simon Willison) on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "It would be like calling Docker/containers just some shell scripts for a kernel feature...conceptually simple, but...novel" — pseudosavant on Hacker News ([link](https://news.ycombinator.com/item?id=45607117))

> "essentially, dynamic context assembling with stuff crossing user boundaries" — ajtejankar on Hacker News ([link](https://news.ycombinator.com/item?id=45607117))

> "CLAUDE.md isn't documentation for Claude to read - it's an operating system" — anonymous on Hacker News ([link](https://news.ycombinator.com/item?id=47543139))

> "you likely should never install ANY skill that you didn't create yourself" — anonymous on Hacker News ([link](https://news.ycombinator.com/item?id=47543139))

> "This is not a traditional coding error...an architectural design decision baked into Anthropic's official MCP SDKs across every supported programming language." — OX Security ([link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/))

> "The line between configuration and execution continues to blur, requiring us to treat project setup files with the same careful attention we apply to executable code." — Check Point Research ([link](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/))

> "If you wrote some docs, you might never learn if they were any good... Now, you can iterate in minutes" — Michael1999 on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Distribution is going to be key here... plugin maintainers do not want to have to build a marketplace as well as a plugin." — anonymous on Hacker News ([link](https://news.ycombinator.com/item?id=45530150))

> "The best Claude Code stack in 2026 isn't the biggest one. It's the one where every entry pays rent." — Build to Launch ([link](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review))
