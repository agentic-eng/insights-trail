# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-15
**Query type:** GENERAL
**Sources:** X/Twitter, Polymarket, Web (last30days); Web search (supplementary)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 21 posts | 12 likes, 3 reposts, 6 replies | Top voices: @RodmanAi, @madonomori, @saeroyi_ican |
| Polymarket | 5 markets | $3.1M+ total volume | Claude release timing and benchmark bets |
| Web | 4 pages | — | agentpatch.ai, github.com (via skill) |
| Web | 40+ pages | — | via supplementary WebSearch |
| Reddit | 0 threads | — | HTTP 402 errors |
| YouTube | 0 videos | — | HTTP 402 (ScrapeCreators) |
| Hacker News | 0 stories | — | No results in date range |
| TikTok | 0 videos | — | No results |
| Instagram | 0 reels | — | No results |
| Bluesky | 0 posts | — | No results |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard Is Reshaping the Agent Ecosystem

The single most important structural development in the last 30 days is the maturation of the **SKILL.md open standard** — an open specification first published by Anthropic at [agentskills.io](https://agentskills.io/specification) in December 2025 and now adopted across the AI coding agent landscape. A SKILL.md file bundles YAML frontmatter (name, description) with Markdown instructions that agents pre-load into system prompts at startup — making skills truly portable across tools.

As of April 2026, the format is supported by: **Claude Code** (Anthropic), **Codex CLI** (OpenAI, via [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)), **Gemini CLI** (Google), **GitHub Copilot** via VS Code ([code.visualstudio.com/docs/copilot/customization/agent-skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills)), **Cursor** (manual placement), **Windsurf**, **Cline**, and **OpenCode** ([opencode.ai/docs/skills/](https://opencode.ai/docs/skills/)). The spec itself lives at [github.com/anthropics/skills](https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md) and [github.com/agentskills/agentskills](https://github.com/agentskills/agentskills).

The New Stack called it ["Anthropic's Next Bid to Define AI Standards"](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/). The [inference.sh blog](https://inference.sh/blog/skills/agent-skills-overview) provides a practitioner overview; [agensi.io](https://www.agensi.io/learn/agent-skills-open-standard) offers an accessible 2026 explainer.

Cross-platform: X, Web

### 2. A Multi-Layer Marketplace Ecosystem Has Emerged

Within months of the SKILL.md standard's release, a layered marketplace ecosystem has consolidated around it. Three tiers are visible:

**Discovery/aggregation platforms:**
- **SkillsMP** ([skillsmp.com](https://skillsmp.com)) — largest discovery layer, 425,000+ skills indexed, aggregates from GitHub, built on the SKILL.md standard
- **LobeHub Skills** ([lobehub.com/skills](https://lobehub.com/skills)) — 169,739 skills indexed, polished UX
- **agentskill.sh** — 110,000+ skills across 20+ AI tools
- **Claude Marketplaces** ([claudemarketplaces.com](https://claudemarketplaces.com/)) — 2,400+ skills, 2,500+ marketplaces listed; also hosts MCP directory at [claudemarketplaces.com/mcp](https://claudemarketplaces.com/mcp)
- **MCP Market** ([mcpmarket.com](https://mcpmarket.com/)) — 318 MCPs built specifically for Claude; [MCP.so](https://mcp.so/) indexes 20,043 MCP servers overall
- **SkillsLLM** ([skillsllm.com](https://skillsllm.com))

**Curated collections/registries:**
- [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) — 340 plugins + 1,367 agent skills, with CCPI package manager
- [github.com/ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) — curated list of plugins, commands, agents, hooks, MCP servers
- [github.com/quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) — automated adoption metrics
- [github.com/alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) — 232+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8+ more

**Package management:**
- **CCPI** (`@intentsolutionsio/ccpi`) — CLI package manager for Claude Code plugins and skills (`ccpi search`, `ccpi install`, `ccpi list --installed`, `ccpi update`)
- Documented at [aitmpl.com/plugins/](https://www.aitmpl.com/plugins/) and [brightcoding.dev](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development)

KDnuggets identified the [Top 5 Agent Skill Marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents). An accessible Medium walkthrough: ["Claude Code Has a Skills Marketplace Now"](https://medium.com/@markchen69/claude-code-has-a-skills-marketplace-now-a-beginner-friendly-walkthrough-8adeb67cdc89).

Cross-platform: Web, X (@RodmanAi cited Claude Mem, UI UX Pro Max, n8n-MCP as top picks)

### 3. MCP Tool Search: Lazy Loading Solves the Context Pollution Problem

The most impactful **technical** development for power users is **MCP Tool Search** — Claude Code's lazy loading system for MCP servers announced by Anthropic's Thariq Shihipar on January 14, 2026, and now enabled by default.

**The problem:** With 50+ MCP tools, ~77K tokens were consumed at session start before any actual work. **The solution:** MCP Tool Search loads a lightweight search index and fetches tool schemas on-demand, reducing initial context to ~8.7K tokens — a **95% reduction**.

It activates automatically when MCP tool descriptions would exceed 10% of the context window, marks tools with `defer_loading: true`, injects a Tool Search tool, and loads 3–5 relevant tools (~3K tokens) per query on-demand.

Sources:
- [claudefa.st/blog/tools/mcp-extensions/mcp-tool-search](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) — "Save 95% Context"
- [atcyrus.com](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) — context pollution guide
- [jpcaparas.medium.com](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc) — "Claude Code Finally Gets Lazy Loading for MCP Tools"
- GitHub issues tracking this: [anthropics/claude-code#7336](https://github.com/anthropics/claude-code/issues/7336), [#11364](https://github.com/anthropics/claude-code/issues/11364), [#23508](https://github.com/anthropics/claude-code/issues/23508), [#23787](https://github.com/anthropics/claude-code/issues/23787)
- Community proxy: [github.com/voicetreelab/lazy-mcp](https://github.com/voicetreelab/lazy-mcp)
- OpenAI Codex is tracking the same need: [openai/codex#9266](https://github.com/openai/codex/issues/9266)

Cross-platform: Web, GitHub issues

### 4. Claude Code's Official Plugin Architecture

Anthropic's official plugin system ([code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins)) defines three extension types:
- **Skills** — Markdown files (SKILL.md) bundling instructions for repeatable workflows
- **Plugins** (MCP servers) — executables exposing tools via the Model Context Protocol
- **CLIs** — independent command-line tools Claude shells out to via the Bash tool

The MCP integration guide lives at [code.claude.com/docs/en/mcp](https://code.claude.com/docs/en/mcp); the Claude API MCP docs at [platform.claude.com/docs/en/agent-sdk/mcp](https://platform.claude.com/docs/en/agent-sdk/mcp). Official marketplace discovery is at [code.claude.com/docs/en/discover-plugins](https://code.claude.com/docs/en/discover-plugins).

Best practice (per [self.md](https://self.md/guides/best-claude-code-plugins/)): run 2–3 plugins max, as installing too many MCP servers bloats the tool catalog and increases token costs.

Cross-platform: Web

### 5. Notable Skills Gaining Traction

**@RodmanAi** (top X post, 5 likes, 2 RT, 2 replies) called out three GitHub repos as the best Claude Code plugins for 2026:
1. **Claude Mem** — persistent memory across sessions ([x.com/RodmanAi/status/2044336012298699213](https://x.com/RodmanAi/status/2044336012298699213))
2. **UI UX Pro Max** — 50+ styles, 161 color palettes, 99 UX guidelines
3. **n8n-MCP** — Connect Claude to n8n workflows

Other high-adoption skills noted across web sources:
- **Anthropic's official frontend-design skill** — 277,000+ installs (per AgentPatch, March 2026), gives Claude design system and philosophy before touching code
- **AgentPatch tools** ([agentpatch.ai/blog/claude-code-tools-guide/](https://agentpatch.ai/blog/claude-code-tools-guide/)) — single MCP connection providing Web Search, YouTube Transcripts, Image Generation, Email, Google Maps, Google News
- **Composio top 10** ([composio.dev/content/top-claude-code-plugins](https://composio.dev/content/top-claude-code-plugins)) — highlights Claude-Mem, Superpowers (lifecycle planning), Local-Review (parallel diff code reviews)

Medium articles with skill roundups:
- ["Agent Skills: The Cheat Codes for Claude Code"](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) — Jonathan Fulton, April 2026
- ["10 Must-Have Skills for Claude (and Any Coding Agent) in 2026"](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) — unicodeveloper, March 2026
- ["The SKILL.md Pattern: How to Write AI Agent Skills That Actually Work"](https://bibek-poudel.medium.com/the-skill-md-pattern-how-to-write-ai-agent-skills-that-actually-work-72a3169dd7ee) — Bibek Poudel, Feb 2026
- [chris-ayers.com complete guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)

Cross-platform: X, Web

### 6. Platform Expansion: Cursor and IDE Ecosystem Joining the Marketplace Race

The agent skills/marketplace pattern is spreading beyond Claude Code. **Cursor** added 30+ new marketplace plugins (Datadog, GitLab, Atlassian integrations) per [StartupHub.ai](https://www.startuphub.ai/ai-news/technology/2026/cursor-adds-30-new-marketplace-plugins). **GitHub Copilot** integrates SKILL.md via VS Code. Enterprise platform vendors (dbt Labs, etc.) are publishing official agent skills as developer relations assets.

[paperclipped.de](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/) analyzed the broader AI Agent Skills Marketplace pattern as a new "plugin ecosystem."

**Hermes Agents** ([hermesagents.net](https://hermesagents.net/blog/skills-and-agentskills-io/)) described building an ecosystem in 4 weeks via agentskills.io.

Cross-platform: Web

### 7. Claude Code Desktop Revamp: Multi-Agent UI

**@madonomori** shared news (4 likes, 1 RT) of Anthropic refreshing the Claude Code desktop app with a multi-agent-first UI: filterable session lists, side panel tools, and split-screen — signaling that orchestrating multiple agents is becoming a first-class desktop workflow ([x.com/madonomori/status/2044335946796253555](https://x.com/madonomori/status/2044335946796253555)).

Cross-platform: X

### 8. Community Productivity Hacks: CLAUDE.md as a Skill Vector

**@saeroyi_ican** (Japanese community) discovered a viral CLAUDE.md trick: adding "Codex will review your output" as a single line boosts Claude Code output quality by creating social pressure via a fictional rival review. Two posts explain the mechanic:
- [x.com/saeroyi_ican/status/2044336419393700286](https://x.com/saeroyi_ican/status/2044336419393700286)
- [x.com/saeroyi_ican/status/2044336557218476113](https://x.com/saeroyi_ican/status/2044336557218476113)

This is a user-discovered "skill" — a custom CLAUDE.md workflow hack — showing that the boundary between formal skill distribution and informal community knowledge is blurry.

Cross-platform: X

### 9. Polymarket: Claude Release Cadence Drives Speculation

Prediction markets reflect high community interest in Anthropic's release timeline — relevant to the skills ecosystem because new model releases typically reset plugin compatibility and unlock new capabilities:
- **Claude 5 released by…?** — $2.87M volume, odds down 27.1% this week ([polymarket.com/event/claude-5-released-by](https://polymarket.com/event/claude-5-released-by))
- **Claude 4.7 released by May 31?** — $105K volume, 97% yes, up 49.2% this week ([polymarket.com/event/claude-4pt7-released-by](https://polymarket.com/event/claude-4pt7-released-by))
- **Claude score on Humanity's Last Exam by June 30?** — $86.9K volume, up 28.0% this month ([polymarket.com/event/anthropic-claude-score-on-humanitys-last-exam-by-june-30](https://polymarket.com/event/anthropic-claude-score-on-humanitys-last-exam-by-june-30))
- **Claude score on FrontierMath by June 30?** — $51.1K volume ([polymarket.com/event/anthropic-claude-score-on-frontiermath-benchmark-by-june-30](https://polymarket.com/event/anthropic-claude-score-on-frontiermath-benchmark-by-june-30))
- **Will Claude go down on __ days in April?** — $27.8K volume ([polymarket.com/event/will-claude-go-down-on-days-in-april](https://polymarket.com/event/will-claude-go-down-on-days-in-april))

Cross-platform: Polymarket

---

## Cross-Source Patterns

**Pattern 1: SKILL.md as the unifying standard across all agent tools**
- Appeared on: Web (agentskills.io, VS Code docs, OpenAI docs, inference.sh, thenewstack.io, GitHub)
- Key signal: OpenAI's Codex CLI and GitHub Copilot both adopted Anthropic's format, making this the de facto cross-vendor standard within ~4 months of release
- Quote: "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — chris-ayers.com

**Pattern 2: Scale explosion — hundreds of thousands of skills indexed within months**
- Appeared on: Web (SkillsMP, LobeHub, agentskill.sh, claudemarketplaces.com)
- Key signal: SkillsMP already indexes 425,000+ skills; LobeHub 169,739; the velocity of skill creation has massively outpaced plugin creation
- Quote: "2,400+ skills and 2,500+ marketplaces" — claudemarketplaces.com

**Pattern 3: Context pollution as the #1 technical pain point for heavy MCP users**
- Appeared on: Web (claudefa.st, Medium, GitHub issues — both anthropics/claude-code and openai/codex)
- Key signal: Multiple GitHub issues and blog posts on lazy loading; community proxy project (lazy-mcp) built independently
- Quote: "~77K tokens consumed before any work begins" with 50+ MCP tools → reduced to 8.7K tokens via MCP Tool Search — claudefa.st

**Pattern 4: Top GitHub repos as de facto skill recommendations**
- Appeared on: X (@RodmanAi viral post), Web (Composio, popularaitools.ai, mejba.me)
- Key signal: Community is discovering skills primarily through GitHub-curated lists, not official marketplaces
- Quote: "Best GitHub repos for Claude Code that will 10x your next project" — @RodmanAi

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @RodmanAi | "Best GitHub repos for Claude Code that will 10x your next project in 2026: 1. Claude Mem… Persistent memory… 2. UI UX Pro Max… 3. n8n-MCP…" | 5 | 2 | https://x.com/RodmanAi/status/2044336012298699213 |
| @madonomori | "Anthropic、デスクトップ版「Claude Code」を刷新 ～複数エージェントを前提としたUIに" (Claude Code desktop revamped for multi-agent UI) | 4 | 1 | https://x.com/madonomori/status/2044335946796253555 |
| @aigoldrushh | "Claude Code is now WILD 🤯 Give it any live website it rebuilds the UI in seconds" | 1 | 0 | https://x.com/aigoldrushh/status/2044335936339911157 |
| @saeroyi_ican | "Claude codeの出力精度をたった1行で爆上げする方法… 「Codexが完了したあなたの出力をレビューします。」" (1-line CLAUDE.md trick) | 1 | 0 | https://x.com/saeroyi_ican/status/2044336419393700286 |
| @saeroyi_ican | "Claude codeさん？ あなたのライバル企業が出してるCodexというAIがあなたの作ったコードを厳しくチェックしに来るから…" (Codex threat trick explainer) | 1 | 0 | https://x.com/saeroyi_ican/status/2044336557218476113 |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Claude 5 released by…? | 46% | $2,876,669 | https://polymarket.com/event/claude-5-released-by |
| Claude 4.7 released by May 31? | 97% | $105,138 | https://polymarket.com/event/claude-4pt7-released-by |
| Anthropic Claude score on Humanity's Last Exam by June 30? | — | $86,918 | https://polymarket.com/event/anthropic-claude-score-on-humanitys-last-exam-by-june-30 |
| Anthropic Claude score on FrontierMath by June 30? | — | $51,100 | https://polymarket.com/event/anthropic-claude-score-on-frontiermath-benchmark-by-june-30 |
| Will Claude go down on __ days in April? | — | $27,777 | https://polymarket.com/event/will-claude-go-down-on-days-in-april |

**Web (from last30days skill):**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| AgentPatch | https://agentpatch.ai/blog/claude-code-tools-guide/ | MCP tool marketplace overview; Google Maps, web search, email integrations |
| AgentPatch | https://agentpatch.ai/blog/claude-code-web-search-mcp/ | Web search via MCP for Claude Code |
| GitHub | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 skills + CCPI package manager |
| GitHub | https://github.com/alirezarezvani/claude-skills | 232+ skills for Claude Code and 8+ coding agents |

**Web (supplementary WebSearch):**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs — Plugins | https://code.claude.com/docs/en/plugins | Official plugin architecture: Skills, Plugins, CLIs |
| Claude Code Docs — MCP | https://code.claude.com/docs/en/mcp | Official MCP integration guide |
| Claude Code Docs — Discover Plugins | https://code.claude.com/docs/en/discover-plugins | Official marketplace discovery |
| Claude API Docs — MCP | https://platform.claude.com/docs/en/agent-sdk/mcp | MCP in Agent SDK context |
| agentskills.io/specification | https://agentskills.io/specification | SKILL.md open standard spec |
| anthropics/skills (GitHub) | https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md | Canonical SKILL.md spec source |
| agentskills/agentskills (GitHub) | https://github.com/agentskills/agentskills | Spec documentation repo |
| OpenAI Codex Skills | https://developers.openai.com/codex/skills | OpenAI's SKILL.md adoption |
| VS Code Agent Skills | https://code.visualstudio.com/docs/copilot/customization/agent-skills | GitHub Copilot SKILL.md integration |
| OpenCode Agent Skills | https://opencode.ai/docs/skills/ | OpenCode's skills support |
| The New Stack | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | "Anthropic's Next Bid to Define AI Standards" |
| inference.sh | https://inference.sh/blog/skills/agent-skills-overview | Open standard practitioner overview |
| agensi.io | https://www.agensi.io/learn/agent-skills-open-standard) | 2026 explainer on the open standard |
| SkillsMP | https://skillsmp.com | 425,000+ skills discovery platform |
| LobeHub Skills | https://lobehub.com/skills | 169,739 skills marketplace |
| SkillsLLM | https://skillsllm.com | AI skills marketplace |
| Claude Marketplaces | https://claudemarketplaces.com/ | 2,400+ skills, 2,500+ marketplaces |
| Claude Marketplaces — MCP | https://claudemarketplaces.com/mcp | MCP server directory |
| MCP Market | https://mcpmarket.com/ | 318 MCPs for Claude |
| MCP Market (Claude) | https://mcpmarket.com/businesses/claude | Claude-specific MCP catalog |
| MCP.so | https://mcp.so/ | 20,043 MCP servers indexed |
| claudefa.st — Best MCP Servers | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers guide |
| claudefa.st — MCP Tool Search | https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search | 95% context reduction via lazy loading |
| atcyrus.com | https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide | MCP context pollution guide |
| Medium — JP Caparas | https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc | Lazy loading explainer (Jan 2026) |
| toolradar.com | https://toolradar.com/blog/claude-desktop-mcp-server-setup | MCP server setup guide for 2026 |
| GitHub — lazy-mcp | https://github.com/voicetreelab/lazy-mcp | Community MCP proxy with lazy loading |
| anthropics/claude-code#7336 | https://github.com/anthropics/claude-code/issues/7336 | Feature request: lazy loading (95% reduction) |
| anthropics/claude-code#11364 | https://github.com/anthropics/claude-code/issues/11364 | Lazy-load MCP tool definitions |
| anthropics/claude-code#23508 | https://github.com/anthropics/claude-code/issues/23508 | Lazy MCP tool group loading |
| anthropics/claude-code#23787 | https://github.com/anthropics/claude-code/issues/23787 | Lazy-load MCP tool schemas |
| openai/codex#9266 | https://github.com/openai/codex/issues/9266 | Same need tracked for Codex |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| quemsah/awesome-claude-plugins | https://github.com/quemsah/awesome-claude-plugins | Adoption metrics via n8n |
| Composio — Top 10 plugins | https://composio.dev/content/top-claude-code-plugins | Top 10 Claude Code plugins |
| popularaitools.ai | https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026 | Skills, plugins, CLIs roundup |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills/plugins/CLIs |
| self.md | https://self.md/guides/best-claude-code-plugins/ | Best plugins guide; 2-3 max recommendation |
| aitmpl.com — Plugins | https://www.aitmpl.com/plugins/ | Plugin/marketplace discovery |
| aitmpl.com — claude-code-plugins-plus | https://www.aitmpl.com/plugins/claude-code-plugins-plus-skills/ | CCPI marketplace detail |
| brightcoding.dev | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | 270+ AI Agent Tools overview |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces |
| SkillsMP (agent) | https://skillsmp.com | Agent-facing skills discovery |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide: skills, plugins, marketplace |
| hermesagents.net | https://hermesagents.net/blog/skills-and-agentskills-io/ | Ecosystem built in 4 weeks |
| StartupHub — Cursor | https://www.startuphub.ai/ai-news/technology/2026/cursor-adds-30-new-marketplace-plugins | Cursor adds 30+ new plugins |
| Medium — Mark Chen | https://medium.com/@markchen69/claude-code-has-a-skills-marketplace-now-a-beginner-friendly-walkthrough-8adeb67cdc89 | Beginner-friendly marketplace walkthrough |
| paperclipped.de | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | "The New Plugin Ecosystem" analysis |
| Medium — Jonathan Fulton | https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d | "Agent Skills: The Cheat Codes for Claude Code" (Apr 2026) |
| Medium — unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills (Mar 2026) |
| Medium — Bibek Poudel | https://bibek-poudel.medium.com/the-skill-md-pattern-how-to-write-ai-agent-skills-that-actually-work-72a3169dd7ee | How to write SKILL.md files (Feb 2026) |
| AgentPatch — Daily News | https://agentpatch.ai/blog/daily-digest-claude-code/ | Daily news digest skill pattern |
| AgentPatch — Google Maps | https://agentpatch.ai/blog/google-maps-claude-code/ | Google Maps MCP integration |
| AgentPatch — Email | https://agentpatch.ai/blog/send-emails-claude-code/ | Email MCP integration |
| AgentPatch — Terminal | https://agentpatch.ai/blog/claude-code-terminal-guide/ | Claude Code as AI terminal |
| AgentPatch — Product Hunt | https://agentpatch.ai/blog/producthunt-search-claude-code/ | Product validation research skill |
| mcp.harishgarg.com | https://mcp.harishgarg.com/use/mcp-market/mcp-server/with/claude-ai | MCP Market + Claude.ai setup guide |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ — │ — (HTTP 402 errors)
├─ 🔵 X: 21 posts │ 12 likes │ 3 reposts
├─ 🔴 YouTube: 0 videos │ — (HTTP 402 / ScrapeCreators)
├─ 🟢 HN: 0 stories │ — │ —
├─ 🟣 TikTok: 0 videos │ —
├─ 🩷 Instagram: 0 reels │ —
├─ 🦋 Bluesky: 0 posts │ —
├─ 📊 Polymarket: 5 markets │ $3.1M+ volume
├─ 🌐 Web (skill): 4 pages
├─ 🌐 Web (search): 50+ pages
└─ 🗣️ Top voices: @RodmanAi, @madonomori, @saeroyi_ican, @aigoldrushh │ agentpatch.ai, claudemarketplaces.com, agentskills.io
```

---

## Data Gaps

- **Reddit**: HTTP 402 (Payment Required) — complete blackout, a significant gap since r/ClaudeAI and r/LocalLLaMA regularly discuss MCP/skills
- **YouTube**: HTTP 402 from ScrapeCreators — no video content captured; likely many tutorial videos exist
- **Hacker News**: 0 results — possible the topic hasn't had a major HN thread in the last 30 days, or the query was too broad
- **GitHub**: No GITHUB_TOKEN — skipped entirely; this is a major gap for tracking repo activity on skills/plugin repos
- **TikTok, Instagram, Bluesky**: 0 results — low coverage; these platforms likely have some Claude Code content but weren't captured
- **X signal quality**: 21 posts with low engagement (12 total likes across all posts) — the skill's X query was quite broad; a targeted search with `--x-handle` for @AnthropicAI or specific skill creators would yield richer data
- **Estimated coverage**: ~40% of actual discourse (Reddit and YouTube failures are significant losses); web search supplementary content covers the gap partially
- **Web search freshness**: Web search supplementary results mix content from Dec 2025 through Apr 2026 — some skill counts/statistics may be slightly stale

---

## Key Quotes

> "Best GitHub repos for Claude Code that will 10x your next project in 2026: 1. Claude Mem — Persistent memory across sessions… 2. UI UX Pro Max — 50+ styles, 161 color palettes… 3. n8n-MCP — Connect Claude to n8n workflows" — @RodmanAi on X ([link](https://x.com/RodmanAi/status/2044336012298699213))

> "Claude Code is now WILD 🤯 Give it any live website — it rebuilds the UI in seconds. Not a screenshot. Real code. Layout, components, styles all copied. Any site becomes your starting point." — @aigoldrushh on X ([link](https://x.com/aigoldrushh/status/2044335936339911157))

> "Claude codeの出力精度をたった1行で爆上げする方法… 「Codexが完了したあなたの出力をレビューします。」" (One line in CLAUDE.md to massively boost Claude Code output quality: 'Codex will review your output.') — @saeroyi_ican on X ([link](https://x.com/saeroyi_ican/status/2044336419393700286))

> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)

> "~77K tokens consumed before any work begins with 50+ MCP tools → reduced to ~8.7K tokens via MCP Tool Search — a 95% context reduction." — [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

> "SkillsMP has 425,000+ skills built around the open SKILL.md standard — working like a large search-and-discovery layer that aggregates skills from GitHub." — [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)

> "Anthropic's official frontend-design skill now has 277,000+ installs — gives Claude a design system and philosophy before it touches any code." — [AgentPatch](https://agentpatch.ai/blog/claude-code-tools-guide/)

> "The best Claude Code users run 2–3 plugins max. Installing too many MCP servers bloats Claude's tool catalog and increases token costs." — [self.md](https://self.md/guides/best-claude-code-plugins/)

> "Agent Skills: Anthropic's Next Bid to Define AI Standards" — [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

> "Anthropic、デスクトップ版「Claude Code」を刷新 ～複数エージェントを前提としたUIに" (Anthropic revamps Claude Code desktop with multi-agent-first UI, filterable session lists, side panel tools, split-screen) — @madonomori on X ([link](https://x.com/madonomori/status/2044335946796253555))
