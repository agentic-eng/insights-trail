# AI Dev Practice — Raw Research Data
**Date:** 2026-04-20
**Query:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks
**Sources:** WebSearch (12 queries), last30days pipeline

---

## PIPELINE NOTES

Platform-specific data (Reddit, X/Twitter, YouTube, HN, TikTok, Bluesky, Polymarket) was not available via direct API pull in this run. The last30days skill launched but did not return structured per-platform data. All findings below are from 12 WebSearch queries across topic dimensions.

---

## WEB SEARCH RAW RESULTS

### Query 1: Vibe coding trends 2026

**URLs returned:**
- https://en.wikipedia.org/wiki/Vibe_coding
- https://www.secondtalent.com/resources/vibe-coding-statistics/
- https://colaninfotech.com/blog/vibe-coding-2026-guide/
- https://www.nxcode.io/resources/news/what-is-vibe-coding-complete-guide-ai-development-2026
- https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code
- https://www.switas.com/articles/the-vibe-coding-revolution-5-ai-tools-shaping-the-future-of-software-development-in-2026
- https://www.dxtalks.com/blog/media-events-1/vibe-coding-2026-complete-guide-ai-development-883
- https://www.blog.brightcoding.dev/2026/04/19/vibe-kanban-10x-your-ai-coding-agent-output
- https://codeweek.eu/blog/ai-coding-tech-trends-2026/
- https://www.taskade.com/blog/state-of-vibe-coding

**Key facts:**
- Vibe coding coined by Andrej Karpathy (OpenAI co-founder, ex-Tesla AI) in February 2025
- 92% of US-based developers adopted some form of vibe coding as of early 2026
- 41% of all new code is AI-generated globally; Gartner projects 60% by end of 2026
- Global AI-assisted coding tools market: $8.5 billion in 2026 (up from hundreds of millions in 2024)
- 8-person team at Kyrylai used AI coding tools to deliver 1 production-ready product, 1 semi-production tool, 3 POCs in 10 weeks
- Kalvium Labs cut time-to-first-commit by 35–40%
- 3-5x faster prototyping, 25-50% acceleration on routine tasks
- 45% of AI-generated code contains security vulnerabilities
- September 2025: Fast Company reported "vibe coding hangover" — senior engineers citing "development hell"
- December 2025 analysis: AI co-authored code has ~1.7x more "major" issues; 2.74x higher security vulnerability rates
- "Graduate workflow" gaining traction: prototype in Bolt/Lovable → refine in Cursor/Claude Code
- BrightCoding (April 19, 2026): "Vibe Kanban" approach for 10x AI coding agent output

---

### Query 2: Cursor vs Windsurf vs GitHub Copilot comparison

**URLs returned:**
- https://www.codeant.ai/blogs/best-ai-code-editor-cursor-vs-windsurf-vs-copilot
- https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2
- https://dev.to/rahulxsingh/best-ai-code-editor-cursor-vs-windsurf-vs-copilot-2026-b4h
- https://www.builder.io/blog/cursor-vs-windsurf-vs-github-copilot
- https://www.buildmvpfast.com/blog/cursor-vs-windsurf-vs-copilot-best-ai-ide-2026
- https://www.mindstudio.ai/blog/best-ai-code-editors
- https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/
- https://dev.to/kainorden/ai-coding-assistants-in-2026-cursor-vs-github-copilot-vs-windsurf-2mm9
- https://diffstudy.com/cursor-vs-github-copilot-vs-windsurf/
- https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison

**Key facts:**
- Cursor: dominant AI code editor for professional developers; $2B ARR by early 2026; 3-5x senior developer productivity gains
- Cursor Automations (late 2025): background agents for scheduled refactors, test generation, dependency updates
- Windsurf: "Cascade" is defining feature — reads files, runs terminal commands, observes output, iterates autonomously
- March 2026 standardized test: Cursor built responsive data table in 2 prompt rounds; Windsurf needed 3; Copilot needed 5 + manual fixes
- Complex task (3000-line Express.js migration): Windsurf Cascade completed in one attempt with 2/47 test failures; Cursor took 3 attempts
- Windsurf pricing March 19, 2026: switched from credit-based to quota-based; Pro raised from $15 to $20/month (matching Cursor); $200/month Max tier added
- GitHub Copilot Coding Agent: turns GitHub issues into PRs autonomously; code review + fix PR generation
- GitHub Copilot CLI: GA as of March 2, 2026 (Visual Studio Magazine)
- GitHub Copilot Autopilot Mode: public preview April 8, 2026 — agents approve their own tool calls, retry errors, work without permission prompts
- Windsurf: 80% of Cursor capabilities at 75% of the price (pre-March 2026 pricing change)
- Most developers combine tools: Cursor/Windsurf for daily coding + Claude Code for large refactors/parallel agents

---

### Query 3: LLMs in production, RAG systems, context engineering

**URLs returned:**
- https://www.meta-intelligence.tech/en/insight-context-engineering
- https://ragflow.io/blog/rag-review-2025-from-rag-to-context
- https://umesh-malik.com/blog/rag-vs-fine-tuning-llms-2026
- https://towardsdatascience.com/rag-isnt-enough-i-built-the-missing-context-layer-that-makes-llm-systems-work/
- https://blog.logrocket.com/llm-context-problem-strategies-2026/
- https://towardsdatascience.com/grounding-your-llm-a-practical-guide-to-rag-for-enterprise-knowledge-bases/
- https://brlikhon.engineer/blog/building-production-rag-systems-in-2026-complete-architecture-guide
- https://blog.bytebytego.com/p/a-guide-to-context-engineering-for
- https://blog.langchain.com/context-engineering-for-agents/
- https://www.elastic.co/search-labs/blog/context-engineering-overview

**Key facts:**
- RAG evolving from "Retrieval-Augmented Generation" → "Context Engine" with intelligent retrieval as core
- Critical bottleneck in 2026: shifted from model side to context side
- Context windows: Claude 200K, Gemini 3 Pro 2M, GPT-4.5 256K — yet RAG still essential
- "Lost in the Middle" problem: LLMs pay significantly more attention to beginning and end of text
- Inference latency for 2M tokens: 30-60 seconds — unsuitable for real-time
- Cost per token increases non-linearly with context length
- Over 70% of errors in modern LLM apps stem from incomplete/irrelevant/poorly structured context
- Production evaluation targets: faithfulness >0.90, answer relevancy >0.85, context recall >0.80, context precision >0.75
- Chunking: "most underestimated lever for RAG performance" — poor chunking torpedoes retrieval accuracy
- Hybrid retrieval (semantic + lexical/BM25) + reranking is best practice for quality
- "RAG-first, tune-second" default for knowledge applications
- Databricks study: model correctness begins falling around 32,000 tokens (context rot)
- ReAct pattern: reason → act (retrieve) → reason again, instead of stuffing all info upfront

---

### Query 4: AI evaluation benchmarks, observability, reliability, failure modes

**URLs returned:**
- https://latitude.so/blog/top-5-ai-agent-evaluation-tools-2026
- https://www.confident-ai.com/knowledge-base/compare/best-ai-observability-tools-2026
- https://www.techloy.com/best-7-llm-evaluation-tools-of-2026-for-genai-systems/
- https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough
- https://medium.com/online-inference/the-best-llm-evaluation-tools-of-2026-40fd9b654dce
- https://www.braintrust.dev/articles/best-ai-agent-observability-tools-2026
- https://www.gartner.com/reviews/market/ai-evaluation-and-observability-platforms
- https://www.ovaledge.com/blog/ai-observability-tools
- https://www.confident-ai.com/blog/definitive-ai-agent-evaluation-guide
- https://logic.inc/resources/ai-model-benchmarks-guide

**Key facts:**
- 37% gap between lab benchmark scores and real-world deployment performance (enterprise agentic AI)
- 50x cost variation for similar accuracy across systems
- MMLU/MMLU-Pro functionally saturated above 88% for frontier models — score differences statistically meaningless
- Humanity's Last Exam: best AI models ~35% accuracy vs human domain experts ~90%
- Data contamination, benchmark gaming, annotation error rates >50% undermine static benchmarks
- Critical failure modes: silent hallucinations, safety regressions, conversational breakdown
- Failures in multi-turn conversations compound — single-turn metrics can't detect experiential failures
- Leading platforms 2026: Latitude, Langfuse, Arize (Phoenix), LangSmith, Galileo, Braintrust
- 89% of organizations have implemented observability for AI agents (industry research)
- Quality issues: primary production barrier at 32%
- Use benchmarks as filters, not verdicts; combine automated eval + model-based screening + human review

---

### Query 5: Prompt-driven development, AI pair programming, productivity

**URLs returned:**
- https://www.refontelearning.com/blog/software-engineering-in-2026-how-ai-and-automation-are-helping-developers-work-smarter
- https://medium.com/@iniyarajan/prompt-engineering-for-developers-master-ai-coding-tools-in-2026-a1ae476b68da
- https://metr.org/blog/2026-02-24-uplift-update/
- https://www.programming-helper.com/tech/prompt-engineering-2026-essential-skill-ai-powered-development
- https://www.cortex.io/post/the-engineering-leaders-guide-to-ai-tools-for-developers-in-2026
- https://medium.com/@addyosmani/my-llm-coding-workflow-going-into-2026-52fe1681325e
- https://trigidigital.com/blog/ai-coding-impact-2026/
- https://dev.to/walid_azrour_0813f6b60398/ai-coding-agents-in-2026-why-every-developer-needs-to-understand-autonomous-software-engineering-2plh
- https://medium.com/@tobore/how-ai-is-reshaping-software-development-and-the-tech-industry-in-2026-4ec7f7a801df
- https://beon.tech/blog/future-ai-engineering/

**Key facts:**
- IBM AI code assistant: 85% acceptance rate for suggested code; 45% productivity boost in preview tests
- Average productivity increase: 31.4% with AI coding assistants vs traditional approaches
- METR (Feb 24, 2026): Updated developer productivity experiment design
- Addy Osmani (Google): "Treat the LLM as a powerful pair programmer that requires clear direction, context and oversight rather than autonomous judgment"
- Addy Osmani workflow: Chunked iteration, not monolithic outputs; focus prompts on one function/bug/feature at a time
- ~90% of Claude Code's own codebase written by Claude Code (Anthropic internal)
- Skill of 2026: "describing what you want built with precision" — not writing code
- Spec-driven development emerging: engineers write specifications, AI generates implementation
- Cortex (2026): AI tools for developers extending beyond coding to incident management, on-call, documentation
- METR uplift study update: changing experiment design methodology for productivity measurement

---

### Query 6: Deploying AI at scale, failure modes

**URLs returned:**
- https://www.pertamapartners.com/insights/ai-project-failure-statistics-2026
- https://earezki.com/ai-news/2026-03-07-5-ai-agent-failures-that-will-kill-your-production-deployment-and-how-i-fixed-them/
- https://www.cloudgeometry.com/blog/what-companies-will-get-wrong-about-ai-in-2026
- https://www.getmaxim.ai/articles/ensuring-ai-agent-reliability-in-production/
- https://medium.com/@prajitdatta/ai-in-2026-why-94-of-companies-are-still-failing-at-production-deployment-and-what-winners-do-759cbf8f9a9f
- https://www.cnbc.com/2026/03/01/ai-artificial-intelligence-economy-business-risks.html
- https://temporal.io/blog/ai-reliability-is-a-decade-old-problem
- https://writer.com/blog/four-ai-failure-modes/
- https://machinelearningmastery.com/5-production-scaling-challenges-for-agentic-ai-in-2026/
- https://www.techaheadcorp.com/blog/ways-multi-agent-ai-fails-in-production/

**Key facts:**
- 80.3% of AI projects fail to deliver intended business value
  - 33.8% abandoned before production
  - 28.4% complete but fail to deliver business value
  - 18.1% deliver some value but can't justify cost
- 95% of GenAI pilots fail to scale to production deployment
- Compound reliability: 20 steps × 95% per-step reliability = 36% success rate
- 5 agents in sequence: 77% reliability (0.95^5)
- 2 agents in sequence: 90.25%; 3 agents: 85.7%
- Scaling cost: 3-agent workflow costs $5-50 in demos → $18,000-90,000/month at scale
- Accuracy drops: 95-98% in pilots → 80-87% in production
- 46% of AI pilots scrapped between POC and broad adoption
- CNBC (March 1, 2026): "Silent failure at scale" — minor AI errors scale over weeks/months
- Real case: beverage manufacturer AI system failed after holiday label redesign → hundreds of thousands of excess cans produced
- Data quality: missing firmographic data/engagement history delays agents months before reliable operation
- 57% of projects face resistance at scale; <40% user adoption in first 6 months for 62% of implementations
- Bias detected post-deployment in 31% of production models; regulatory concerns emerge avg 3.2 months post-deployment
- Infrastructure costs: 3-5x initial projections at production scale

---

### Query 7: Context engineering vs prompt engineering

**URLs returned:**
- https://www.firecrawl.dev/blog/context-engineering
- https://www.elastic.co/search-labs/blog/context-engineering-vs-prompt-engineering
- https://intuitionlabs.ai/articles/context-engineering-vs-prompt-engineering-ai
- https://neo4j.com/blog/agentic-ai/context-engineering-vs-prompt-engineering/
- https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- https://dev.to/serenitiesai/context-engineering-why-its-replacing-prompt-engineering-in-2026-1b4g
- https://www.lyzr.ai/blog/context-engineering/
- https://stackademic.com/blog/prompt-engineering-vs-context-engineering-the-ai-skills-battle-you-need-to-win-in-2026
- https://www.deepset.ai/blog/context-engineering-the-next-frontier-beyond-prompt-engineering
- https://qubittool.com/blog/context-engineering-complete-guide

**Key facts:**
- Context engineering: managing entire information environment (memory, retrieved docs, tool definitions, history)
- Prompt engineering: how you communicate; context engineering: what information the model accesses
- With larger context windows, "prompt phrasing" matters less; context quality matters more
- "Context rot": Databricks study shows correctness drops around 32K tokens even in ultra-long windows
- In 2026: high-quality, precise context has become "incredibly expensive" while prompts are "cheap"
- Anthropic engineering blog: published "Effective context engineering for AI agents"
- Center of gravity shifting: writing better prompts → engineering better contexts
- Agents running in loops generate ever-expanding context: tool outputs, retrieved docs, conversation history
- ReAct pattern addresses context bloat: reason → retrieve → reason (vs. stuff-everything upfront)

---

### Query 8: GitHub Copilot agent mode

**URLs returned:**
- https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents
- https://docs.github.com/en/copilot/get-started/features
- https://sagnikbhattacharya.com/blog/copilot-agent-mode-vscode
- https://github.com/newsroom/press-releases/coding-agent-for-github-copilot
- https://visualstudiomagazine.com/articles/2026/03/02/github-copilot-cli-reaches-general-availability-bringing-agentic-coding-to-the-terminal.aspx
- https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent
- https://code.visualstudio.com/docs/copilot/copilot-cloud-agent
- https://github.blog/news-insights/product-news/github-copilot-meet-the-new-coding-agent/
- https://www.meritforgeai.com/ai-coding/github-copilot-autopilot-mode-guide/
- https://github.com/features/copilot

**Key facts:**
- Copilot Coding Agent: assign GitHub issue → Copilot writes code, runs tests, opens PR autonomously
- Agent mode in VS Code + JetBrains as of March 2026: determines files, edits multi-file, runs terminal, iterates on errors
- Copilot CLI: GA March 2, 2026 — agentic coding in terminal
- Autopilot Mode: public preview April 8, 2026 — agents approve own tool calls, retry errors, no permission prompts
- Available on Pro, Pro+, Business, Enterprise plans
- Code review gathers full project context before suggesting changes → passes suggestions to coding agent for fix PRs
- Caveat: "agent mode produces functional but not always optimal code — variable names may be generic, error messages vague, performance-sensitive paths use naive implementations"
- Pragmatic Engineer survey (906 engineers, Feb 2026): Claude Code #1 most loved at 46%; GitHub Copilot leads overall workplace adoption at 29%; Cursor at 18% (tied with Claude Code); Windsurf at ~8%

---

### Query 9: Vibe coding security vulnerabilities

**URLs returned:**
- https://vibecoding.app/blog/ai-generated-code-security-risks
- https://checkmarx.com/blog/security-in-vibe-coding/
- https://www.nbcnews.com/tech/security/ai-code-vibe-claude-openai-chatgpt-rcna258807
- https://towardsdatascience.com/the-reality-of-vibe-coding-ai-agents-and-the-security-debt-crisis/
- https://www.trendmicro.com/en_us/research/26/c/the-real-risk-of-vibecoding.html
- https://www.databricks.com/blog/passing-security-vibe-check-dangers-vibe-coding
- https://retool.com/blog/vibe-coding-risks
- https://newly.app/articles/vibe-coding-limitations
- https://modall.ca/blog/vibe-coding-security-risks
- https://labs.cloudsecurityalliance.org/research/csa-research-note-ai-generated-code-vulnerability-surge-2026/

**Key facts:**
- AI code generators produce vulnerabilities at ~2x the rate of human-written code
- Typical vibe-coded apps ship with 8-14 security findings per agency audit
- 62% of AI-generated code in Cloud Security Alliance study contained vulnerabilities
- Most common issues: disabled row-level security (~70% of Lovable apps per Beesoul data), leaked secrets, missing webhook verification, absent soft deletes
- Reddit scan of 200+ vibe-coded sites: exposed secrets common; average security score 52/100
- March 2026: Georgia Tech Vibe Security Radar tracked 35 new CVEs directly from AI-generated code (up from 6 in January)
- Moltbook platform breach: Wiz researchers found exposed production database — 1.5M API tokens, 35K emails, private messages
- Vibe-coded projects accumulate technical debt 3x faster
- Developers spend 63% more time fixing AI-generated bugs
- Trendmicro (2026): "The real risk of vibe coding isn't AI writing insecure code. It's humans shipping code they never had a chance to secure."
- NBC News coverage of vibe coding security risks

---

### Query 10: AI dev tool ecosystem (Cursor/Windsurf/Claude Code combined analysis)

**URLs returned:**
- https://www.nxcode.io/resources/news/cursor-vs-windsurf-vs-claude-code-2026
- https://www.shareuhack.com/en/posts/cursor-vs-claude-code-vs-windsurf-2026
- https://dev.to/pockit_tools/cursor-vs-windsurf-vs-claude-code-in-2026-the-honest-comparison-after-using-all-three-3gof
- https://www.shareuhack.com/en/posts/ai-coding-ide-comparison-guide-2026
- https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison
- https://www.mindstudio.ai/blog/windsurf-vs-cursor-vs-claude-code
- https://thenewstack.io/ai-coding-tool-stack/
- https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2
- https://www.tldl.io/resources/ai-coding-tools-2026
- https://neuronad.com/windsurf-vs-cursor/

**Key facts:**
- Three dominant tools: Cursor (AI IDE, 1M+ users), Windsurf (budget agentic IDE, Cascade pioneer), Claude Code (terminal-native, 1M token context)
- March 19, 2026: Windsurf pricing change — Pro $15→$20, $200 Max tier added
- The New Stack (2026): "Cursor, Claude Code, and Codex are merging into one AI coding stack nobody planned"
- Claude Code: 1M token context window; excels at large refactors, security audits, multi-agent parallel tasks
- Pragmatic Engineer (Feb 2026, 906 engineers): Claude Code most loved (46%), Cursor most used workplace tool (29% → 18% tied with CC)
- Common workflow: Cursor/Windsurf for daily + Claude Code for complex/long-context work
- DEV community "5-way showdown" article: comprehensive comparison with real app build

---

### Query 11: AI observability and LLMOps tools

**URLs returned:**
- https://www.braintrust.dev/articles/best-ai-observability-tools-2026
- https://www.confident-ai.com/knowledge-base/compare/top-7-llm-observability-tools
- https://o-mega.ai/articles/top-5-ai-agent-observability-platforms-the-ultimate-2026-guide
- https://mlflow.org/top-5-agent-observability-tools
- https://www.getmaxim.ai/articles/top-5-llm-observability-platforms-for-2026/
- https://agenta.ai/blog/top-llm-observability-platforms
- https://www.braintrust.dev/articles/langfuse-alternatives-2026
- https://www.braintrust.dev/articles/best-ai-observability-platforms-2025
- https://www.firecrawl.dev/blog/best-llm-observability-tools
- https://arize.com/llm-evaluation-platforms-top-frameworks/

**Key facts:**
- Top 5 LLM observability platforms 2026: Maxim AI, Arize AI (Phoenix), LangSmith, Langfuse, Braintrust
- Langfuse: open-source; self-hosted; trace viewing, prompt versioning, cost tracking; ClickHouse analytical backend
- Braintrust: evaluation-first; 80x faster query performance vs alternatives; experiment framework for systematic prompt iteration; SDK/OpenTelemetry/AI Proxy integration
- Arize Phoenix: open-source, self-hosted; vendor-agnostic; supports LlamaIndex, LangChain, DSPy, Haystack
- 89% of organizations implemented observability for AI agents
- Quality issues: primary production barrier at 32%
- Observability is now "non-negotiable" as agents move from prototypes to mission-critical systems
- Gartner market: AI Evaluation and Observability Platforms — active reviews

---

### Query 12: Addy Osmani LLM coding workflow

**URLs returned:**
- https://medium.com/@addyosmani/my-llm-coding-workflow-going-into-2026-52fe1681325e
- https://addyo.substack.com/p/my-llm-coding-workflow-going-into
- https://addyosmani.com/blog/ai-coding-workflow/
- https://www.linkedin.com/posts/addyosmani_ai-programming-softwareengineering-activity-7407683628396298240-G0hd
- https://www.linkedin.com/posts/addyosmani_ai-programming-softwareengineering-activity-7420197342873735168-xmGX
- https://open.substack.com/pub/addyo/p/my-llm-coding-workflow-going-into?comments=true
- https://dev.to/weekly/weekly-53-2025-llm-workflows-code-bottlenecks-ai-adoption-in-2026-c26
- https://addyosmani.com/blog/code-agent-orchestra/
- https://app.daily.dev/posts/my-llm-coding-workflow-going-into-2026-ulft9bddl

**Key facts:**
- Addy Osmani (Google Chrome): advocates chunked iteration — break into focused prompts, one function/bug/feature at a time
- LLMs as "extremely fast junior dev whose work is instantly checked by a tireless QA engineer"
- AI writes code → automated tools catch issues → AI fixes → loop — engineer oversees high-level direction
- Quality gates + testing essential alongside AI-generated code
- No matter how much AI is used: "engineer remains accountable — only merge/ship code after understanding it"
- "Code Agent Orchestra" article: what makes multi-agent coding work
- ~90% of Claude Code written by Claude Code itself (Anthropic)

---

## STATISTICS SUMMARY

| Metric | Value | Source |
|--------|-------|--------|
| US developer vibe coding adoption | 92% | SecondTalent |
| All new code that is AI-generated | 41% | Multiple |
| Gartner 2026 projection | 60% AI-generated code | Gartner |
| AI code tools market 2026 | $8.5B | Multiple |
| AI-generated code with security vulnerabilities | 45-62% | Multiple |
| Code quality: AI vs human major issues | 1.7x more | Dec 2025 analysis |
| Security vulnerability rate ratio | 2.74x higher | Dec 2025 analysis |
| Technical debt accumulation | 3x faster | Multiple |
| Developer time fixing AI bugs | 63% more | Multiple |
| AI project failure rate | 80.3% | Pertama Partners |
| GenAI pilot-to-production failure | 95% | Multiple |
| Benchmark-to-production gap | 37% | Enterprise data |
| 20-step workflow reliability (95%/step) | 36% | Math |
| IBM AI assistant acceptance rate | 85% | IBM |
| Average productivity increase | 31.4% | Survey |
| Cursor ARR | $2B | Early 2026 |
| Claude Code "most loved" rating | 46% | Pragmatic Engineer (Feb 2026, n=906) |
| GitHub Copilot workplace adoption | 29% | Same survey |
| New CVEs from AI code (March 2026) | 35 | Georgia Tech |
| Context errors causing LLM failures | >70% | Industry data |
| Organizations with AI observability | 89% | Industry research |
