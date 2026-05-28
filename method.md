---
layout: page
title: Method
permalink: /method/
---

A software team has two ways to fail.

The first is technical. The build breaks, the database melts, the API
returns the wrong shape. These failures are visible, painful, and
solvable. Every engineer I have worked with has tools to address them.

The second way is invisible. The team ships exactly what was asked,
exactly on time, and nobody uses it. Or the customer uses it and is
quietly disappointed. Or six months later a new requirement reveals
that the wrong abstraction was baked into the schema. These failures
are not technical. They are framing failures. They were written into
the requirements long before any code was touched.

Most of my career has been spent on the second failure mode. What
follows is what I have learned.

> Spend more time understanding the problem than designing the solution.

This is the only rule. Everything below is a way to live up to it.

## 1. The art of the unbiased interview

Discovery starts with a conversation, and most engineering
conversations are quietly biased toward the answer the interviewer
already has in mind. The bias is rarely deliberate. It is in the
shape of the questions.

A solution-shaped question prompts a solution-shaped answer. *"Would
it help if you had a button that exported the report?"* presupposes
a button, an export, and a report. The stakeholder, eager to be
useful, says yes. You have not learned what they actually do with the
data. You have learned that they will not refuse a button.

The unbiased interview is a discipline:

- **Open questions over closed ones.** *"Walk me through the last time
  you needed this."* not *"Do you need this every week?"*
- **No leading words.** Drop *"obviously"*, *"easy"*, *"just"*,
  *"don't you think"*. Each of them tilts the room.
- **Solution-free phrasing.** Ask about the problem, the pain, the
  workaround. Never about your idea. If the stakeholder volunteers a
  solution, write it down and keep asking about the problem.
- **The five whys.** The first answer is almost always the surface.
  Keep asking until you reach a constraint, a fear, or an economic
  fact.
- **Silence as a tool.** People fill silence with the things they did
  not plan to say. Wait three extra seconds before your next question.

The output of a good interview is not agreement. It is a richer
picture of the problem than either of you had at the start.

## 2. FIR: a structure for what you heard

After the interview comes the trap: the urge to immediately propose a
solution. The protection against the trap is to write down what you
heard, in three separate layers, with no skipping.

### Facts

What was actually said or observed, in the speaker's own words. No
paraphrase, no interpretation. *"Marion processes the reservation
file every Monday morning. She uses Excel. The file has between
2 000 and 5 000 rows. She told me she stays late on Monday."*

Facts are the only layer that can be checked against reality.

### Insights

What the facts mean once you read them together. Patterns,
contradictions, gaps, surprises. *"Marion's workload doubles on
Mondays, but the team capacity plan treats every day equally. The
manual nature of the work explains the late evenings, and no one has
ever computed the cost of that overtime."*

Insights are an interpretation. They are falsifiable. A second
listener can disagree, and the disagreement is productive.

### Recommendations

Actions that follow from the insights. *"Automate the row-level
validation of the file. Surface the actual Monday workload in the
team capacity plan. Measure the overtime cost before deciding whether
the automation pays for itself."*

Recommendations are cheap and disposable. They are the part of the
work that gets argued about most, and it is fine, because the Facts
and Insights underneath them are solid.

The discipline is to **never skip a layer**. Recommendations without
Insights are opinions. Insights without Facts are guesses.

## 3. Ubiquitous language as the test

When the team and the business can argue about a feature using the
same words, you have understood the problem. When the engineers
silently translate every business word into a different engineering
word, you have not.

This is Eric Evans's diagnostic from *Domain-Driven Design*, and it
is the single most reliable signal I know of in software discovery.

> If the conversation in the standup uses words that would not be
> recognised at a customer review, the model is not shared.

Ubiquitous language is not a glossary. A glossary is what you write
to *pretend* the language is shared. The language is real when you
hear an engineer correct a product manager on a fine distinction, in
the product manager's own vocabulary, and the product manager nods.

I treat it as a forcing function. If the team cannot find a single
word for a concept, the concept is not yet stable. Until it is, no
schema, no API, no migration.

## 4. Executable specification (BDD)

Behavior-Driven Development is not a testing framework. It is a
discovery technique that happens to produce tests.

The artifact is a sentence in three parts: *Given* a context, *when*
an event occurs, *then* a result is expected. Each part has to be
specific enough that an engineer can build it and a business owner
can sign off on it.

```
Given a reservation file with 3 000 rows including 12 invalid entries,
when Marion uploads the file at 09:00 on Monday,
then the system flags the 12 invalid rows in under 30 seconds
and stores the 2 988 valid rows in the inventory.
```

The first time a team writes specifications like this, half of them
turn out to be impossible to write. The numbers are not known. The
edge cases were never discussed. The expected behaviour was assumed.
That is the value of the exercise: BDD makes the gaps in your
understanding loud.

The artifact is reviewable by the business and executable by the
engineers. It outlives the meeting. It survives the team rotation.
It is the single best functional specification I have ever shipped.

## 5. The functional specification as a contract

Everything above produces one tangible deliverable: a functional
specification that holds the shared understanding. It contains the
facts you observed, the insights you drew, the recommendations you
chose, the ubiquitous language you agreed on, and the executable
scenarios that test it.

This document is not a wishlist. It is a contract: between business
and engineering, and against your future self. When the team rotates
or the product evolves, the spec is what protects the original
intent from being silently rewritten by whoever is in the room next.

A good specification is short. It is precise about what is in scope,
honest about what is out of scope, and clear on what success looks
like. It is editable, versioned, and reviewed like code.

## How I use this in practice

Most of my engagements start the same way. I sit with three or four
stakeholders, in separate sessions, and ask them to walk me through
their work. I listen for the words they use, the moments they
hesitate, the workarounds they apologise for. I take notes in the
Facts layer only.

Between sessions, I write the Insights. Patterns surface. Two
stakeholders use the same word for different things, or different
words for the same thing. The team's mental model of its own process
turns out to have holes.

By the time I propose recommendations, the business has done most of
the convergence work itself, by hearing its own Facts read back to
it. The recommendations are rarely the bottleneck. The framing is.

If you want to see what this looks like applied to my current team
at OVHcloud, the [Projects]({{ '/projects/' | relative_url }}) page
has concrete examples.
