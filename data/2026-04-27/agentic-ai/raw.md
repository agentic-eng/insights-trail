# Agentic AI — Raw Research Output
**Date:** 2026-04-27
**Topic:** AI agents, agentic coding, multi-agent orchestration, MCP protocol, Claude Code, Anthropic Claude updates and releases, agent frameworks (LangGraph, CrewAI, AutoGen, Agno), agent-to-agent communication, tool use patterns, self-improving agents, production agent deployments, developer experience, community reactions

---

## HACKER NEWS

### 1. "We tasked Opus 4.6 using agent teams to build a C Compiler"
- **URL:** https://news.ycombinator.com/item?id=46903616
- **Points:** 735
- **Comments:** 738
- **Key Comments:**
  - **ndesaulniers**: "The compiler cost nearly $20,000 across 2,000 Claude sessions. Successfully produces bootable Linux on x86, ARM, and RISC-V architectures. However, the generated code is inefficient: outputs less efficient code than GCC with all optimizations disabled."
  - **shakna**: "Claude relies on GCC for the 16-bit x86 bootstrap phase rather than implementing it natively."
  - **Philpax**: Defended the accomplishment: "the compiler itself functions properly—it simply cannot generate optimized-enough code for one specific, tiny bootloader constraint."
  - **disgruntledphd2**: "Notes this represents genuine progress in AI capabilities. Emphasizes the importance of comprehensive test suites enabling this success."

### 2. "Claude Code's new hidden feature: Swarms"
- **URL:** https://news.ycombinator.com/item?id=46743908
- **Points:** 521
- **Comments:** 335
- **Key Comments:**
  - **mafriese**: "I actually got the best quality of code (completely ignoring that the cost is likely 10x more) by having a full 'project team'" — used 9 different Claude agents across roles (Manager, Product Owner, Scrum Master, Architect, Archaeologist, CAB, Dev Pair, Librarian). "Agents are 'fighting against' each other to some extend? The Architect tries to design while the CAB tries to reject."
  - **alphazard**: Skeptical — questioning whether role-based management actually works, suggesting simpler explanations (adversarial techniques, parallelism, model selection) better explain improvements.
  - **rlayton2**: "The main reason splitting up work is effective is context management."
  - **purplepatrick**: "Task isolation, rather than preserving your current session's context budget, is where subagents shine."

### 3. "Claude Managed Agents"
- **URL:** https://news.ycombinator.com/item?id=47693047
- **Points:** 169
- **Comments:** 86
- **Key Comments:**
  - **jameslk**: "We're in the early days of agentic frameworks, like the pre-PHP web."
  - **cedws**: "Anthropic wants to shift developers on to their platform where they're in control." — platform move signals IPO positioning.
  - **0o_MrPatrick_o0**: "Being locked into a single model provider is a deal breaker."
  - **mccoyb**: "The best performance...is by mixing agents from different companies."
  - **lifecodes**: "MANAGED AGENTS sounds like progress, but also like we're standardizing around current limitations."

### 4. "MCP is a fad"
- **URL:** https://news.ycombinator.com/item?id=46552254
- **Points:** 145
- **Comments:** 117
- **Key Comments:**
  - **kburman**: "MCP allows any client (Claude, Cursor, IDEs) to dynamically discover and interact with any resource (Postgres, Slack) without custom glue code."
  - **embedding-shape**: "We already had the 'HTTP API' movement, and it still didn't allow 'without custom glue code', because someone still had to write the glue."
  - **the_mitsuhiko**: "The agent writes its own glue code so the benefit does not seem to really exist in practice... when I ask the agent to just write its own skill it works better."
  - **Simon Willison** (referenced): "Almost everything I might achieve with an MCP can be handled by a CLI tool instead."
  - **fxj**: "MCP is just a small, boring protocol that lets agents call tools in a standard way... it just gives tools a common shape."
  - **falloutx**: "You can create an MCP server to exfil sensitive data by creating tools which AI at first thinks are doing something else."
  - **rvz**: "It was a completely broken one security-wise from day 0. The folks who wrote it have never written an RFC or an internet standard before."

### 5. "Show HN: MCP Isn't Dead. You're Just Using It Wrong"
- **URL:** https://news.ycombinator.com/item?id=47412133
- **Points:** 6
- **Comments:** 7
- **Key Comments:**
  - **quietbuilder**: Raised concerns about context limits from loading 50+ tools and security implications of credentials in runtime memory.
  - **PaulHoule**: "a masterclass in how to not design an API."
  - Creator: "Dynamic tool registration extends an MCP server's abilities beyond that of just a glorified swagger doc - allowing the server...to dynamically add and remove new tools in real time. It elegantly solves the main problem most people had with MCP in the first place - context bloat."

### 6. "Show HN: MCPlexor – MCP multiplexer that cuts agent context usage by 95%"
- **URL:** https://news.ycombinator.com/item?id=46942466
- **Points:** 6
- Creator quote: "MCP is great for giving LLMs access to external tools. But if you connect multiple servers (GitHub, Linear, Postgres, Slack), you end up with 40-50k tokens of tool definitions injected into every request." Solution brings usage "from ~20k" down to approximately 500 tokens per operation. Built in Go as a single binary.

### 7. "Show HN: MCP Kit – a toolkit for building, mocking and optimizing AI agents"
- **URL:** https://news.ycombinator.com/item?id=44304245
- **Points:** 4
- Creators: "We found ourselves repeatedly writing glue code to connect OpenAPI specs, mock APIs, and deploy custom toolchains."

### 8. "Model Context Protocol (MCP) Clearly Explained"
- **URL:** https://news.ycombinator.com/item?id=43943899
- (Rate limited during fetch)

### 9. "MCP Specification – version 2025-06-18 changes"
- **URL:** https://news.ycombinator.com/item?id=44314289

### 10. "Claude Code: An Agentic cleanroom analysis"
- **URL:** https://news.ycombinator.com/item?id=44153053

### 11. "Claude Opus 4.7"
- **URL:** https://news.ycombinator.com/item?id=47793411
- Notable quote surfaced: "The latest version defaults to NOT including a human-readable reasoning token summary in the output, requiring 'display': 'summarized' to get that feature."
- Comment: "Every agent framework is completely reinvented every week due to new patterns and new models."

### 12. "Claude Managed Agents Overview"
- **URL:** https://news.ycombinator.com/item?id=47697641

### 13. "Show HN: Klaus – a Claude Code native delegating agentic harness"
- **URL:** https://news.ycombinator.com/item?id=46760506

---

## REDDIT

### r/ClaudeAI
- Active discussions on Claude Opus 4.7 — consensus: "net-positive but heavily qualified"
- Top concern: "same pricing... 4.7 / 4.6.. it feels like we got 'smart' 4.6 back but with the new higher token usage" — token burn estimated 1.5-3x more expensive in practice
- Users sharing agentic CAD runs, multi-file refactors across large monorepos
- Key complaint cluster: runaway token burn, "ambiguity tax" (model no longer silently rescues vague prompts), confidently broken output on marathon runs

### r/vibecoding (89k members)
- Claude Code: 226 mentions — highest of any tool analyzed in 2026
- Community describes Claude Code as "part workspace, part builder, part teacher"
- Real use cases: building entire apps through natural language

### r/AI_Agents
- Key debate: "self-organization aims for emergent coordination and adaptability; orchestration is top-down control of roles, context flow, and delegation"
- LocalLLaMA contributor: "enterprise workflows often require specialized swarms, with separate agents for coding, reasoning, and checks"
- Coordination challenges: "politeness loops" and "non-deterministic behavior in messy chatroom-style setups"

### r/LocalLLaMA (266,500+ members)
- Grew substantially as users value privacy, control, no subscription costs
- Best 35B agentic models as of March 2026: Qwen3.5 and GLM-4.7-Flash
- Recommendation for agentic local work: Ollama + Open WebUI
- Community evaluating MiniMax M2.5/M2.7 for agentic/tool-heavy workloads

### r/ArtificialIntelligence
- Concern about "agent washing" — marketing automation as genuine AI agents
- Genuine agents distinguished: "Real agents reason, make decisions, use tools, access external data, and complete end-to-end tasks."
- Stack Overflow Developer Survey: 84% daily AI coding tool usage, only 29% trust AI-generated code in production without review

---

## YOUTUBE

### "My Claude Code Workflow for 2026"
- **URL:** https://www.youtube.com/watch?v=sy65ARFI9Bg
- (Page could not be fully scraped)

### "Claude Code and the Evolution of Agentic Coding" — Boris Cherny, Anthropic (AI Engineer World's Fair)
- **URL:** https://www.classcentral.com/course/youtube-claude-code-the-evolution-of-agentic-coding-boris-cherny-anthropic-465473
- 18-minute conference talk from Claude Code creator at Anthropic

### Udemy Course: "Claude Code 2026: Subagents, MCP, Skills and Plugins Bootcamp"
- **URL:** https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/

### DeepLearning.AI: "Claude Code: A Highly Agentic Coding Assistant"
- **URL:** https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/66b35/introduction
- Built in partnership with Anthropic; features Elie Schoppik from the Claude Code team

---

## TIKTOK

### @samdespo — "These best Claude Skills will automate hours of work"
- **URL:** https://www.tiktok.com/@samdespo/video/7627255461456399636
- About Claude Skills automating workflows

### #claude tag
- **URL:** https://www.tiktok.com/tag/claude
- Active creator community using Claude Code for content automation

### Context:
- Real creators using Claude Code to run full social media pipelines: research → create → edit → caption → voice-over → post
- Content: AI agents for TikTok ads management, Instagram content engines, viral video automation

---

## POLYMARKET

### "Which company has the best AI model end of April?"
- **URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-april
- **Odds:** Anthropic 95%, OpenAI 5.5%, Google <1%
- **Volume:** $19,801,609
- Resolution: April 30, 2026 — based on Chatbot Arena LLM Leaderboard

### "Claude Mythos released by…?"
- **URL:** https://polymarket.com/event/claude-mythos-released-by
- **Odds:** June 30: 30%, April 30: 1%
- **Volume:** $334,069
- Context: Data leaked March 26, 2026; Mythos Preview announced April 7, 2026

### "Will Anthropic or OpenAI IPO first?"
- **URL:** https://polymarket.com/event/will-anthropic-or-openai-ipo-first
- **Odds:** Anthropic 66%
- Context: Anthropic revenue $30B ARR vs. OpenAI $25B ARR in early 2026

### "Which company has the best AI model end of May?"
- **URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-may

### "Claude Opus 4.7: Arena Debut?"
- **URL:** https://polymarket.com/event/next-anthropic-model-arena-debut

### "Claude 4.7 released by...?"
- **URL:** https://polymarket.com/event/claude-4pt7-released-by

---

## WEB — KEY ARTICLES

### Anthropic Announcements

**Claude Opus 4.7 Official Blog**
- **URL:** https://www.anthropic.com/news/claude-opus-4-7
- Release Date: April 16, 2026
- Key features: xhigh effort level, task budgets (public beta), /ultrareview command
- Benchmarks: 87.6% SWE-bench Verified (agentic), 64.3% SWE-bench Pro (#1 GA slot), CursorBench 70% (vs. 58% for 4.6)
- Quote: "Users can hand off their hardest coding work—the kind that previously needed close supervision—to Opus 4.7 with confidence."
- Vision: 3× resolution improvement (2,576px / ~3.75MP from 1,568px)
- Memory: Better at file-system-based memory; auto mode extended to Max users

**Claude Managed Agents launch**
- **URL:** https://platform.claude.com/docs/en/managed-agents/quickstart
- Launched April 8, 2026 (public beta)
- Pricing: $0.08 per agent runtime hour
- Built-in toolset (agent_toolset_20260401): bash execution, file read/write, web search, web fetch, grep, glob
- Early adopters: Notion, Sentry, Asana, Rakuten

**Claude Mythos Preview**
- **URL:** https://red.anthropic.com/2026/mythos-preview/
- Announced April 7, 2026; restricted release only
- Project Glasswing consortium: AWS, Apple, Google, JPMorganChase, Microsoft, Nvidia
- Key capability: "Can identify and exploit zero-day vulnerabilities in every major OS and web browser"
- Not publicly available due to dual-use cybersecurity risks

**Claude Code Agent Teams documentation**
- **URL:** https://code.claude.com/docs/en/agent-teams
- Team lead coordinates via shared task list; teammates communicate directly with each other
- As of March 2026: all agents must run the same model (role-based model selection not yet supported)

### Research & Analysis

**"Dive into Claude Code: The Design Space of Today's and Future AI Agent Systems"**
- **URL:** https://arxiv.org/html/2604.14228v1
- Authors: Jiacheng Liu, Xiaohan Zhao, Xinyi Shang, Zhiqiang Shen (VILA Lab, Mohamed bin Zayed University)
- Key findings:
  - Only ~1.6% of codebase constitutes AI decision logic; 98.4% is operational infrastructure
  - Deny-first safety model: "Deny rules always take precedence over allow rules, even when the allow rule is more specific."
  - Five core human values: Human Decision Authority, Safety/Security/Privacy, Reliable Execution, Capability Amplification, Contextual Adaptability
  - 27% of tasks "wouldn't be attempted without the tool" per user data
  - Auto-approval rates increase from ~20% at 50 sessions to 40% by 750 sessions (graduated trust)
  - Seven independent safety layers operate in parallel

**LangChain State of Agent Engineering (2025 survey)**
- **URL:** https://www.langchain.com/state-of-agent-engineering
- 1,340 respondents (Nov 18–Dec 2, 2025)
- 57.3% have agents in production (up from 51% YoY)
- Top challenges: Quality (32%), Latency (20%), Cost (declining), Security (rising for enterprises)
- 67%+ use OpenAI GPT, but 75% employ multiple models
- 89% have observability implemented
- Daily usage leaders: Claude Code, GitHub Copilot, then custom LangChain/LangGraph

**Stanford AI Index 2026**
- **URL:** https://www.beri.net/article/stanford-ai-index-2026-agents-66-percent-success
- Agents hit 66% success rate on benchmarks
- 89% of enterprise AI agents never reach production
- Implementation costs: $150,000–$800,000 per enterprise agent

### MCP Security

**"Anthropic MCP Design Vulnerability Enables RCE"**
- **URL:** https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html
- Affects 7,000+ publicly accessible servers
- 150+ million downloads affected
- CVEs: dozens in first months of 2026; CVSS 9.6 RCE flaw in one package (~500k downloads)

**"MCP 'design flaw' puts 200k servers at risk"**
- **URL:** https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/
- The Register coverage of the design-level vulnerability enabling arbitrary command execution

**OWASP MCP Top 10**
- **URL:** https://owasp.org/www-project-mcp-top-10/
- Published: 2026
- Top risks: token mismanagement, privilege escalation, tool poisoning, supply chain attacks, command injection, intent flow subversion, insufficient auth, lack of audit/telemetry, shadow MCP servers, context injection/over-sharing

**"MCP Security 2026: State of Incidents"**
- **URL:** https://pipelab.org/blog/state-of-mcp-security-2026/

### Agent Frameworks

**LangGraph vs CrewAI vs AutoGen (2026 comparison)**
- **URL:** https://dev.to/pockit_tools/langgraph-vs-crewai-vs-autogen-the-complete-multi-agent-ai-orchestration-guide-for-2026-2d63
- LangGraph: best for production, stateful execution, streaming, checkpointing, time-travel debugging
- CrewAI: best for moving fast, intuitive role-based abstraction
- AutoGen/AG2: conversational GroupChat model
- IBM case study: LangChain reduced orchestration latency by 40% vs. AutoGen in 100-agent workflow

**Agno Agent Framework**
- **URL:** https://github.com/agno-agi/agno | https://www.agno.com/
- Python agent framework, multi-agent, production-grade
- MCP support: single-line integration
- Design principle: "Agents work best when they have a singular purpose, a narrow scope, and a small number of tools."
- Built-in integrations: Pinecone, Weaviate, Qdrant, AWS S3, Slack, Notion

**A2A Protocol (Agent2Agent)**
- **URL:** https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
- Introduced by Google (April 2025), now widely adopted
- Agent Cards in JSON format for capability advertisement
- Gartner: 40% of enterprise apps will feature task-specific AI agents by 2026

### Industry Reports & Analysis

**Fortune: "The Supervisor Class"**
- **URL:** https://fortune.com/2026/03/31/fortune-com-2026-03-26-ai-agents-vibe-coding-developer-skills-supervisor-class/
- March 31, 2026
- New developer paradigm: orchestrating AI agents rather than writing code
- Term coined by Karpathy: "agentic engineering" — designing systems where AI agents plan, write, test, ship code under human oversight

**Anthropic 2026 Agentic Coding Trends Report**
- **URL:** https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf
- Key finding: Daily AI coding tool usage at 84% of developers
- Only 29% trust AI-generated code in production without review

**AI Agents in April 2026 - DEV Community**
- **URL:** https://dev.to/aibughunter/ai-agents-in-april-2026-from-research-to-production-whats-actually-happening-55oc
- 65% of organizations experimenting with AI agents
- Fewer than 25% have successfully scaled to production
- Top 3 production barriers: reliability, cost unpredictability (10 calls → 80+ in agentic loops), governance gaps

**AI Agent Scaling Gap March 2026**
- **URL:** https://www.digitalapplied.com/blog/ai-agent-scaling-gap-march-2026-pilot-to-production

**"AI Agents in Production: Frameworks, Protocols, and What Actually Works in 2026"**
- **URL:** https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/
- MCP+A2A architecture becoming enterprise default

**AI Agent News April 2026 - Fazm Blog**
- **URL:** https://fazm.ai/blog/ai-agent-news-april-2026-claude-code-openclaw
- Key timeline:
  - April 1: Claude Code v2.1.90 — NO_FLICKER rendering engine (74% reduction in rendering cycles)
  - April 2: Microsoft Agent Governance Toolkit — open-source, addresses all 10 OWASP agentic risks
  - April 2: Google Gemma 4 — Apache 2.0, AIME math 20.8% → 89.2%
  - April 4: v2.1.92 — Bedrock wizard for enterprise
  - April 7: Claude Mythos Preview announcement
  - April 8: Claude Managed Agents public beta launch
  - April 8: Visa Intelligent Commerce Connect — supports 4 agentic protocols simultaneously
  - April 9: v2.1.98 — PID namespace isolation for Linux subprocess security
  - April 9: OpenClaw v2026.4.9 (Dreaming release) — REM Backfill memory consolidation
  - April 10: v2.1.101 — team onboarding automation
  - April 14: Claude Code desktop complete redesign + Routines feature
  - April 16: Claude Opus 4.7 released (general availability)
  - April 23: Opus 4.7 becomes default model for Claude Code

**Multi-Agent Orchestration for Claude Code in 2026**
- **URL:** https://shipyard.build/blog/claude-code-multi-agent/
- Three approaches: Agent Teams (native), Gas Town ("Kubernetes for AI agents"), Multiclaude
- Agent Teams: direct teammate communication vs. subagents reporting bottleneck
- Warning: "Running three concurrent Claude Max accounts to maintain the pace" may be necessary

**Claude Mythos Cybersecurity Analysis**
- **URL:** https://foreignpolicy.com/2026/04/20/claude-mythos-preview-anthropic-project-glasswing-cybersecurity-ai-hacking-danger/
- Foreign Policy coverage of the dual-use risks and Project Glasswing
- "Can identify and exploit zero-day vulnerabilities in every major OS and every major web browser"

**Self-Improving AI Agents 2026 Guide**
- **URL:** https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
- Core mechanism: Reflexion (Princeton/MIT 2023) — verbal self-reflection stored in persistent memory
- Multi-Agent Evolve (MAE, Oct 2025): three co-evolving agents (Proposer, Solver, Judge) via RL

**Bluesky Attie AI Integration**
- **URL:** https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/
- March 28, 2026: Bluesky launched Attie app for AI-powered custom feed creation
- Plan: allow users to "vibe-code" their own social apps

**Three Ways to Build AI Agents With Claude**
- **URL:** https://cobusgreyling.medium.com/three-ways-to-build-ai-agents-with-claude-54db80194127
- April 2026: Claude offers three agent-building approaches targeting different personas

**Claude Managed Agents Community Analysis**
- **URL:** https://medium.com/@roeyzalta/claude-managed-agents-deploy-your-first-production-agent-in-10-minutes-8af00f608209
- "Infrastructure problem blocking most teams from shipping agents in production now resolved"

**Anthropic Introduces Managed Agents - InfoQ**
- **URL:** https://www.infoq.com/news/2026/04/anthropic-managed-agents/

**AI Weekly: April 9–15, 2026**
- **URL:** https://dev.to/alexmercedcoder/ai-weekly-agents-models-and-chips-april-9-15-2026-486f

---

## SUPPLEMENTARY SOURCE INVENTORY

### All URLs by Source Type

**Anthropic official:**
- https://www.anthropic.com/news/claude-opus-4-7
- https://red.anthropic.com/2026/mythos-preview/
- https://platform.claude.com/docs/en/managed-agents/quickstart
- https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-7
- https://platform.claude.com/docs/en/release-notes/overview
- https://code.claude.com/docs/en/agent-teams
- https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf

**Hacker News:**
- https://news.ycombinator.com/item?id=46903616 (C Compiler, 735pts/738 comments)
- https://news.ycombinator.com/item?id=46743908 (Swarms, 521pts/335 comments)
- https://news.ycombinator.com/item?id=47693047 (Managed Agents, 169pts/86 comments)
- https://news.ycombinator.com/item?id=46552254 (MCP is a fad, 145pts/117 comments)
- https://news.ycombinator.com/item?id=47412133 (MCP not dead, 6pts/7 comments)
- https://news.ycombinator.com/item?id=46942466 (MCPlexor, 6pts)
- https://news.ycombinator.com/item?id=44304245 (MCP Kit, 4pts)
- https://news.ycombinator.com/item?id=43943899 (MCP Clearly Explained)
- https://news.ycombinator.com/item?id=44314289 (MCP Spec changes)
- https://news.ycombinator.com/item?id=44153053 (Claude Code cleanroom)
- https://news.ycombinator.com/item?id=47793411 (Claude Opus 4.7)
- https://news.ycombinator.com/item?id=47697641 (Managed Agents Overview)
- https://news.ycombinator.com/item?id=46760506 (Klaus harness)
- https://news.ycombinator.com/item?id=46975121 (Neuro-Symbolic Finance)

**Polymarket:**
- https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-april ($19.8M vol, Anthropic 95%)
- https://polymarket.com/event/claude-mythos-released-by ($334k vol)
- https://polymarket.com/event/will-anthropic-or-openai-ipo-first (Anthropic 66%)
- https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-may
- https://polymarket.com/event/next-anthropic-model-arena-debut
- https://polymarket.com/event/claude-4pt7-released-by
- https://polymarket.com/predictions/anthropic (185 markets, $8.5M volume)

**Industry news/analysis:**
- https://www.marktechpost.com/2026/04/18/anthropic-releases-claude-opus-4-7-a-major-upgrade-for-agentic-coding-high-resolution-vision-and-long-horizon-autonomous-tasks/
- https://www.cnbc.com/2026/04/16/anthropic-claude-opus-4-7-model-mythos.html
- https://www.axios.com/2026/04/16/anthropic-claude-opus-model-mythos
- https://github.blog/changelog/2026-04-16-claude-opus-4-7-is-generally-available/
- https://aws.amazon.com/blogs/aws/introducing-anthropics-claude-opus-4-7-model-in-amazon-bedrock/
- https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html
- https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/
- https://foreignpolicy.com/2026/04/20/claude-mythos-preview-anthropic-project-glasswing-cybersecurity-ai-hacking-danger/
- https://fortune.com/2026/03/31/fortune-com-2026-03-26-ai-agents-vibe-coding-developer-skills-supervisor-class/
- https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/

**Research/community:**
- https://arxiv.org/html/2604.14228v1
- https://www.langchain.com/state-of-agent-engineering
- https://www.beri.net/article/stanford-ai-index-2026-agents-66-percent-success
- https://owasp.org/www-project-mcp-top-10/
- https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
- https://github.com/a2aproject/A2A

**Frameworks/tools:**
- https://github.com/agno-agi/agno
- https://www.agno.com/
- https://dev.to/pockit_tools/langgraph-vs-crewai-vs-autogen-the-complete-multi-agent-ai-orchestration-guide-for-2026-2d63
- https://www.datacamp.com/tutorial/crewai-vs-langgraph-vs-autogen

**Blogs/guides:**
- https://fazm.ai/blog/ai-agent-news-april-2026-claude-code-openclaw
- https://shipyard.build/blog/claude-code-multi-agent/
- https://dev.to/aibughunter/ai-agents-in-april-2026-from-research-to-production-whats-actually-happening-55oc
- https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/
- https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
- https://ctlabs.ai/blog/self-organizing-agents-on-reddit-what-builders-are-learning-in-2026
- https://medium.com/@roeyzalta/claude-managed-agents-deploy-your-first-production-agent-in-10-minutes-8af00f608209
- https://botmonster.com/posts/claude-opus-4-7-x-reddit-reception/
- https://cobusgreyling.medium.com/three-ways-to-build-ai-agents-with-claude-54db80194127
- https://medium.com/ai-software-engineer/anthropic-launches-claude-managed-agents-that-make-agentic-ai-workflows-real-91134b6f2b56
- https://www.infoq.com/news/2026/04/anthropic-managed-agents/
- https://dev.to/alexmercedcoder/ai-weekly-agents-models-and-chips-april-9-15-2026-486j
- https://www.ai.cc/blogs/claude-code-desktop-redesign-2026-multi-session-routines-automation/
- https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns

**YouTube:**
- https://www.youtube.com/watch?v=sy65ARFI9Bg
- https://www.classcentral.com/course/youtube-claude-code-the-evolution-of-agentic-coding-boris-cherny-anthropic-465473
- https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/66b35/introduction

**TikTok:**
- https://www.tiktok.com/@samdespo/video/7627255461456399636
- https://www.tiktok.com/tag/claude
