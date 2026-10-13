# How We Built Clear Writing

Built on October 13, 2026, in a collaborative session with Codex.

## The request

The user wanted prose that explains its subject directly: concrete facts,
familiar words, no empty opening phrases, and no em dashes. Gilbert Strang was
named as an example of explanation that makes a difficult idea understandable.

The goal included both writing quality and persistent setup in ChatGPT and
Codex. Personal reference material helped identify the preference; those
private documents and account screenshots are not part of this repository.

## Research before rules

The first pass covered two skill prompts and product configuration guidance.
The user challenged its depth and asked for more research, including the
agent harness. That changed the scope of the investigation.

We inspected five skill prompts: Writing Clearly and Concisely, Humanizer,
Stop Slop, and two Russian Humanizer implementations. We also read writing
guidance from Google, the US National Archives, Gopen and Swan, Maxim Ilyakhov,
Paul Graham, and a teaching interview with Strang.

The useful principles were concrete claims, logical flow, meaningful examples,
and preserving qualifications. Some anti-AI-writing rules were too rigid:
banning every adverb or passive construction can damage a correct explanation.
A writer should not invent an actor simply to satisfy an active-voice rule.

The [research notes](../skills/clear-writing/references/research.md) link the
sources and distinguish their advice from our interpretation. Third-party
skill prompts were inspected, not benchmarked against one another.

## The harness changed the design

An installed skill does not necessarily affect every answer. The host first
sees its name and description, then loads its instructions when it selects
the skill. Persistent preferences therefore belong in the host's personal
instructions; detailed editing belongs in a task-scoped skill.

Agent harnesses can also supply their own tone, progress-message, and output
instructions. We reviewed guidance from Anthropic in 2025 and 2026 and OpenAI's
Codex documentation. The practical lesson was to keep the context relevant,
use examples to clarify behavior, and revisit scaffolding when models change.
The articles do not establish that this particular writing skill works.

## Packaging

The runtime entrypoint stayed compact. The package has one SKILL.md, optional
Codex display metadata, fictional examples, and a research reference loaded
only when needed. There are no scripts, network calls, or dependencies.

The workflow checks what a sentence contributes and whether editing changes
its meaning. Removing a phrase is a failure if it also removes a qualification,
changes a number, or turns a hypothesis into an established cause.

The instructions were written in English. A companion set of personal
instructions was compressed below the observed 5,000-character ChatGPT field
limit while retaining requirements for depth and causal explanation. The
account-specific companion text is not published here.

## Two checks in the actual product

Both checks used a temporary ChatGPT conversation with this question:

> Why can a profitable company run out of cash? Give one numerical example.

| Check | Observed behavior | Change prompted by the observation |
| --- | --- | --- |
| First | The answer began with the mechanism and contained no em dashes, but ended with a repeated "Key takeaway". | Added an explicit stopping rule and named recap labels; selected the Efficient tone. |
| Second | The answer still used two tables and repeated the explanation after the example. | Added a short positive style example near the beginning of the persistent instructions. |

These checks tested ChatGPT personal instructions and tone settings. They did
not isolate SKILL.md. The model's randomness, existing personalization, and
simultaneous changes prevent causal attribution to a single rule.

After the final change, we verified that the English instructions were saved
in both products and stayed within the field limit. We also validated the
skill package. We did not run a broad behavioral evaluation after adding the
positive example.

## What remains to be tested

A useful evaluation would cover short answers, unfamiliar concepts, formulas,
editing with numbers, insufficient evidence, tool progress messages, and long
conversations. Test Russian and English separately. Compare factual fidelity,
clarity, and unnecessary repetition before drawing conclusions about quality.

A punctuation scan can establish whether an em dash remains. It cannot
establish whether the reader understands the answer. Treat marker counts and
model self-scores as diagnostic signals, not a quality benchmark.
