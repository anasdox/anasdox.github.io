---
layout: page
title: Projects
permalink: /projects/
---

Tools I have built in the open, and engagements I have run.
Both told through the same lens as the
[Method]({{ '/method/' | relative_url }}): what was the actual
problem, what did the framing reveal, what was built.

## Open-source

<div class="project">
  <h2><a href="https://github.com/anasdox/factly">factly</a> -- discovery as a typed workspace</h2>
  <p class="meta">Open-source · TypeScript · 2026</p>
  <p>
    <strong>The problem.</strong> Discovery sessions get lost. The
    facts are stuck in someone's notebook, the insights live in a
    different document, and the recommendations end up disconnected
    from the evidence they were drawn from. Three months later, no
    one can reconstruct why a given decision was made.
  </p>
  <p>
    <strong>The framing.</strong> The FIR pipeline is not a habit
    you can leave to discipline alone. It has to be the data model:
    Input, Fact, Insight, Recommendation, Output, with explicit
    relationships between each layer. A recommendation that does
    not point back to an insight is malformed. An insight that does
    not point back to a fact is malformed.
  </p>
  <p>
    <strong>What was built.</strong> A web app that enforces that
    structure as a visual grid. Optional AI-assisted extraction
    surfaces fact candidates from raw documents, but the shape of
    the reasoning stays the same whether the facts are entered by a
    human or by a model. A discovery session you can audit, replay
    and challenge layer by layer.
  </p>
  <p class="tags">
    <span>FIR</span><span>Discovery</span>
    <span>TypeScript</span><span>Open-source</span>
  </p>
</div>

<div class="project">
  <h2><a href="https://github.com/anasdox/bdd-with-ai">bdd-with-ai</a> -- BDD-first repository template</h2>
  <p class="meta">Open-source · stack-neutral · 2026</p>
  <p>
    <strong>The problem.</strong> Most teams know they should write
    executable specifications before code, and most teams stop
    doing it within a sprint or two. The discipline collapses under
    pressure unless the repository itself enforces it. Adding AI
    coding agents to that loop turns ambiguous requirements into
    the wrong implementation faster than ever.
  </p>
  <p>
    <strong>The framing.</strong> The contract is not the code, and
    it is not the prose. The contract is the executable scenario,
    versioned next to the code, signed off by the business, and
    traceable to a functional specification that humans and agents
    read in the same way.
  </p>
  <p>
    <strong>What was built.</strong> A stack-neutral repository
    template that captures ubiquitous language, separates functional
    intent from technical design, and enforces traceability between
    specification and implementation. Three operating modes cover
    greenfield, brownfield, and template work. Gates are bypassable
    on purpose, so the rule is a tool, not a ritual.
  </p>
  <p class="tags">
    <span>BDD</span><span>Ubiquitous language</span>
    <span>Functional specification</span><span>Open-source</span>
  </p>
</div>

<div class="project">
  <h2><a href="https://github.com/anasdox/workline">workline</a> -- attestations as a first-class object</h2>
  <p class="meta">Open-source · Go · 2026</p>
  <p>
    <strong>The problem.</strong> AI agents now write code, run
    tests, and produce summaries at machine speed. Most project
    tools were not designed for that. They blur two things that
    should never have been one: machine-verifiable facts (CI passed,
    lint clean, review approved), and human-owned decisions (this is
    ready, this is accepted, this risk is mine).
  </p>
  <p>
    <strong>The framing.</strong> The FIR distinction applied to
    delivery. Facts attest themselves. Responsibility is named,
    dated and human. The Definition of Ready and Definition of Done
    are not checklists, they are policies over attestations, and
    the event log records who attested what, when.
  </p>
  <p>
    <strong>What was built.</strong> A CLI-first project manager
    where every task carries its attestations, every gate cites the
    policy it enforces, and the responsibility line is always
    legible. Designed so an agent can do the factual work safely
    and a human stays accountable for the decisions.
  </p>
  <p class="tags">
    <span>Attestations</span><span>FIR</span>
    <span>Go</span><span>Open-source</span>
  </p>
</div>

<div class="project">
  <h2><a href="https://github.com/anasdox/jinnsynth">jinnsynth</a> -- language to synth patch, with the why included</h2>
  <p class="meta">Open-source · TypeScript · 2026</p>
  <p>
    <strong>The problem.</strong> Hardware synthesizers expose dozens
    of parameters that interact non-trivially. The gap between
    "I want a warm pad" and the patch that produces it is wide, and
    most tools either generate a patch with no explanation, or
    explain sound design abstractly with no patch.
  </p>
  <p>
    <strong>The framing.</strong> Describe the sound in natural
    language. The system returns two artifacts of equal weight: a
    patch validated against the device's parameter ranges, and an
    explanation of why the patch sounds the way it does. Treating
    the explanation as a first-class output turns the tool from a
    generator into a learning instrument. A recommendation without
    its insight is a guess, whether the domain is software or sound.
  </p>
  <p>
    <strong>What was built.</strong> A platform-neutral core (typed
    patch schema, validator, prompts) with thin shells: an Express
    proxy, a Svelte browser UI, Web MIDI, and SysEx encoding for
    the Audiothingies MicroMonsta 2. The same core could drive an
    MCP server tomorrow without touching the agent logic.
  </p>
  <p class="tags">
    <span>Synthesis</span><span>Explainability</span>
    <span>TypeScript</span><span>Open-source</span>
  </p>
</div>

## Engagements and companies

<div class="project">
  <h2>Bare Metal Undercloud -- engineering team leadership at OVHcloud</h2>
  <p class="meta">OVHcloud · 2022 - present · Rennes</p>
  <p>
    <strong>The scope.</strong> I lead a team of six engineers (two
    technical leads, four senior contributors) responsible for the
    Undercloud orchestration layer behind OVHcloud Bare Metal: the
    system that turns racks of physical servers into allocatable
    compute, tracks every server through its lifecycle (stock,
    reserved, connected, delivered, reallocated, decommissioned), and
    exposes the customer-facing APIs through which our cloud and
    enterprise customers see that state. The team owns several
    parallel chantiers at any time: self-encrypting drives rollout,
    server intervention status communication, dynamic server
    reallocation, OS reinstall rationalisation, server inventory
    synchronisation, monitoring migration. Direction asks two outcomes
    from us: predictability of delivery, and anticipation of delays.
  </p>
  <p>
    <strong>What framing kept revealing.</strong> Across every
    chantier the bottleneck was rarely engineering speed. It was the
    shared understanding across boundary teams. "Delivered" meant
    something else to the Industry team than to ours. "Blocked" tickets
    often were not blocked. The same word travelled through Industry,
    Cloud API, hardware engineering and data centre ops, and quietly
    drifted at every hand-off. Ubiquitous language failure at the
    organisational seam. The standing rituals re-derived the same
    intermediate facts every Monday by hand, and the slippage between
    sprints showed up only once a sprint had been lost to it.
  </p>
  <p>
    <strong>What I changed.</strong> Each chantier now starts as a
    framing exercise: who are the actors, draw the flows end to end,
    surface where the language breaks across teams, write the contract
    that both sides will sign. The quarterly review pipeline runs on
    weekly snapshots, structured drift radars and sprint-granular
    P50/P90 forecasts per epic, and the status that goes to direction
    fits on a single screen. Cross-team escalation has moved from
    ad-hoc messages to traceable, Jira-anchored hand-offs that survive
    a holiday week.
  </p>
  <p class="tags">
    <span>Engineering leadership</span><span>Bare Metal</span>
    <span>Undercloud</span><span>Cross-team framing</span>
    <span>Ubiquitous language</span>
  </p>
</div>

<div class="project">
  <h2>a4m -- internal AI-native engineering workbench</h2>
  <p class="meta">OVHcloud · Python (stdlib only) · 2025 - present</p>
  <p>
    <strong>The problem.</strong> Reporting and ritual work consumed
    a disproportionate share of my week. The data needed to answer
    "where is this team actually at" lived in four different systems
    (Jira, Confluence, Bitbucket, Webex) in four different shapes,
    and every Monday the same intermediate facts had to be re-derived
    by hand before any meaningful conversation could happen.
  </p>
  <p>
    <strong>The framing.</strong> The team's ubiquitous language
    (epic, chantier, blocked, done, sprint-granular ETA, P50 / P90
    forecast, drift) was already in active use. It just lived in
    human memory and got re-interpreted on every report. If the
    language was captured in code instead, every report would come
    from the same source, and the discovery discipline (Facts,
    Insights, Recommendations) could be the default shape of the
    tool, not an extra step.
  </p>
  <p>
    <strong>What was built.</strong> A standard-library Python CLI
    that orchestrates the four services behind a single verb-driven
    interface, captures the team's vocabulary in code, and emits
    Facts (drift radars, capacity snapshots, hygiene audits,
    sprint-granular forecasts), Insights (where exactly things are
    slipping and why), and Recommendations ready to send. The
    repository ships with an explicit <code>CLAUDE.md</code> so that
    a Claude session reads the team's conventions in one pass and
    becomes a first-class user, not a bolt-on. Every weekly delivery
    ritual now runs through it.
  </p>
  <p class="tags">
    <span>FIR</span><span>AI-native</span><span>Python</span>
    <span>CLI design</span><span>Internal tooling</span>
  </p>
</div>

<div class="project">
  <h2>Placemeet -- SaaS for online professional events</h2>
  <p class="meta">Co-founder &amp; CEO · 2020 - 2022</p>
  <p>
    <strong>The problem.</strong> Professional event organisers needed
    an online tool that respected the social mechanics of a real event,
    not a video grid. The market shipped video grids.
  </p>
  <p>
    <strong>What discovery revealed.</strong> The complaints were not
    about the tools. They were about the loss of incidental
    interaction (the hallway, the coffee, the "do you have a minute").
    Building a video platform would not have addressed any of that.
  </p>
  <p>
    <strong>What was built.</strong> A SaaS platform whose architecture
    centred on those interactions rather than on broadcast quality.
    I shipped the product end to end through the COVID demand surge,
    hired the engineering team, and built the operations underneath.
  </p>
  <p class="tags">
    <span>Customer discovery</span><span>SaaS</span><span>Architecture</span>
    <span>CEO</span>
  </p>
</div>

<div class="project">
  <h2>DevOps transformations at Niji</h2>
  <p class="meta">Solutions Architect / VP of Engineering · 2014 - 2018</p>
  <p>
    Enterprise clients in banking, telecom and media all wanted
    "DevOps", and meant different things by it. The pain was never
    the pipeline. It was the handoff between the team that wrote the
    code and the team that ran it, encoded in a contract neither side
    had actually read. I built a discovery-first consulting practice
    that started every engagement with structured interviews, FIR
    write-ups and a shared functional specification. The internal
    orchestrator we shipped automated the lifecycle, but it was
    always the spec that closed the engagement.
  </p>
  <p class="tags">
    <span>Pre-sales</span><span>Consulting</span><span>FIR</span>
    <span>Orchestrator</span>
  </p>
</div>

<div class="project">
  <h2>ozzo.io -- evolutionary algo-trading platform</h2>
  <p class="meta">Founder · 2019</p>
  <p>
    Algo traders did not want automated re-tuning of their strategies.
    They wanted to understand <em>which</em> market conditions each
    strategy was silently betting on. The product I built turned
    static strategies into evolutionary ones that adapted to changing
    regimes, with explicit visibility into which regime each variant
    was tuned for.
  </p>
  <p class="tags">
    <span>FinTech</span><span>Evolutionary computing</span>
    <span>Founder</span>
  </p>
</div>
