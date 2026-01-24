# Antigravity: Turn-Based GSD Protocol

A disciplined methodology for autonomous software development in "Turn-Based" AI environments (like Antigravity, Cursor, or Windsurf).

## 🛑 The Problem: "The Loop Trap" & Amnesia

Most "Agentic" workflows try to force a Chat-based AI to behave like a CLI loop (running commands infinitely). In VS Code environments, this fails because:
1.  **Context Rot**: Long sessions degrade reasoning quality.
2.  **Turn Limits**: The system eventually forces a stop.
3.  **The Amnesia Gap**: When starting a new chat, the Agent has no idea what happened in the last one, leading to repetitive work or missed requirements.

## 💡 The Solution: Turn-Based GSD

Instead of pretending to be infinite, we embrace the constraints. We treat development like a **Turn-Based Strategy Game** with strict **Save Points**.

### 1. The "Save Game" Mechanic (`STATE.md`)
We decouple the project state from the Chat Context.
-   **Chat Context**: Ephemeral, prone to rotting.
-   **File System (`.planning/`)**: Permanent, infinite.

After **EVERY** task, the Agent must update `STATE.md`. This means you can crash the chat window, start a new one, and resume instantly with zero context loss.

### 2. The GSD Boot Sequence (Fixing Amnesia)
When starting a new session, you don't just "talk" to the Agent. You **Boot** it.
The `/gsd-boot` command (found in `.agent/workflows`) forces the Agent to internalize the rules, history, and roadmap before writing a single line of code.

---

## 🛠️ Usage

### 1. New Project Setup
1.  Copy the `.antigravity` folder and `workflows` to your workspace.
2.  In a chat, say: `/gsd start`.
3.  The Agent will interview you to build the Roadmap.

### 2. Resuming a Session (The Boot)
If you start a new chat or the context feels "heavy", say:
```
/gsd-boot
```
This forces the Agent to read `rules.md`, `STATE.md`, and `ROADMAP.md` immediately.

---

## 📂 Repository Structure

-   `.antigravity/rules.md`: The "Brains". The rules that govern how the Agent behaves.
-   `.agent/workflows/`: Standard Operating Procedures (SOPs) for the Agent.
-   `.planning/`: Where your project identity and history live.

---

*Designed for the next generation of IDE-integrated Agents (v2.0).*
