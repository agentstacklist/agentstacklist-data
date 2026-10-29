<h1 align="center">AgentStackList Data</h1>
<p align="center">An open dataset of 106 SaaS tools rated for AI coding agents, from <a href="https://agentstacklist.com">AgentStackList</a>.</p>
<p align="center">
<img src="https://img.shields.io/badge/license-CC%20BY%204.0-blue" alt="License: CC BY 4.0">
<img src="https://img.shields.io/badge/tools-106-brightgreen" alt="Tools: 106">
<img src="https://img.shields.io/badge/last%20updated-2026--10--30-informational" alt="Last updated: 2026-10-30">
</p>

## What is this?

Every tool on [agentstacklist.com](https://agentstacklist.com) is checked for how well it works with AI coding agents (Claude Code, Codex, Cursor, GitHub Copilot and Antigravity): whether it ships an MCP server, an agent skill or plugin, and how much setup it needs. This repo publishes those ratings as plain JSON and CSV so you can build on them.

## Files

| File | Description |
|---|---|
| `tools.json` | All 106 tools with per-agent scores |
| `tools.csv` | Same data, flat (no per-agent scores) |
| `schema.json` | JSON Schema (draft 2020-12) for `tools.json` |
| `LICENSE` | CC BY 4.0 |

## Quick start

**curl**
```bash
curl -sL https://raw.githubusercontent.com/agentstacklist/agentstacklist-data/main/tools.json | jq '.[] | select(.has_mcp) | .name'
```

**JavaScript**
```js
const res = await fetch("https://raw.githubusercontent.com/agentstacklist/agentstacklist-data/main/tools.json");
const tools = await res.json();
console.log(tools.filter(t => t.fit_score >= 4).map(t => t.name));
```

**Python**
```python
import json, urllib.request
url = "https://raw.githubusercontent.com/agentstacklist/agentstacklist-data/main/tools.json"
tools = json.load(urllib.request.urlopen(url))
print([t["name"] for t in tools if t["category"] == "database"])
```

## Fields

| Field | Type | Description |
|---|---|---|
| `name` | string | Tool name |
| `slug` | string | Unique ID, used in AgentStackList URLs |
| `category` | string | Category, e.g. `database`, `payments` |
| `url` | string | Official website |
| `page` | string | Tool page on agentstacklist.com |
| `fit_score` | integer or null | Overall AI-agent fit score (higher is better) |
| `has_mcp` | boolean or null | Ships an MCP server (null = not verified yet) |
| `has_skill` | boolean or null | Ships an agent skill or plugin (null = not verified yet) |
| `agent_scores` | object | Score per agent (`claude-code`, `codex`, `cursor`, `github-copilot`, `antigravity`); null means not rated yet |
| `description` | string | Short description |

How scores are made: [agentstacklist.com/methodology](https://agentstacklist.com/methodology/).

## Categories

| Category | Tools |
|---|---|
| database | 12 |
| monitoring | 11 |
| payments | 8 |
| testing | 8 |
| hosting | 7 |
| productivity | 6 |
| storage | 6 |
| ci-cd | 5 |
| cms | 5 |
| crm | 5 |
| analytics | 4 |
| auth | 4 |
| email | 4 |
| search | 4 |
| ai-apis | 3 |
| background-jobs | 3 |
| vector-db | 3 |
| ecommerce | 2 |
| feature-flags | 2 |
| forms | 2 |
| maps | 2 |
| **Total** | **106** |

## License

[CC BY 4.0](LICENSE). You can copy, share and adapt this data, including commercially, as long as you credit AgentStackList with a link.

Credit line: *Data from [AgentStackList](https://agentstacklist.com), licensed CC BY 4.0.*

## How to cite

```bibtex
@misc{agentstacklist_data_2026,
  title  = {AgentStackList Data: SaaS tools rated for AI coding agents},
  author = {AgentStackList},
  year   = {2026},
  url    = {https://agentstacklist.com}
}
```

## Contact

Corrections or new tools: [agentstacklist.com/submit](https://agentstacklist.com/submit/) or hello@agentstacklist.com.
