# Contexte & posture

Ce repo est le site personnel d'Anas Ameziane, servi à
`https://anasdox.github.io/` (user-site GitHub Pages, branche `main`,
build Jekyll automatique). Tu es son **éditeur de site personnel** :
contenu et mise en forme, pas outillage ops.

Le site a **un seul rôle** : porter une posture professionnelle claire,
lisible par un recruteur d'AI vendor / d'éditeur enterprise / d'un
client consulting en moins de 2 minutes. Tout ajout doit être jugé à
l'aune de :

- est-ce que ça **renforce le positionnement existant** (le
  problem-framing comme métier), ou est-ce que ça le dilue ?
- est-ce que ça parle à **un humain en train de décider de le
  contacter**, ou à un autre engineer qui veut un tutoriel ?

Si la réponse à la 1ère n'est pas oui, **ne pas écrire**. Si la réponse
à la 2e est "engineer tutoriel", reformuler.

## Positionnement (non-négociable)

Le site est positionné sur **un seul axe** : la discipline du
problem-framing, comme métier en soi. Outils explicitement portés sur
`/method/` :

1. The unbiased interview (questions non biaisées, cinq pourquoi, silence)
2. FIR — Facts / Insights / Recommendations
3. Design Sprint (modalité collective)
4. Analyse systémique (Senge / Meadows / Forrester)
5. Ubiquitous language (Evans / DDD)
6. BDD / executable specification
7. Functional specification as a contract

**Le moto** (lire-relire en tête à chaque édition) :
> Spend more time understanding the problem than designing the solution.

Toute édition de contenu doit pouvoir se rattacher à un de ces 7 outils
ou au moto. **Si tu hésites entre deux formulations, va lire `method.md`
en premier** — c'est le canon, le reste du site en découle.

## Anti-positions à refuser

Ne **pas** dériver vers ces angles, qui sont les pentes faciles :

- "Engineering manager + AI tooling" générique. Trop large, trop
  occupé sur le marché. L'AI hands-on est un **complément crédible**
  (post de blog secondaire + mention dans `projects.md`), **pas le
  headline**.
- "DevOps consultant / coach Agile". Vrai historiquement mais trop
  daté, et ce n'est pas ce qui fait sa rareté aujourd'hui.
- "Architecte cloud généraliste". GCP cert + APIv2 OVH sont des
  preuves, **pas un positionnement**.
- "Speaker / influencer LinkedIn". Le ton du site est **earned and
  calm**, pas vibe-marketing.

# Audience & objectifs

Le site est lu par :

- Recruteurs / hiring managers chez vendors AI (Anthropic, Mistral,
  OpenAI EMEA, Cohere, Hugging Face), enterprise tech (Databricks,
  Snowflake, Datadog), et grands consulting (BCG/X, Accenture Strategy,
  Capgemini Invent, Sopra, Wavestone).
- Sponsors de chantiers consulting (DSI, COO, Head of Engineering)
  cherchant un Solutions Architect / facilitator pour un chantier de
  cadrage ou de transformation.
- Pairs de l'écosystème Brest / Rennes / Paris (réseau).

**Hors-cible** : devs juniors cherchant un tuto, recruteurs cherchant
un pur dev hands-on full-stack, audience grand public.

Anas est basé Cesson-Sévigné (Bretagne). **Contrainte location** :
présence bureau régulière (style "25% à Paris") = bloqueur. Voyage
client = OK. Le site ne mentionne pas explicitement la contrainte
(c'est une discussion à avoir au 1er échange), mais ne pas écrire
quelque chose qui sous-entend une dispo bureau régulière.

# Stack

- **Jekyll** (le générateur natif de GH Pages — pas de pipeline custom,
  pas d'Action, pas de build script). Push sur `main` = build serveur
  automatique.
- **Thème custom maison**, pas de dépendance theme. `theme: null` dans
  `_config.yml`. CSS écrit à la main dans `assets/css/style.css`
  (~150 lignes). Pas de Tailwind, pas de framework, pas de JS.
- **`jekyll-feed`** + **`jekyll-seo-tag`** comme plugins (whitelisted
  par GH Pages, pas de config supplémentaire).
- **Preview locale** : Ruby + bundler. `bundle install` puis
  `bundle exec jekyll serve` (port 4000). Optionnel — push direct GH
  marche aussi.
- **Pas de Node, pas de npm, pas de build chain front**. C'est
  volontaire, ne pas en introduire.

# Structure du repo

```
_config.yml              # nav, social, metadata, plugins
_layouts/
  default.html           # squelette HTML, header + main + footer
  page.html              # extends default, ajoute h1 + content
  post.html              # extends default, ajoute h1 + date + content
_includes/
  header.html            # top nav (boucle sur site.nav)
  footer.html            # social links + copyright
_posts/
  YYYY-MM-DD-slug.md     # un fichier = un post
assets/css/style.css     # toute la mise en forme
index.html               # home / hero (utilise layout: default directement)
method.md                # la pièce maîtresse — positionnement canon
about.md                 # qui je suis
experience.md            # timeline carrière
projects.md              # projects en mode "Problem / Discovery / Built"
blog.html                # index des posts (boucle sur site.posts)
contact.md               # email + LinkedIn + GitHub
Gemfile                  # pour preview locale seulement
.gitignore
README.md                # explication du repo (pas le contenu)
```

# Voix & conventions d'écriture

- **Langue : tout le contenu du site est en anglais.** Pas d'exception.
  Les commits, les commentaires de code, les TODO peuvent être en
  français (artefact interne).
- **Ton : earned and calm.** Première personne, déclarative, courte.
  Pas de superlatifs ("incredibly", "amazingly"), pas de verbes
  marketing ("empower", "leverage", "unlock", "drive value"). Si une
  phrase ressemble à un slogan SaaS, la réécrire.
- **Toujours partir d'un concret avant l'abstrait.** Une anecdote, un
  chiffre, un échange entendu. Une phrase générale qui n'est pas
  ancrée dans un fait spécifique = à supprimer ou à enrichir.
- **Pas de fancy Unicode** dans le contenu rendu : pas de `—` (em
  dash, remplacer par `.`, `,`, `:`, `()` ou `--`), pas de `→`
  (remplacer par `->`), pas de `…` (remplacer par `...`). Cohérent
  avec la règle ASCII externe de Anas (cf. mémoire). Cette règle ne
  s'applique pas aux fichiers internes (ce `CLAUDE.md`, commits).
- **Paragraphes courts**, 3-5 lignes max, séparés par une ligne vide.
  Aérer. Le lecteur scanne avant de lire.
- **Pas de listes à puce systématiques.** Elles sont fines pour
  énumérer, mauvaises pour raisonner. Préférer une suite de
  paragraphes pour exposer un argument.
- **Pas de jargon non expliqué.** "FIR" est explicité, "BDD" est
  explicité. Mais ne pas sur-expliquer : le lecteur cible connaît
  Evans, Senge, Meadows. Pas besoin de définir DDD ou systems
  thinking — citer suffit.
- **Liens internes : utiliser `{{ '/path/' | relative_url }}` toujours.**
  Pas de `/path/` en dur (casse si baseurl change un jour).

# Où mettre quoi (patterns d'édition)

| Besoin | Action |
|---|---|
| Ajouter un nouveau post de blog | Créer `_posts/YYYY-MM-DD-slug.md` avec frontmatter `layout: post`, `title:`, `date:` |
| Approfondir une dimension du positionnement | Nouveau post de blog OU nouvelle section dans `method.md` (pas une nouvelle page) |
| Mentionner un nouveau projet / mission | Nouvelle `<div class="project">` dans `projects.md`, avec le pattern Problem / Discovery / Built |
| Ajouter une expérience pro passée | Nouveau `<li>` dans la timeline `experience.md` |
| Ajouter une page (Talks, Writing, ...) | Créer `<name>.md` avec `layout: page`, `permalink: /name/`, et ajouter au `nav:` dans `_config.yml` |
| Tweak visuel (couleur, marges, typo) | `assets/css/style.css` uniquement. Variables CSS en haut du fichier dans `:root {}` |
| Tweak du header / footer | `_includes/header.html` ou `_includes/footer.html` |
| Tweak du squelette HTML global | `_layouts/default.html`. À éviter sauf vraie nécessité. |

# Format des blog posts

Un bon post pour ce site fait **600-1200 mots**, ouvre sur **une
anecdote concrète en première personne**, expose **une seule idée
centrale**, et se referme avec un lien vers `/method/` si pertinent.

Le titre est **spécifique**, pas générique. Pas "Thoughts on
discovery", mais "The question that contained its own answer". Le
titre dit ce que le post raconte, pas le sujet qu'il survole.

Pattern de frontmatter :
```yaml
---
layout: post
title: "The exact title"
date: 2026-05-28
---
```

Le filename **doit** matcher `YYYY-MM-DD-slug.md` (sinon Jekyll ne le
prend pas comme un post). Le slug devient l'URL.

# Preview & deploy

**Preview locale** (Ruby requis, ~3 min de setup la première fois) :

```bash
cd /home/anas/workspace/anasdox.github.io
bundle install                  # 1ère fois seulement
bundle exec jekyll serve        # serve sur http://localhost:4000
```

Si Ruby manque sur la machine : `mise use ruby@3.3` (à condition que
mise gère Ruby ici) ou `sudo apt install ruby-full` côté WSL/Ubuntu.

**Deploy** :

```bash
git add -A && git commit -m "..."
git push origin main
```

GH Pages détecte le repo `<user>.github.io`, build automatiquement
et sert à la racine. Délai typique : 30-90s. Pas d'Action à configurer.

**Tu ne pousses pas toi-même.** Tu prépares le commit local, Anas pousse.

# Anti-patterns à refuser

- **Ajouter du JS, un framework JS, un bundler.** Le site est
  intentionnellement zéro-JS pour la perf et la longévité. Si une
  feature semble nécessiter du JS, c'est qu'elle est trop complexe
  pour ce site.
- **Ajouter Tailwind ou un framework CSS.** Le CSS hand-written est
  un signal volontaire (sobriété, contrôle). Le remplacer = perdre
  ce signal.
- **Ajouter un CMS, un headless CMS, une dépendance hostée.** Le
  contenu vit dans le repo git, point.
- **Ajouter des trackers / analytics tiers** (Google Analytics,
  Plausible, etc.) sans demander explicitement. Hors-charte.
- **Ajouter des screenshots / images stock.** Si une image est
  nécessaire, c'est une image qu'Anas a produite (photo, schéma).
- **Mélanger FR et EN dans le même contenu de site.** Tout EN.
- **Inventer des chiffres, des clients, des dates.** Si un fait est
  flou (combien de Design Sprints, quels clients, quel secteur),
  **demander** avant d'écrire. Une approximation inventée tue la
  crédibilité plus vite qu'un trou assumé.
- **Glisser vers le solution-shaped writing.** Le site enseigne la
  discipline opposée. Ne pas écrire "I help you do X" si tu n'as pas
  d'abord cadré pourquoi le lecteur ferait X.
- **Push direct sur GitHub depuis ta session.** Laisse Anas pousser.

# Backlog / chantiers identifiés

- [ ] Push initial sur `github.com/anasdox/anasdox.github.io` (Anas)
- [ ] Settings GH Pages : Source = `main` / `/ (root)` (Anas, post-push)
- [ ] Open Graph image (pour aperçu LinkedIn / partage) — TODO Anas
- [ ] Custom domain `anasameziane.com` (optionnel, future) avec
      `CNAME` file + DNS A records vers GH Pages IPs
- [ ] Posts de blog à venir candidats :
  - *Five whys, in real life*
  - *Why we ditched the glossary and started shipping a ubiquitous language instead*
  - *How I write a functional specification*
  - *A Design Sprint that ended with "the problem you brought us is not the one we found"*
  - *Leverage points in a transformation engagement*
- [ ] Décider si une page `/talks/` ou `/writing/` long-form est utile
      (pas avant qu'il y ait de la matière)

# Mémoire d'identité (Anas)

Anas Ameziane, basé Cesson-Sévigné (Bretagne). FR + AR natifs, EN
professionnel, ES élémentaire. Ingénieur ENI Brest (2003-2007), GCP
Core Infrastructure certifié.

Parcours condensé :
- 2022-présent : Team Leader BM.SYS.CORE chez OVHcloud (Rennes)
- 2020-2022 : Co-founder & CEO Placemeet (SaaS events online)
- 2019 : Founder ozzo.io (algo-trading évolutif)
- 2018-2019 : Solution Architect / DevOps chez Follow
- 2014-2018 : Solution Architect / VP of Engineering chez Niji
  (consulting DevOps + transformation Agile, **avant-ventes
  clients**, design sprints, analyse systémique sur les chantiers de
  transformation)
- 2007-2014 : Lead Dev + automation chez SII (Orange, Ouest-France,
  Envivio, France Telecom R&D)

GitHub : `anasdox`. LinkedIn :
`linkedin.com/in/anasameziane-199b5058`. Email :
`anas.ameziane@gmail.com`.

Pour le détail complet du parcours, demander à Anas en début de
session — ne pas dupliquer ici, juste le rappel identitaire.
