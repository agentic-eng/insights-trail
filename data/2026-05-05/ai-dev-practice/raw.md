# AI Dev Practice — Raw Research Data
**Date:** 2026-05-05
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## SEARCH BATCH 1: Vibe Coding & AI-Assisted Development

### Search Query: "vibe coding AI-assisted development 2026 Reddit discussion"

**Sources found:**
- https://ghelburlabs.substack.com/p/ai-automation-trends-shaping-2026 — AI Automation Trends Shaping 2026: From Vibe Coding to Claude-Powered Builds
- https://www.morphllm.com/reddit-vibe-coding — Vibe Coding on Reddit: What Developers Actually Think (2026)
- https://www.producthunt.com/p/vibecoding/will-vibe-coding-dominate-app-dev-in-2026-from-a-10-year-dev-s-view — ProductHunt discussion
- https://medium.com/@addyosmani/vibe-coding-is-not-the-same-as-ai-assisted-engineering-3f81088d5b98 — Addy Osmani on Medium
- https://en.wikipedia.org/wiki/Vibe_coding — Wikipedia: Vibe coding
- https://stackoverflow.blog/2026/01/02/a-new-worst-coder-has-entered-the-chat-vibe-coding-without-code-knowledge/ — Stack Overflow Blog
- https://aibudwp.com/best-vibe-coding-ai-on-reddit-what-the-community-recommends-for-smarter-faster-coding/ — AI Bud: Best Vibe Coding AI on Reddit
- https://roadmap.sh/vibe-coding/best-tools — The 10 Best Vibe Coding Tools in 2026
- https://madewithlove.com/blog/a-guide-to-vibe-coding-vs-ai-assisted-development/ — Guide to vibe coding vs AI-assisted development
- https://news.harvard.edu/gazette/story/2026/04/vibe-coding-may-offer-insight-into-our-ai-future/ — Harvard Gazette article

**Key findings:**
- Reddit communities (r/vibecoding, r/ChatGPTCoding) show mixed opinions on vibe coding
- Common workflow: prototype in Lovable/Bolt → graduate to Cursor/Claude Code for production
- Google's Addy Osmani drew key distinction: vibe coding ≠ AI-assisted engineering
- Reddit consensus: vibe coding is a prototyping methodology, not a production methodology
- Andrej Karpathy coined term in February 2025; Collins Dictionary named it Word of the Year

---

## SEARCH BATCH 2: AI Coding Tools (Cursor, Windsurf, Copilot)

### Search Query: "Cursor Windsurf GitHub Copilot agent mode AI coding tools 2026"

**Sources found:**
- https://artificialanalysis.ai/agents/coding — Coding Agents Comparison
- https://www.mindstudio.ai/blog/best-ai-code-editors — Best AI Code Editors in 2026
- https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2 — 5-way comparison
- https://www.codeant.ai/blogs/best-ai-code-editor-cursor-vs-windsurf-vs-copilot — Codeant comparison
- https://medium.com/@kanerika/github-copilot-vs-claude-code-vs-cursor-vs-windsurf-2026-c54f8a5cc051 — Kanerika comparison
- https://dev.to/kainorden/ai-coding-assistants-in-2026-cursor-vs-github-copilot-vs-windsurf-2mm9 — DEV Community comparison
- https://www.nxcode.io/resources/news/best-ai-code-editor-2026-cursor-windsurf-copilot-zed-compared — NxCode comparison
- https://www.buildmvpfast.com/blog/cursor-vs-windsurf-vs-copilot-best-ai-ide-2026 — BuildMVPFast comparison
- https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison — daily.dev comparison
- https://toolradar.com/guides/best-ai-coding-tools — Toolradar guide

**Key findings:**
- Cursor: crossed $1 billion ARR in under two years
- GitHub Copilot: 4.7M paid subscribers, 20M total users, 42% market share, 90% Fortune 100 adoption
- Windsurf: ~80% of Cursor's capability at ~75% of the price
- Tool categories: IDE extensions (Copilot, Cline, Continue), dedicated IDEs (Cursor, Windsurf, Zed), CLI tools (Claude Code, Aider), cloud platforms (Devin, OpenHands, Jules)

**5-Way App Build Comparison Results:**
| Tool | Time to MVP | Code Quality | Bugs | Security Issues |
|------|-------------|--------------|------|-----------------|
| Cursor | 4h 23m | B (74) | 8 | 3 |
| Claude Code | 5h 12m | A (86) | 5 | 1 |
| Windsurf | 3h 58m | C (62) | 11 | 4 |
| Replit Agent | 4h 47m | C (58) | 9 | 2 |
| GitHub Copilot | 5h 56m | A (89) | 4 | 0 |

---

## SEARCH BATCH 3: LLMs in Production, RAG, Context Engineering

### Search Query: "LLMs in production RAG systems context engineering 2026"

**Sources found:**
- https://ragflow.io/blog/rag-review-2025-from-rag-to-context — RAGFlow: From RAG to Context
- https://towardsdatascience.com/grounding-your-llm-a-practical-guide-to-rag-for-enterprise-knowledge-bases/ — TDS: Grounding Your LLM
- https://www.meta-intelligence.tech/en/insight-context-engineering — Context Engineering Guide 2026
- https://towardsdatascience.com/rag-isnt-enough-i-built-the-missing-context-layer-that-makes-llm-systems-work/ — TDS: RAG Isn't Enough
- https://umesh-malik.com/blog/rag-vs-fine-tuning-llms-2026 — RAG vs Fine-Tuning 2026
- https://lushbinary.com/blog/rag-retrieval-augmented-generation-production-guide/ — RAG Production Guide 2026
- https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems — RAG is Dead, Long Live Context Engineering
- https://ranksquire.com/2026/04/13/llm-architecture-2026/ — LLM Architecture 2026
- https://blog.logrocket.com/llm-context-problem-strategies-2026/ — LogRocket: LLM context problem in 2026
- https://intuitionlabs.ai/articles/what-is-context-engineering — What Is Context Engineering?

**Key findings:**
- RAG evolving into "Context Engine" with intelligent retrieval as core capability
- Critical bottleneck has shifted from model side to context side
- Industry analysis: when RAG fails, failure point is retrieval 73% of the time
- Ultra-long context windows (200K+ tokens) not a silver bullet — attention blind spots
- LangChain's four context strategies: write, select, compress, isolate
- Hybrid approach becoming standard: retrieval for facts, fine-tuning for style/policy

---

## SEARCH BATCH 4: AI Evaluation and Benchmarks

### Search Query: "AI evaluation benchmarks LLM reliability failure modes production 2026"

**Sources found:**
- https://llm-stats.com/benchmarks — LLM Benchmarks 2026
- https://medium.com/@adnanmasood/reliability-benchmarks-for-production-llm-systems-a-field-guide-to-llm-benchmarks-78e4354ac8c1 — Field Guide to LLM Benchmarks
- https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough — Kili Technology: AI Benchmarks 2026
- https://roboticsandautomationnews.com/2026/04/10/how-to-run-llm-evaluation-for-better-ai-performance/100499/ — LLM Evaluation Frameworks
- https://www.lxt.ai/blog/llm-benchmarks/ — LXT: LLM Benchmarks 2026
- https://iternal.ai/llm-selection-guide — 30+ Models Ranked
- https://creati-ai.gitbook.io/blog/ai-development/the-best-9-llm-evaluation-tools-of-2026 — Best 9 LLM Evaluation Tools
- https://www.confident-ai.com/knowledge-base/best-llm-observability-platforms-to-improve-ai-product-reliability-2026 — Best LLM Observability Platforms
- https://www.mlaidigital.com/blogs/llm-evaluation-frameworks-2025-vs-2026-what-matters-now-2026 — Evaluation Frameworks 2025 vs 2026
- https://contextqa.com/blog/llm-testing-tools-frameworks-2026/ — LLM Testing Tools 2026

**SWE-bench Data (May 2026):**
- Claude Mythos Preview: 93.9% (leads SWE-bench Verified)
- Claude Opus 4.7 (Adaptive): 87.6%
- GPT-5.3 Codex: 85%
- Average across 83 models: 63.4%
- Live-SWE-agent (open source + Claude Opus 4.5): 79.2%

**Key findings:**
- MMLU ceiling: frontier models scoring above 88%, differences are statistical noise
- 37% gap between lab benchmark scores and real-world enterprise performance
- International AI Safety Report 2026: models behave safer during testing than in production
- "METR research found one model, tasked with optimizing execution speed, simply rewrote the timer function to report fast results"
- Production evaluation requires layered approach: automated metrics + LLM-as-a-judge + human expert review

---

## SEARCH BATCH 5: AI Observability

### Search Query: "AI observability deploying AI at scale monitoring 2026"

**Sources found:**
- https://www.microsoft.com/en-us/microsoft-cloud/blog/2026/04/16/your-ai-steering-committees-2026-checklist-observability/ — Microsoft: Observability Checklist 2026
- https://www.logicmonitor.com/blog/observability-ai-trends-2026 — LogicMonitor: Observability Trends
- https://www.braintrust.dev/articles/best-ai-observability-tools-2026 — Braintrust: AI Observability Tools
- https://uptimerobot.com/knowledge-hub/observability/ai-observability-the-complete-guide/ — UptimeRobot: AI Observability Guide
- https://middleware.io/blog/how-ai-based-insights-can-change-the-observability/ — Middleware: AI-Based Insights
- https://agility-at-scale.com/ai/architecture/monitoring-and-observability/ — AI Monitoring and Observability
- https://atlan.com/know/ai-agent-observability/ — AI Agent Observability Guide
- https://www.ibm.com/think/insights/observability-trends — IBM: Observability Trends 2026
- https://gogloby.com/insights/best-observability-tools-to-track-ai-agents/ — Best LLM Observability Tools
- https://www.ovaledge.com/blog/ai-observability-tools — AI Observability Tools

**Key findings:**
- Without centralized view, "shadow AI" and unmanaged agents create security/data risks
- Tool consolidation as default strategy: fewer platforms = less overhead + unified data
- Key monitoring dimensions: latency, cost (token consumption), success rate
- 89% of agent deployments have observability; 62% have detailed tracing (LangChain State of Agent Engineering)
- Uber reportedly burned through 2026 AI budget in 4 months after rolling out Claude Code ($500-$2,000 per engineer/month)

---

## SEARCH BATCH 6: Vibe Coding — What Works vs What Breaks

### Search Query: "vibe coding AI pair programming what works what breaks engineering teams 2026"

**Sources found:**
- https://dev.to/pockit_tools/vibe-coding-in-2026-the-complete-guide-to-ai-pair-programming-that-actually-works-42de — DEV Community guide
- https://en.wikipedia.org/wiki/Vibe_coding — Wikipedia
- https://colaninfotech.com/blog/vibe-coding-2026-guide/ — Colain Infotech guide
- https://pockit.tools/blog/vibe-coding-ai-pair-programming-guide/ — Pockit tools guide
- https://vibecoding.app/blog/agentic-engineering-for-software-teams — Agentic Engineering for Software Teams
- https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code — daily.dev guide
- https://www.alexcloudstar.com/blog/vibe-coding-revolution-2026/ — Alex Cloudstar: Revolution or Risk?
- https://tateeda.com/blog/vibe-coding-vs-professional-engineering — TATEEDA: Vibe Coding vs Engineering
- https://news.harvard.edu/gazette/story/2026/04/vibe-coding-may-offer-insight-into-our-ai-future/ — Harvard Gazette
- https://madewithlove.com/blog/a-guide-to-vibe-coding-vs-ai-assisted-development/ — Madewithlove guide

**What Works:**
- 25-55% task completion speedup with AI assistance
- Senior engineers (3+ years): 40-50% productivity gains
- Flow state development: AI handles mechanical parts, humans focus on architecture
- Rapid prototyping: instant scaffolding for MVPs

**What Breaks:**
- AI co-authored code has 1.7x more "major" issues than human-written code
- Security vulnerabilities: 2.74x higher in AI-generated code
- Misconfigurations: 75% more common in AI code
- Only 48% of developers consistently review AI code before committing (despite 96% not fully trusting it)
- Junior engineers see only 15-25% improvement (vs 40-50% for seniors)
- Tim Lorent (March 2026): Cursor's auto-edit mode leads to code that "builds for now, not for later"

---

## SEARCH BATCH 7: Hacker News Discussions

### Sources found:
- https://news.ycombinator.com/item?id=44740930 — "Context engineering is the new vibe coding" (HN thread)
- https://news.ycombinator.com/item?id=44427757 — "The new skill in AI is not prompting, it's context engineering" (915 points)
- https://news.ycombinator.com/item?id=47062534 — "The Future of AI Software Development" (202 points, 142 comments)
- https://news.ycombinator.com/item?id=46489061 — "My LLM coding workflow going into 2026"
- https://news.ycombinator.com/item?id=45751880 — "Vibe Coding vs. Context-Aware Coding"
- https://news.ycombinator.com/item?id=47155394 — "Show HN: I built an AI senior architect"
- https://news.ycombinator.com/item?id=45880284 — "Context engineering can save your company from AI vibe code overload"
- https://news.ycombinator.com/item?id=46596038 — "Vibe Engineering: What I've Learned Working with AI Coding Agents"
- https://news.ycombinator.com/item?id=45821587 — "From vibe coding to context engineering: 2025 in software development"
- https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 — Developers Digest summary

**HN Thread Highlights:**

"Context engineering is the new vibe coding" (HN #44740930):
- simonw highlighted Drew Breunig's work on context failure modes: Tool Loadout, Context Quarantine, Context Pruning, Context Summarization
- Critics: "whether they call it now 'prompt' or 'context' engineering...it's the same tinkering"
- Practical finding: Most meaningful context fits within ~10k tokens despite claimed larger windows
- Breaking complex tasks across multiple specialized agents works better than single large-context approaches

"The Future of AI Software Development" (HN #47062534, 202 points, 142 comments):
- "Code is now like steel. It's somewhat valuable by itself, but we don't need the town blacksmith."
- simonw: "Code becoming commodity; future lies in knowing what's possible to build"
- "Velocity without understanding is not sustainable"
- "Code is disposable and regenerable; what we review, version-control changes"
- Uber burned through entire 2026 AI budget in 4 months after Claude Code rollout ($500-$2,000/engineer/month)

---

## SEARCH BATCH 8: GitHub Copilot Agent Mode

### Sources found:
- https://docs.github.com/copilot/concepts/agents/coding-agent/about-coding-agent — GitHub Docs: About Coding Agent
- https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents — NxCode guide
- https://docs.github.com/en/copilot/get-started/features — GitHub Copilot features
- https://code.visualstudio.com/docs/copilot/copilot-cloud-agent — VS Code: Copilot Cloud Agent
- https://github.com/features/copilot/agents — GitHub Copilot Agents
- https://docs.github.com/copilot/using-github-copilot/coding-agent/asking-copilot-to-create-a-pull-request — Asking Copilot to create a PR
- https://github.blog/changelog/2026-04-27-github-copilot-code-review-will-start-consuming-github-actions-minutes-on-june-1-2026/ — Copilot code review billing change
- https://github.com/orgs/community/discussions/159068 — Coding agent GA announcement
- https://github.com/features/copilot — GitHub Copilot main page
- https://thoughtminds.ai/blog/why-teams-use-github-copilot-wrong-and-fix-it — Why Teams Use Copilot Wrong

**Key findings:**
- Copilot cloud agent: autonomous GitHub Actions-powered environment, issue → PR workflow
- March 2026: Copilot Coding Agent works in VS Code and JetBrains
- Code review feature shipped on agentic architecture March 5, 2026
- Code review will start consuming GitHub Actions minutes June 1, 2026
- Available on Pro, Pro+, Business, Enterprise plans

---

## SEARCH BATCH 9: Context Engineering (Thoughtworks, The New Stack, Martin Fowler)

### Sources found:
- https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html — Context Engineering for Coding Agents
- https://thenewstack.io/context-is-ai-codings-real-bottleneck-in-2026/ — Context is AI coding's real bottleneck
- https://thenewstack.io/rag-isnt-dead-but-context-engineering-is-the-new-hotness/ — RAG isn't dead but context engineering is hot
- https://www.thoughtworks.com/en-us/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices — Spec-driven development
- https://thenewstack.io/why-agentic-ai-needs-a-context-based-approach/ — Agentic AI needs context-based approach
- https://thenewstack.io/context-engineering-going-beyond-prompt-engineering-and-rag/ — Context Engineering beyond prompt engineering
- https://www.thoughtworks.com/insights/blog/machine-learning-and-ai/vibe-coding-context-engineering-2025-software-development — From vibe coding to context engineering
- https://thenewstack.io/context-engineering-the-foundation-for-reliable-ai-agents/ — Context Engineering foundation
- https://www.thoughtworks.com/en-ca/radar/techniques/context-engineering — Thoughtworks Radar: Context engineering

**Key findings from Thoughtworks:**
- "The transition from 'vibe coding' to 'context engineering' highlights that human developers remain absolutely critical"
- "After years of the industry assuming progress in AI is all about scale and speed, we're starting to see that what matters is the ability to handle context effectively"
- Teams using reference applications as contextual anchors
- Deploying teams of specialized agents rather than single all-knowing agents
- MCP and A2A protocols emerging as consensus standards
- Structured Prompt-Driven Development (SPDD) — Thoughtworks method treating prompts as first-class artifacts

---

## SEARCH BATCH 10: Prompt Engineering to Context Engineering

### Sources found:
- https://fungies.io/ai-prompt-engineering-best-practices-2026/ — Prompt Engineering Best Practices 2026
- https://codeling.dev/blog/prompt-engineering-best-practices/ — Codeling: Prompt Engineering Best Practices
- https://www.sdggroup.com/en/insights/blog/the-evolution-of-prompt-engineering-to-context-design-in-2026 — Evolution: Prompt Eng to Context Design
- https://packmind.com/context-engineering-ai-coding/context-engineering-best-practices/ — Context Engineering Best Practices
- https://sombrainc.com/blog/ai-context-engineering-guide — Context Engineering Guide
- https://www.lakera.ai/blog/prompt-engineering-guide — Lakera: Prompt Engineering Guide
- https://martinfowler.com/articles/structured-prompt-driven/ — Structured-Prompt-Driven Development (SPDD)
- https://thomas-wiegold.com/blog/prompt-engineering-best-practices-2026/ — Prompt Engineering Best Practices
- https://www.braintrust.dev/articles/best-prompt-engineering-tools-2026 — Best Prompt Engineering Tools
- https://www.promptitude.io/post/the-complete-guide-to-prompt-engineering-in-2026-trends-tools-and-best-practices — Complete Guide to Prompt Engineering 2026

**Key findings:**
- Optimal prompt length: 150-300 words for most tasks
- LLM reasoning performance degrades after ~3,000 tokens even in models with million-token context windows
- Structured Prompt-Driven Development (SPDD) on martinfowler.com: prompts as first-class artifacts in version control
- Context engineering is infrastructure-level thinking, not prompt-level thinking

---

## SEARCH BATCH 11: Reddit AI Coding Tools

### Sources found:
- https://claw.mobile/blog/best-ai-coding-tool-reddit-2026 — Best AI Coding Tools: Reddit Recommends
- https://www.aitooldiscovery.com/guides/best-ai-for-coding-reddit — Best AI for Coding: Reddit's Top Picks
- https://www.aitooldiscovery.com/guides/cursor-reddit — Cursor AI Reddit: What Developers Really Think
- https://beginnersinai.org/best-ai-tools-reddit-2026/ — Best AI Tools in 2026: Reddit Recommends
- https://www.aitooldiscovery.com/guides/best-ai-tools-reddit — Reddit's Top AI Tools
- https://zapier.com/blog/ai-coding-tools/ — Zapier: Best AI Coding Tools in 2026
- https://www.faros.ai/blog/best-ai-model-for-coding-2026 — Best AI Models for Coding: Real-World Reviews

**Reddit Community Quotes:**
- r/MachineLearning: "Switched from Copilot after Composer built my entire React auth flow across 15 files in 20 mins. Copilot just suggests lines, Cursor executes."
- r/programming (devopsguru): "Tab predicts your next edit, not just lines. 2x faster than Copilot."
- r/cursor_ai (fullstackninja): "Cursor's Composer is transformative. 'Update all components using old Button API' and it diffs every file perfectly."
- r/cursor_ai (ratelimiteddev): "Pro hits limits after 50 heavy Composer uses/day, back to free Copilot."
- r/cursor_ai (enterprise dev): "100K+ file repos lag hard; needs better indexing."
- r/webdev, r/ExperiencedDevs: "I spent 3 hours fixing what the AI broke in 3 minutes"
- r/ExperiencedDevs (800+ comments): "It works until someone enters an emoji in the name field" (on edge case failures)

---

## SEARCH BATCH 12: AI Agent Reliability

### Sources found:
- https://neuralwired.com/2026/04/28/why-ai-agents-fail-production/ — Why AI Agents Fail in Production
- https://asanify.com/blog/news/ai-agent-hallucination-april-29-2026/ — The AI Agent Hallucination Trap
- https://temporal.io/blog/ai-reliability-is-a-decade-old-problem — AI Reliability: Decade-Old Problem
- https://suprmind.ai/hub/insights/ai-hallucination-statistics-research-report-2026/ — AI Hallucination Statistics 2026
- https://suprmind.ai/hub/ai-hallucination-rates-and-benchmarks/ — AI Hallucination Rates & Benchmarks
- https://tfir.io/ai-agents-production-reliability-mezmo-aura/ — Why AI Agents Fail: Mezmo
- https://latitude.so/blog/top-5-ai-agent-evaluation-tools-2026 — Top AI Agent Evaluation Tools
- https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026 — International AI Safety Report 2026
- https://www.getmaxim.ai/articles/top-6-reasons-why-ai-agents-fail-in-production-and-how-to-fix-them/ — Top 6 Reasons AI Agents Fail
- https://www.getmaxim.ai/articles/measuring-llm-hallucinations-the-metrics-that-actually-matter-for-reliable-ai-apps/ — Measuring LLM Hallucinations

**Key failure statistics:**
- 90-95% of AI agent pilots never reach production
- 40%+ of agentic AI projects predicted to be canceled by 2027 (Gartner)
- 88% of organizations experienced at least one AI agent security incident in 2025
- 82% of AI bugs stem from hallucinations/accuracy failures (not crashes)
- Deloitte: 47% of enterprise AI users based at least one major business decision on hallucinated content
- Production systems cost 5-10x more than pilots ($100K-$400K+ vs $5K-$50K)

**Five Core Failure Classes (NeuralWired):**
1. Context Drift — attention dilution after 30-50 steps
2. Hallucination Cascades — wrong inferences propagating as facts
3. Tool Execution Failure Propagation — silent errors cascade downstream
4. Memory Architecture Mismatch — retrieval misses decision-critical info
5. Epistemic Blindness — agents can't distinguish knowledge from hallucination

---

## SEARCH BATCH 13: Developer Surveys

### Sources found:
- https://survey.stackoverflow.co/2025/ — Stack Overflow Developer Survey 2025
- https://survey.stackoverflow.co/2025/ai/ — Stack Overflow AI section
- https://stackoverflow.blog/2025/12/29/developers-remain-willing-but-reluctant-to-use-ai-the-2025-developer-survey-results-are-here/ — SO Blog: Willing but Reluctant
- https://www.getpanto.ai/blog/ai-coding-assistant-statistics — AI Coding Statistics
- https://www.secondtalent.com/resources/ai-coding-assistant-statistics/ — AI Coding Assistant Statistics 2026
- https://www.index.dev/blog/developer-productivity-statistics-with-ai-tools — Developer Productivity Statistics 2026
- https://shiftmag.dev/stack-overflow-survey-2025-ai-5653/ — 84% use AI, most don't trust it
- https://www.index.dev/blog/ai-pair-programming-statistics — AI Pair Programming Statistics 2026
- https://www.netcorpsoftwaredevelopment.com/blog/ai-generated-code-statistics — AI-Generated Code Statistics 2026
- https://www.technologyreview.com/2025/12/15/1128352/rise-of-ai-coding-developers-2026/ — MIT Technology Review: AI coding is everywhere

**Key survey data:**
- 84% of developers using or planning to use AI tools (up from 76%)
- 51% of professional developers use AI tools daily
- 92% of US developers use AI coding tools daily (broader measure)
- 70% of agent users agree AI has reduced time on specific tasks
- METR study: developers believed AI made them 20% faster, but objective tests showed 19% slower
- DX analysis: average 3.6 hours/week saved per developer
- 66% cite "AI solutions that are almost right, but not quite" as a concern
- 45% find debugging AI-generated code more time-consuming than writing from scratch
- 48% of AI-generated code contains security vulnerabilities
- Developer positive sentiment: 70%+ (2023/2024) → 60% (2025)

---

## SEARCH BATCH 14: Karpathy / X/Twitter

### Sources found:
- https://x.com/karpathy/status/2019137879310836075 — Karpathy: 1-year anniversary retrospective
- https://x.com/karpathy/status/1886192184808149383 — Karpathy: original vibe coding tweet
- https://dev.to/h1gbosn/what-is-vibe-coding-in-2026-one-year-from-karpathys-tweet-5f43 — One Year from Karpathy's Tweet
- https://app.dealroom.co/news/note/vibe-coding-was-just-the-warmup-andrej-karpathy-on-the-dawn-of-software-3-0 — Karpathy on Software 3.0
- https://twitter.com/karpathy/status/1903870973126045712 — Karpathy tweet on agentic engineering
- https://www.coderabbit.ai/blog/a-semantic-history-how-the-term-vibe-coding-went-from-a-tweet-to-prod — Semantic history of vibe coding
- https://medium.com/ai-systems-lab/why-vibe-coding-ends-in-2026-karpathy-explains-f9c490f5f019 — Why Vibe Coding Ends in 2026
- https://www.teamday.ai/blog/vibe-coding-to-agentic-engineering — From Vibe Coding to Agentic Engineering
- https://thenewstack.io/vibe-coding-is-passe/ — Vibe coding is passé
- https://simonwillison.net/2025/Mar/19/vibe-coding/ — Simon Willison: Not all AI-assisted programming is vibe coding

**Key findings:**
- Karpathy's original tweet (Feb 2025) got 4.5M views — described as a "shower of thoughts throwaway tweet"
- February 2026 anniversary: Karpathy coined new term "agentic engineering"
- Quote (Karpathy): "programming via LLM agents is increasingly becoming a default workflow for professionals, except with more oversight and scrutiny, with the goal to claim the leverage from agents but without any compromise on software quality"
- Simon Willison (simonw): "Not all AI-assisted programming is vibe coding"
- "Code is now like steel. It's somewhat valuable by itself, but we don't need the town blacksmith." (HN)

---

## SEARCH BATCH 15: RAG/TDS/LangChain Deep Sources

### Sources found:
- https://towardsdatascience.com/beyond-rag/ — Is RAG Dead? Rise of Context Engineering
- https://towardsdatascience.com/why-context-is-the-new-currency-in-ai-from-rag-to-context-engineering/ — Context is New Currency in AI
- https://www.langchain.com/blog/context-engineering-for-agents — LangChain: Context Engineering for Agents
- https://towardsdatascience.com/grounding-your-llm-a-practical-guide-to-rag-for-enterprise-knowledge-bases/ — Grounding Your LLM
- https://towardsdatascience.com/rag-isnt-enough-i-built-the-missing-context-layer-that-makes-llm-systems-work/ — RAG Isn't Enough
- https://towardsdatascience.com/understanding-context-and-contextual-retrieval-in-rag/ — Contextual Retrieval in RAG
- https://www.langchain.com/state-of-agent-engineering — State of Agent Engineering (LangChain)
- https://towardsdatascience.com/six-lessons-learned-building-rag-systems-in-production/ — Six Lessons Learned

**LangChain State of Agent Engineering (1,340 survey responses, Nov-Dec 2025):**
- 57.3% have agents in production; 30.4% actively developing
- Top use cases: customer service (26.5%), research/data analysis (24.4%), internal workflow automation (18%)
- Biggest barriers: quality (32%), latency (20%), security for enterprises (24.9%)
- Quality issue = "hallucinations and consistency of outputs"
- 89% have implemented observability; 62% detailed tracing
- 67%+ use OpenAI's GPT models; 75%+ use multiple models
- 57% do not fine-tune; prefer base models with prompt engineering and RAG

---

## SEARCH BATCH 16: SWE-bench and Coding Benchmarks

### Sources found:
- https://epoch.ai/benchmarks/swe-bench-verified — Epoch AI: SWE-bench Verified
- https://labs.scale.com/leaderboard/swe_bench_pro_public — Scale: SWE-Bench Pro
- https://www.vals.ai/benchmarks/swebench — SWE-bench
- https://benchlm.ai/benchmarks/sweVerified — BenchLM: SWE-bench Verified 2026
- https://www.swebench.com/ — SWE-bench Leaderboards
- https://www.codeant.ai/blogs/swe-bench-scores — SWE-bench Scores 2026
- https://openai.com/index/introducing-swe-bench-verified/ — OpenAI: SWE-bench Verified
- https://www.bracai.eu/post/best-ai-for-coding — Best AI for coding
- https://agentmarketcap.ai/blog/2026/04/11/live-swe-agent-open-source-scaffold-swe-bench-2026 — Live-SWE-agent at 79.2%
- https://dasroot.net/posts/2026/04/benchmaxxed-swe-bench-score-local-coding-agents/ — Benchmaxxed SWE-bench score

---

## SEARCH BATCH 17: Addy Osmani Article Deep Dive

### Key content from: https://medium.com/@addyosmani/vibe-coding-is-not-the-same-as-ai-assisted-engineering-3f81088d5b98

**Core distinction:**
- Vibe coding: "fully giving in to the creative flow with an AI, essentially forgetting the code exists"
- AI-assisted engineering: structured workflow with design, testing, human oversight

**CTO Survey Data (August 2025, Final Round AI):**
- 16 of 18 CTOs experienced production disasters from AI-generated code
- Types: performance degradation, security lapses, unmaintainability

**Key quotes:**
- "AI promised to make us all 10x developers, but instead it's making juniors into prompt engineers and seniors into code janitors cleaning up AI's mess."
- "I just wish people would stop pinging me on PRs they obviously haven't even read themselves."
- "AI tools are copilots, not autopilots." — CTO

**Approved vibe coding use cases:**
- Rapid prototyping and hackathons
- Internal one-off tools and scripts
- Greenfield projects (with experienced engineers validating outputs)

---

## SEARCH BATCH 18: Harvard Gazette Article

### Content from: https://news.harvard.edu/gazette/story/2026/04/vibe-coding-may-offer-insight-into-our-ai-future/

**Key quotes:**
- "Vibe coding makes the production of software...accessible to more people. You can have an idea and realize that idea without having a degree in computer science."
- "Vibe coding is often optimized for _how much wow can I get in the next hour_, rather than for the quality of what's created."
- "Being able to imagine possibilities, express clearly what we want to see in the world, review what we create, and iterate, will be incredibly helpful capabilities."

**Concerns:**
- Environmental costs and computational expense
- Privileges strong verbal communicators
- Students struggled articulating problems when AI output fell short

---

## SEARCH BATCH 19: Industry Statistics

### Vibe coding industry:
- Source: https://reborn.hr/unwrapped/vibe-coding-from-a-throwaway-tweet-to-a-6-6-billion-industry
- Lovable valuation: $6.6 billion, $400M ARR by March 2026, 15M daily active users
- Medvi: $1.8B projected 2026 revenue, built by 2 people with $20K investment
- 46% of all new code generated by AI (GitHub data)
- 87% of Fortune 500 use at least one vibe coding platform
- Developer trust: 77% favorable (2023) → 60% favorable (2026)
- Only 33% trust AI code for accuracy
- 63% of developers spend more time debugging AI output than coding from scratch

---

## SEARCH BATCH 20: YouTube Content

### Sources found:
- https://www.youtube.com/watch?v=v7UcVPO4y3c — Vibe Coding Complete Tutorial and Tips - Cursor/Windsurf (Matthew Berman)
- https://ytscribe.com/v/YWwS911iLhg — Transcript of Berman vibe coding tutorial
- https://www.youtube.com/watch?v=YWwS911iLhg — Vibe Coding Tutorial and Best Practices (Matthew Berman)
- https://www.youtube.com/watch?v=qIO9Mg1Man4 — AI Vibe Coding Tutorial + Workflow (Cursor, PRD, Rules, MCP)
- https://www.youtube.com/watch?v=8TcWGk1DJVs — Windsurf Tutorial for Beginners (Better than Cursor??)

---

## SUPPLEMENTARY SOURCES (not yet categorized above):

- https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems — RAG Is Dead, Long Live Context Engineering
- https://buttondown.com/dailyaidigest/archive/dad-burning-through-the-token-budget-the-case-of/ — Daily AI Digest: Uber burning through token budget
- https://thenewstack.io/context-engineering-the-foundation-for-reliable-ai-agents/ — Context Engineering: Foundation for Reliable AI Agents
- https://packmind.com/context-engineering-ai-coding/best-context-engineering-tools/ — Best Context Engineering Tools
- https://www.sdggroup.com/en/insights/blog/the-evolution-of-prompt-engineering-to-context-design-in-2026 — Evolution from Prompt Engineering to Context Design
- https://www.langchain.com/blog/context-engineering-for-agents — LangChain blog on context engineering
- https://www.thoughtworks.com/en-ca/radar/techniques/context-engineering — Thoughtworks Radar: context engineering
- https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html — Context Engineering for Coding Agents (Martin Fowler)
- https://martinfowler.com/articles/structured-prompt-driven/ — Structured-Prompt-Driven Development (SPDD)
- https://simonwillison.net/2025/Mar/19/vibe-coding/ — Simon Willison on vibe coding
- https://www.technologyreview.com/2025/12/15/1128352/rise-of-ai-coding-developers-2026/ — MIT Technology Review: AI coding everywhere
- https://www.index.dev/blog/developer-productivity-statistics-with-ai-tools — Developer Productivity Statistics
- https://www.index.dev/blog/ai-pair-programming-statistics — AI Pair Programming Statistics
- https://internationalaisafetyreport.org/publication/international-ai-safety-report-2026 — International AI Safety Report 2026
- https://dev.to/ceaksan/11-ways-llms-fail-in-production-with-academic-sources-4mf9 — 11 Ways LLMs Fail in Production

