# Writesonic Plugins for Claude Code

Official Writesonic plugins for AI coding tools. Turn your AI assistant into a GEO analyst and an operator for your Writesonic Agents workspace — track brand visibility across AI platforms, diagnose drops, prioritize actions, and manage tasks, playbooks, grids and knowledge, directly from your editor.

Works with **Claude Code**. The same MCP servers also connect to **Claude.ai**, **Claude Desktop** and **ChatGPT** as custom connectors (see [MCP Configuration](#mcp-configuration-for-other-clients)).

---

## Installation

### Claude Code

```
/plugin marketplace add Writesonic/mcp-plugins
/plugin install writesonic@writesonic
/plugin install writesonic-agents@writesonic
```

Then run `/mcp`, select the server, and follow the browser prompt to sign in with your Writesonic account. No API keys to paste.

Once listed in the community marketplace, the same plugins install as `writesonic@claude-community` and `writesonic-agents@claude-community`.

---

## Local development

To work on a plugin from a local checkout in Claude Code:

```bash
git clone https://github.com/Writesonic/mcp-plugins
claude --plugin-dir ./mcp-plugins/plugins/writesonic --plugin-dir ./mcp-plugins/plugins/agents
```

Then run `/mcp` from inside Claude Code, select the server, and authenticate. Edit a `SKILL.md` and run `/reload-plugins` to pick up changes. Validate before committing:

```bash
claude plugin validate . --strict
```

---

## What's Inside

| Plugin | Description |
| --- | --- |
| [writesonic](./plugins/writesonic/) | AI search visibility (AEO/GEO): share of voice, citations, sentiment, competitor benchmarking and Action Center recommendations across ChatGPT, Claude, Perplexity, Google AI Overviews, Gemini and more |
| [writesonic-agents](./plugins/agents/) | Writesonic Agents workspace: tasks, playbooks, grids, Knowledge Base, Brand Kit and Pages reports |

---

## Writesonic Plugin

Turns your assistant into a GEO analyst over 87 MCP tools. Skills are organized into three areas plus quick commands.

### Reports & Briefings

| Skill | What it does |
| --- | --- |
| `weekly-geo-digest` | Weekly digest — visibility change vs last week, sentiment shift, biggest-moving prompts, top three actions |
| `monthly-performance-report` | Monthly summary of visibility, citation and sentiment trends |
| `quarterly-visibility-report` | One-page quarterly summary — score, trend, top three topic gainers and losers with a reason each |

### Diagnostics & Competitive

| Skill | What it does |
| --- | --- |
| `visibility-drop` | Pinpoints which topics and platforms drove a decline, whether citations or sentiment moved, the exact prompts responsible, and a fix per cause |
| `competitor-teardown` | Full teardown of one competitor — where they're cited and you aren't, topics and platforms where they lead, and a plan to overtake them |

### Content & Actions

| Skill | What it does |
| --- | --- |
| `content-gap-brief` | Top content gaps by estimated impact, briefed, with optional prompt tracking and citation monitoring once published |
| `page-optimization` | Prioritized, rationale-backed changes to make a page easier for AI to cite, plus how to verify the lift |
| `action-center` | Recommended actions ranked by impact — the three with the biggest lift for the least effort |

### Quick commands

| Command | What it does |
| --- | --- |
| `/writesonic:projects [query]` | List your projects with type (STANDARD / PITCH) |
| `/writesonic:kpi <project>` | KPI snapshot with deltas vs the previous period |
| `/writesonic:sov [platform] [days]` | Share of voice vs competitors, e.g. `/writesonic:sov ChatGPT 30` |
| `/writesonic:topics <project>` | Visibility by topic, strongest to weakest |
| `/writesonic:markets <project>` | Visibility by geographic market |

---

## Writesonic Agents Plugin

Operates your Agents workspace: 20 core tools plus `execute_batch` / `execute_plan` for chaining reads.

### Tasks & Agents

| Skill | What it does |
| --- | --- |
| `task-triage` | Open task counts by assignee, then the high-priority tasks that aren't done |
| `agent-run-review` | Step-by-step walkthrough of what an agent did on a task |
| `status-snapshot` | One-shot status — open tasks, recent playbook runs, failing integrations — via a single batched call |

### Quick commands

| Command | What it does |
| --- | --- |
| `/writesonic-agents:whoami [project]` | Who you're signed in as and which projects you can access |
| `/writesonic-agents:tasks [filter]` | List tasks, e.g. `/writesonic-agents:tasks high priority open` |
| `/writesonic-agents:new-task <title>` | Create a task (confirms first) and assign it to you |
| `/writesonic-agents:brand-voice <question>` | Answer from the Brand Kit / Knowledge Base |

---

## Repository Structure

```text
.claude-plugin/
  marketplace.json            # Marketplace catalog (Claude Code)
plugins/
  writesonic/
    .claude-plugin/
      plugin.json             # Plugin manifest
    .mcp.json                 # MCP server: https://mcp.writesonic.com/mcp
    skills/
      action-center/
      competitor-teardown/
      content-gap-brief/
      kpi/
      markets/
      monthly-performance-report/
      page-optimization/
      projects/
      quarterly-visibility-report/
      sov/
      topics/
      visibility-drop/
      weekly-geo-digest/
  agents/
    .claude-plugin/
      plugin.json             # Plugin manifest
    .mcp.json                 # MCP server: https://mcp.agents.writesonic.com/mcp
    skills/
      agent-run-review/
      brand-voice/
      new-task/
      status-snapshot/
      task-triage/
      tasks/
      whoami/
```

---

## MCP Configuration for other clients

The plugins are thin wrappers around two hosted MCP servers, which any MCP-compatible client can use directly:

| Server | URL | Docs |
| --- | --- | --- |
| Writesonic (GEO) | `https://mcp.writesonic.com/mcp` | [Setup guide](https://apidocs.writesonic.com/mcp/setup) |
| Writesonic Agents | `https://mcp.agents.writesonic.com/mcp` | [Setup guide](https://apidocs.writesonic.com/agents-mcp/setup) |

- **Claude.ai / Claude Desktop** — Settings → Connectors → Add custom connector → paste the URL → sign in.
- **Claude Code without the plugin** — `claude mcp add writesonic --transport streamable-http https://mcp.writesonic.com/mcp`
- **ChatGPT** — enable Developer Mode and add the URL as a connector.

---

## Requirements

- **Claude Code** (or another MCP-compatible client)
- **Writesonic account** with an active paid plan and at least one project with tracked prompts (`writesonic`)
- **Writesonic Agents access** — currently limited to selected enterprise and agency accounts in beta (`writesonic-agents`)

---

## Contributing

1. Fork this repo
2. Create a branch for your change
3. Follow the existing patterns in `plugins/` — one folder per skill with a `SKILL.md`
4. Run `claude plugin validate . --strict`
5. Submit a PR with a clear description

---

## Resources

- [Writesonic MCP docs](https://apidocs.writesonic.com/mcp/mcp-server) · [Use cases](https://apidocs.writesonic.com/mcp/examples) · [Tools reference](https://apidocs.writesonic.com/mcp/tools-reference)
- [Writesonic Agents MCP docs](https://apidocs.writesonic.com/agents-mcp/mcp-server) · [Use cases](https://apidocs.writesonic.com/agents-mcp/examples) · [Tools reference](https://apidocs.writesonic.com/agents-mcp/tools-reference)
- [MCP Protocol](https://modelcontextprotocol.io/)

---

## License

MIT

---

## Support

- **Issues**: [GitHub Issues](https://github.com/Writesonic/mcp-plugins/issues)
- **Email**: support@writesonic.com
- **Writesonic**: [writesonic.com](https://writesonic.com)
