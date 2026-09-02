# SourceMedium for Cursor and Grok Bot

Use SourceMedium's secure MCP server to analyze the commerce data your organization maintains in SourceMedium. The plugin installs the remote server and gives the agent a data-analysis workflow that preserves SourceMedium's metric definitions and data boundaries.

## What it provides

- SourceMedium MCP tools for warehouse, Shopify, Meta Ads, health, catalog, and documentation data.
- OAuth connection through SourceMedium's existing authorization flow.
- An agent skill that starts with data context, prefers canonical metrics, bounds custom SQL, and reports assumptions.

The server is read-only. It cannot change provider settings, credentials, connections, or warehouse data.

## Install

Install **SourceMedium** from the Cursor Marketplace, then select **Connect SourceMedium** in Cursor or Grok Bot. Complete the SourceMedium sign-in and consent flow. Your organization membership determines the data available to the server.

## Local development

Symlink this repository into Cursor's local plugin directory, then run **Developer: Reload Window**:

```bash
mkdir -p ~/.cursor/plugins/local
ln -s /absolute/path/to/cursor-plugin ~/.cursor/plugins/local/sourcemedium
```

Confirm the plugin appears in **Customize**, its logo renders, the SourceMedium MCP server appears under **Tools & MCP**, and OAuth completes before submitting a release.

## Data-use workflow

For an analysis session, the agent should first inspect the available data with `get_data_context`, use `search_data_catalog` before querying, and prefer `query_metrics` for SourceMedium-defined metrics. It should only use custom SQL after inspecting the relevant tables and columns, and should state the source, date range, freshness, and assumptions in its answer.

## Support

For help, contact [SourceMedium support](mailto:support@sourcemedium.com).
