---
layout: page
title: Projects
permalink: /projects/
---

What I build in the open outside of the day job: tools that codify
the [Method]({{ '/method/' | relative_url }}), and the music I make
on the side. For the engagements I have run, see
[Experience]({{ '/experience/' | relative_url }}).

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

## Music

<div class="project">
  <h2><a href="https://www.twitch.tv/ramas_music">ramas_music</a> -- live music on Twitch</h2>
  <p class="meta">Twitch · live</p>
  <p>
    Live improvised electronic music. No presets, no map, just
    exploration.
  </p>
  <p class="tags">
    <span>Live</span><span>Improvisation</span>
    <span>Electronic</span>
  </p>
</div>
