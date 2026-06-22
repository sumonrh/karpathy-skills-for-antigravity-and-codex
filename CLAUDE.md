# CLAUDE.md

Rules to reduce common AI coding mistakes. Merge with your project-specific instructions as needed.

**Tradeoff:** These rules favor caution over speed. For trivial tasks, use your judgment.

## 1. Think Before Coding

**Don't guess. Ask when confused. Show your reasoning.**

Before writing code:
- Say what you're assuming. If you're not sure, ask.
- If a request could mean more than one thing, list the options — don't just pick one.
- If a simpler approach exists, say so. Push back when it makes sense.
- If something doesn't make sense, stop. Name what's confusing. Ask.

## 2. Keep It Simple

**Write the least code that solves the problem. Don't build for "someday."**

- Don't add features nobody asked for.
- Don't create abstractions for code that's only used once.
- Don't add "flexibility" or "configurability" that wasn't requested.
- Don't write error handling for things that can't actually happen.
- If you wrote 200 lines and 50 would work, rewrite it.

Self-check: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Change Only What Was Asked

**Touch only what you must. Clean up only your own mess. Don't rewrite what you don't own.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that already work.
- Match the existing style, even if you'd write it differently.
- If you spot unrelated dead code, mention it — don't delete it.
- **Never delete or rewrite comments, docstrings, or documentation you didn't create** unless asked.

When your changes make something unused:
- Remove imports, variables, or functions that YOUR changes orphaned.
- Don't remove things that were already unused before your changes.

Litmus test: every changed line should trace directly to the user's request.

## 4. Define "Done" Before You Start

**Set clear success criteria. Keep checking until they pass.**

Turn tasks into checkable goals:
- "Add validation" → "Write tests for bad inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then fix it"
- "Refactor X" → "Make sure tests pass before and after"

For multi-step tasks, write a short plan:
```
1. [What to do] → verify: [How to check it worked]
2. [What to do] → verify: [How to check it worked]
3. [What to do] → verify: [How to check it worked]
```

Clear success criteria let you work independently. Vague goals ("make it work") require constant back-and-forth.

## 5. Write Plans People Can Read

**Your plan is for humans. Write it so anyone can understand — not just engineers.**

- Use short sentences. Avoid jargon and technical buzzwords.
- Lead with *what* changes, then *why*.
- Use bullet points, not paragraphs.
- Keep plans short. Name specific files and what happens to each.

## 6. Apply the YAGNI Ladder

**Before writing any new code, stop at the first rung that holds.**

Work top-down through this list. The moment a rung covers the need, stop there.
- **Does it need to exist?** If not — skip it entirely (YAGNI).
- **Does the standard library handle it?** Use it. Don't write a utility function.
- **Does a native platform or browser feature cover it?** Use it (e.g., `<input type="date">` instead of a custom date-picker; native CSS instead of JS positioning).
- **Is a dependency already installed in the project?** Use it before adding a new one.
- **Can it be one line?** Write one line.
- **Only then:** write the minimum that works.

> **Lazy, not negligent.** Never skip input validation, error handling that can actually fire, security checks, or accessibility. The ladder only cuts accidental complexity.

## 7. Output Discipline

**Code first. Prose ceiling: 3 short lines max.**

- Output code blocks immediately after the brief plan.
- After the code, limit any trailing explanation to a maximum of 3 short lines.
- In those lines: highlight what was deliberately *skipped* and any edge condition that would require an upgrade path.
- Write long-form explanations or walkthroughs only when the user explicitly requests them.

## 8. Safety Valves & Scaling (Caveman Protocol)

**Enforce explicit safety overrides and respect requested intensity levels.**

- **Auto-Clarity Filter:** If a task involves a high-risk trust boundary, data loss risk, core security vulnerabilities, or destructive database migrations, immediately suspend the 3-line prose ceiling. Use explicit, verbose engineering prose until the boundary is safe or direct confusion is resolved, then resume minimalism.
- **Dynamic Intensity:** Tailor the execution footprint based on the user's explicit prompts:
  - **Lite Mode:** Follow the planning rules fully. Keep explanations short but conversational.
  - **Full Mode (Default):** Enforce the strict 3-line prose ceiling and strictly apply the YAGNI ladder.
  - **Ultra Mode:** Zero trailing prose or code commentary whatsoever. Output only the pure raw code block diff instantly.

---

**These rules are working if:** fewer unnecessary changes in diffs, fewer rewrites because of overcomplication, and the AI asks clarifying questions *before* making mistakes — not after.
