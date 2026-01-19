# Antigravity: Turn-Based GSD Protocol

A disciplined methodology for autonomous software development in "Turn-Based" AI environments (like Antigravity, Cursor, or Windsurf).

## 🛑 The Problem: "The Loop Trap"

Most "Agentic" workflows try to force a Chat-based AI to behave like a CLI loop (running commands infinitely). In VS Code environments, this fails because:
1.  **Context Rot**: Long sessions degrade reasoning quality.
2.  **Turn Limits**: The system eventually forces a stop.
3.  **Loss of State**: When the agent eventually crashes or hallucinates, you lose track of "What was it doing exactly?"

## 💡 The Solution: Turn-Based GSD

Instead of pretending to be infinite, we embrace the constraints. We treat development like a **Turn-Based Strategy Game** with strict **Save Points**.

### 1. The "Save Game" Mechanic (`STATE.md`)
We decouple the project state from the Chat Context.
-   **Chat Context**: Ephemeral, prone to rotting.
-   **File System (`.planning/`)**: Permanent, infinite.

After **EVERY** task, the Agent must update `STATE.md`. This means you can crash the chat window, start a new one, and resume instantly with zero context loss.

### 2. The Protocol

#### Phase 0: The Interview (Planning)
Before writing code, the Agent must "Interview" the project.
-   **Brain Dump**: Vision & Value.
-   **Rule Dump**: Constraints & Naming.
-   **Outcome**: A committed `.planning/ROADMAP.md`.

#### Phase 1: The Turn-Based Loop
The Agent enters "Autonomous Mode" but respects the Turn structure:
1.  **Load State**: Read `STATE.md`.
2.  **Execute**: Build *one* task.
3.  **Verify**: Run tests/scripts.
4.  **Save Game**: Update `STATE.md` with the result.
5.  **Status Check**: Output a token/vibe estimate.
6.  **Yield**: "Task Complete. Continue?"

#### Phase 2: The Handover
When the context gets "heavy" (or the user decides to reset):
1.  User says "Reset".
2.  Agent generates a **Handover Prompt** summarizing the exact state.
3.  User pastes prompt into New Chat.
4.  Development resumes instantly.

## 🛠️ Usage

1.  **Install**: Copy the `.antigravity` folder to your workspace.
2.  **Start**: Open a chat and say:
    ```
    Read .antigravity/rules.md
    /gsd start
    ```
3.  **Hand over control**: Let the Agent interview you, then watch it execute the roadmap task-by-task.

## 📂 Repository Structure

-   `.antigravity/rules.md`: The "System Prompt Injection" that enforces the protocol.
-   `workflows/turn-based-gsd.md`: The step-by-step logic for the Agent to follow.

---

*Designed for the next generation of IDE-integrated Agents.*
