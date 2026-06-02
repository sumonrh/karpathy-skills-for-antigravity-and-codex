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

---

**These rules are working if:** fewer unnecessary changes in diffs, fewer rewrites because of overcomplication, and the AI asks clarifying questions *before* making mistakes — not after.
