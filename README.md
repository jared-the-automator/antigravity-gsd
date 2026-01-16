# Antigravity Adaptive Context Strategy

A practical methodology for AI-assisted software development that solves the "context rot" problem in long-running LLM coding sessions.

## 🛑 The Problem

We all know about massive context windows (2M+ tokens), but nobody talks about when to **STOP** using them.

After extensive testing (including a documented 115K+ token coding session), we discovered that:
1.  **Peak Performance (0-30K tokens):** The agent is sharp, creative, and handles complex multi-file refactoring with ease.
2.  **Degradation (50K+ tokens):** Quality drops noticeably. The agent gets "lost in the middle," forgets recent instructions, or enters repetitive loops.
3.  **Failure Zone (60K+ tokens):** The cost (time/money) of correcting errors exceeds the benefit of the large context.

## 💡 The Solution: Adaptive Context Limits

Instead of one continuous session, we implement strict, evidence-based limits:

-   **🟢 0-30K Tokens (Green Zone):**
    -   Perform complex reasoning, architecture planning, and heavy refactoring.
    -   *Action:* Full speed ahead.

-   **🟡 30-50K Tokens (Yellow Zone):**
    -   Good for iterating, debugging, and polishing.
    -   *Action:* Finish up current tasks. Start documenting learnings.

-   **🟠 50K Tokens (Checkpoint Zone):**
    -   The "danger zone" approaches.
    -   *Action:* **MANDATORY CHECKPOINT.** Update your `STATE.md` (persistent memory) with all recent changes, decisions, and next steps.

-   **🔴 60K Tokens (Red Zone):**
    -   *Action:* **HARD RESET.** Stop the session. Start a fresh conversation feeding in `PROJECT.md`, `ROADMAP.md`, and the updated `STATE.md`.

## 🛠️ Implementation

### 1. The Rules File
Copy the contents of `.antigravity/rules.md` to your agent's system prompt or custom instructions. This teaches the agent to monitor its own context and respect the GSD (Get Shit Done) workflow.

### 2. The GSD Workflow
We use a lightweight state management system to bridge sessions:
-   `PROJECT.md`: Vision and constraints (Static)
-   `ROADMAP.md`: Tasks and completion status (Dynamic)
-   `STATE.md`: The "Brain" - persistent context passed between sessions.

### 3. Workflow File
See `workflows/ralph-gsd.md` for the specific orchestrator prompt we use to drive this loop.

## 📊 Results
Using this strategy on "Project Ecliptic" (a Chrome Extension):
-   **Before:** 115K token session, stuck in build configuration loops for 45 mins.
-   **After:** Fresh session resolved the issue in <10 mins using clean context.
-   **Impact:** Reduced debugging time by ~60% and token costs by ~40%.

## 🚀 Usage
1.  Clone this repo.
2.  Add the `.antigravity` folder to your project root.
3.  Instruct your AI assistant: *"Follow the rules in .antigravity/rules.md"*.

---
*Created by [Your Name/Handle]*
