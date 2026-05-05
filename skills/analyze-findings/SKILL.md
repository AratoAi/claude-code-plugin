---
description: Analyze findings from a simulation report
---

# Analyze Findings

Pull and analyze findings from a completed simulation run or report.

## Workflow

1. **Identify the report.** Ask for the workspace and report ID. If unknown, call `list_reports` to show recent reports. Alternatively, ask for a run ID and call `get_run_status` to find the associated report.

2. **Fetch findings.** Call `list_findings` with the run ID to get all findings. Call `get_report` to get the full report with summary data.

3. **Analyze and present.** Provide:
   - **Executive summary** — overall quality score and key takeaways
   - **Critical issues** — findings with critical or high severity that need immediate attention
   - **Patterns** — common themes across findings (e.g., repeated categories, affected areas)
   - **Remediation priorities** — ordered list of what to fix first, based on severity and frequency
   - **Risk assessment** — overall quality and risk posture

4. **Deep dive.** If the user wants details on specific findings, use `list_run_assets` to find screenshots, transcripts, or conversation logs that provide context.

## Tips

- Group findings by category first (accuracy, security, compliance, UX), then by severity within each category.
- Highlight any finding that appears across multiple conversations — patterns indicate systematic issues.
- If the report shows a low quality score, focus the user on the top 3 highest-impact issues rather than overwhelming them with the full list.
