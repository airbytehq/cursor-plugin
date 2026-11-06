# Airbyte MCP

The Airbyte MCP is a [Model Context Protocol](https://modelcontextprotocol.io/) server that connects Cursor's agent to your Airbyte organization. Your agent works with Airbyte on your behalf, using the same permissions you have in Airbyte.

With the Airbyte MCP, your agent can:

- **Build and manage data pipelines**: deploy sources and destinations, create connections, select streams, and start syncs.
- **Troubleshoot and maintain pipelines**: check sync status, read job logs, check connector configurations, and explain failures.
- **Read data directly from sources and destinations**: when your organization enables the [context layer](https://docs.airbyte.com/platform/context-layer), your agent can read live data from supported sources and query supported destinations without waiting for a sync.
- **Search synced data**: find records by keyword, meaning, or both using context layer search in Airbyte Cloud.
- **Answer questions about Airbyte**: your agent can search Airbyte's documentation, API specifications, and other sources to answer questions about how Airbyte works.

## Prerequisites

- An [Airbyte Cloud](https://cloud.airbyte.com) account.
- [Cursor](https://cursor.com/).
- To read data directly from sources and destinations, an organization admin must [enable the context layer](https://docs.airbyte.com/platform/context-layer/manage-access). You can use the Airbyte MCP to manage pipelines without it.

## Get started

1. Install the Airbyte MCP plugin from the Cursor Marketplace.
2. In **Cursor Settings** > **Tools and MCP**, find **airbyte** and click **Connect**.
3. Your browser opens the Airbyte Cloud sign-in page. Sign in and grant access. If your organization uses single sign-on, select **Sign in with SSO** and enter your company identifier.
4. In the chat panel, ask the agent to work with Airbyte in plain language.

The Airbyte MCP never asks for your password or API keys in the chat. It uses OAuth to sign you in to Airbyte Cloud. If you belong to more than one workspace, it uses your default workspace. Ask the agent to list your workspaces or switch to a different one at any time.

## Example prompts

- "List the connections in my Airbyte workspace and tell me which ones failed in the last day."
- "Why did my last Salesforce sync fail? Read the logs and suggest a fix."
- "Create a connection from my Postgres source to my BigQuery destination that syncs every 6 hours."
- "Show me the 10 most recently updated HubSpot contacts." This requires agent access to be enabled in your organization's context layer.

## Safety

- The agent can only see and change the workspaces, connectors, and connections your Airbyte role allows.
- Tools that permanently delete sources, destinations, connections, and custom connector definitions only work if the resource's name contains `delete-me` or `deleteme`.
- Direct reads and searches are read-only.
- To give the agent read-only access to Airbyte, change the server URL in your Cursor MCP settings to `https://mcp.airbyte.com/mcp?read-only=true`.

## Learn more

- [Airbyte MCP documentation](https://docs.airbyte.com/platform/airbyte-mcp)
- [Install the Airbyte MCP](https://docs.airbyte.com/platform/airbyte-mcp/install)
- [Airbyte MCP tools](https://docs.airbyte.com/platform/airbyte-mcp/tools)
- [Advanced configuration](https://docs.airbyte.com/platform/airbyte-mcp/advanced-configuration)

## Feedback and support

The Airbyte MCP is in active development. To report a problem or request a feature, [open an Airbyte MCP issue](https://github.com/airbytehq/PyAirbyte/issues/new?template=airbyte-mcp-beta.yml) on GitHub. Don't include secrets or credentials in these issues, because they're publicly viewable.

## License

This plugin is licensed under the [MIT License](LICENSE).
