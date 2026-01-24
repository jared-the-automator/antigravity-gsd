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
**Protocol**:
1.  **Load Context**: Read `ROADMAP.md`, `STATE.md`.
2.  **Pick Task**: Identify the next `[ ]` item.
3.  **Skill Check (Optional)**:
    -   **IF AND ONLY IF** the `.agent/skills` directory exists (Attributes: [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)):
        -   Cross-reference the task with available skills.
        -   Read the relevant `SKILL.md` before proceeding.
4.  **Build**:
    -   Implement features.
    -   **Mock & Move**: If blocked by keys/auth, mock it and log in `STATE.md`.
    -   **Self-Correct**: Attempt to fix build failures up to 3 times.
5.  **Verify & Checkpoint**:
    -   Run tests/build.
    -   **Git Sync**: Run `git add .`, `git commit -m "feat: [task]"`, and `git push`.
    -   **Update STATE.md**: Log the completed task and current status immediately.
    -   **Report**: Show result to user.
    -   **Status Footer**: You MUST end your turn with:
        > **Status**: [Current Phase/Task]
        > **Est. Tokens**: [Your best guess, e.g., low/medium/high or ~15k]
        > **Vibe Check**: [Stable/Degrading]
        > **Next Action**: [Next Task]

### Context Management & Handover
**Agent Responsibility**:
-   **Always Be Saving**: Ensure `.planning/STATE.md` is updated after every task.
-   **Handover Protocol**: If the user says "Reset", "Handover", or you reach a major milestone, you MUST generate a **Handover Prompt**.

#### The Handover Prompt Template
When generating a handover, you MUST use this structure:
```markdown
# GSD HANDOVER: [Project Name]

## 🚨 BOOT SEQUENCE (MANDATORY)
1. Read `.antigravity/rules.md` (Internalize the Turn-Based GSD Protocol).
2. Read `.planning/STATE.md` (Current task and blockers).
3. Read `.planning/ROADMAP.md` (The master plan).
4. Verify local tools (`ls`, `git --version`).

## 📊 CURRENT STATE
[Copy/Paste latest from STATE.md]

## 🛠 NEXT ACTION
[Specific task to execute once rules are internalized]
```

**Instruction to User**: "Copy the text below into a New Chat to resume development with full context and the GSD protocol active."

## Tech Stack Standards
Frontend: Tailwind CSS, React/Next.js.
Backend: Python 3.12+ or Node.js.
Docker: Verify "docker ps".

## Tool Pre-Flight
**Mandatory**: At the start of ANY session, verify your tools (`ls`, `node -v`, MCP capabilities).
