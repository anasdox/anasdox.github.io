---
layout: post
lang: en
permalink: /ai-writes-the-code-in-ten-minutes-did-your-ci-keep-up/
translation_key: ci-cadence
description: "Agents speed up the code. The delivery cycle only gets shorter if the validation chain can absorb the new pace. Otherwise, the queue just moves downstream."
title: "AI writes the code in ten minutes. Did your CI keep up?"
date: 2026-10-09
---

A problem in production. To understand what is going on, we need to
add logs. A few lines, which an agent writes in a minute.

Except that adding logs means changing the code. Changing the code
means running the functional tests again. And the functional tests did
not run in parallel: one hour of CI. One hour during which production
stays stuck, without a single extra clue.

The other option was to skip the CI. That is no better: it is exactly
how you create a regression while trying to fix an incident.

The code was ready in a minute. Trust in that code cost an hour. Do the
math on your own pipeline: the review that waits until tomorrow, the
deployment reserved for Thursday morning, preferably when Mercury is
not in retrograde. The agent saves hours on implementation. The full
cycle does not move.

### The bottleneck moved again

In [an earlier post]({{ '/when-the-agent-ships-faster-than-i-can-read/' | relative_url }}),
I wrote that agents had collapsed the build phase to minutes, and that
the bottleneck had moved to review. Then that
[BDD]({{ '/agents-made-bdd-affordable-not-delegable/' | relative_url }})
lets you define what must be true, and review scenarios rather than
diffs.

The next step follows mechanically. If code is cheaper and the
contract is clear, the question becomes: how fast can we verify that
the code honors the contract, and put it in production safely? That is
the job of CI/CD. And it was not designed for this pace.

AI speeds up code production. CI/CD has to speed up trust. If it does
not, the acceleration stays upstream, in the form of branches waiting
in line.

### A deterministic chain around a probabilistic producer

An agent does not produce the same code twice for the same request.
That is its nature, and it is not a flaw as long as something
reproducible judges the result. That something is the validation
chain.

It has to check, the same way on every run:

- the expected behaviors, meaning the scenarios;
- the critical invariants, the ones that must never break;
- the absence of regressions;
- security;
- the quality of the produced artifact.

The agent proposes. The chain attests. The human decides what the
chain cannot attest. That is the split I explore with
[workline]({{ '/labo/' | relative_url }}): what a machine can prove on
its own, and what must stay a decision.

### Coverage is not enough

A high coverage percentage says that lines were executed. It does not
say a test would have failed if the behavior had disappeared. A test
that asserts nothing covers its lines and goes green.

With an agent, the risk grows: it knows how to write tests that pass,
and it is rewarded when they pass. The checks that matter are the ones
that actively try to make the code fail:

- **business scenarios**, which state what must be true;
- **property-based testing**, which hunts for the counterexample
  instead of checking three hand-picked cases;
- **fuzzing**, on anything that parses external input;
- **mutation testing**, which changes the code and checks that at
  least one test notices. It is the only measure that answers the
  question "can my tests fail?";
- a few **targeted integration tests**, where the mocks lie.

### Parallelize validation

When code production speeds up, a suite that runs sequentially turns
into a queue. Adding tests without thinking about their order makes
every cycle longer by the same amount, for every change.

The suite has to be organized as a graph, not a list: by dependencies,
by risk level, and by what the change actually touches. A change to
the documentation does not rerun the integration tests. A change to
the payment module reruns all of them. Fast, decisive checks go first,
to fail early. The hour of CI in my incident was not inevitable: it was
a suite of functional tests waiting their turn one behind the other.

### Stop piling everything onto the plate

The other way to make a CI longer is to stack up everything that can
be checked. Spelling in the specifications. Mermaid diagram syntax.
Markdown formatting. Each of these checks is reasonable on its own. On
a repository with a lot of files, their sum costs minutes on every
run, and it blocks changes that have nothing to do with them.

I ask the question differently: what does this check protect? A typo
in a specification does not change the system's behavior. A human
reads past it, and an LLM understands it without trouble. A functional
regression, on the other hand, ships to production.

These checks belong in the editor, in a local hook, or in a job that
blocks nothing. Not on the critical path between a fix and production.
A CI that runs good functional and acceptance tests fast, with real
behavior coverage, beats an exhaustive CI that delivers typo-free
specifications late.

### Produce an artifact you can trust

The same artifact, built once and versioned, has to travel through
every environment. Not a rebuild at each stage, with dependencies
resolved at different times and a result nobody actually tested.

What the CI validated must be exactly what ships to production.
Otherwise, the validation applies to an object that no longer exists.

### Rollback is part of deployment

A rollback that was never tested is a hope written in YAML.

When the delivery pace increases, the number of production releases
increases with it, and so does the number of times one of them goes
wrong. The answer is not to slow down. It is to limit the blast radius
of each release:

- **feature flags**, to separate deployment from activation;
- **progressive rollouts**, on a fraction of the traffic first;
- **observability** that tells you within minutes whether production
  behavior matches the expected behavior;
- a **rollback** that is part of the normal path, exercised regularly,
  and not an emergency procedure you discover the day you need it.

### Speed up trust

Agents made code cheap. They did not make verification, release or
rollback cheap. If those three keep their old pace, the delivery cycle
keeps its old pace too, and the acceleration turns into a stock of
changes waiting in line.

So the question to ask your pipeline is not "how fast do we produce
code?". It is "how fast can we trust what we ship?".
