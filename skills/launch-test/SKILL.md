---
description: Launch a simulation test for an application
---

# Launch Test

Guide the user through launching a simulation run for their application.

## Workflow

1. **Identify the workspace.** Ask which workspace to use. Call `list_workspaces` if they're unsure.

2. **Identify the application.** Call `list_applications` to show available apps. Let the user pick one, or accept an application ID directly.

3. **Choose a test suite.** Call `list_test_suites` to show available suites. Help the user pick the right one based on their testing goals. If they want to see what's in a suite, call `get_test_suite_tests` to list individual tests.

4. **Configure the run.** Ask how many parallel conversations to run (1–100, default 5). Ask if they want to run all tests or select specific ones.

5. **Launch.** Call `launch_run` with the chosen test suite, test IDs (if specific), and parallel count.

6. **Monitor.** After launching, call `get_run_progress` to show live status. Offer to check again or wait for completion.

## Tips

- If the application has no virtual users yet, suggest running `/setup-app` first.
- For a quick smoke test, suggest running with 1–3 parallel conversations.
- For comprehensive testing, suggest running the full suite with higher parallelism.
