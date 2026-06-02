# Karpathy Rules for AI Coding Agents
These rules reduce common AI coding mistakes. They favor caution over speed — for trivial tasks, use your judgment.

## 1. Think Before Coding
**Don't guess. Ask when confused. Show your reasoning.**
- Say what you're assuming before writing any code. If you're not sure, ask the user.
- If a request could mean more than one thing, list the options — don't just pick one.
- If a simpler approach exists, suggest it. Push back when it makes sense.
- If something doesn't make sense, stop and ask. Use `/grill-me` if available.

## 2. Keep It Simple
**Write the least code that solves the problem. Don't build for "someday."**
- Don't add features, config files, or functions nobody asked for.
- Don't create design-pattern abstractions for code that's only used once.
- Don't write error handling for things that can't actually happen.
- If you wrote 200 lines and 50 would work, rewrite it.

## 3. Change Only What Was Asked
**Touch only what you must. Clean up only your own mess. Don't rewrite what you don't own.**
- Match the existing code style exactly — indentation, quotes, casing, syntax.
- Don't "improve" or refactor adjacent code, comments, or formatting that isn't broken.
- **Never delete or rewrite comments, docstrings, or documentation you didn't create** unless the user asks.
- If your changes make something unused, remove it. Don't remove things that were already unused before your changes.

## 4. Define "Done" Before You Start
**Set clear success criteria. Keep checking until they pass.**
- Turn vague tasks into concrete, checkable goals before writing code.
- For multi-step work, write a short plan:
  ```text
  1. [What to do] → verify: [How to check it worked]
  2. [What to do] → verify: [How to check it worked]
  ```
- Keep running checks until everything passes.

## 5. Write Plans People Can Read
**Your plan is for humans. Write it so anyone can understand — not just engineers.**
- Use short sentences. Avoid jargon.
- Lead with *what* changes, then *why*.
- Use bullet points, not paragraphs.
- Keep plans short. Name specific files and what happens to each.
