# Leapwork Play for Google Antigravity

Create, record, run and debug [Leapwork Play](https://leapwork.ai/) tests from the Antigravity agent, using your own Leapwork Play account.

## Install

```bash
agy plugin install https://github.com/leapwork/play-antigravity-plugin
```

The first time the agent uses Leapwork Play, sign in in the browser window that opens. If a call later returns `Unauthorized`, sign in again under **MCP Servers**.

## Local setup

1. Clone this repository.
2. Point `~/.gemini/config/plugins.json` at the clone:

   ```json
   { "entries": [ { "path": "C:/path/to/play-antigravity-plugin" } ] }
   ```

3. Restart Antigravity and check **Customizations → Installed** for **Leapwork Play**. Later edits are picked up without a restart.

## Try

- "Create a test case for this bug in Leapwork."
- "Go to example.com, search for pencil, and record it as a Leapwork test."
- "Run TC-28 and tell me why it failed."

## Limitations

Antigravity cannot show Leapwork Play's confirmation dialogs yet, so deletes and plan approvals have to be done in Leapwork Play.
