# Context management

The model has a large window. Treat it as a ceiling, not a budget.
Attention quality falls off long before the limit, and a 27B degrades earlier
than a frontier model.

## Handoff rule

Check the context percentage in `environment_details` at each step.

**At 50% usage, stop and propose `new_task`.** Do not continue to 70%+.

The handoff `<context>` block must contain, and nothing more:

- The single module being worked on (path)
- What is done, as a short bullet list
- What is next, as one sentence
- Any test currently failing, by name only — not its full output
- Paths of files already modified

Do not carry over: file contents, full test output, terminal logs, reasoning
from the previous session, or any part of `docs/PROJECT-PLAN.md`.

## Reading discipline

- Use file mentions to read named files. Do not `search_files` across the repo.
- Never read a file "to understand the project". The rules file is the project.
- If a file is over ~800 lines, read the specific range you need, not the whole
  file.
- Never read `docs/PROJECT-PLAN.md`, `CHANGELOG.md`, or `package-lock.json`.

## When you are stuck

Two failed attempts at the same edit means stop and tell me. Do not try a third
approach. Repeated failed diffs burn context faster than anything else and are
usually a sign the task was scoped wrong.
