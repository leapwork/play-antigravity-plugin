# Leapwork Play for Google Antigravity

Build, run and fix [Playwright](https://playwright.dev/)-based tests in [Leapwork Play](https://leapwork.ai/) without leaving Antigravity. Your agent can create and record tests, run them and whole runlists, debug failures, build agents, and hand bigger jobs to Play's AI workflows. It works with your own Leapwork Play account.

<!-- TODO: add a screenshot or short GIF: sign-in, then a prompt, then the resulting test -->

## What you can do

| Area | Examples |
| --- | --- |
| **Create** | Create test cases, or generate them from specs you upload to a knowledge base |
| **Record** | Describe a flow in plain English and Play records it as Playwright steps in a cloud browser |
| **Run** | Run a test case or a whole runlist, now or on a schedule, and see the results |
| **Debug and fix** | Find out why a run failed, fix the failing step, and rerun only the failed steps |
| **Build agents** | Create Leapwork agents that run on a schedule, an event or an API call |

## The Leapwork Play MCP server

The plugin connects Antigravity to the Leapwork Play MCP server at `https://mcp.leapwork.ai/mcp`. You sign in with your Leapwork Play account the first time the agent uses it, and every call runs with your own permissions. The server gives the agent these tools:

| Tool | What it does |
| --- | --- |
| `play_get_skill` | Step-by-step instructions for a job, such as creating, running or debugging a test |
| `play_list_capabilities` | Lists everything Leapwork Play can do directly |
| `play_call_capability` | Runs one or more of those capabilities, such as creating a test case or starting a run |
| `play_call_workflow` | Hands a bigger job to Leapwork Play's AI, such as recording steps in a browser or fixing Playwright code |
| `play_get_pending` | Checks on a request that is still running or waiting for an answer |
| `play_respond` | Sends your answer to a question or approval from Leapwork Play |
| `play_cancel_workflow` | Stops a request that is still running |
| `play_get_artifacts` | Gets the screenshots and videos of a test run |

## Requirements

- A [Leapwork Play](https://leapwork.ai/) account. <!-- TODO: add sign-up link and note any free tier/trial -->
- Google Antigravity <!-- TODO: minimum version --> with the `agy` CLI available.


## Try it

- "Create a test case for this bug in Leapwork."
- "Go to example.com, search for pencil, and record it as a Leapwork test."
- "Run TC-28 and tell me why it failed."
- "Run the smoke suite and summarise the failures."
- "Update TC-28 to match the new login page."

---

Playwright is a trademark of Microsoft Corporation. This project is not affiliated with or endorsed by Microsoft.
 