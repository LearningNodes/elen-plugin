# Elen plugin

## What Elen does

Elen gives your Bots a shared record of decisions. Before a Bot makes a choice it checks what was already decided, and after it decides it records why. Old decisions get replaced in the open, never quietly contradicted. You see who decided what, and why, in one place. Read and add only: it never sends, shares or deletes anything.

## Install

From the Grok Bot or Cursor marketplace, choose Authorize, sign in or create a free Learning Nodes account, pick a workspace. Decisions appear at https://workstation.learningnodes.com/bots.

The Workstation shows a connection under the name the app gives when it connects. Grok Bot's connector gives the name "Cursor", so the sign-in page says "Connect Cursor to Elen" and the connection is listed as Cursor under Connected apps at https://workstation.learningnodes.com/settings/api-keys. You disconnect it there.

## Elen on your computer

The same tools run locally with `npx -y @learningnodes/elen-mcp`. Connect to the same workspace with a key from https://workstation.learningnodes.com/settings/api-keys. See [Elen online](https://github.com/LearningNodes/Elen#elen-online) in the Elen repository README for connected mode.

## Other clients

Configure `https://api.learningnodes.com/mcp` with the header `Authorization: Bearer <key>`:

```json
{
  "mcpServers": {
    "elen": {
      "url": "https://api.learningnodes.com/mcp",
      "headers": {
        "Authorization": "Bearer ${env:LEARNINGNODES_API_KEY}"
      }
    }
  }
}
```

Read the key from an environment variable named `LEARNINGNODES_API_KEY`. The variable syntax differs between clients.


## Tools

Hosted mode exposes six tools:

- `elen_suggest`: Before you make a choice that other bots or people will rely on, find decisions already made. Returns short pointers to active decisions.
- `elen_expand`: Get the full decision behind a pointer: its basis, evidence, links and the history of decisions on the same question.
- `elen_commit`: Record a decision you made: the question, what you chose and why, the facts that bounded it and where they came from. If a similar active decision exists, nothing is written and you get it back to cite, supersede or force.
- `elen_supersede`: Replace an active decision with a new one when its basis no longer holds. The old decision is kept and marked replaced.
- `elen_list`: List decisions, newest first, filtered by bot, domain, date or status.
- `elen_status`: Show which workspace this connection writes to, which bots have recorded decisions, and the totals.

## Allowing calls without approval cards

Suggest allowing `elen_suggest`, `elen_expand`, `elen_list` and `elen_status` automatically, and keeping approvals for `elen_commit` and `elen_supersede` until you trust your bots' logging.

## Data

What is stored: what your bots write, the bot name and the app name, in your Learning Nodes workspace. The connection reads and adds decisions only. Nothing is shared, sent or deleted. Data that arrives through this plugin is not used to train models. See https://www.learningnodes.com/terms and https://www.learningnodes.com/privacy.

## Support

Use the contact options on www.learningnodes.com.

## License

MIT for this repository. Elen itself is open source under AGPL-3.0 in its own repository.
