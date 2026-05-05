---
description: Set up a new application for AI testing
---

# Setup App

Walk the user through onboarding a new application for simulation testing. This is a sequential, multi-step process.

## Workflow

1. **Create the application.** Ask for the app name and URL. Call `create_application` to create it.

2. **Generate the application brief.** Call `regenerate_brief` to auto-analyze the chat interface. The brief defines what should be tested and why. Wait for generation to complete, then call `get_brief` to show the result. Ask if the user wants to refine it — if so, use `comment_on_brief` with their feedback, then `regenerate_brief` again.

3. **Generate virtual users.** Call `generate_virtual_users` to create AI personas that will test the chat. These personas are based on the brief. Show the generated users with `list_virtual_users`.

4. **Review available skills.** Call `list_skills` to show testing capabilities (security checks, compliance rules, custom validations). Help the user understand which skills are relevant for their application.

5. **Run the first simulation.** Call `list_test_suites` to find the right suite, then `launch_run` to start. Suggest starting with a small run (1–3 parallel conversations) for the first test.

## Tips

- The brief quality drives everything downstream. Encourage the user to review it and provide feedback.
- Virtual user generation depends on the brief, so always generate the brief first.
- If the user already has an application created, skip step 1 and start from step 2.
