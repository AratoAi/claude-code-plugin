---
description: Diagnose failed or problematic simulation runs
---

# Triage Failures

Help the user diagnose why a simulation run failed or produced unexpected results.

## Workflow

1. **Get run status.** Ask for the workspace and run ID. Call `get_run_status` to check the current state. If the run is still running, call `get_run_progress` for live details.

2. **Diagnose based on status.**

   - **`failed`** — The run encountered an error. Check the run details for error messages. Common causes: application URL unreachable, authentication issues, chat interface not detected.

   - **`stopped`** — Someone manually stopped the run. Confirm whether this was intentional.

   - **`completed` with poor results** — The run finished but findings indicate problems. Call `list_findings` and `get_report` to understand what went wrong. Check if virtual users were unable to interact with the chat (suggests interface detection issues) or if the application returned errors.

3. **Check run progress.** Call `get_run_progress` to see per-persona status. Look for:
   - Personas stuck in a specific state
   - High error rates across all personas (suggests a systemic issue)
   - Individual persona failures (suggests edge cases)

4. **Review assets.** Call `list_run_assets` to check screenshots and conversation transcripts. Screenshots from failed conversations often reveal what the agent saw (e.g., login page instead of chat, error modal, CAPTCHA).

5. **Suggest next steps.** Based on the diagnosis:
   - URL issues → verify the app is accessible and suggest updating the application URL
   - Auth issues → suggest checking auth profiles and credentials
   - Interface detection → suggest regenerating the brief with more specific context
   - Intermittent failures → suggest re-running with the same configuration

## Tips

- Always check `get_run_progress` before declaring a run as failed — it might still be running.
- Screenshots are the single most useful artifact for diagnosing failures. Always check them.
- If multiple personas fail the same way, the issue is likely with the application or configuration, not with individual test cases.
