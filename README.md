# Callbox plugin

[Callbox](https://callbox.cc) records your calls in Google Meet, Zoom, Teams or
any browser tab, saves them to your own Google Drive and transcribes them. This
plugin connects your AI assistant to your recordings, transcripts, projects and
notes through Callbox's MCP server.

- MCP server: `https://api.callbox.cc/mcp` (Streamable HTTP, OAuth 2.1 with PKCE)
- Documentation: https://callbox.cc/agents
- Support: support@callbox.cc
- Privacy: https://callbox.cc/privacy · Terms: https://callbox.cc/terms

## What is in this repository

```
.
├── .cursor-plugin/marketplace.json     # the Cursor Marketplace entry (one plugin)
├── plugins/callbox/
│   ├── .cursor-plugin/plugin.json      # name, description, logo
│   ├── mcp.json                        # the MCP server: a URL only (OAuth comes from discovery)
│   ├── assets/logo.svg
│   ├── rules/callbox.mdc               # a rule: the few things to always do
│   └── skills/
│       ├── callbox/                    # what Callbox is, which tool for what, the rules
│       ├── callbox-after-call/         # summary + action items on a transcribed call
│       ├── callbox-inbox-triage/       # file Inbox recordings, propose rules
│       └── callbox-weekly-digest/      # a weekly per-project digest (a routine)
├── server.json                         # the official MCP Registry entry (cc.callbox/callbox)
└── chatgpt/                            # the ChatGPT plugin package
```

Nothing here is secret: the plugin holds a URL, text and a logo. You sign in
on Callbox's own page.

## How to use it

### Grok Bot and Cursor

1. Open **Plugins**, search for "Callbox" and click **Add**.
2. The connect card opens Callbox's consent page. Sign in and choose the
   permissions. Read and organize are on by default; delete, settings and
   webhooks stay off until you allow them.
3. In a chat, `@Callbox` attaches the tools and `/` lists the skills.

### Any other MCP client

Add a remote MCP server with the URL `https://api.callbox.cc/mcp`. The client
finds the OAuth settings by itself (Callbox supports Client ID Metadata
Documents and Dynamic Client Registration).

## What the assistant can and cannot do

It can find calls, read and search transcripts, save summaries and action
items as notes, create projects and routing rules, and move recordings. It
cannot start a recording, delete a recording for good, change your Google
connection or delete your account. Transcripts are treated as data, never as
instructions.

You need a Callbox account (a free plan is available) and a Google account.

## License

MIT, see [LICENSE](LICENSE).
