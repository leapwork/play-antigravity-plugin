# Leapwork Play

- For anything about Leapwork test cases, runlists, runs, knowledge bases or agents, use the `play` MCP server. Get the steps for the job with `play_get_skill` and follow them. Do not guess Leapwork APIs or write REST calls to Leapwork yourself.
- Leapwork Play acts with the signed-in user's own permissions. If a call is denied, say so; do not retry in another team.
- When a Leapwork result is unexpected, act on its `message` or tell the user what came back. Do not search the workspace or Leapwork source code to work out why.
- Ask the user before creating anything in Leapwork Play they did not ask for by name, such as a new knowledge base, folder or runlist to hold their work. Offer the existing ones that fit, and a new one.

## Workspace and team

Antigravity cannot show Leapwork Play's workspace and team form: a call that needs them and has none, `team.getMembers` and `team.getCurrent` included, comes back `cancelled` with "The user did not go ahead". This takes precedence over Leapwork Play's own instructions. Before the first call about the user's assets, settle them like this, before any other `play_call_capability` or `play_call_workflow` call (`play_get_skill` is fine):

1. `play_call_capability` with `{ "path": "user.listAccessibleWorkspaces" }`. One workspace: use its `companyId`. Several: call `ask_question` with each `label` as an option, and stop until the user answers.
2. `play_call_capability` with `{ "path": "user.listAccessibleTeams", "companyId": <companyId> }`. One team: use it. Several: call `ask_question` with each `name` as an option, and stop until the user answers. Send its `id` as the number `teamId`.

Never choose a workspace or team yourself when there are several, not even the first one or the one that looks like the user's own. Only the user's answer, or a workspace or team they named in this conversation, settles it.

Send `companyId` and `teamId` at the top level of every later `play_call_capability` call, beside `path` or `steps`, and in `play_call_workflow`'s `context`. Show the user labels and names, never ids. A call that still comes back `cancelled` without them: settle them as above and call again.
