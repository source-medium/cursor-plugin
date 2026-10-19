# SourceMedium for Cursor and Grok Bot

Use SourceMedium's secure MCP server to analyze the commerce data your organization maintains in SourceMedium. The plugin installs the remote server and gives the agent a data-analysis workflow that preserves SourceMedium's metric definitions and data boundaries.

## What it provides

- SourceMedium MCP tools for warehouse, Shopify, Meta Ads, health, catalog, and documentation data.
- OAuth connection through SourceMedium's existing authorization flow.
- An agent skill that starts with data context, prefers canonical metrics, bounds custom SQL, and reports assumptions.

The server is read-only. It cannot change provider settings, credentials, connections, or warehouse data.

## Install

SourceMedium is submitted to the Cursor Marketplace and awaiting Cursor's review, so it is not listed there yet. Until it is, install it from this repository:

- **Team marketplace** (Cursor Teams and Enterprise): in the Cursor dashboard, open **Plugins & MCPs**, choose **Add Marketplace** under **Team Marketplaces**, then **Import from Repo**, and paste `https://github.com/source-medium/cursor-plugin`. Add the plugin and save; your team finds it in **Customize**.
- **Local folder:** clone this repository into Cursor's local plugin directory, as in [Local development](#local-development).

Then connect SourceMedium and complete the SourceMedium sign-in and consent flow. Your organization membership determines the data available to the server.

In Grok Bot, send `Connect SourceMedium MCP at https://mcp.sourcemedium.com/mcp` in a new chat, approve the add, and complete the same sign-in.

## Local development

Clone this repository into Cursor's local plugin directory, then run **Developer: Reload Window**. Cursor skips a symlink there that points to a repository elsewhere on disk, so clone into the folder itself:

```bash
mkdir -p ~/.cursor/plugins/local
git clone https://github.com/source-medium/cursor-plugin ~/.cursor/plugins/local/sourcemedium
```

On Cursor Teams and Enterprise, an admin must turn on **Allow Local Plugin Imports** (Dashboard → Settings → Security & Identity → Marketplace and Plugins). Confirm the plugin appears in **Customize**, its logo renders, the SourceMedium MCP server appears under **Tools & MCP**, and OAuth completes before submitting a release.

## Data-use workflow

For an analysis session, the agent should first inspect the available data with `get_data_context`, use `search_data_catalog` before querying, and prefer `query_metrics` for SourceMedium-defined metrics. It should only use custom SQL after inspecting the relevant tables and columns, and should state the source, date range, freshness, and assumptions in its answer.

## Support

For help, contact [SourceMedium support](mailto:support@sourcemedium.com).
