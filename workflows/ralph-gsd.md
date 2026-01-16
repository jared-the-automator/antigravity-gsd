---
description: Execute the Ralph-GSD loop using Antigravity's full capabilities
---

# Ralph-GSD Workflow for Antigravity

This workflow adapts the "Get Shit Done" framework to work with Antigravity, leveraging full tool access instead of blind text generation.

## How to Use

Simply say: `/gsd` or `/ralph` in chat, and I'll execute one GSD iteration.

For multiple iterations: `/gsd 5` (runs 5 tasks)

---

## Workflow Steps

### 1. **Load Context**
Read the planning files to understand the project:
- `.planning/PROJECT.md` - Vision and constraints
- `.planning/ROADMAP.md` - Task backlog
- `.planning/STATE.md` - Persistent memory (if exists)

### 2. **Identify Next Task**
Find the first unchecked `[ ]` task in ROADMAP.md

If all tasks are complete, celebrate and stop!

### 3. **Implement the Task**
Using my full toolkit:
- View existing files to understand patterns
- Search the codebase for examples
- Read documentation if needed
- Generate/modify code files
- Create necessary tests

### 4. **Verify**
Run the project's test command (from `.planning/config.env` or `package.json`)

### 5. **Self-Debug** (if tests fail)
- Analyze error output
- View failing test files
- Check related source files
- Make targeted fixes
- Re-run tests
- Repeat up to 3-5 times

### 6. **Commit**
If tests pass:
```bash
git add .
git commit -m "feat: <task description>"
```

### 7. **Update Roadmap**
Mark the task as complete: `[ ]` → `[x]`

### 8. **Update State** (optional)
Add learnings to `.planning/STATE.md` for future iterations

### 9. **Loop**
If more iterations requested, go to step 2

---

## Key Differences from Shell Ralph

| Shell Ralph (agent.js) | Antigravity GSD |
|------------------------|-----------------|
| Blind text generation | Can view files first |
| Guesses at fixes | Can grep/search for examples |
| 5 retry limit | Can debug iteratively until solved |
| No conversation | Can ask you for clarification |
| Text-only context | Can read docs, search web if needed |

---

## Example Invocation

**You say:** `/gsd`

**I do:**
1. Read PROJECT.md, ROADMAP.md
2. See next task: "Implement ChatObserver"
3. View existing chatObserver.js to understand current state
4. Search for similar observer patterns in codebase
5. Generate improved implementation
6. Run `npm test`
7. Tests fail - view the failing test file
8. Fix the issue
9. Re-run tests - pass!
10. Commit with message "feat: Implement ChatObserver for DOM monitoring"
11. Mark task complete in ROADMAP.md
12. Report back to you with summary

---

## Advantages

✅ **Full debugging capability** - I can actually fix issues, not just guess
✅ **Learns from codebase** - Can view existing patterns and examples  
✅ **Interactive** - Can ask you questions if unclear
✅ **No retry limit** - Will keep debugging until it works
✅ **Transparent** - You see exactly what I'm doing

---

## Configuration

The workflow reads configuration from `.planning/config.env`:

```bash
# Example config.env
TEST_CMD="npm test"
LINT_CMD="npm run lint"
BUILD_CMD="npm run build"
```

If not present, falls back to package.json scripts.
