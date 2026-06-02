---
layout: post
title: "The why I owed the next devs"
date: 2026-05-29
---

For the first half of my career I was the developer at the end of
the chain. A feature would land on my plate, with a spec, a
deadline, sometimes a Jira ticket and a Figma link. What it never
came with was an answer to the question I kept asking: *why are we
building this?*

I do not mean "what business problem does it solve" in the
polished form that ends up on a slide. I mean: who is hurting,
what did they actually say, what did we observe, what made us pick
this option and not the other three. The information that would
let me push back when an edge case in the design quietly
contradicted the apparent intent. The information that would let
me make a small judgement call without escalating.

Every time I dug for that information, one of two things turned
out to be true. Either the problem had been poorly identified
upstream, and the spec was the polished output of a fuzzy
conversation no one quite remembered. Or the information existed,
somewhere, in the head of a product manager, in the margin of a
slide deck, in the minutes of a meeting I could not access. And
getting to it cost more political capital than the question was
worth.

So I built the feature on the signal I had. Most of the time it
shipped, got used, was fine. Sometimes a year later we discovered
we had built the wrong thing precisely, and nobody could quite
reconstruct how we had gotten there.

---

Years later I crossed sides. I became a solutions architect on
pre-sales engagements: in the room with the client, framing the
problem, designing the response, then handing the engagement off
to the delivery team to actually build. For the first time I was
the one writing the spec the next dev would read.

I had a very specific promise to keep, which was not to do to
those devs what had been done to me.

That promise sounds obvious. In practice it is harder than it
looks. The pressure on the architect is to compress: clean
recommendation, estimated effort, tidy diagram. The pressure is
to remove the noise, the contradictions, the half-said things
from the discovery, because the proposal needs to read decisively.
Every gram of compression makes the next dev's life harder.

What I needed was a discipline that let me compress the
conclusion without compressing the trail.

---

The discipline I converged on is FIR: Facts, Insights,
Recommendations. Each layer is written separately, and each
conclusion at one layer must cite the items in the layer below.

**Facts** are what was actually said or observed during discovery.
The user's own words. The screenshot of the broken receipt. The
number on the dashboard. No paraphrase.

**Insights** are what the Facts mean once you read several of
them together. Patterns, contradictions, gaps. Each Insight
references the Facts it interprets. A second reader can disagree,
and the disagreement is grounded.

**Recommendations** are what to do. Each Recommendation
references the Insights it follows from.

The point of the structure is not the elegance. The point is that
the dev who picks up the spec six weeks later, in a different
timezone, can walk a recommendation back to its supporting
insight, and that insight back to a sentence someone actually
said. The why is not in the architect's head anymore. It is in
the chain.

The variant I now use day to day is called Atomic Research. Same
three layers, with the experiences that produce the facts
(interviews, observation sessions, surveys, raw data) treated as
first-class objects in the structure. I wrote up the methodology
for my current employer's discovery practice so that the trail
would not depend on whether I happened to be in the meeting.

---

What I did not realise for years is that the structure does not
survive a regular document. Slides invert the hierarchy:
recommendation as a heading, facts as a footnote. Notion tables
let everything land in one Notes column. Excel forgives any
column you do not use. The three layers survive the first
session. They do not survive the third.

So I built [factly](https://github.com/anasdox/factly), a small
workspace where the columns are not optional. Inputs on the left,
then Facts, then Insights, then Recommendations, then Outputs.
Each item links back to what it depends on. An Insight with no
Fact does not exist in the grid. A Recommendation with no Insight
does not exist in the grid. The dev who reads the output can
follow the line back to the original observation. The discipline
becomes mechanical, which is the only way it survives a long
quarter.

---

I am not naive about this. Plenty of engagements still ship a
polished recommendation and very little of the trail. But on the
ones where the trail did survive, the next devs asked sharper
questions, made better local decisions, and pushed back on things
the original framing had gotten wrong. That outcome was the only
one that mattered to me from the day I switched sides.

The full method is on the
[Method]({{ '/method/' | relative_url }}) page. The version I
keep re-reading at the top of every readout deck is shorter:

> Spend more time understanding the problem than designing the solution.
