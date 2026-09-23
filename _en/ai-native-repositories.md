---
layout: post
lang: en
permalink: /ai-native-repositories/
translation_key: context-repo
description: "AI coding assistants fail less because of the model than because of the repository. What a context contract at the root of a repo should contain."
title: "On AI-native repositories"
date: 2026-05-20
---

Most engineers I talk to about AI coding assistants describe the same
arc: a few impressive demos, then a long tail of frustration. The model
hallucinates a function that doesn't exist, suggests a deprecated API,
or rewrites a working file with a slightly worse version of itself.

The usual response is to blame the model. I think the model is
usually fine. The repository is the problem.

### The repository as context

A large language model has no access to your team's intuition. It has
no memory of the architecture review last quarter, no idea which
abstraction is load-bearing, no clue that `customfield_12320` means
"Acceptance Criteria" in your Jira instance. Every interaction starts
from a cold cache.

If you want the model to be useful, you have to write that intuition
down. Not as comments scattered through the code, but as a top-level
contract the model can read in a single pass. In my own repositories
this lives in a file called `CLAUDE.md`, conventionally placed at the
root. It is the first thing the model reads, and it is the difference
between a model that helps and a model that ships broken code.

### What goes in there

Three things, in order of importance:

1. **Posture.** Who is the user, what are they trying to accomplish,
   and what voice should the model adopt when answering them. Not
   tone-of-voice fluff: actual guardrails. "Surface risks clearly.
   Propose decisions, not observations. Brief, direct."

2. **Conventions.** The non-obvious things. Where Acceptance Criteria
   actually live. Which fields are writable through which API. Which
   link types are real dependencies and which are anti-patterns. Every
   piece of tribal knowledge a new engineer would learn in their first
   month.

3. **Anti-patterns to refuse.** The mistakes I have seen the model
   make twice. Not as suggestions, as rules. "Never output a Jira link
   as `Blocks <- X` because the direction is ambiguous. Always render
   the full verb from the queried issue's perspective."

That file gets edited every time the model is wrong in a new way. Over
months it accumulates the same texture as a senior engineer's working
memory, except it is shared, versioned, and re-loaded on every prompt.

### The leverage

The leverage is not that the model writes more code. It is that the
model writes code that fits. Pull requests get smaller. Reviews get
faster. The pieces that used to require a fifteen-minute Slack
exchange now happen in the prompt itself.

I would not call this a productivity gain. I would call it a
collaboration upgrade.
