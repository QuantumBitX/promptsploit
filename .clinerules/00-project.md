# PromptSploit — core rules

Keep this file short. It is re-sent on every request.

## What this repo is

Hard fork of promptfoo (TypeScript, MIT). Being progressively ported to Python
and unified with garak and PyRIT as red-team engines.

Full charter: `docs/PROJECT-PLAN.md`. **Do not read it unless I ask.** It is
written for a human and will flood your context.

## Hard boundaries — never violate

1. **Never modify `LICENSE`.** `Copyright (c) Promptfoo 2025` must survive
   verbatim. Removing it terminates our licence to the code.
2. **Never work outside the scope of the current task.** One module per task.
   If you notice unrelated problems, list them at the end. Do not fix them.
3. **Never port `src/providers/` or `src/app/`.** Both are out of scope
   permanently. They are in `.clineignore` — do not ask me to unignore them.
4. **Never delete or rewrite a test to make it pass.** A failing test is a
   finding. Report it; do not "fix" it.
5. **Never add a default that resolves to a specific vendor's model.** The
   entire point of this fork is that graders are explicitly chosen. If a code
   path needs a default, raise an error instead.

## Working agreement

- Read only what the task names. Do not explore the repo "for context".
- Prefer showing me a diff over describing what you would do.
- If the task is ambiguous, ask **one** question and stop. Do not guess.
- Conventional Commits for all commit messages (`feat:`, `fix:`, `chore:`).

## Stack facts

- Current: TypeScript / Node, Jest tests, `npm test`
- Target: Python 3.11+, pytest, LiteLLM for provider calls
- Both languages coexist during the port. That is expected, not a problem.
