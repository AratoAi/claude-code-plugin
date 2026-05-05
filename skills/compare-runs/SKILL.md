---
description: Compare two simulation runs for regressions or improvements
---

# Compare Runs

Compare two simulation runs to identify regressions, improvements, or unchanged behavior.

## Workflow

1. **Identify the runs.** Ask for the workspace and two run IDs: a baseline (typically the older run) and a comparison (typically the newer run). If unknown, call `list_runs` to show recent runs.

2. **Fetch both runs.** Call `get_run_status` for both run IDs. Verify both are in `completed` status — comparison is unreliable for incomplete runs.

3. **Fetch findings.** Call `list_findings` for both runs. Call `get_report` for both if reports are available.

4. **Compare and present:**
   - **Status comparison** — success rate, completion status, duration differences
   - **New findings** — issues in the comparison run that weren't in the baseline (potential regressions)
   - **Resolved findings** — issues in the baseline that are gone in the comparison (improvements)
   - **Severity changes** — findings that changed severity between runs
   - **Performance** — differences in conversation count, duration, error rates
   - **Verdict** — overall assessment: regression, improvement, or neutral

5. **Actionable summary.** If regressions are found, highlight the most critical new findings. If improvements are found, confirm what was fixed.

## Tips

- The most meaningful comparisons are between runs of the same test suite against the same application — ideally before and after a code change.
- Focus on new critical/high findings first. Minor findings appearing or disappearing between runs is normal variance.
- If both runs have very different test configurations, note that the comparison may not be apples-to-apples.
