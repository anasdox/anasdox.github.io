---
layout: post
lang: en
permalink: /agents-made-bdd-affordable-not-delegable/
translation_key: bdd-agents
description: "BDD died of its writing and maintenance cost. Agents collapsed that cost. The one move they cannot make on your behalf: signing off on the behavior scenario."
title: "Agents made BDD affordable. Not delegable."
date: 2026-10-09
---

While building [bdd-with-ai](https://github.com/anasdox/bdd-with-ai),
a repository where agents work from behavior scenarios, I saw two
things that seemed to contradict each other.

The first: an agent proposed an error scenario nobody had thought of.
A real case, one we would have discovered in production.

The second: an agent whose code failed a scenario did not fix its
code. It changed the scenario. The tests went green.

These are two sides of the same finding. Agents finally make BDD
affordable. They can also empty it of its meaning in a single edit.

### Why BDD kept dying

Behavior-Driven Development never had an idea problem. Describe the
expected behavior before writing the code, in a language the business
can read: nobody argues with the principle.

It had a cost problem. Writing the scenarios took time. Writing the
glue code between the Gherkin steps and the system took more. And
above all, everything had to be maintained: every product change broke
steps, duplicated phrases, and left scenarios describing behavior that
no longer existed.

I have seen it up close. The discipline held as long as the team had
time. At the first sprint under pressure, the scenarios moved to
"we'll catch up later". Nobody caught up. The `features/` folder
turned into a museum.

### What agents change in the cost

Almost every line of that cost is work an agent does well and fast:

- drafting a first set of scenarios from a need described in a few
  paragraphs;
- proposing the cases nobody wrote, especially the error paths;
- generating and maintaining the step glue code;
- spotting duplicated phrases and overlapping scenarios;
- realigning the steps when the system evolves.

Take a simple scenario:

```gherkin
Feature: Booking import

  Scenario: Valid lines are recorded
    Given a file of 3,000 bookings, 12 of them invalid
    When the operator uploads the file
    Then the 2,988 valid lines are recorded
    And the 12 invalid lines are reported
```

Ask an agent what is missing, and it comes back with useful questions.
What happens if the same file is uploaded twice? If every line is
invalid? If the file is empty? Each one is a scenario the team should
have written, and usually discovered in production.

The marginal cost of a scenario has collapsed. "We don't have time"
no longer holds. That is the good news, and it is real.

### The trap: a contract that signs itself

The next temptation is logical: if the agent writes the scenarios, the
glue code and the implementation, why not hand it the whole chain? You
describe the need, the agent produces the rest, the tests pass.

At that point, BDD is useless. A scenario only has value because it is
written **independently** of the code it judges. If the same hand
writes the rule and what satisfies it, green proves one thing only:
the agent agrees with itself. It took you a minute to get a circular
contract.

That is worse than missing tests, because it looks like tests. The
column is filled, the scenarios are well written, the report is green.
None of it tells you whether the behavior is the one the business
expected.

### Proposing is not deciding

The split that holds is simple to state:

- **The agent proposes.** First draft, missing cases, rewording,
  duplicate detection. It is better than I am at exhaustiveness.
- **The human decides.** I review the scenarios, settle the open
  questions with the people who will live with the feature, and freeze
  the contract before implementation starts.
- **The contract does not move during implementation.** If the agent
  needs to change a scenario to make its code pass, that is a warning
  sign, not a fix. Either the scenario was wrong, and changing it is a
  human decision. Or the code is wrong, and the scenario just did its
  job.

In practice, that means scenarios and code do not arrive in the same
review. The scenarios are reviewed and approved first, as a change of
their own. The code comes next, and is judged against them.

### Living documentation, on one condition

People often say Gherkin files become documentation that no longer
rots, since the agent can keep it up to date. That is true on one
condition: every scenario must be able to **fail** the day the
behavior disappears. A scenario whose steps check nothing documents an
intention, not the system. It is even more dangerous than an outdated
page, because it is green.

The agent makes maintenance free. It does not make verification
automatic. Making sure green still means something is your job.

### What changed, and what did not

What changed: writing and maintaining scenarios costs almost nothing
now. BDD no longer has an economic excuse to be abandoned.

What did not change: someone has to say what "correct" means for this
software, and answer for it. That move cannot be delegated. Agents
made BDD affordable. They made it more important to sign off on, not
easier to drop.

The loop I use day to day is described in
[When the agent ships faster than I can read]({{ '/when-the-agent-ships-faster-than-i-can-read/' | relative_url }}),
and the place of BDD in framing a problem is on the
[Method]({{ '/method/' | relative_url }}) page. The repository
template lives at
[github.com/anasdox/bdd-with-ai](https://github.com/anasdox/bdd-with-ai).
