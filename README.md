# Adaptive Recall

Adaptive memory system for AI applications. Patent pending.

[adaptiverecall.com](https://adaptiverecall.com) | [Documentation](https://adaptiverecall.com/docs.php) | [Sign Up Free](https://adaptiverecall.com/auth.php?action=signup)

## What It Does

Adaptive Recall is a hosted memory server that stores, retrieves, and manages long-term memory for AI applications. It connects via MCP or REST API.

- **Multi-strategy retrieval**: four search strategies run in parallel (vector similarity, temporal recency, full-text keyword, knowledge graph traversal) and the system learns which to prioritize for each type of query
- **Cognitive scoring**: results ranked using ACT-R activation modeling from cognitive science, factoring in recency, access frequency, entity connections, and validated confidence
- **Knowledge graph**: entities and relationships extracted automatically from stored memories, used as a retrieval pathway alongside text similarity
- **Memory lifecycle**: memories progress through stages, gain or lose confidence based on corroborating evidence, and fade naturally when unused
- **Self-improving**: ML models train on your usage patterns, every parameter change must pass statistical validation against real query history before being adopted
- **Retrieval quality monitoring**: the system verifies its own retrieval consistency and identifies knowledge gaps

## Connect

Sign up at [adaptiverecall.com](https://adaptiverecall.com/auth.php?action=signup) to get your server URL and API key.

### MCP Configuration

Add to your MCP client config (Claude Code, Codex, Cursor, or any MCP-compatible tool):

```json
{
  "mcpServers": {
    "adaptive-recall": {
      "type": "url",
      "url": "https://YOUR_SERVER_URL/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

For Claude Code, add this to `.mcp.json` in your project or `~/.claude/settings.json` for global access. For Gemini CLI, add to `~/.gemini/settings.json` using `httpUrl` instead of `url`. For Codex, add to your Codex MCP configuration.

### REST API

Every action is also available as an HTTP endpoint at `https://YOUR_SERVER_URL/v1/`. All requests require a Bearer token in the Authorization header.

## Actions

| Action | Description |
|--------|-------------|
| **store** | Save a new memory. Generates embeddings and extracts entities automatically. |
| **recall** | Search memories using multi-strategy retrieval with cognitive scoring. |
| **update** | Modify an existing memory. Re-embeds automatically if content changes. |
| **forget** | Remove a memory by ID or by finding the closest match to a query. |
| **graph** | Explore the knowledge graph, traversing entity relationships by name and depth. |
| **status** | System health, memory counts, confidence distribution, and knowledge gap detection. |
| **snapshot** | Get a formatted overview of stored memories, organized by type. |
| **feedback** | Send feedback directly to the Adaptive Recall developers. |

## Memory Types

When storing memories, assign a type that affects how the memory is managed:

**Learning types** (evolve over time, gain/lose confidence, have lifecycle stages):
- `general_knowledge` - facts, observations, reference information
- `user_knowledge` - information about people and their preferences

**Lookup types** (static reference, no lifecycle):
- `callable_scripts` - tool and script references
- `work_project` - project tracking, tasks, deadlines
- `cross_reference` - pointers to external information and resources
- `learned_procedure` - multi-step workflows and procedures

## Pricing

Free, Starter, Pro, and Business plans available. See [adaptiverecall.com](https://adaptiverecall.com/pricing.php) for details.

## Links

- [Website](https://adaptiverecall.com)
- [Documentation](https://adaptiverecall.com/docs.php)
- [Sign Up](https://adaptiverecall.com/auth.php?action=signup)
