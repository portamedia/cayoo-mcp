# Cayoo MCP server

Connect your AI assistant to Cayoo — search procedures, collections, news and controlled documents, see your open tasks, and prepare drafts, all with **your own Cayoo permissions**.

> **Status: in development — not available yet.**
> The server address below is planned and does not answer yet. Watch this repository to hear when the first, read-only version goes live.

## What it is

Cayoo runs one hosted [Model Context Protocol](https://modelcontextprotocol.io) server. You do not install or host anything: you add one URL to your assistant and sign in with your normal Cayoo account.

```
https://mcp.cayoo.online/mcp
```

- **Your rights, not more.** The assistant acts as you. It sees what you can see in Cayoo and nothing else.
- **Your institute decides.** An institute administrator switches the connection on, chooses between read-only and draft access, and can disconnect any assistant.
- **People stay in charge.** Approving, publishing, confirming that you have read something, and deleting are never available to an assistant.
- **Everything is logged.** Each action an assistant takes appears in your institute's activity log.

## Connect

You need a Cayoo account in an institute that has enabled the MCP connection.

**Assistants with remote connector support** (Claude, ChatGPT, Copilot and others): add a custom connector / remote MCP server, paste the URL above, and sign in to Cayoo when asked.

**Claude Code**

```bash
claude mcp add --transport http cayoo https://mcp.cayoo.online/mcp
```

**Clients that can only start local servers**: use the generic [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) bridge.

```json
{
  "mcpServers": {
    "cayoo": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.cayoo.online/mcp"]
    }
  }
}
```

## What an assistant can do

The tools you get depend on your Cayoo role. Full list: [docs/tools.md](docs/tools.md).

| Area | Examples | Access |
|---|---|---|
| Knowledge & search | search content, ask Cayoo AI, read a procedure or news item | read |
| My work | open read confirmations, my trainings, notifications | read |
| Files & controlled documents | browse and read; upload and PDF import for editors | read, drafts |
| Authoring | create a procedure or news draft, edit blocks, comment | drafts |
| Approval queue | see what is waiting, compare versions | read |
| Equipment & training, statistics, organisation, surveys | planned for a later version | — |

## Security and privacy

See [docs/security.md](docs/security.md) for the permission model and what leaves Cayoo.

Content your assistant retrieves is sent to the provider of that assistant. Check with your institute before connecting an assistant to clinical or confidential content.

## Questions and feedback

Open an [issue](https://github.com/portamedia/cayoo-mcp/issues). Please do not post confidential content or credentials. For security reports see [SECURITY.md](SECURITY.md).

## Licence

The documentation and examples in this repository are released under the [MIT licence](LICENSE). The hosted Cayoo MCP server itself is a Cayoo service and is not part of this repository.
