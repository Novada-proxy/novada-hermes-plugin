# Novada MCP plugin for Hermes Agent

Connects Hermes Agent to Novada's hosted MCP server at
[`mcp.novada.com`](https://mcp.novada.com/mcp). It lets the agent search the web, extract the
content of public web pages, gather cited research material, and retrieve structured search-result
and platform data, using your own Novada account.

This package is configuration only: `plugin.json` and `mcp.json`. It contains no local code and
runs no local process.

## Example prompts

- "Search the web for the EU AI Act implementation timeline and list the top 5 results with links."
- "Extract the main content of https://www.python.org/about/ and summarize it in three bullet points."
- "Show the top 5 Google search results in the US for \"python web framework\" with position, title and URL."

## Sign in

The server uses OAuth. On first use Hermes opens a browser page on `mcp.novada.com` where you sign
in with your Novada account. You do not put an API key in Hermes configuration. Requests are billed
to the Novada account you connect, under your existing plan.

## Data handling

Every tool call is sent to `mcp.novada.com`. The server receives the queries, URLs and parameters the
agent sends, and the connected account identity, and returns publicly available web content. To
retrieve a public page, the request is sent on to the target website through Novada's network. The
plugin does not read files on your machine and does not sign in to third-party websites on your behalf.

The set of tools is served by the remote server at runtime and is not covered by the pinned commit
of this package. Some tools can spend account balance or change account resources (for example
proxy sub-account and static IP management), so the package marks the server `untrusted`, which
makes Hermes ask before write-capable tools run.

- [Privacy policy](https://www.novada.com/legal/privacy-policy/)
- [Terms of service](https://www.novada.com/legal/terms-of-service/)

## Support

- Product page: <https://www.novada.com/products/novada-mcp/>
- Email: support@novada.com
- [Report an issue](https://github.com/Novada-proxy/novada-hermes-plugin/issues)
