# Connecting Big Head to your IDuh Genius apps (optional, off by default)

This is an optional add-on. The pack works fully without it, and it stays off until you turn it on yourself.

## What it does

The IDuh Genius MCP server (`https://mcp.iduhgenius.com/mcp`) lets Big Head read and add to the Scatterplot inbox of an IDuh Genius account you sign in to. Today that means:

- **Read:** list, search, and open items in your Scatterplot inbox (`scatterplot.read`).
- **Add:** add a note, a link, or a transcript you gave him as text (`scatterplot.capture:write`).

He cannot edit, file, dismiss, or delete anything, and he has no tool to send messages or spend money.

## Before you start

- You need an IDuh Genius account (GeniusID) and a Scatterplot inbox. Without them, leave this off.
- Joshua has to register Big Head as a GeniusID client and add the two grants to it. Until that is done, sign-in is refused. This step is not in the pack.
- Anything Big Head reads from your inbox is your own captured content. He treats it as data, never as instructions.

## Turning it on

1. Ask Joshua for the Big Head client ID for GeniusID. Do not paste any secret into Discord.
2. Add the server to your `config.yaml`, using the block below (it is commented out in the pack).
3. Run `/reload-mcp` in Hermes, then sign in when Hermes asks.
4. Check the consent card: it must list "Read and search your Scatterplot inbox" and, if you want him to add items, "Add notes, links and transcripts". Approve only what you want.

```yaml
# mcp_servers:
#   iduh-genius:
#     url: https://mcp.iduhgenius.com/mcp
#     auth: oauth
#     oauth:
#       client_id: <Big Head's GeniusID client id>
```

Verify these field names against the Hermes MCP reference before you enable it. The block above follows the reference as published at the time of writing; the mirror sites differ.

## Turning it off

Remove the block (or leave it commented out) and run `/reload-mcp`. To revoke the sign-in, open Connected apps on id.iduhgenius.com and disconnect it. That ends every token for this client.

## What Big Head can and cannot do through it

- Can: read and search your inbox, open items, and add notes, links, or transcripts you give him.
- Cannot: edit, file, dismiss, delete, upload files, change tags or placement, or send anything.
- Every added item records that Big Head wrote it.

## Status

Draft for review. Not in the 0.1.0 release. Pack release waits for Joshua's go.
