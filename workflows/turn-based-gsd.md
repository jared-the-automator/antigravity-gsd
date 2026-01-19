---
description: Execute the Turn-Based GSD loop with Antigravity
---

# Turn-Based GSD Workflow

This workflow adapts the "Get Shit Done" framework to work with Antigravity's turn-based chat environment.

## How to Use

Simple: Read the `.antigravity/rules.md` file and say `/gsd start`.

---

## Workflow Steps

### 1. **Initiate (Planning Phase)**
We define the project together before a single line of code is written.
- **Brain Dump**: You tell me the vision.
- **Context Dump**: You tell me the stack.
- **Rule Dump**: You tell me the constraints.
- **Output**: I generate `.planning/ROADMAP.md` for your approval.

### 2. **Execute (The Loop)**
Once the Roadmap is approved:
- I enter "Autonomous Mode".
- I load the Roadmap and `STATE.md`.
- I pick the next task -> Build it -> Test it -> Update State.
- I **DO NOT STOP** until the task is verifiable.

### 3. **Verify & Checkpoint**
- I show you the proof (Video/Test results).
- I update `STATE.md` ("Save Game").
- I verify: "Task Done. Continue?"

### 4. **Handover (User-Led)**
- When context gets heavy or a Phase completes:
- You say "Reset".
- I generate a `context-handoff` prompt.
- You paste it into a new chat to resume instantly.

---

## Key Differences from CLI Agents

| CLI Agent (Ralph) | Antigravity (Turn-Based) |
|-------------------|--------------------------|
| Infinite Loop | Turn-Based Execution |
| Blind Generation | Human Verification Step |
| Automated Config | Interactive Planning |
| System Crash | "Save Game" (STATE.md) |

---

## Configuration

The workflow reads configuration from `.planning/config.env`:

```bash
# Example config.env
TEST_CMD="npm test"
LINT_CMD="npm run lint"
BUILD_CMD="npm run build"
```
