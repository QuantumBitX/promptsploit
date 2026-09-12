# Porting protocol (Phase 3 — toggle OFF until then)

Governs TypeScript → Python ports. The test suite is the specification.

## The rule that makes this safe

**Never translate implementation code directly.** Work only against tests.

For each module, in order:

1. I supply a ported pytest file. **You do not write these** — mistranslated
   tests fail silently and produce a passing implementation of the wrong
   behaviour. Test translation is done outside this harness.
2. You read the pytest file and the original TypeScript implementation.
3. You write Python until the tests pass.
4. You run `pytest <file>` and iterate on real failures only.

If asked to port a module with no test file present, stop and say so.

## Semantic traps — check every time

TypeScript and Python differ in ways that pass type checks and fail at runtime:

- `undefined` vs `null` vs `None` — TS distinguishes two absent values, Python
  has one. State which you mapped to what.
- Truthiness: `0`, `""`, `[]` behave differently. Never assume.
- `async`/`await`: TS resolves microtasks differently from asyncio. Sequential
  awaits in TS may need `asyncio.gather` or may not — check the test.
- Numeric: TS `number` is float64. Python `int` is arbitrary precision.
- Sort stability and default comparators differ.

Call out every one of these you hit in your summary. Do not silently pick one.

## Definition of done

- All tests in the ported file pass
- No test was modified to achieve that
- Semantic decisions listed explicitly
- No new dependency added without asking

## Scope

One module per task. `matchers/` first, then `assertions/`. Do not touch the
config layer until both are green.
