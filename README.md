# Clear Writing

An agent skill for specific, factual prose that readers can understand on the
first reading. It supports Russian and English output; its instructions are
written in English.

The skill removes filler, bureaucratic wording, staged contrasts, and repeated
conclusions. It preserves explanations, uncertainty, numbers, and conditions.
It does not impose a fixed response length or claim to detect AI authorship.

## Example

Before:

> It is important to note that caching represents a significant performance optimization mechanism that enables improved efficiency of repeated computational operations.

After:

> A cache stores a result so the next request can reuse it. A service can fetch an exchange rate once and reuse it for five minutes. This reduces API calls, but the rate can become stale during that interval.

## Install in Codex

Clone the repository and link the skill into Codex's user skill directory:

```sh
git clone https://github.com/kezouke/clear-writing.git "$HOME/clear-writing"
mkdir -p "$HOME/.agents/skills"
ln -s "$HOME/clear-writing/skills/clear-writing" "$HOME/.agents/skills/clear-writing"
```

If `clear-writing` is already installed, inspect the existing directory before
replacing it. Follow the host's discovery rules for other agents that support
[Agent Skills](https://agentskills.io/specification).

Invoke it explicitly:

```text
Use $clear-writing to explain this concept.
Use $clear-writing to edit this draft without changing its claims.
```

The host may select the skill automatically when the request matches its
description. Automatic selection is not guaranteed. The full instructions
load when the skill activates.

For ChatGPT, put the stable writing preferences in Custom Instructions. A local
Codex skill is not automatically installed in ChatGPT on the web. The two
surfaces need their own supported setup.

## What the skill checks

- Does the opening answer the question or state a substantive claim?
- Does each paragraph develop one idea with clear logical connections?
- Are technical terms, mechanisms, and necessary assumptions explained?
- Are numbers, comparisons, negations, and degrees of certainty preserved?
- Can a sentence be removed without losing information?

The no-em-dash rule is a style preference. Exact quotations, code, names, and
identifiers retain their original punctuation.

## How we built it

This skill grew out of a collaborative session with Codex. The request was for
plain, concrete writing with no filler or em dashes, while retaining the depth
of a good mathematical explanation.

We reviewed five existing skill prompts, primary writing guides, and agent
harness documentation. We then separated persistent style preferences from
an editing workflow, added fictional examples, and checked the setup in real
ChatGPT conversations. The first two checks exposed remaining repetition;
they did not establish a reliable improvement rate.

Read [the creation notes](docs/how-we-built-it.md) for the sequence, decisions,
and limits of the checks. The [research notes](skills/clear-writing/references/research.md)
contain the source comparison and harness retrospective.

## Files

| File | Purpose |
| --- | --- |
| [SKILL.md](skills/clear-writing/SKILL.md) | Task-scoped writing and editing instructions |
| [Examples](skills/clear-writing/references/examples.md) | Fictional before/after examples |
| [Research](skills/clear-writing/references/research.md) | Sources, skill comparison, and harness considerations |
| [Creation notes](docs/how-we-built-it.md) | What we did and what the checks demonstrated |
| [Codex metadata](skills/clear-writing/agents/openai.yaml) | Display name, description, and invocation prompt |

## Evidence so far

The skill passed the Skill Creator's structural validator. That checks the
package format, not the quality of its decisions.

Two temporary ChatGPT checks tested personal instructions and tone settings.
They were not an evaluation of this skill in isolation. The final version
received a short positive style example after those checks; it was not then
retested across topics, languages, or long conversations.

No accuracy percentage, token reduction, or claim of universal adherence has
been measured. Improve the instructions from observed failures and check
factual fidelity separately from presentation.
