# AI Dev Practice — Raw Research Data
**Date:** 2026-04-24
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## HACKER NEWS

### Ask HN: Cursor or Windsurf?
**URL:** https://news.ycombinator.com/item?id=43959710
**Key discussion points:**
- Top comment: Zed as alternative (316 points) — "felt much less janky" with superior performance on M-series Macs
- Cursor tab completion "understands what I want to do next about 95% of the time"
- Windsurf limitation: reads "only 50-200 lines at a time," struggles with files over 800 lines
- Quality vs Cost: Cursor better results but higher cost; Windsurf lower pricing with free autocomplete
- Alternatives discussed: Claude Code, Aider, Cline
- Platform stability concerns: dominant tools will increase pricing once market position solidifies

### Windsurf and Cursor feel like temporary stopgaps
**URL:** https://news.ycombinator.com/item?id=43904473
**Key discussion points:**
- Main thesis: Windsurf and Cursor are "temporary stopgaps, products of a narrow window in time before the landscape shifts again"
- Microsoft predicted to replicate their features within a year
- Cline has 1.4M downloads as VSCode-native alternative
- Community push-back: Microsoft's mixed track record cited
- "Both tools are riddled with bugs that don't exist upstream, especially in their AI assistant features"

### Ask HN: How much better are AI IDEs vs. copy pasting into chat apps?
**URL:** https://news.ycombinator.com/item?id=43922759
**Key discussion points:**
- AI IDEs win on convenience and automated context management
- Context management remains key—embedding-based retrieval still falls short on large codebases
- Cursor $20/month unlimited vs Claude Code $3-5 per session
- "The workflow paradox": copy-pasting forces better prompt discipline

### Ask HN: Why do Cursor, Windsurf and Claude Code dominate the conversation?
**URL:** https://news.ycombinator.com/item?id=44635075
**Key discussion points:**
- Network effects and mindshare concentration: "Three is already a lot of tools to be doing more or less the same thing"
- GitHub stars don't correlate with adoption: Gemini CLI 62k stars, Claude Code 25k stars but Claude Code wins in usage
- Claude Code rapid momentum since launch, dominates YouTube benchmarks
- Claude Code Max plan $200/month avoids credit-based anxiety
- Tools like Replit and Bolt target non-professional developers, explaining HN absence

### This is why platforms like Claude Code, Cursor and Windsurf are essential
**URL:** https://news.ycombinator.com/item?id=43504267

### My LLM coding workflow going into 2026
**URL:** https://news.ycombinator.com/item?id=46489061

---

## REDDIT

### r/programming — Banned LLM content (April 2026)
**Source:** https://www.tomshardware.com/tech-industry/artificial-intelligence/the-largest-programming-community-on-reddit-just-banned-all-content-related-to-ai-llms-r-programming-is-prioritizing-only-high-quality-discussions-about-ai
- r/programming (6.9 million members) implemented ban on all LLM-related discussions for April 2026
- Ban includes: news stories about new models, guides on building/modifying models, discussions about AI replacing developers
- Some users questioned if it was an April Fool's joke

### Vibe Coding on Reddit (Aggregated Analysis)
**Source:** https://www.morphllm.com/reddit-vibe-coding
**Subreddits discussed:** r/programming, r/webdev, r/ExperiencedDevs, r/cscareerquestions, r/SideProject

**Key quotes from Reddit:**
- "Like building with someone who has great hands but no memory" (on AI architectural limitations)
- "AI is still just soooooo stupid and it will fix one thing but destroy 10 other things in your code"
- Users "believed afterward they had been 20% faster" despite being 19% slower in reality

**Three Reddit camps identified:**
1. Believers — view as paradigm shift comparable to high-level languages
2. Skeptics — cite production failures and security vulnerabilities
3. Pragmatists — context-dependent usage (prototypes vs. production)

**Most common workflow:** Prototype fast in Lovable or Bolt → graduate to Cursor or Claude Code for production

**Failure points cited:**
- Context window limits
- Security blind spots
- The fix-one-break-ten cycle
- Architectural drift (AI-generated code becomes internally inconsistent)

---

## X / TWITTER

### Andrej Karpathy — Original "vibe coding" coinage
Karpathy posted on X in February 2025: "There's a new kind of coding I call vibe coding, where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."

### Addy Osmani — LLM coding workflow
**URL:** https://x.com/addyosmani/status/2002438238309658656
Tweet: "My LLM coding workflow going into 2026: Specs, skills, MCPs, small iterative chunks, and always review what the AI suggests."

### Ed Zitron — Claude Code pricing change
First flagged via Bluesky: Anthropic removing Claude Code from $20 Pro subscription tier
**Source:** https://aitoolly.com/ai-news/article/2026-04-22-anthropic-reportedly-removes-claude-code-from-20-monthly-pro-subscription-tier

### Developer sentiment data (via surveys)
- 95% of developers use AI tools at least weekly
- 75% use AI for more than half of their coding work
- 84% use AI coding tools daily — but only 29% trust AI-generated code in production without review
- Claude Code "most loved" at 46% among developers; Cursor 19%; Copilot 9%

---

## YOUTUBE

### Vibe Coding Tutorial and Best Practices (Cursor / Windsurf) — Matthew Berman
**URL:** https://www.youtube.com/watch?v=YWwS911iLhg
Published: March 5, 2025
Topics: AI agent coding with minimal actual code writing, agent-based coding in Cursor or Windsurf

### Vibe Coding Complete Tutorial and Tips — Matthew Berman
**URL:** https://www.youtube.com/watch?v=v7UcVPO4y3c
Published: March 30, 2025
Topics: Comprehensive vibe coding stack, addressing common questions

### AI Vibe Coding Tutorial + Workflow (Cursor, Best Practices, PRD, Rules, MCP)
**URL:** https://www.youtube.com/watch?v=qIO9Mg1Man4
Published: April 9, 2025
Topics: Advanced workflow, PRDs, rules, MCP integration

### Windsurf Tutorial for Beginners (AI Code Editor) — Better than Cursor??
**URL:** https://www.youtube.com/watch?v=8TcWGk1DJVs
Published: February 1, 2025
Topics: Windsurf vs Cursor comparison, beginners guide

---

## TIKTOK

### @rileybrown.ai — "Is programming going to be replaced by vibe coding?"
**URL:** https://www.tiktok.com/@rileybrown.ai/video/7481370901808762142
Content: Vibe coding described as "writing code in the hottest programming language rn *english*"

### @rileybrown.ai — Vibe Coding and frontend engineers
**URL:** https://www.tiktok.com/@rileybrown.ai/video/7532564726652456222
Content: "Vibe Coding allows anyone to build front ends. It's good for entrepreneurs but bad for front end engineers."

### TikTok discover pages with high activity:
- https://www.tiktok.com/discover/vibe-coding
- https://www.tiktok.com/discover/coding-with-ai
- https://www.tiktok.com/discover/ai-tools-for-coding

### Mobile Vibe Coding Context:
- Apple banning vibe coders — blocked Replit's "Vibe Code" app
- 84% jump in App Store submissions in a single quarter
- **Source:** https://stormy.ai/blog/mobile-vibe-coding-ai-app-builders-tiktok-trends

---

## POLYMARKET

### Will Cursor be acquired before 2027?
**URL:** https://polymarket.com/event/which-companies-will-be-acquired-before-2027
**Odds:** 77% Yes (84% implied after SpaceX April 22 announcement)
**Volume:** $20,354
- Yes shares: 78¢ | No shares: 24¢
- SpaceX announced $10B collaboration with Cursor + $60B buyout option exercisable by year-end
- Reflects accelerating AI consolidation around advanced coding LLMs

---

## GITHUB TRENDING (April 22, 2026)

**Source:** https://www.shareuhack.com/en/posts/github-trending-weekly-2026-04-22

### Top Repositories by Weekly Stars:
1. forrestchang/andrej-karpathy-skills — +44,394 stars, total 71,863 (skills/CLAUDE.md config)
2. NousResearch/hermes-agent — +30,630 stars, total 108,034 (Python, self-evolving agent)
3. thedotmack/claude-mem — +12,472 stars, total 65,121 (TypeScript, Claude memory)
4. microsoft/markitdown — +7,084 stars, total 114,020 (Python)
5. multica-ai/multica — +7,009 stars, total 18,471 (TypeScript)
6. jamiepine/voicebox — +5,936 stars, total 22,127 (TypeScript, voice AI)
7. Lordog/dive-into-llms — +5,703 stars, total 33,329 (Jupyter)
8. EvoMap/evolver — +4,032 stars, total 6,307 (JavaScript, self-evolving agents)
9. virattt/ai-hedge-fund — +3,950 stars, total 56,811 (Python)
10. openai/openai-agents-python — +3,078 stars, total 24,360 (Python)

### New Repositories (April 14-22, 2026):
1. kyegomez/OpenMythos — 6,690 stars (Python)
2. browser-use/browser-harness — 4,372 stars (Python)
3. vercel-labs/wterm — 2,269 stars (TypeScript)

### Context Engineering Tools (Long-standing leaders):
- Langflow: 146k stars
- Dify: 136k stars
- Flowise: 51k stars
- caramaschiHG/awesome-ai-agents-2026: 300+ resources

**Themes:**
- Skills ecosystem expansion — configuration culture for AI coding agents hit mainstream
- Self-evolving agents
- Voice AI infrastructure competition
- CLAUDE.md single file reaching 71,863 stars — "AI coding behavior standardization" at critical mass

---

## WEB / BLOGS

### Datadog: State of AI Engineering (2026)
**URL:** https://www.datadoghq.com/state-of-ai-engineering/
**Key Statistics:**
- 5% of LLM call spans reported errors in February 2026; dropped to 2% in March 2026
- Rate limit errors account for ~33% of all failures (dominant failure mode)
- 8.4 million rate limit errors recorded in March 2026
- OpenAI maintains 63% market share (down from 75% a year ago)
- Anthropic Claude and Google Gemini grew 20 and 23 percentage points respectively
- 70%+ of organizations deploy 3+ models in production
- Organizations using 6+ models nearly doubled YoY
- Agent framework adoption doubled: 9% (early 2025) → 18% (early 2026)
- 59% of agentic requests made only a single service call
- 69% of input tokens allocated to system prompts and scaffolding
- Token usage per request more than doubled; quadrupled for power users
- Only 28% of LLM calls utilize prompt caching despite availability

### Addy Osmani: My LLM Coding Workflow Going Into 2026
**URL:** https://addyosmani.com/blog/ai-coding-workflow/
**Also:** https://addyo.substack.com/p/my-llm-coding-workflow-going-into
**Key Workflow:**
1. Plan before coding — "Waterfall in 15 minutes"
2. Break into small chunks — one function, one bug at a time
3. Provide extensive context
4. Choose right model for task
5. Keep humans in the loop — "Think of an LLM pair programmer as over-confident and prone to mistakes"
6. Commit frequently as safety net
7. Embrace automation (CI/CD, linters, code review bots)
**Tools:** Claude, Gemini, ChatGPT, GitHub Copilot, Claude Code, Jules, Codex CLI, Gemini CLI, Cursor, gitingest, Context7, Chrome DevTools MCP

### Fortune: Cursor CEO Warns About Vibe Coding
**URL:** https://fortune.com/article/cursor-ceo-vibe-coding-warning/
- Cursor CEO warns vibe coding builds "shaky foundations" and eventually "things start to crumble"

### Anton Morgunov: Vibe Coding Killed Cursor
**URL:** https://ischemist.com/writings/long-form/how-vibe-coding-killed-cursor
- Cursor's optimization for simple changes ("tunnel vision") hurt complex programming tasks
- Each iterative change requires re-feeding entire conversation history → exponential token cost
- Gemini 2.5 Pro achieves 90% pass@1 on LongCodeEdit benchmark at 128k context vs Sonnet 4.5's 30%
- Recommends AI Studio (free Gemini 2.5 Pro) for broad codebase visibility

### Medium: Vibe Coding in 2026 is Complete Fucking Bullshit
**URL:** https://medium.com/@developer_programmer/vibe-coding-in-2026-is-complete-fucking-bullshit-and-were-all-paying-for-it-92f41e2d4672
- "Code breaks in production on day three, and everyone claps"
- Criticizes as "expensive, unmaintainable AI slop"

### JetBrains Research: Which AI Coding Tools Do Developers Actually Use at Work?
**URL:** https://blog.jetbrains.com/research/2026/04/which-ai-coding-tools-do-developers-actually-use-at-work/
**Survey of 10,000+ developers (January 2026):**
- 90% of developers regularly use at least one AI tool
- GitHub Copilot: 29% work adoption (76% awareness)
- Cursor: 18% work adoption (69% awareness)
- Claude Code: 18% work adoption (57% awareness); 24% in US/Canada
- ChatGPT for coding: 28%
- Claude Code CSAT: 91%, NPS: 54
- Claude Code growth: ~3% (April-June 2025) → 18% (January 2026) — 6x in 9 months

### AI Coding Tools War (Redreamality)
**URL:** https://redreamality.com/blog/ai-coding-tools-war-vibe-coding-mainstream/
- Key finding: "The model is becoming less differentiating than the loop"
- Once multiple tools access similar frontier models, differentiation shifts to context capacity, test execution, workflow continuity
- Market dividing into two camps: IDE-first (Cursor, Windsurf, Copilot) vs terminal-first (Claude Code, Aider)
- Three vibe coding behaviors: draft-first, flow-state building, delegated execution

### DEV Community: AI Agents in April 2026 — From Research to Production
**URL:** https://dev.to/aibughunter/ai-agents-in-april-2026-from-research-to-production-whats-actually-happening-55oc
- 65% of organizations experimenting with AI agents
- Fewer than 25% successfully scaled to production
- Key barriers: memory lifecycle management, cost attribution at workflow levels, appropriate failure recovery semantics
- "April 2026 feels like the moment where AI stopped being experimental and started being infrastructure"

### DEV Community: AI Weekly April 9-15, 2026
**URL:** https://dev.to/alexmercedcoder/ai-weekly-agents-models-and-chips-april-9-15-2026-486f
- 84% of developers use AI coding tools in April 2026; only 29% trust what they ship
- Cursor rebuilt interface for parallel agent orchestration
- OpenAI released official plugin for Claude Code
- Claude Mythos Preview: 93.9% on SWE-bench Verified (50 partner orgs)
- MCP v2.1 now supported in Claude Desktop and Cursor
- Microsoft Agent Framework 1.0 with browser-based DevUI
- April 9 = one-year anniversary of Google A2A Protocol; 150+ organizations
- NVIDIA: AI compressed "10-month, 8-engineer GPU design task into an overnight job"

### Cobus Greyling: Context Engineering Is the Real Product (Medium)
**URL:** https://cobusgreyling.medium.com/context-engineering-is-the-real-product-d938be65ce7e
- "Context is a budget, not a log. Every token you spend on a stale tool output is a token you can't spend on the user's actual question."
- "Most agent failures aren't reasoning failures. They're context failures."
- After ~15 tool calls, models stop following system prompts
- 5-Stage Adaptive Compaction Pipeline reduces session from 15-20 turns to 30-40+ turns
- Observation masking reduces output tokens from thousands to ~15 per observation

### Solving the 78% Problem — Why AI Agent Pilots Work and Production Doesn't
**URL:** https://earezki.com/ai-news/2026-04-22-the-78-problem-why-ai-agent-pilots-work-and-production-deployments-dont/

### AI Agents Production Reliability — Overlook VC
**URL:** https://overlookvc.substack.com/p/edition-43-2026-failure-modes-of
**Five structural failure modes:**
1. Intent Drift — 90% of drifted actions fall within normal permission bounds; 76% of multi-step agent pilots experience critical drift within 90 days
2. Authority Mismatch — 88% organizations reported security incidents from agent over-permissioning; only 21.9% treat agents as identity-bearing entities
3. Parasitic Feedback Loops — 39-70% degradation in sequential reasoning quality in autonomous loops
4. Coordination Collapse — 3 agents need 3 paths; 10 agents need 45; ceiling ~15 tools
5. Cascading failures amplify initial errors through multi-step reasoning chains

### Enterprise AI Agent Failure in Production
**URL:** https://aiassemblylines.com/post/enterprise-ai-agents-fail-production-2026
- 97% of executives report deploying AI agents in past year
- Only 12% of agent initiatives successfully reach production at scale
- Transition from pilot to production failing at 88% rate
- Observability tools record failures after they happen; need governance plane before tool calls execute

### AI Agent Failure Modes — Latitude
**URL:** https://latitude.so/blog/ai-agent-failure-modes-detection-playbook

### Why AI Agents Fail in Production — TFiR/Mezmo
**URL:** https://tfir.io/ai-agents-production-reliability-mezmo-aura/

### ICML 2026 Workshop: Failure Modes in Agentic AI
**URL:** https://fmai-workshop.github.io/

### Context Engineering — Callstack: RAG Is Dead
**URL:** https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems
- RAG evolving from specific pattern to "Context Engine" with "intelligent retrieval"
- 80% of RAG failures trace back to ingestion layer, not the LLM

### Roadie: RAG vs Context Engineering in Production
**URL:** https://roadie.io/blog/rag-vs-context-engineering-production/
- Treating RAG as complete context engineering creates production failures
- RAG is one retrieval primitive; agent needs 6 different context slot mechanisms

### Context Engineering Guide — Meta Intelligence
**URL:** https://www.meta-intelligence.tech/en/insight-context-engineering
- 70%+ of LLM app errors stem from incomplete or poorly structured context

### DEV Community: Context Engineering Replacing Prompt Engineering
**URL:** https://dev.to/serenitiesai/context-engineering-why-its-replacing-prompt-engineering-in-2026-1b4g
- Evolution: Stage 1 Prompt Engineering (2023) → Stage 2 Agentic Workflow (2024) → Stage 3 Context Engineering (2025-2026)

### DEV Community: AI Coding Agents for Production-Grade Software
**URL:** https://dev.to/alexchen31337/ai-coding-agents-for-production-grade-software-mjd
- MCP handles vertical connection (agent → tools); A2A handles horizontal (agent ↔ agent)

### SiliconAngle: Cursor Refreshes Vibe Coding Platform with AI Agents
**URL:** https://siliconangle.com/2026/04/02/cursor-refreshes-vibe-coding-platform-focus-ai-agents/
- Cursor rebuilt interface for parallel agent orchestration (April 2026)
- Reports $2 billion annualized revenue run rate (crossed in early March 2026)

### Fortune: Cursor CEO Vibe Coding Warning
**URL:** https://fortune.com/article/cursor-ceo-vibe-coding-warning/

### SpaceX $60B Cursor Deal
**URL:** https://startup.pk/spacex-just-paid-10-billion-for-the-right-to-buy-cursor-and-it-could-reshape-ai-coding-forever/
- SpaceX struck deal: $10B collaboration + $60B buyout option exercisable by year-end

### NxCode: GitHub Copilot Complete Guide 2026
**URL:** https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents
- Agent Mode generally available (VS Code and JetBrains) as of March 2026
- Agentic code review ships March 2026
- 4.7 million paid Copilot subscribers (75% YoY increase)
- Copilot larger business than GitHub itself was worth at time of $7.5B acquisition

### DEV: GitHub Copilot in 2026 Is Not What You Think
**URL:** https://dev.to/carlosjcastrog/github-copilot-in-2026-is-not-what-you-think-it-is-anymore-ij3

### DEV: I Built the Same App 5 Ways (Cursor vs Claude Code vs Windsurf vs Replit vs Copilot)
**URL:** https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2

### DEV: AI Coding Assistants in 2026 (KainOrden)
**URL:** https://dev.to/kainorden/ai-coding-assistants-in-2026-cursor-vs-github-copilot-vs-windsurf-2mm9

### Roadmap.sh: Top 10 Vibe Coding Tools in 2026
**URL:** https://roadmap.sh/vibe-coding/best-tools

### daily.dev: Vibe Coding in 2026
**URL:** https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code
- 92% of US developers adopted vibe coding practices
- 60% of all new code written globally is AI-generated
- Global AI coding market hit $8.5 billion

### LLM Context Problem — LogRocket
**URL:** https://blog.logrocket.com/llm-context-problem-strategies-2026/

### Simon Willison: LLM Predictions for 2026
**URL:** https://simonwillison.net/2026/Jan/8/llm-predictions-for-2026/

### Deepset: Context Engineering — Next Frontier Beyond Prompt Engineering
**URL:** https://www.deepset.ai/blog/context-engineering-the-next-frontier-beyond-prompt-engineering

### IntuitionLabs: What Is Context Engineering?
**URL:** https://intuitionlabs.ai/articles/what-is-context-engineering

### Braintrust: Best LLM Monitoring Tools 2026
**URL:** https://www.braintrust.dev/articles/best-llm-monitoring-tools-2026

### TrueFoundry: Best AI Observability Platforms 2026
**URL:** https://www.truefoundry.com/blog/best-ai-observability-platforms-for-llms-in-2026

### Confident AI: Top 7 LLM Observability Tools
**URL:** https://www.confident-ai.com/knowledge-base/compare/top-7-llm-observability-tools

### Artificial Analysis: Coding Agents Benchmark
**URL:** https://artificialanalysis.ai/agents/coding
- Claude Sonnet 4 leads SWE-bench with 72.7%; Claude Opus 4 at 72.5%

### BSWEN: Best Open Source LLM for Coding 2026
**URL:** https://docs.bswen.com/blog/2026-03-23-best-open-source-llm-coding/

### Claude Code Removed from $20 Pro Tier (April 22, 2026)
**URL:** https://aitoolly.com/ai-news/article/2026-04-22-anthropic-reportedly-removes-claude-code-from-20-monthly-pro-subscription-tier

### Bluesky: Attie AI for Custom Feeds
**URL:** https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/

### Wikipedia: Cursor Code Editor
**URL:** https://en.wikipedia.org/wiki/Cursor_(code_editor)

### GitHub Community Discussion: Best AI Tools for Developers 2026
**URL:** https://github.com/orgs/community/discussions/187143

### Blacksky: Policy on Agentic Coding
**URL:** https://blackskyweb.xyz/blacksky-algorithms-policy-towards-agentic-coding/

### Jay (Bluesky team) on Bluesky
**URL:** https://bsky.app/profile/jay.bsky.team/post/3micqcyeawc2g
- "Bluesky is made with AI, with the engineers and even some non-engineers using Claude Code"

### Augment Code: Context Engine vs RAG
**URL:** https://www.augmentcode.com/guides/context-engine-vs-rag-5-technical-showdowns-for-code-ai

### RAG at Scale — Redis
**URL:** https://redis.io/blog/rag-at-scale/

### RAGFlow: RAG Review 2025
**URL:** https://ragflow.io/blog/rag-review-2025-from-rag-to-context

### ArXiv: Context Engineering paper
**URL:** https://arxiv.org/pdf/2603.09619

### AI-that-works GitHub repo
**URL:** https://github.com/ai-that-works/ai-that-works

### Agents Radar Issue 652
**URL:** https://github.com/duanyytop/agents-radar/issues/652

### VoltAgent: Awesome AI Agent Papers
**URL:** https://github.com/VoltAgent/awesome-ai-agent-papers

### Caramaschi: Awesome AI Agents 2026
**URL:** https://github.com/caramaschiHG/awesome-ai-agents-2026

---

## KEY STATISTICS COMPILATION

### Market size / revenue
- Cursor: $2B ARR (March 2026), $100M → $2B in 14 months
- GitHub Copilot: 4.7M paid subscribers, 75% YoY growth
- Global AI coding market: $8.5B
- LLM observability market: $2.69B in 2026, projected $9.26B by 2030 at 36.2% CAGR
- Lovable: $400M ARR, $6.6B valuation
- Claude Code CSAT 91%, NPS 54

### Developer adoption
- 90% of developers regularly use at least one AI tool
- 84% use AI coding tools daily
- 95% use weekly
- 29% trust AI-generated code in production without review
- 60% of all new code globally is AI-generated
- 92% of US developers adopted vibe coding
- r/programming ban on LLM content (April 2026)

### Production AI reliability
- 5% LLM error rate in February 2026 → 2% in March 2026
- 33% of failures = rate limit errors
- 8.4M rate limit errors in March 2026
- 65% experimenting with AI agents, <25% at production scale
- 12% of agent initiatives reach production at scale
- 97% of executives deployed AI agents; only 12% at scale
- 88% pilot-to-production transition failure rate
- 76% of multi-step agent pilots experience critical drift within 90 days
- 88% of organizations had security incidents from agent over-permissioning

### Context engineering
- 69% of input tokens go to system prompts and scaffolding
- Token usage doubled (median), quadrupled (90th percentile)
- Only 28% use prompt caching
- 70%+ of LLM app errors from poorly structured context
- After ~15 tool calls, models stop following system prompts
- 80% of RAG failures from ingestion layer (not LLM)
- Semantic caching cuts LLM costs by up to 68.8%

### Model market share
- OpenAI: 63% (down from 75% YoY)
- Anthropic: grew 20pp YoY
- Google Gemini: grew 23pp YoY
- 70%+ organizations use 3+ models in production
- Claude Code top SWE-bench: 72.7% (Sonnet 4), 72.5% (Opus 4)
- Claude Mythos Preview: 93.9% SWE-bench Verified
