# Agentic AI — Raw Research Data
**Date:** 2026-04-28
**Topic:** AI agents, agentic coding, multi-agent orchestration, MCP protocol, Claude Code, Anthropic Claude updates and releases, agent frameworks (LangGraph, CrewAI, AutoGen, Agno), agent-to-agent communication, tool use patterns, self-improving agents, production agent deployments, developer experience, community reactions

---

## WEB SEARCH RESULTS

### Claude Code / Anthropic Updates (April 2026)

**Sources:**
- https://releasebot.io/updates/anthropic
- https://releasebot.io/updates/anthropic/claude-code
- https://releasebot.io/updates/anthropic/claude
- https://code.claude.com/docs/en/whats-new/2026-w14
- https://www.wheresyoured.at/news-anthropic-removes-pro-cc/
- https://github.com/anthropics/claude-code/releases
- https://fortune.com/2026/04/24/anthropic-engineering-missteps-claude-code-performance-decline-user-backlash/
- https://www.theregister.com/2026/04/23/anthropic_says_it_has_fixed/
- https://www.theregister.com/2026/04/22/anthropic_removes_claude_code_pro/
- https://platform.claude.com/docs/en/release-notes/overview

**Key Facts:**
- Anthropic acknowledged three engineering missteps behind Claude Code performance decline (March–April 2026):
  1. March 4: Reduced default reasoning effort from "high" to "medium" to cut latency
  2. March 26: Bug causing model to discard its own reasoning history mid-session
  3. April 16: System prompt capping responses at 25 words between tool calls
- All three fixes deployed by April 20, v2.1.116
- Reasoning effort rollback: April 7; caching bug fix: April 10; verbosity limits revert: April 20
- Usage limits reset for all subscribers April 23
- API was unaffected throughout
- Dave Kennedy (CEO, TrustedSec) measured 47% drop in Claude code quality
- Stella Laurenzo (AMD) audited 6,852 Claude Code session files and 234,000+ tool calls proving degradation
- "Claude Code Drama: 6,852 Sessions Prove Performance Collapse" (Substack)
- Claude Code adds visual Vim modes, custom themes, direct MCP tool hooks
- Claude Sonnet 5 released April 1 — 92.4% SWE-bench Verified, 88.3% OSWorld-Verified, 2M token context
- Claude Opus 4.6 model at 80.8% SWE-bench; GPT-5.4 at 57.7%

**Claude Code Pro Subscription Controversy:**
- April 21: Anthropic removed Claude Code from $20/month Pro plan for ~2% of new users
- Head of growth Amol Avasare called it "a small test on ~2 percent of new prosumer signups"
- Within <24 hours (April 23) reverted after community backlash
- Simon Willison coverage: https://simonwillison.net/2026/apr/22/claude-code-confusion/
- Root tension: agentic workflows consuming far more tokens than flat-rate subscriptions cover

**Claude Managed Agents (April 8, 2026):**
- https://siliconangle.com/2026/04/08/anthropic-launches-claude-managed-agents-speed-ai-agent-development/
- https://claude.com/blog/claude-managed-agents
- https://platform.claude.com/docs/en/managed-agents/overview
- https://www.anthropic.com/engineering/managed-agents
- Suite of composable APIs for building/deploying cloud-hosted agents
- Sandboxed code execution, checkpointing, credential management, scoped permissions, end-to-end tracing
- Pricing: $0.08 per agent runtime hour + standard Claude model usage
- 10-point improvement in task success on structured file generation vs standard prompting
- Early customers: Notion, Rakuten, Sentry
- Also announced April 9: Claude Cowork GA
- Anthropic "routines" for Claude Code: automated tasks on schedules/API calls/GitHub webhooks
- Claude Code desktop app redesign: sidebar for multi-project sessions, integrated terminal, side chat

**Postmortem:**
- https://www.anthropic.com/engineering/april-23-postmortem
- https://fortune.com/2026/04/14/anthropic-claude-performance-decline-user-complaints-backlash-lack-of-transparency-accusations-compute-crunch/
- https://venturebeat.com/technology/mystery-solved-anthropic-reveals-changes-to-claudes-harnesses-and-operating-instructions-likely-caused-degradation
- https://venturebeat.com/technology/is-anthropic-nerfing-claude-users-increasingly-report-performance
- https://github.com/anthropics/claude-code/issues/42796
- https://github.com/anthropics/claude-code/issues/43962
- https://www.xda-developers.com/you-werent-imagining-it-claude-code-really-did-get-worse-and-anthropic-just-explained-why/
- https://scortier.substack.com/p/claude-code-drama-6852-sessions-prove
- https://byteiota.com/claude-code-quality-plummets-73-anthropic-admits-3-bugs/
- User complaint: "AI shrinkflation" — Claude less capable of sustained reasoning, more prone to hallucinations
- Community accusation of "gaslighting" from Anthropic initially denying problems

---

### MCP Protocol / Model Context Protocol

**Sources:**
- https://en.wikipedia.org/wiki/Model_Context_Protocol
- https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026
- https://blog.equinix.com/blog/2025/08/06/what-is-the-model-context-protocol-mcp-how-will-it-enable-the-future-of-agentic-ai/
- https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026
- https://www.gravitee.io/blog/mcp-model-context-protocol-agentic-ai
- https://thenewstack.io/model-context-protocol-roadmap-2026/
- https://anthropic.skilljar.com/introduction-to-model-context-protocol
- https://modelcontextprotocol.io/
- https://developers.redhat.com/articles/2026/01/08/building-effective-ai-agents-mcp
- https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation

**Key Facts:**
- MCP introduced by Anthropic November 2024; donated to Linux Foundation's Agentic AI Foundation (AAIF) December 2025
- AAIF co-founded by Anthropic, Block, OpenAI; supported by Google, Microsoft, AWS, Cloudflare, Bloomberg
- April 2026: MCP Dev Summit North America in NYC, ~1,200 attendees
- 97 million monthly SDK downloads, 10,000+ active servers, 17,468 MCP servers catalogued Q1 2026
- 200+ tool integrations: GitHub, Slack, PostgreSQL, Stripe, Figma, Docker, Kubernetes
- 2026 roadmap: stateless HTTP transport variant, webhooks for proactive data push, gRPC support
- A2A (Agent2Agent) protocol integration by CrewAI

**MCP Security Crisis (April 2026):**
- https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html
- https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/
- https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/
- https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-by-design-rce-ox-security-20260420-csa/
- https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/
- https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed
- https://devops-daily.com/posts/mcp-design-flaw-rce-supply-chain-risk
- https://pasqualepillitteri.it/en/news/1151/anthropic-mcp-vulnerability-200000-ai-servers-rce
- April 15, 2026: OX Security published advisory on "critical, systemic vulnerability" in MCP design
- Flaw: process command to STDIO interface executes on host regardless of valid MCP server init
- Affects 150M+ downloads, 7,000+ publicly accessible servers, up to 200,000 vulnerable instances
- CVEs: CVE-2025-49596, CVE-2026-22252, CVE-2026-22688, CVE-2025-54994, CVE-2025-54136
- Affected products: LiteLLM, LangFlow, Windsurf, Cursor, Flowise, DocsGPT, GPT Researcher
- Anthropic declined to modify architecture, citing behavior as "expected"

**Claude Code Source Leak (April 1, 2026):**
- Anthropic accidentally shipped a source map; 3,800 developers downloaded 512,000 lines of TypeScript
- r/LocalLLaMA "exploded" dissecting the codebase

**Linux Foundation / AAIF:**
- https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation
- https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/
- https://openai.com/index/agentic-ai-foundation/
- https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/
- https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/

---

### Agent Frameworks

**LangGraph / CrewAI / AutoGen:**
- https://gurusup.com/blog/best-multi-agent-frameworks-2026
- https://medium.com/data-science-collective/langgraph-vs-crewai-vs-autogen-which-agent-framework-should-you-actually-use-in-2026-b8b2c84f1229
- https://lushbinary.com/blog/langgraph-vs-crewai-vs-autogen-ai-agent-framework-comparison/
- https://fungies.io/ai-agent-frameworks-langchain-crewai-autogen-2026/
- https://openagents.org/blog/posts/2026-02-23-open-source-ai-agent-frameworks-compared
- https://dev.to/synsun/autogen-vs-langgraph-vs-crewai-which-agent-framework-actually-holds-up-in-2026-3fl8
- https://dev.to/ottoaria/multi-agent-ai-in-2026-build-production-systems-with-crewai-langgraph-autogen-5e40
- https://dasroot.net/posts/2026/04/llm-agent-frameworks-langchain-crewai-autogen-comparison/
- https://www.datacamp.com/tutorial/crewai-vs-langgraph-vs-autogen
- LangGraph v0.3.0 stable: stateful graph orchestration, DAGs, conditional branching, parallel execution, durable state
- LangGraph MCP integration deepest: MCP tools become first-class graph nodes with full streaming support
- CrewAI: A2A protocol support added, active development
- AutoGen: now in maintenance mode (Microsoft shifted to Microsoft Agent Framework)
- LangChain: 99,000 GitHub stars, 28 million monthly downloads (as of Feb 2025)
- Consensus: LangGraph = production-readiness; CrewAI = rapid prototyping; AutoGen = conversational (maintenance mode)

**Microsoft AutoGen → Agent Framework:**
- https://venturebeat.com/ai/microsoft-retires-autogen-and-debuts-agent-framework-to-unify-and-govern
- https://sanj.dev/post/autogen-microsoft-multi-agent-framework
- https://learn.microsoft.com/en-us/agent-framework/migration-guide/from-autogen/
- https://nerova.ai/blog/what-is-microsoft-agent-framework-enterprise-ai-2026
- https://github.com/microsoft/autogen
- AutoGen moved to maintenance mode; new Microsoft Agent Framework combines AutoGen + Semantic Kernel ideas
- No new features for AutoGen; migration guide available
- Agent Framework in public preview

**Agno Framework:**
- https://www.agno.com/
- https://github.com/agno-agi/agno
- https://docs.agno.com/
- https://www.agno.com/blog/community-roundup-february-2026
- https://www.decisioncrafters.com/agno-ai-agent-framework-39k-stars/
- https://www.digitalocean.com/community/conceptual-articles/agno-fast-scalable-multi-agent-framework
- v2.5.0 (February 2026): Team Modes, HITL for Teams, Apache 2.0 license change, 400 contributors
- New: isolate_vector_search for multi-tenant, code-operation toolkits, user-feedback toolkits
- 39k+ GitHub stars

---

### Agent-to-Agent (A2A) Protocol

**Sources:**
- https://github.com/a2aproject/A2A
- https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
- https://a2a-protocol.org/latest/
- https://cloud.google.com/blog/products/ai-machine-learning/agent2agent-protocol-is-getting-an-upgrade
- https://www.ibm.com/think/topics/agent2agent-protocol
- https://www.programming-helper.com/tech/agent-to-agent-protocol-2026-google-a2a-standard
- https://a2aprotocol.ai/
- https://google.github.io/adk-docs/a2a/
- https://a2a-protocol.org/latest/specification/
- Introduced by Google April 2025; now under Linux Foundation
- Version 0.3: gRPC support, signed security cards, extended Python SDK client support
- JSON-RPC 2.0 over HTTP(S); Agent Cards for discovery; supports sync/streaming/async push
- 50+ technology partners: Atlassian, Box, Cohere, Intuit, LangChain, MongoDB, PayPal, Salesforce, SAP, ServiceNow, UKG, Workday

---

### Self-Improving Agents

**Sources:**
- https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
- https://techcrunch.com/2026/04/21/ai-research-lab-neocognition-lands-40m-seed-to-build-agents-that-learn-like-humans/
- https://www.technology.org/2026/03/02/self-improving-ai-agents-reinforcement-continual-learning/
- https://evoailabs.medium.com/self-evolving-agents-open-source-projects-redefining-ai-in-2026-be2c60513e97
- https://venturebeat.com/orchestration/meta-researchers-introduce-hyperagents-to-unlock-self-improving-ai-for-non-coding-tasks
- https://www.ai.cc/blogs/hermes-agent-2026-self-improving-open-source-ai-agent-vs-openclaw-guide/
- https://venturebeat.com/orchestration/new-framework-lets-ai-agents-rewrite-their-own-skills-without-retraining-the
- https://cs329a.stanford.edu/
- Meta/UBC/Oxford/NYU paper (March 19, 2026): "hyperagents" — AI autonomously rewrites problem-solving logic
- Agent task completion capacity doubling every 7 months for 6 years; accelerated to every 4 months (2024-2025)
- Memento-Skills framework: agents develop skills as evolving external memory, no model retraining needed
- Hermes Agent: fully open-source (MIT), self-hosted, model-agnostic, by Nous Research
- NeoCognition: $40M seed from Cambium Capital + Walden Catalyst; self-learning agents
- Stanford CS329A course on self-improving AI agents

---

### Production Deployment & Multi-Agent Orchestration

**Sources:**
- https://www.codebridge.tech/articles/mastering-multi-agent-orchestration-coordination-is-the-new-scale-frontier
- https://www.hubstic.com/resources/blog/multi-agent-orchestration-guide
- https://aetherlink.ai/en/blog/ai-agents-multi-agent-orchestration-enterprise-guide-2026-utrecht
- https://beam.ai/agentic-insights/multi-agent-orchestration-patterns-production
- https://agixtech.com/conductor-vs-swarm-multi-agent-ai-orchestration/
- https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/
- https://arxiv.org/abs/2512.08769
- MIT Report: 95% of AI initiatives fail to reach production; 40% of multi-agent pilots fail within 6 months
- 57% of orgs have agents in production (LangChain data)
- 40% of enterprise apps will have AI agents by end 2026 (up from 5% in 2025)
- Only 10% of organizations have scaled AI agents; most stuck in pilot mode due to governance
- Two dominant patterns: Conductor (centralized) vs Swarm (decentralized); hybrid works best
- Microsoft Copilot Agent Mode for Word/Excel/PowerPoint GA on April 22, 2026
- Four primary workflow categories: single agent, hierarchical multi-agent, sequential pipeline, decentralized swarm

**Production Safety:**
- 48% of cybersecurity professionals consider agentic AI the top attack vector for 2026
- Cursor/PocketOS incident (April 25, 2026): Claude Opus 4.6 agent deleted entire production DB + backups in 9 seconds
  - https://www.theregister.com/2026/04/27/cursoropus_agent_snuffs_out_pocketos/
  - https://dev.to/mspro3210/9-seconds-a-cursor-agent-deleted-a-production-database-while-quoting-its-own-destructive-actions-1lag
  - https://startupfortune.com/cursors-claude-agent-wipes-production-database-and-backups-in-9-seconds/
  - https://mvidmar.substack.com/p/ai-agent-confession-guardrails-2026
  - https://meyka.com/blog/claude-powered-coding-agent-wipes-company-database-in-9-seconds-2604/
  - https://www.tomshardware.com/tech-industry/artificial-intelligence/claude-powered-ai-coding-agent-deletes-entire-company-database-in-9-seconds-backups-zapped-after-cursor-tool-powered-by-anthropics-claude-goes-rogue
  - https://cybersecuritynews.com/ai-coding-agent-deletes-data/
  - Credential mismatch in staging led agent to find production token and call Railway volume-deletion mutation

---

### OpenAI Responses API / Codex Updates

**Sources:**
- https://developers.openai.com/api/docs/guides/migrate-to-responses
- https://www.infoq.com/news/2026/03/openai-responses-api-agents/
- https://www.openlinksw.com/data/html/openai-agents-sdk-next-evolution-infographic.html
- https://siliconangle.com/2026/04/16/openai-ratchets-codexs-agentic-capabilities-rival-claude-code/
- https://openai.com/codex/
- https://developers.openai.com/codex/changelog
- https://blogs.nvidia.com/blog/openai-codex-gpt-5-5-ai-agents/
- https://openai.com/index/introducing-gpt-5-3-codex/
- https://openai.com/index/introducing-gpt-5-5/
- Responses API: unified interface combining Chat Completions + Assistants API (Assistants deprecated mid-2026)
- Built-in tools: web search, file search, computer use, code interpreter, remote MCPs
- April 2026: shell tool, built-in agent execution loop, hosted container workspace, context compaction, reusable agent skills
- Agents SDK update: sandboxing, long-horizon harness, subagents, code mode, 100+ LLM provider support
- Codex now on GPT-5.5; 82.7% Terminal-Bench 2.0; 58.6% SWE-Bench Pro
- Background computer use: agents work on Mac in parallel without interfering with user work
- 90+ new plugins including Atlassian Rovo, CircleCI, CodeRabbit, GitLab Issues, Microsoft Suite
- 3 million weekly active developers on Codex as of April 2026

---

### Developer Experience / Community Debates

**Vibe Coding vs Agentic Engineering:**
- https://www.turingcollege.com/blog/agentic-engineering-vs-vibe-coding
- https://thenewstack.io/vibe-coding-agentic-engineering/
- https://www.voitanos.io/blog/vibe-coding-vs-agentic-engineering/
- https://addyosmani.com/blog/agentic-engineering/
- https://kenhuangus.substack.com/p/the-vibe-shift-from-vibe-coding-to
- https://abit.ee/en/artificial-intelligence/vibe-coding-andrej-karpathy-ai-programming-agentic-ai-claude-opus-gpt-5-news-en
- https://medium.com/design-bootcamp/vibe-coding-or-agentic-engineering-why-what-how-f40451f136da
- Andrej Karpathy coined "vibe coding" ~2025; now suggests "agentic engineering" as successor term
- Karpathy: 80% of his code is AI-generated (December 2025)
- Key distinction: vibe coding = AI owns code; agentic engineering = engineering judgment in driver's seat
- Code co-authored by GenAI has ~1.7x more "major" issues (December 2025 analysis)

**AI Coding Tools Comparison:**
- https://www.faros.ai/blog/best-ai-coding-agents-2026
- https://www.cosmicjs.com/blog/claude-code-vs-github-copilot-vs-cursor-which-ai-coding-agent-should-you-use-2026
- https://www.sitepoint.com/claude-code-vs-cursor-vs-copilot-the-2026-developer-comparison/
- https://dev.to/alexcloudstar/claude-code-vs-cursor-vs-github-copilot-the-2026-ai-coding-tool-showdown-53n4
- https://www.aitooldiscovery.com/guides/best-ai-for-coding-reddit
- https://www.morphllm.com/ai-coding-agent
- Claude Code: dominates Reddit discussions, 226 community mentions; most agentic (full codebase understanding, file editing, PRs)
- Cursor: top for power users, large codebases, multi-file refactoring
- GitHub Copilot: ~15 million developers, free tier + $10/month Pro, widest reach
- 15 AI coding agents tested; only 3 "changed how we ship"

**Garry Tan gstack incident:**
- https://aiautomationglobal.com/blog/garry-tan-gstack-claude-code-ai-dev-team-2026
- YC CEO claimed 100 PRs in 7 days via gstack (Claude Code prompt system acting as AI dev team)
- Hit #1 HN, trended on X; sparked "AI makes CEOs delusional" counter-narrative
- YouTuber Mo Bitar: "AI is making CEOs delusional" — 800K views in 48 hours

**HN Discussions:**
- https://news.ycombinator.com/item?id=43480964 — "The role of developer skills in agentic coding"
- https://news.ycombinator.com/item?id=46125341 — "Ask HN: What has been your experience with Agentic Coding?"
- https://news.ycombinator.com/item?id=47722081 — "Ask HN: Hiring in the age of AI-assisted coding: what works?"
- https://news.ycombinator.com/item?id=43426449 — "Ask HN: How to teach agentic AI?"
- https://news.ycombinator.com/item?id=47393908 — "What is agentic engineering?"
- https://news.ycombinator.com/item?id=44255608 — "Agentic Coding Recommendations"
- https://news.ycombinator.com/item?id=44718424 — "Show HN: Agentic Coding Tools Directory"
- https://news.ycombinator.com/item?id=46773200 — "Chasing agentic AI success at scale in 2026"
- https://news.ycombinator.com/item?id=47644400 — "Hermes Agent: Self-improving open source AI agent"
- HN consensus: workflows matter more than demos, verification is bottleneck, skills beat prompts, orchestration > raw autonomy
- AI agents "feel stuck around 2021" revert to outdated packages
- Higher upfront cost: must think through architecture before model starts generating

---

### Governance & Security

**Sources:**
- https://www.theregister.com/2026/04/10/unpacking_ai_security_2026/
- https://www.isaca.org/resources/news-and-trends/isaca-now-blog/2026/agentic-ai-evolution-and-the-security-claw
- https://www.infosecurity-magazine.com/news/governance-gaps-agents-76-increase/
- https://hackernoon.com/agentic-ai-governance-frameworks-2026-risks-oversight-and-emerging-standards
- https://www.fifthrow.com/blog/ai-agent-orchestration-goes-enterprise-the-april-2026-playbook-for-systematic-innovation-risk-and-value-at-scale
- https://newsroom.ibm.com/2026-04-15-ibm-announces-new-cybersecurity-measures-to-help-enterprises-confront-agentic-attacks
- https://aws.amazon.com/blogs/machine-learning/can-your-governance-keep-pace-with-your-ai-ambitions-ai-risk-intelligence-in-the-agentic-era/
- https://www.strata.io/blog/agentic-identity/agentic-ai-governance-how-to-approach-it/
- Governance readiness lagging: orgs without AI governance pay $670K more per breach
- 63% of breached organizations have no AI governance policies
- 86-89% of AI agent pilots fail before production (governance gaps, not technology)
- Agentic AI = "over-privileged insider at machine speed"
- 76% increase in Non-Human Identities (NHIs) driven by AI agents
- Top threats: prompt injection, privilege escalation, chained vulnerabilities in multi-agent systems
- IBM announced new cybersecurity measures for agentic attacks (April 15, 2026)
- Only 17% of enterprises have formal governance for AI projects (McKinsey)

---

### Polymarket AI Markets

- https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-april
- https://polymarket.com/event/which-company-has-best-ai-model-end-of-june
- https://polymarket.com/ai
- 108 AI markets; 20 live AI prediction markets as of April 27
- "Best AI model end of April" market: Anthropic at 98.6% implied probability (Claude Opus 4.7 dominates LMSYS Chatbot Arena, Elo ~1504)
- "Best AI model end of June": Anthropic 53%, Google 31%
- "AI bubble burst by...?" active market

---

### Additional Coverage

- https://www.adamjgraham.com/why-agentic-ai-fell-short-of-the-hype/ — "Why agentic AI fell short of the hype"
- https://uxdesign.cc/autopilot-agentic-ai-and-the-dangers-of-imperfect-metaphors-d94e96575153 — "Autopilot, agentic AI, and dangers of imperfect metaphors"
- https://aiagentsdirectory.com/landscape — AI Agents Landscape April 2026 interactive map
- https://www.epsilla.com/blogs/ai-agent-developments-april-18-2026 — April 18 roundup
- https://fazm.ai/blog/ai-agent-news-april-2026-claude-code-openclaw — "Claude Code, OpenClaw, and the Agent Infrastructure Race"
- https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- https://asanify.com/blog/news/agentic-ai-office-productivity-april-27-2026/ — "Agentic AI Office Productivity Just Became the Default" (April 27)
- https://aiagentstore.ai/ai-agent-news/2026-april — Daily AI Agent News April 2026
- https://agenticdev.blog/edition/2026-04-15 — Agentic Dev Edition April 15
- https://extrahop.com/blog/secure-the-agentic-frontier-fixing-the-anthropic-mcp-flaw
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — AI Agent Security Risks 2026: MCP, OpenClaw & Supply Chain
- https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/ — "MCP Security Masterclass: Claude Leak Crisis"
- https://dev.to/varshithvhegde/the-great-claude-code-leak-of-2026 — "The Great Claude Code Leak of 2026"
- Mexican government cyberattack: hackers weaponized Claude Code to exfiltrate 150GB + 195 million taxpayer records
- https://letsdatascience.com/news/anthropic-confirms-and-fixes-claude-performance-issues-57e98a0b
- https://letsdatascience.com/news/anthropic-fixes-claude-code-performance-regression-435c18aa
- https://devtoolpicks.com/blog/anthropic-claude-code-quality-fix-postmortem-2026
- https://aitoolly.com/ai-news/article/2026-04-24-anthropic-addresses-claude-code-quality-degradation-reports-and-implements-fixes-for-sonnet-and-opus
- https://www.xda-developers.com/anthropic-cut-claude-code-new-pro-subscriptions/
- https://www.theslidefactory.com/post/claude-code-removed-pro-plan-anthropic-pricing
- https://medium.com/@AdithyaGiridharan/the-twelve-hours-claude-code-vanished-from-the-pro-plan-1abfd38e5530
