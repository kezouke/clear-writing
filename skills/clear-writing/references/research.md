# Clear Writing and the Agent Harness

Reviewed on October 13, 2026. Primary guidance and five skill prompts were
inspected. The third-party skills were not tested in a comparative experiment.
Repository popularity is not evidence of effectiveness.

## Writing principles

| Source | Applicable principle |
| --- | --- |
| [National Archives: Plain Language](https://www.archives.gov/open/plain-writing/10-principles.html) | Main point before detail; familiar words; actions in verbs; one topic per paragraph. Explain unfamiliar terms. |
| [Google: Short Sentences](https://developers.google.com/tech-writing/one/short-sentences) | Remove unnecessary words and separate independent ideas. This is guidance, not a mandatory word limit. |
| [Google: Paragraphs](https://developers.google.com/tech-writing/one/paragraphs) | The opening establishes the topic; following sentences develop it. Repeated short fragments can impair coherence. |
| [Google: Audience](https://developers.google.com/tech-writing/one/audience) | Supply the knowledge the reader lacks for the task. Expertise in one field does not imply familiarity with another. |
| [Gopen and Swan: The Science of Scientific Writing](https://wstomv.win.tue.nl/quotes/science-of-scientific-writing.html) | Link a sentence to familiar information before introducing new information. Keep subjects and verbs close. These English-language recommendations need adaptation to Russian. |
| [Maxim Ilyakhov: Numbers in Context](https://maximilyahov.ru/blog/all/number-in-context/) | A number needs context and a meaningful comparison. Including digits alone does not make prose understandable. |
| [Ilyakhov: Weak Company Copy](https://maximilyahov.ru/blog/all/cliche/) | Replace general evaluations with specific information. Obtain missing information or narrow the claim. |
| [Paul Graham: How to Write Usefully](https://www.paulgraham.com/useful.html) | A precise claim must remain true. Qualifications may define scope and certainty; do not delete them mechanically. |
| [Paul Graham: Writing, Briefly](https://www.paulgraham.com/writing44.html) | Cut unnecessary wording, rewrite awkward passages, check rhythm, and convey useful new information. |
| [Gilbert Strang: MIT OCW Interview](https://ocw.mit.edu/courses/18-065-matrix-methods-in-data-analysis-signal-processing-and-machine-learning-spring-2018/14d608fa21de1a71016c8c2b0f4828f0_t36jZG07MYc.pdf) | His advice to teachers includes avoiding haste and the urge to cover everything. Our application: choose pace and detail for understanding. This is an interpretation, not a Strang-authored prompt. |

## Skill comparison

| Skill | Useful contribution | Limitation for this task |
| --- | --- | --- |
| [obra/writing-clearly-and-concisely](https://github.com/obra/the-elements-of-style/blob/main/skills/writing-clearly-and-concisely/SKILL.md) | Specific language, removing unnecessary words, paragraph organization. | The full reference targets English and uses substantial context. English punctuation rules do not become Russian rules. |
| [blader/humanizer](https://github.com/blader/humanizer/blob/main/SKILL.md) | Removes staged openings, empty contrasts, inflated claims, and formulaic rhythm. Requires claim preservation. | Its default pasted-text output includes a draft, remaining patterns, and final rewrite. That is excessive for ordinary replies. A sample's punctuation can override its dash guidance. |
| [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop/blob/main/SKILL.md) | Directness, specificity, and no em dashes. | Banning every adverb and passive construction, and requiring a human subject in every sentence, overconstrains technical explanations. Its 50-point self-score does not measure reader comprehension. |
| [ilyautov/humanizer-ru](https://github.com/ilyautov/humanizer-ru/blob/main/skills/humanizer-ru/SKILL.md) | Russian editing, factual fidelity, preserving voice, separate audit and edit modes. | A large catalog and scanner measure markers. Their absence does not establish clarity or truth. The author's claims about their own experiments need separate verification. |
| [thevseprod/humanizer-ru](https://github.com/thevseprod/humanizer-ru/blob/main/SKILL.md) | Russian and English guidance, protection against losing substantive claims. | A long combined reference. Its promise to influence all subsequent writing applies only when the harness actually loads the skill. |

Selected setup: persistent personal instructions plus a compact editing
skill. The em-dash prohibition is the user's punctuation preference, not a
test of whether an AI wrote the text.

## Harness retrospective

[Anthropic, September 29, 2025](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents):
behavior depends on the whole context, including tools, history, and examples.
The authors recommend sufficient minimal prompts, adding guidance after
observed failures, and diverse examples instead of exhaustive exception lists.

[Codex Prompting Guide](https://developers.openai.com/cookbook/examples/gpt-5/codex_prompting_guide):
personality and progress messages have their own harness instructions. The
guide distinguishes updates before GPT-5.3-Codex from those starting with it.
Old advice about preambles must be checked against the actual version.

[Anthropic, March 24, 2026](https://www.anthropic.com/engineering/harness-design-long-running-apps):
study traces on realistic tasks and reconsider scaffolding when models change.
The article concerns application development; its outcomes do not establish
the effectiveness of Russian writing rules. Testing in the real product is
our application of this approach.

[OpenAI, September 11, 2026](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra):
revisit AGENTS.md and skills, remove unnecessary reading, and avoid rigid
recipes. The advice concerns Astra; results should not be attributed to other models.
We adopt the general principle of keeping context relevant.

## Persistent controls and their limits

1. [ChatGPT Custom Instructions](https://learn.chatgpt.com/docs/personalize): persistent preferences. Preserve depth and factual rigor while specifying presentation. The observed web editor requires fewer than 5,000 characters. The final English instructions use 4,824 characters, excluding the file's final newline.
2. [Codex AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md): global instructions live in CODEX_HOME and load at run initialization. More local project instructions can override general guidance.
3. [Skills](https://learn.chatgpt.com/docs/build-skills): full instructions load when a skill activates. Installation alone does not ensure continuous application. Put detailed editing guidance here.
4. [Personality and configuration](https://learn.chatgpt.com/docs/config-file/config-reference): pragmatic is available for models advertising supportsPersonality and may be overridden by a chat. It does not replace factual rules.
5. Output verbosity and writing clarity are different controls. A short answer can still contain vague claims or omit necessary reasoning. Check support for the selected model before changing verbosity.
6. model_instructions_file replaces built-in instructions. Replacing the entire instruction set would change more behavior than this style task needs.

The public [Codex default.md](https://github.com/openai/codex/blob/main/codex-rs/protocol/src/prompts/base_instructions/default.md)
contains preamble and tone guidance. It is not proof of the exact prompt used
by this desktop version: model and product context can differ.

## Verification

Evaluate factual fidelity and presentation separately. Search can detect an
em dash; comprehension and causality require inspecting the answer.

Useful checks: a short question, an unfamiliar idea, an explanation with a
formula, editing with numbers, insufficient evidence, a progress update after
tools, and continuation after a long conversation. Repeat after a model or
harness change. This is a verification plan, not a claim that every scenario
has been tested.

One smoke check in a temporary ChatGPT conversation asked why a profitable
company can run out of cash, with one numerical example. The initial answer
started with the mechanism and used no em dashes, but added a repeated
"Key takeaway" closing. The instructions were revised to state where to stop
and name those recap labels. The web personality was set to Efficient, whose
observed description is "Concise and plain." This is a response to a concrete
failure, not a controlled comparison or a guarantee of future adherence.

A second temporary-chat check still used two tables and repeated the
explanation after the example. A short positive style example was therefore
added near the start of the persistent instructions. The final field remains
under 5,000 characters. These small checks reveal failures; they do not
establish a reliable improvement rate.
