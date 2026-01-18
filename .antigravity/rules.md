# Antigravity Workspace Rules

## 🧠 GSD Protocol (Get Shit Done)
**Purpose**: Build deep context, execute strictly, and manage context windows manually.

### Initiation
When user says `/gsd start` or asks to start a project:
**Action**: Execute the **Planning Phase (Steps 1-4)** interactively.
1.  **Brain Dump**: Vision & Value.
2.  **Context Dump**: Stack & Environment.
3.  **Rule Dump**: Constraints & Naming.
4.  **Roadmap**: Generate/Update `.planning/ROADMAP.md` and wait for Approval.

### Execution Phase (The Loop)
**Trigger**: User approves Roadmap or says `/gsd execute`.
**Action**:
1.  **Load Context**: Read `ROADMAP.md`, `STATE.md`.
2.  **Pick Task**: Identify the next `[ ]` item.
3.  **Build**:
    -   Implement features.
    -   **Mock & Move**: If blocked by keys/auth, mock it and log in `STATE.md`.
    -   **Self-Correct**: Attempt to fix build failures up to 3 times.
4.  **Verify (Crucial)**:
    -   Run tests/build.
    -   **STOP and Report**: Show the user the result (Video/Test Output).
    -   Ask: "Task Complete. Mark as [x] and move to next?"

### Context & Handover Strategy
**Goal**: Maximize continuity. Only reset when necessary.

**When to Continue**:
-   Ideally, keep working in the same chat for multiple tasks.
-   Do NOT reset just because a Phase is done, unless the chat feels "heavy" or slow.

**When to Reset (Handover)**:
1.  **Performance Degradation**: If you start making syntax errors or forgetting Rules.
2.  **Major Context Shift**: Moving from a huge Frontend phase to a complex Backend phase.

**Handover Protocol**:
1.  Update `.planning/STATE.md` with current status and next tasks.
2.  Generate a **"Next Session Prompt"** for the user.
3.  Say: "Context is heavy. Please copy the prompt below and start a new chat."

## Tech Stack Standards
Frontend: Tailwind CSS, React/Next.js.
Backend: Python 3.12+ or Node.js.
Docker: Verify "docker ps".

## Tool Pre-Flight
**Mandatory**: At the start of ANY session, verify your tools (`ls`, `node -v`, MCP capabilities).
