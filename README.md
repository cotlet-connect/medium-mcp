# How to connect Medium to Claude Code, ChatGPT and any AI agent

**Yes, Claude, ChatGPT and other AI agents can work in your Medium account.** Medium no longer gives API access to new integrations. Cotlet.dev connects your own Medium account to any AI agent, so the AI can draft, format and publish your stories and read your stats.

## What you can ask

> Turn this Google Doc into a Medium draft with headings and the cover image.

> Which of my stories got the most reads this month?

> Submit my latest draft to the publication I write for.

> Add these 5 tags to my last three stories.

> Reply to new responses on my most read story. Show me the drafts first.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install medium-cotlet-mcp        # or run it once: uvx medium-cotlet-mcp connect
medium-cotlet-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 medium_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 medium_agent.py status    # is Medium ready in your Cotlet.dev account
python3 medium_agent.py guide     # Medium screens and sign-in link
python3 medium_agent.py read      # open Medium, read the page, close the browser
python3 medium_agent.py tools     # list Cotlet.dev tools
```

## Questions from Medium users

**Does Medium have an API?**

Medium has an old REST API, but it no longer supports new integrations. Cotlet.dev works in your own Medium account, so your AI agent can publish without it.

**How do I connect Medium to ChatGPT?**

Add Cotlet.dev as an app in ChatGPT (Settings → Apps, connector URL `https://cotlet.dev/mcp/v1`), sign in to Medium once in your Cotlet.dev Cloud Browser, and ask ChatGPT in plain words. No code and no Medium API key.

**Is there a way to use Claude with Medium?**

Yes. In Claude Code run the one-line `claude mcp add` command above; in the Claude app add `https://cotlet.dev/mcp/v1` as a custom connector. Claude then works in your own Medium account.

**Is there a Medium MCP server?**

Medium has no official MCP server. Cotlet.dev is a hosted MCP server that works in Medium for you, 24/7, with Claude, ChatGPT, Cursor, Codex, n8n, Make and Zapier.

## Also works with

- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/medium-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=medium

Start free: https://cotlet.dev/signup?app=medium&utm_source=github&utm_medium=readme&utm_campaign=medium
