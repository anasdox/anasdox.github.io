---
layout: post
lang: en
permalink: /the-question-that-contained-its-own-answer/
translation_key: question
description: "A leading question in a discovery session cost two months of automation nobody used. The three interview rules I have followed since."
title: "The question that contained its own answer"
date: 2026-05-28
---

Early in my consulting years I sat in a discovery session with a
client's operations manager. I wanted to understand how her team
processed a daily reconciliation file. I had a hypothesis: the work
was repetitive, it would benefit from automation, the team was
probably under-staffed for the volume.

The first thing I asked was: *"Don't you think it would help if we
automated this?"*

She said yes. Of course she said yes. I had asked her, in front of
her own boss, whether she would like her team to be relieved. The
only answer that did not make her look ungrateful was the one I had
already written into the question.

We spent two months building the automation. The team used it for a
week and quietly went back to Excel.

When I went back to ask why, the real story came out. The
reconciliation was not the painful part of their day. The painful
part was the upstream file: it arrived late, in inconsistent
formats, with rows that contradicted last week's rows. The Excel
workflow had grown around those quirks. The automation we built was
strict where they had learned to be flexible, and it broke on the
first malformed row.

The real fix was upstream and it was not technical. It was a
conversation with the data producer about format guarantees. A
conversation we never had, because my first question had closed the
door on it before it opened.

---

That session is the moment I started taking the interview seriously
as a craft. I rebuilt my discovery practice around three rules, and I
have followed them ever since.

**No solution-shaped questions.** The format of the question
constrains the format of the answer. *"Would it help if you had X?"*
will get a polite yes. *"Walk me through the last time this hurt"*
will get the story you need.

**Five whys, with no shortcuts.** The first answer is the surface.
The second is the workaround. The third is usually the constraint.
Beyond the fourth you are touching the actual driver, which is
almost always organisational, economic, or about fear of looking
bad.

**Write Facts first, Insights second, Recommendations last.** The
two months we lost on the wrong automation were two months of
recommendations built on a single biased fact. If I had written down
*"I asked a leading question; she said yes"* in the Facts layer, no
honest Insight would have survived contact with it.

---

The discipline is not glamorous and it does not impress in a
proposal deck. But it is the only thing I know that prevents the
quiet failure mode: shipping the wrong thing on time, on budget,
correctly built, and quietly unused.

I write about the full method on the
[Method]({{ '/method/' | relative_url }}) page. The short version is
the one at the top: spend more time understanding the problem than
designing the solution.
