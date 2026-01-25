---
description: initialize the GSD protocol for a new chat session
---
# /gsd-boot: The GSD System Initializer

Follow these steps EXACTLY to ensure the Agent has full context and follows the Turn-Based GSD Protocol.

1. **Internalize Protocol**:
   - READ `.antigravity/rules.md` immediately.
   - Acknowledge that you are in "Turn-Based GSD Mode".

2. **Load Project State**:
   - READ `HANDOVER.md` (if it exists) to capture the immediate context from the previous session.
   - READ `.planning/STATE.md` to identify the current active task and any recent blocks/mocks.
   - READ `.planning/ROADMAP.md` to understand where this task fits in the overall vision.

3. **Verify Capabilities**:
   - Run a `Tool Pre-Flight`: Check for existence of expected CLI tools (npm, git, docker) and MCP servers.
   - **Skills Check**: Check if `.agent/skills` exists. If it does, note available skills. If not, proceed silently (do not error).

4. **Confirm Readiness**:
   - Summarize the "Next Step" you have identified.
   - Wait for user confirmation or enter the GSD Execution Loop if previously approved.
