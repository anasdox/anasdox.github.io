---
layout: page
title: Le labo
eyebrow: Expériences
permalink: /labo/
redirect_from:
  - /projects/
subtitle: >-
  Chaque idée défendue sur ce site est mise à l'épreuve dans un outil
  open source. Une expérience part d'une question, pas d'une techno.
description: >-
  Expériences open source en AI-Native Product Engineering : discovery
  typée, dépôt BDD-first pour agents, attestations machine contre
  décisions humaines.
cta: true
---

<div class="experiment">
  <p class="meta"><span>TypeScript</span><span>2026</span><span>Discovery</span></p>
  <h2><a href="https://github.com/anasdox/factly">factly</a></h2>
  <dl>
    <dt>Question</dt>
    <dd>Peut-on rendre la chaîne Faits, Insights, Recommandations impossible à court-circuiter ?</dd>
    <dt>Construit</dt>
    <dd>
      Un modèle de données typé (entrée, fait, insight, recommandation,
      livrable) avec des relations explicites entre couches, et une
      application web qui l'impose sous forme de grille. Une
      recommandation doit pointer vers un insight ; un insight, vers un
      fait.
    </dd>
    <dt>Ce que ça teste</dt>
    <dd>
      Qu'une discipline de discovery ne survit à un long trimestre que
      si l'outil la rend mécanique. Chaque séance devient auditable
      couche par couche.
    </dd>
  </dl>
</div>

<div class="experiment">
  <p class="meta"><span>Agnostique</span><span>2026</span><span>Spécification &amp; BDD</span></p>
  <h2><a href="https://github.com/anasdox/bdd-with-ai">bdd-with-ai</a></h2>
  <dl>
    <dt>Question</dt>
    <dd>Que devient un dépôt quand le contrat n'est plus le code ni la prose, mais le scénario exécutable ?</dd>
    <dt>Construit</dt>
    <dd>
      Un modèle de dépôt indépendant de la stack. Il capture le langage
      omniprésent, sépare l'intention fonctionnelle de la conception
      technique, et impose la traçabilité entre spécification et
      implémentation.
    </dd>
    <dt>Ce que ça teste</dt>
    <dd>
      Qu'on peut relire le comportement plutôt que le code. Les portes
      sont contournables à dessein : la règle doit rester un outil, pas
      un rituel.
    </dd>
  </dl>
</div>

<div class="experiment">
  <p class="meta"><span>Go</span><span>2026</span><span>Validation &amp; qualité</span></p>
  <h2><a href="https://github.com/anasdox/workline">workline</a></h2>
  <dl>
    <dt>Question</dt>
    <dd>Qu'est-ce qu'un agent peut attester seul, et qu'est-ce qui doit rester une décision humaine ?</dd>
    <dt>Construit</dt>
    <dd>
      Un gestionnaire de projet en ligne de commande qui sépare deux
      choses que la plupart des outils confondent : les faits
      vérifiables par une machine (la CI est passée, le lint est propre)
      et les décisions portées par un humain (c'est prêt, c'est
      accepté). Definition of Ready et Definition of Done y sont des
      politiques sur des attestations, pas des checklists.
    </dd>
    <dt>Ce que ça teste</dt>
    <dd>
      Qu'on peut confier le travail factuel à un agent en sécurité, tout
      en gardant un humain responsable des décisions.
    </dd>
  </dl>
</div>

<div class="experiment">
  <p class="meta"><span>TypeScript</span><span>2026</span><span>Explicabilité</span></p>
  <h2><a href="https://github.com/anasdox/jinnsynth">jinnsynth</a></h2>
  <dl>
    <dt>Question</dt>
    <dd>Une IA qui produit un résultat doit-elle aussi produire son pourquoi ?</dd>
    <dt>Construit</dt>
    <dd>
      On décrit un son en langage naturel. Le système rend deux
      artefacts de même poids : un patch de synthétiseur validé contre
      les plages de paramètres de l'appareil, et une explication de
      pourquoi il sonne ainsi.
    </dd>
    <dt>Ce que ça teste</dt>
    <dd>
      Le même principe hors du logiciel : une recommandation sans son
      insight est une supposition, que le domaine soit le code ou le son.
    </dd>
  </dl>
</div>
