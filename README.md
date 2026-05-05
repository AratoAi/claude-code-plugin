# Arato Simulate — Claude Plugin

Test your AI applications from Claude using [Arato Simulate](https://simulate.arato.ai).

Arato Simulate evaluates AI chat and voice applications by running automated simulations with realistic user personas. This plugin connects Claude to the Arato platform, giving you access to all 25 Arato tools directly from your editor or desktop app.

## Prerequisites

- An [Arato Simulate](https://simulate.arato.ai) account
- [Claude Code](https://code.claude.com) or [Claude Desktop](https://claude.ai/download)

## Installation

### Claude Code

```
/plugin marketplace add AratoAi/claude-code-plugin
/plugin install arato-simulate@arato-plugins
```

This gives you the full experience: MCP tools, skills, and the `@simulation-operator` agent.

### Claude Desktop

Add the Arato MCP server to your Claude Desktop config:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "arato-simulate": {
      "url": "https://simulate.arato.ai/mcp"
    }
  }
}
```

Restart Claude Desktop after saving. All 25 MCP tools will be available. Skills and agents are Claude Code-only.

## Authentication

The plugin uses **OAuth 2.1 with PKCE** — the recommended authentication method. On first use, Claude Code opens a browser window for you to log in to Arato. No API keys or config files needed. Your session is refreshed automatically.

Alternatively, for headless or CI environments, you can pass a bearer token directly. Create an API key under **Settings > API Keys** in the Arato UI, then set it in your Claude Code MCP settings:

```json
{
  "mcpServers": {
    "arato-simulate": {
      "url": "https://simulate.arato.ai/mcp",
      "headers": {
        "Authorization": "Bearer sk_your_api_key_here"
      }
    }
  }
}
```

## Skills

| Skill | Description |
|-------|-------------|
| `/launch-test` | Launch a simulation run — pick test suite, configure parallelism, monitor progress |
| `/setup-app` | Onboard a new app — create application, generate brief, generate personas, first run |
| `/analyze-findings` | Analyze findings from a completed simulation — severity grouping, patterns, remediation |
| `/triage-failures` | Diagnose failed or problematic runs — check status, screenshots, error patterns |
| `/compare-runs` | Compare two runs — identify regressions, improvements, severity changes |

## Agent

| Agent | Description |
|-------|-------------|
| `@simulation-operator` | Expert Arato operator — guides you through the full testing workflow proactively |

## Available MCP Tools

All tools are provided by the Arato MCP server. The plugin connects to the server automatically.

### Applications
| Tool | Description |
|------|-------------|
| `list_applications` | List all applications in a workspace |
| `get_application` | Get details of a specific application |
| `create_application` | Create a new application with a name and URL |

### Briefs
| Tool | Description |
|------|-------------|
| `get_brief` | Get the brief for an application |
| `comment_on_brief` | Add a comment to refine the brief |
| `regenerate_brief` | Regenerate the brief from scratch |

### Virtual Users
| Tool | Description |
|------|-------------|
| `list_virtual_users` | List virtual users for an application |
| `generate_virtual_users` | Generate virtual user personas |

### Test Suites & Skills
| Tool | Description |
|------|-------------|
| `list_test_suites` | List available test suites |
| `get_test_suite_tests` | Get individual tests within a suite |
| `list_skills` | List available testing skills |

### Simulation Runs
| Tool | Description |
|------|-------------|
| `launch_run` | Launch a simulation run |
| `get_run_status` | Check run status |
| `get_run_progress` | Get live per-persona progress |
| `stop_run` | Stop a running simulation |
| `list_runs` | List runs with optional status filter |

### Reports & Findings
| Tool | Description |
|------|-------------|
| `get_report` | Get the full report for a completed run |
| `list_reports` | List simulation reports |
| `list_findings` | List findings from a run |

### Run Assets
| Tool | Description |
|------|-------------|
| `list_run_assets` | List artifacts (screenshots, transcripts, videos, summaries) |

### Interactive Views
| Tool | Description |
|------|-------------|
| `view_run_dashboard` | Interactive dashboard with live status and progress |
| `view_findings` | Interactive findings explorer with filtering |
| `view_report` | Interactive report viewer with summary metrics |

### Workspaces
| Tool | Description |
|------|-------------|
| `list_workspaces` | List available workspaces |

## Documentation

Full documentation is available at [simulate.arato.ai/docs/mcp-integration](https://simulate.arato.ai/docs/mcp-integration).

## License

MIT
