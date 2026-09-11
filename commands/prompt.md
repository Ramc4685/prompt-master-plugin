---
name: prompt
description: Write or fix a prompt for a specific AI tool using the prompt-master skill
argument-hint: [rough idea, or a prompt to fix, and the target tool]
---

Use the `prompt-master` skill to handle this request.

Request: $ARGUMENTS

If the request is empty, ask what the prompt is for and which tool it targets.
Follow the skill's rules exactly: confirm the target tool before writing, extract
the intent dimensions, route to the matching tool section, and deliver a single
copyable prompt block followed by the target line and the one-sentence rationale.
