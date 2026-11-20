# Writesonic Plugin

> Track Brand Visibility in AI. Access AI search visibility (AEO/GEO) analytics across ChatGPT, Claude, Perplexity, Google AI Overviews, Gemini, and more. Track visibility score, citation share, share of voice, competitor performance, and brand sentiment using data from 500M+ real AI conversations across 50+ markets.

Claude connects multiple Writesonic reports in a single conversation - identifying gaps, surfacing trends, and pinpointing where to focus your GEO strategy.

The same plugin connects your **Writesonic Agents** workspace: triage tasks, follow what agents did, inspect playbook runs, read grids, search your Knowledge Base and Brand Kit, and pull Pages reports.

Works with **Claude Code**. The MCP servers also connect to **Claude.ai**, **Claude Desktop** and **ChatGPT**.

---

## Installation

Claude Code:

```
# Add the Writesonic marketplace (one-time)
/plugin marketplace add Writesonic/mcp-plugins

# Install this plugin
/plugin install writesonic@writesonic
```

Then `/mcp` → select `geo` → sign in with your Writesonic account in the browser. If you use Writesonic Agents, do the same for `agents`.

---

## What's Included

### GEO

| Skill | What it does |
| ----- | ------------ |
| **weekly-geo-digest** | Weekly digest — visibility change vs last week, sentiment shift, biggest-moving prompts, top three recommended actions |
| **monthly-performance-report** | Monthly summary of visibility, citation and sentiment trends |
| **quarterly-visibility-report** | One-page quarterly summary — overall score and trend, top three topic gainers and losers with a one-line reason each |
| **visibility-drop** | Diagnose a drop — topics and platforms that declined, lost citations, sentiment turn, exact prompts responsible, a fix per cause |
| **competitor-teardown** | Where one competitor is cited and you aren't, topics and platforms where they lead, and a plan to overtake them |
| **content-gap-brief** | Top content gaps by estimated impact, briefed; optional prompt tracking and citation monitoring once published |
| **page-optimization** | Prioritized, rationale-backed changes to make a page easier for AI to cite, plus verification |
| **action-center** | Recommended actions ranked by impact — the three with the biggest lift for the least effort |
| **projects** | `/writesonic:projects [query]` — list projects with type (STANDARD / PITCH) |
| **kpi** | `/writesonic:kpi <project>` — KPI snapshot with deltas vs the previous period |
| **sov** | `/writesonic:sov [platform] [days]` — share of voice vs competitors |
| **topics** | `/writesonic:topics <project>` — visibility by topic, strongest to weakest |
| **markets** | `/writesonic:markets <project>` — visibility by geographic market |

### Writesonic Agents

| Skill | What it does |
| ----- | ------------ |
| **task-triage** | Open task counts grouped by assignee, then the high-priority tasks that aren't done |
| **agent-run-review** | Step-by-step walkthrough of what an agent did on a task |
| **status-snapshot** | One-shot status — open tasks, recent playbook runs, failing integrations — chained in a single `execute_batch` call |
| **whoami** | `/writesonic:whoami [project]` — identity and accessible projects |
| **tasks** | `/writesonic:tasks [filter]` — list tasks by priority, status, assignee or keyword |
| **new-task** | `/writesonic:new-task <title>` — create a task (confirms first) and assign it to you |
| **brand-voice** | `/writesonic:brand-voice <question>` — answer from the Brand Kit / Knowledge Base |

---

## Requirements

- **MCP-compatible client** – Claude Code, Claude.ai, Claude Desktop or ChatGPT
- **Writesonic account** – with an active paid plan and at least one project with tracked prompts
- **Writesonic Agents access** (for the Agents skills) – currently limited to selected enterprise and agency accounts in beta

---

## Usage

**Just ask naturally** – skills auto-trigger based on your request:

```
"Build this week's GEO digest"                                  → weekly-geo-digest activates
"Monthly performance summary for my brand"                      → monthly-performance-report activates
"Write a one-page visibility summary for this quarter"          → quarterly-visibility-report activates
"Our visibility fell this month — what drove it?"               → visibility-drop activates
"Do a complete teardown of [Competitor]"                        → competitor-teardown activates
"Find our top three content gaps by impact"                     → content-gap-brief activates
"For [page URL], what should I change to win more AI citations?" → page-optimization activates
"What should I work on this week?"                              → action-center activates
```

Quick commands run on demand: `/writesonic:kpi`, `/writesonic:sov ChatGPT 30`, `/writesonic:topics`, `/writesonic:markets`, `/writesonic:projects`.

### Example Workflows

#### Weekly GEO Digest

1. Ask: "Build a weekly GEO digest"
2. Skill pulls week-over-week KPIs, the sentiment trend, and the answers that appeared or disappeared this week
3. Skill ranks the Action Center recommendations by impact
4. You get a four-section digest with numbers and periods — ready to paste into Slack or Notion

#### Diagnose a Visibility Drop

1. Ask: "Our overall visibility fell noticeably this month. What caused it?"
2. Skill splits the change by topic and by platform, then checks citations and sentiment over the same window
3. Skill finds the exact prompts whose answers changed and checks for configuration changes that mimic a drop
4. You get cause → evidence → recommended fix, one block per cause

#### Competitor Teardown

1. Ask: "Do a complete teardown of Acme"
2. Skill finds every prompt where Acme is cited and you aren't
3. Skill compares topic-by-topic and platform-by-platform share of voice, and pulls third-party pages citing them but not you
4. You get a prioritized plan — biggest gap first, one concrete action per gap

#### Content Gap to Published Brief

1. Ask: "Find our top three content gaps by impact"
2. Skill lists questions AI answers where you have no page, ranked by estimated visibility lift
3. Skill drafts a one-paragraph brief per gap and, only on your confirmation, starts tracking the underlying prompts
4. You get briefs plus the exact tool to watch each page's first AI citations after publishing

#### Quarterly Visibility Report

1. Ask: "Write a one-page visibility summary for this quarter"
2. Skill pulls headline KPIs with quarter-over-quarter deltas and the weekly trend line
3. Skill compares every topic against the prior quarter to find the three biggest gainers and losers
4. You get a one-page summary with a one-line reason per topic — ready for a deck

---

## Writesonic Agents Usage

```
"How many open tasks do I have, grouped by assignee?"           → task-triage activates
"What did the agent do on task ABC-123? Walk me through it"      → agent-run-review activates
"Give me a status snapshot of the workspace"                     → status-snapshot activates
```

Quick commands run on demand: `/writesonic:whoami`, `/writesonic:tasks high priority open`, `/writesonic:new-task Refresh the pricing page for AI search`, `/writesonic:brand-voice what does our guide say about tone`.

Only `create_task`, `update_task` and `comment_on_task` change anything — everything else is read-only, and writes are shown to you and confirmed before they happen.

### Agents Example Workflows

#### Task Triage

1. Ask: "How many open tasks do I have, grouped by assignee?"
2. Skill resolves your project, then counts open tasks per person
3. Skill lists the high-priority tasks that aren't done
4. You get a workload table and the list that needs attention

#### Follow an Agent's Work

1. Ask: "What did the agent do on task ABC-123?"
2. Skill fetches the runs for that task
3. Skill walks the latest run's steps in order
4. You get what was asked, each step, the outcome, and anything that failed

#### Status Snapshot

1. Ask: "Give me a status snapshot: open tasks, recent playbook runs, failing integrations"
2. Skill chains the three reads in one batched call instead of round-tripping
3. Skill flags disconnected or failing integrations
4. You get a three-section status you can paste into a standup

---

## MCP Configuration

The plugin connects to two hosted MCP servers — no local server or API keys:

- `geo`: `https://mcp.writesonic.com/mcp`
- `agents`: `https://mcp.agents.writesonic.com/mcp`

- **Claude.ai / Claude Desktop**: Settings → Connectors → Add custom connector → paste the URL → sign in
- **Claude Code without the plugin**: `claude mcp add writesonic --transport streamable-http https://mcp.writesonic.com/mcp` (and `claude mcp add writesonic-agents --transport streamable-http https://mcp.agents.writesonic.com/mcp`)
- **ChatGPT**: enable Developer Mode and add the URL as a connector

Agents docs: [MCP server](https://apidocs.writesonic.com/agents-mcp/mcp-server) · [Setup](https://apidocs.writesonic.com/agents-mcp/setup) · [Use cases](https://apidocs.writesonic.com/agents-mcp/examples) · [Tools reference](https://apidocs.writesonic.com/agents-mcp/tools-reference)


GEO docs: [MCP server](https://apidocs.writesonic.com/mcp/mcp-server) · [Setup](https://apidocs.writesonic.com/mcp/setup) · [Use cases](https://apidocs.writesonic.com/mcp/examples) · [Tools reference](https://apidocs.writesonic.com/mcp/tools-reference)
Privacy: https://writesonic.com/privacy-policy · Terms: https://writesonic.com/terms · Support: support@writesonic.com
