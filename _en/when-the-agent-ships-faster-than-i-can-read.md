---
layout: post
lang: en
permalink: /when-the-agent-ships-faster-than-i-can-read/
translation_key: agent
description: "Coding agents collapsed the build phase to minutes. Specify, validate and review did not move. Why I now review behavior, not code."
title: "When the agent ships faster than I can read"
date: 2026-05-29
---

The exchange usually goes like this. I describe a feature in two
paragraphs. The agent comes back ten minutes later with three
thousand lines of code, a clean diff, green tests, and a PR
description that reads better than the one I would have written.

I scroll. I scroll some more. The tests are passing. The structure
looks reasonable. The naming is on-brand. I have ten other things to
do today.

I approve.

That is the moment where I have stopped being the engineer and
started being a spectator of my own codebase. The agent has no
on-call, no customer impact, no incident postmortem to fear. The
risk did not move. It is still mine. But my ability to see the risk
just dropped by an order of magnitude, because I am reviewing code I
did not write, against an architecture the agent inferred, in a time
budget that has not changed.

I started noticing this a few months in. The first time, I shrugged.
The third time, my ego felt it.

### The center of gravity shifted

Software has four phases that used to take roughly comparable time:
specify, build, validate, review. Generative coding agents collapsed
the build phase to minutes. The other three did not change. They are
human phases. They take human time, human attention, human bandwidth.

The result is that the bottleneck moved, and we did not. We ship
code that nobody fully understood being written, into codebases that
nobody fully understood absorbing it. The honest description of what
happens then is: *we approve and move on*. The cost of approving
without understanding is invisible until the incident.

### The problem is no longer "how to code"

The problem is "how to stay in control". The agent can generate. It
cannot take responsibility. If I am the one paged on Sunday morning,
I am the one who owes the codebase a level of attention the agent
is incapable of providing on my behalf.

That sounds obvious written down. It is much less obvious when the
PR is green and the agent is waiting for the next prompt.

### Review behavior, not code

The shift that worked for me is the one Behavior-Driven Development
has been quietly waiting to make. Before generative agents, writing
executable specifications before the code felt like overhead. Teams
wrote the scenarios, but slowly, and only when the feature was big
enough to justify the ceremony. The discipline collapsed the first
time a sprint got hot.

Generative agents reverse the economics. Now the code is cheap. The
behavior specification is the only artifact whose meaning I still
have to absorb. Reading one Gherkin scenario takes thirty seconds.
Reading the three thousand lines that implement it takes half a day
I do not have.

So the unit of review moved one level up. I now spend my attention
on five to ten scenarios at a time, written in the project's
ubiquitous language, signed off by the people who will live with the
feature. The agent then implements, runs the tests, iterates until
they pass, demonstrates the result, and waits.

The cognitive load goes down because the artifacts I read are short
and meaningful. The control goes up because nothing reaches the
codebase without surviving a behavior contract I actually understood.
The quality goes up because the contract is also the regression
suite.

### What the loop looks like

The shape of the loop is the same every time. I write a feature
description with three to ten scenarios in Given-When-Then form. The
agent generates the test scaffolding from the scenarios, and I
review the scaffolding. The agent generates the production code that
makes the tests pass. I review the result against the scenarios, not
against the line diff. The agent demonstrates the running behavior.
I sign off, or I refine the scenarios and we run another round.

{::nomarkdown}
<div class="mermaid">
flowchart TD
  Start(["Feature description, 3 to 10 scenarios"]) --> Scaffold["Agent: test scaffolding"]
  Scaffold --> ReviewSpec{"Human review: tests match scenarios?"}
  ReviewSpec -- no --> Start
  ReviewSpec -- yes --> Implement["Agent: production code"]
  Implement --> Run["Agent: runs tests, iterates"]
  Run --> Demo["Agent: demonstrates behavior"]
  Demo --> Validate{"Human: behavior correct?"}
  Validate -- no --> Start
  Validate -- yes --> Done(["Sign off"])
</div>
{:/nomarkdown}

What I am doing in that loop is the same thing I have always done as
an engineer: deciding what "correct" means for this software, in
language a stakeholder could read. What changed is that I stopped
spending most of my day in the editor that produces the code, and
started spending it in the document that decides what the code must
do.

The agent shipped the implementation. I shipped the contract. That
is the division of labour I want for the codebases I plan to be
responsible for in two years.

If you want the template I use as a starting point, it lives at
[github.com/anasdox/bdd-with-ai](https://github.com/anasdox/bdd-with-ai).
The longer write-up of why behavior specifications sit at the centre
of how I work is on the [Method]({{ '/method/' | relative_url }})
page.
