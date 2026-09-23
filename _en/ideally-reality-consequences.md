---
layout: post
lang: en
permalink: /ideally-reality-consequences/
translation_key: irc
description: "Three mandatory sections in every epic, none of which may contain a solution. Why the wall between problem and solution protects the engineer downstream."
title: "Ideally, Reality, Consequences"
date: 2026-05-29
---

Every epic my team writes has a description with three mandatory
sections, and a small linter rejects it when one is missing. The
sections are always the same, always in the same order: Ideally,
Reality, Consequences. None of the three is allowed to contain a
solution.

That last rule is the whole point. The pattern is not a template for
writing tickets faster. It is a constraint that forces the problem to
exist on the page before anyone is allowed to design against it.

### What each section is for

**Ideally** is the world as it should be. The state we would observe
if the problem did not exist. *"Any server that fails an automated
network check is reallocated without a human touching it."* It is a
description of a destination, written in the present tense, with no
reference to how we get there.

**Reality** is the world as it is today. The gap. *"Today the check
fires, but the reallocation stalls on a manual approval that nobody
owns, so servers sit unassigned for an average of four days."* This
is the section that must be checkable against facts. If Reality is
vague, the problem is not understood yet, and no amount of solution
design will rescue it.

**Consequences** is what the gap costs. The so-what. *"Four days of
idle hardware per incident, a recurring escalation to the on-call,
and a customer-facing delivery SLA we quietly miss twice a month."*
Without this section, every problem looks equally urgent and nothing
can be prioritised. With it, the reader can size the thing before
spending a single day on it.

Three sections, and a solution appears in none of them. The solution
comes later, in a separate field, written by someone who has now read
all three.

### Why the order, and why the wall

The order is not decoration. You cannot write Consequences honestly
until Reality is specific, and you cannot write Reality until you
have committed to an Ideally precise enough to measure the gap
against. Each section is load-bearing for the next. Skip Ideally and
Reality becomes a list of complaints. Skip Reality and Consequences
becomes a fear.

The wall between the problem and the solution is the part people
resist. It feels inefficient. The author usually arrives already
holding an answer, and the three sections feel like ceremony standing
between them and writing it down.

But the wall is exactly what protects the engineer downstream.

### The failure mode it prevents

Hand an engineer a ticket that already contains a solution, and they
will build that solution. This is not laziness. It is the rational
response to a clear instruction. The trouble is that a solution
written as a problem statement has no gap and no cost attached to it,
so the engineer has nothing to check it against. Where the
instruction is silent, their own judgement fills the space, and their
judgement is a different person's subjectivity than the one who wrote
the ticket. The result reads as compliant and is quietly wrong.

I have watched this happen often enough to trust the pattern more
than I trust my own discipline. An engineer who receives Ideally,
Reality, Consequences receives the problem instead of the answer.
They can see the destination, the gap, and the stakes. Now they can
do the thing I actually want from them, which is to design the right
response, or to come back and tell me the problem as stated is not
the real one. A ticket that starts with a solution forecloses both.

### The same discipline, a different artifact

This is the same rule I keep coming back to in every form of
discovery work. In an interview, it shows up as solution-free
questions: you ask about the problem, the pain, the workaround, never
about your idea. In a written readout, it shows up as Facts before
Insights before Recommendations, with the conclusion forbidden from
contaminating the evidence. In a Jira epic, it shows up as Ideally,
Reality, Consequences, with the solution kept out of all three.

Different artifacts, one principle: keep the problem and the solution
in separate compartments, and write the problem first. The compartment
wall is cheap to build and expensive to skip. Every hour spent making
Reality specific is an hour the team does not spend building something
precise and useless.

I write up the full method on the
[Method]({{ '/method/' | relative_url }}) page. The version that sits
above all of it is shorter:

> Spend more time understanding the problem than designing the solution.
