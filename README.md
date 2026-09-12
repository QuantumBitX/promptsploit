# PromptSploit

**PromptSploit is a hard fork of [promptfoo](https://github.com/promptfoo/promptfoo), originally created by Promptfoo Inc. and licensed under MIT. This project is not affiliated with, endorsed by, or connected to Promptfoo Inc. or OpenAI.**

Enormous credit is due to promptfoo's authors and its open-source contributors. This fork exists because of the quality of their work, not in spite of it.

## Status

**Very early. Nothing here is production-ready.** This is a solo project in its first weeks. If you need a maintained LLM evaluation and red teaming tool today, use [upstream promptfoo](https://github.com/promptfoo/promptfoo) — it is excellent, actively developed, and not going anywhere.

## Why this fork exists

Three reasons, in order of importance.

**1. A unified red team harness.** Practitioners currently run promptfoo, [garak](https://github.com/NVIDIA/garak) and [PyRIT](https://github.com/Azure/PyRIT) separately, with three output formats and three configuration models, then collate results by hand. PromptSploit aims to run them as engines behind one harness with one findings schema.

**2. Grader independence.** promptfoo's default grading path falls through to an OpenAI model. When the system under test is also an OpenAI model, the grader and the subject share a vendor. That is a structural conflict regardless of who owns the project, and it matters for anyone producing red team evidence for an auditor. PromptSploit is working toward explicit grader selection and cross-vendor judge panels.

**3. Python-native.** The AI security ecosystem — garak, PyRIT, Giskard — is Python. promptfoo is TypeScript. Unification is only practical in one language.

OpenAI's acquisition of promptfoo in March 2026 prompted this work but is not the justification for it. OpenAI has publicly committed to maintaining promptfoo as open source, and at the time of writing it is actively maintained.

## Roadmap

**Short term** — grader defaults no longer fall through to a single vendor's model; remote generation opt-in rather than opt-out, so no phone-home by default; vendor branding removed.

**Medium term** — garak and PyRIT integrated as first-class engines; unified SARIF-based findings schema.

**Long term** — progressive port of the evaluation core to Python.

Divergences from upstream are logged in `NEUTRALITY.md` as they land.

## Licence and attribution

PromptSploit is distributed under the MIT Licence, inherited from promptfoo.

Portions derive from promptfoo, Copyright (c) Promptfoo 2025, MIT licensed. The full upstream commit history — and therefore every contributor's authorship — is preserved in this repository's git log.

When garak (Apache 2.0) is integrated, the combined work will move to Apache Licence 2.0, as Apache-2.0 code cannot be relicensed under MIT.

"promptfoo" is a trademark of Promptfoo Inc. and is used here only to identify the upstream project from which this fork derives.
