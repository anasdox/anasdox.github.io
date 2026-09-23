---
layout: page
title: Méthode
eyebrow: La moitié amont
permalink: /methode/
redirect_from:
  - /method/
subtitle: >-
  Tout ce qui se passe avant que l'agent écrive la première ligne.
description: >-
  La méthode de cadrage derrière l'AI-Native Product Engineering :
  entretien sans biais, FIR (Faits, Insights, Recommandations), Design
  Sprint, analyse systémique, langage omniprésent, BDD et spécification
  fonctionnelle comme contrat.
cta: true
---

Cette page décrit la moitié amont de l'AI-Native Product Engineering.
Je l'ai construite avant les agents, sur des années de conseil, de
produit et d'équipes d'ingénierie. Elle compte davantage depuis : quand
le code ne coûte presque plus rien, une erreur de cadrage est
implémentée en quelques minutes, et elle a l'air aussi propre que le
reste.

---

Une équipe logicielle a deux façons d'échouer.

La première est technique. Le build casse, la base de données
s'effondre, l'API renvoie la mauvaise forme. Ces échecs sont visibles,
douloureux, et solubles. Tous les ingénieurs avec qui j'ai travaillé
ont des outils pour les traiter.

La seconde est invisible. L'équipe livre exactement ce qui a été
demandé, exactement à l'heure, et personne ne s'en sert. Ou le client
s'en sert et il est discrètement déçu. Ou six mois plus tard, un
nouveau besoin révèle que la mauvaise abstraction a été gravée dans le
schéma. Ces échecs ne sont pas techniques. Ce sont des échecs de
cadrage. Ils étaient écrits dans les exigences bien avant que la
moindre ligne de code soit touchée.

J'ai passé l'essentiel de ma carrière sur ce second mode d'échec. Voici
ce que j'en ai appris.

> Passer plus de temps à comprendre le problème qu'à concevoir la solution.

C'est la seule règle. Tout ce qui suit est une façon de s'y tenir.

## 1. L'art de l'entretien sans biais

La discovery commence par une conversation, et la plupart des
conversations d'ingénierie penchent discrètement vers la réponse que
l'intervieweur a déjà en tête. Le biais est rarement délibéré. Il est
dans la forme des questions.

Une question en forme de solution appelle une réponse en forme de
solution. *«&nbsp;Est-ce que ça vous aiderait d'avoir un bouton qui exporte
le rapport ?&nbsp;»* présuppose un bouton, un export et un rapport.
L'interlocuteur, soucieux d'être utile, dit oui. Vous n'avez pas appris
ce qu'il fait réellement des données. Vous avez appris qu'il ne
refusera pas un bouton.

L'entretien sans biais est une discipline :

- **Des questions ouvertes plutôt que fermées.** *«&nbsp;Racontez-moi la
  dernière fois que vous en avez eu besoin.&nbsp;»* et non *«&nbsp;Vous en avez
  besoin chaque semaine ?&nbsp;»*
- **Pas de mots qui orientent.** Bannir *«&nbsp;évidemment&nbsp;»*, *«&nbsp;facile&nbsp;»*,
  *«&nbsp;juste&nbsp;»*, *«&nbsp;vous ne pensez pas que&nbsp;»*. Chacun fait pencher la
  pièce.
- **Des formulations sans solution.** Interroger le problème, la
  douleur, le contournement. Jamais votre idée. Si l'interlocuteur
  propose une solution, notez-la et continuez à interroger le problème.
- **Les cinq pourquoi.** La première réponse est presque toujours la
  surface. Continuez jusqu'à atteindre une contrainte, une peur ou un
  fait économique.
- **Le silence comme outil.** Les gens remplissent le silence avec ce
  qu'ils n'avaient pas prévu de dire. Attendez trois secondes de plus
  avant la question suivante.

Le produit d'un bon entretien n'est pas un accord. C'est une image du
problème plus riche que celle que chacun avait au départ.

## 2. FIR : une structure pour ce qu'on a entendu

Après l'entretien vient le piège : l'envie de proposer immédiatement
une solution. La protection contre ce piège, c'est d'écrire ce qu'on a
entendu, en trois couches séparées, sans en sauter aucune.

{::nomarkdown}
<div class="mermaid">
flowchart LR
  F["Faits (observables)"] --> I["Insights (interprétatifs)"] --> R["Recommandations (actionnables)"]
</div>
{:/nomarkdown}

### Faits

Ce qui a réellement été dit ou observé, avec les mots de la personne.
Pas de paraphrase, pas d'interprétation. *«&nbsp;Marion traite le fichier
des réservations chaque lundi matin. Elle utilise Excel. Le fichier
compte entre 2 000 et 5 000 lignes. Elle m'a dit qu'elle reste tard le
lundi.&nbsp;»*

Les Faits sont la seule couche qu'on peut vérifier contre la réalité.

### Insights

Ce que signifient les faits quand on les lit ensemble. Des motifs, des
contradictions, des manques, des surprises. *«&nbsp;La charge de Marion
double le lundi, mais le plan de capacité de l'équipe traite tous les
jours de la même façon. La nature manuelle du travail explique les
soirées tardives, et personne n'a jamais calculé le coût de ces heures
supplémentaires.&nbsp;»*

Les Insights sont une interprétation. Ils sont réfutables. Un second
auditeur peut ne pas être d'accord, et ce désaccord est productif.

### Recommandations

Les actions qui découlent des insights. *«&nbsp;Automatiser la validation
ligne à ligne du fichier. Faire apparaître la vraie charge du lundi
dans le plan de capacité. Mesurer le coût des heures supplémentaires
avant de décider si l'automatisation se rentabilise.&nbsp;»*

Les Recommandations sont bon marché et jetables. C'est la partie du
travail sur laquelle on se dispute le plus, et c'est très bien, parce
que les Faits et les Insights en dessous sont solides.

La discipline consiste à **ne jamais sauter une couche**. Des
Recommandations sans Insights sont des opinions. Des Insights sans
Faits sont des suppositions.

## 3. Le Design Sprint comme cadrage collectif

Le couple entretien et FIR est fait pour l'écoute en tête-à-tête. Il y
a des moments où c'est le mauvais outil : quand dix parties prenantes
portent dix modèles mentaux du même problème, quand l'agenda ne
survivra pas à quinze séances de discovery successives, quand la
décision est assez politique pour que personne ne s'engage en privé
sur ce qu'il assumerait en public.

Dans ces moments-là, j'anime un Design Sprint. La structure d'origine
sur cinq jours (Map, Sketch, Decide, Prototype, Test) est celle que
j'ai le plus souvent utilisée avec des clients, adaptée aux contraintes
de chaque engagement.

{::nomarkdown}
<div class="mermaid">
flowchart LR
  Map["Jour 1 : Map"] --> Sketch["Jour 2 : Sketch"] --> Decide["Jour 3 : Decide"] --> Proto["Jour 4 : Prototype"] --> Test["Jour 5 : Test"]
</div>
{:/nomarkdown}

Le résultat qui compte est rarement le prototype. Le prototype est une
fonction de forçage : il oblige la salle à s'engager sur une seule
formulation partagée du problème, parce qu'on ne peut pas prototyper
une ambiguïté. Au milieu de la semaine, la salle sait quel est le
problème, d'une manière qu'aucun atelier précédent n'avait produite. La
séance de test utilisateurs à la fin devient alors une discipline :
confronter cette compréhension partagée à de vrais utilisateurs, et
découvrir quelles parties ils ne partageaient pas, en réalité.

J'ai animé des sprints de ce type pour plusieurs clients dans
différents secteurs. Ceux qui ont le mieux marché sont ceux où le
sponsor avait accepté, à l'avance, que la réponse puisse être : *«&nbsp;le
problème que vous nous avez apporté n'est pas celui que nous avons
trouvé.&nbsp;»* Cet engagement préalable est plus difficile que les cinq
jours.

## 4. L'analyse systémique quand le problème, c'est le système

Certains problèmes ne survivent pas à un exercice de cadrage ponctuel,
aussi bon que soit l'entretien. Le bug revient sans cesse. L'équipe
s'épuise sans cesse. Le client part sans cesse. Chaque correction
fonctionne isolément, et l'ensemble empire.

Quand ce motif apparaît, l'unité d'analyse n'est plus la
fonctionnalité. C'est le système : les acteurs, les flux entre eux, les
stocks qui s'accumulent ou s'épuisent, et les boucles de rétroaction
qui les renforcent ou les équilibrent. Le vocabulaire vient de la
pensée systémique (Senge, Meadows, Forrester), et la question
diagnostique est celle que Donella Meadows a rendue célèbre : *où sont
les points de levier*.

J'ai mené des chantiers de transformation où le périmètre technique
était visible mais la cause structurelle ne l'était pas. Le motif
récurrent était le même : l'équipe optimisait depuis des années un
point de faible levier (un nouvel outil, un nouveau processus, un
nouveau rituel), et la structure des incitations en amont annulait
chaque optimisation en moins d'un trimestre.

{::nomarkdown}
<div class="mermaid">
flowchart LR
  Struct["Structure (incitations, flux)"] --> Loop["Boucle de rétroaction"] --> Sym["Symptôme (ce qui fait mal)"]
</div>
{:/nomarkdown}

C'est en lisant de droite à gauche qu'on trouve le levier : le
symptôme est bruyant mais peu rentable à pousser, la structure est
silencieuse mais c'est le seul endroit où une poussée se cumule.

L'analyse systémique est la même discipline d'écoute que l'entretien,
appliquée à un autre objet. On pose le même genre de questions, on
écrit les Faits avant les Insights, mais les Faits portent sur des flux
et des boucles plutôt que sur des fonctionnalités, et les Insights
portent sur la structure qui produit les symptômes. Les
recommandations disent alors où pousser dans la structure, pas quel
symptôme étouffer.

Sans cette lentille, les chantiers de transformation se contentent par
défaut de renommer les problèmes au lieu de les résoudre. Avec elle, le
chantier devient beaucoup plus petit en périmètre et beaucoup plus
inconfortable en conclusion, ce qui me paraît être la bonne forme.

## 5. Le langage omniprésent comme test

Quand l'équipe et le métier peuvent se disputer sur une fonctionnalité
avec les mêmes mots, vous avez compris le problème. Quand les
ingénieurs traduisent en silence chaque mot métier en un autre mot
d'ingénierie, vous ne l'avez pas compris.

C'est le diagnostic d'Eric Evans dans *Domain-Driven Design*, et c'est
le signal le plus fiable que je connaisse en discovery logicielle.

> Si la conversation au stand-up utilise des mots qu'on ne reconnaîtrait
> pas en revue client, le modèle n'est pas partagé.

Le langage omniprésent (*ubiquitous language*) n'est pas un glossaire.
Un glossaire, c'est ce qu'on écrit pour *faire semblant* que la langue
est partagée. La langue est réelle quand on entend un ingénieur
corriger un product manager sur une distinction fine, dans le
vocabulaire du product manager lui-même, et que le product manager
acquiesce.

Je le traite comme une fonction de forçage. Si l'équipe ne trouve pas
un seul mot pour un concept, le concept n'est pas encore stable. Tant
qu'il ne l'est pas : pas de schéma, pas d'API, pas de migration.

## 6. La spécification exécutable (BDD)

Le Behavior-Driven Development n'est pas un framework de test. C'est
une technique de discovery qui se trouve produire des tests.

L'artefact est une phrase en trois parties : *étant donné* un contexte,
*quand* un événement se produit, *alors* un résultat est attendu.
Chaque partie doit être assez précise pour qu'un ingénieur puisse la
construire et qu'un responsable métier puisse la valider.

```
Étant donné un fichier de réservations de 3 000 lignes dont 12 invalides,
quand Marion dépose le fichier le lundi à 09:00,
alors le système signale les 12 lignes invalides en moins de 30 secondes
et enregistre les 2 988 lignes valides dans l'inventaire.
```

La première fois qu'une équipe écrit des spécifications de ce type, la
moitié se révèlent impossibles à écrire. Les chiffres ne sont pas
connus. Les cas limites n'ont jamais été discutés. Le comportement
attendu était supposé. C'est toute la valeur de l'exercice : le BDD
rend bruyants les trous de votre compréhension.

L'artefact est relisible par le métier et exécutable par les
ingénieurs. Il survit à la réunion. Il survit à la rotation de
l'équipe. C'est la meilleure spécification fonctionnelle que j'aie
jamais livrée.

Avec des agents, il devient aussi l'unité de relecture : on ne relit
plus les trois mille lignes, on relit les scénarios qu'elles doivent
satisfaire. C'est le sujet de
[Quand l'agent livre plus vite que je ne lis]({{ '/quand-l-agent-livre-plus-vite-que-je-ne-lis/' | relative_url }}).

## 7. La spécification fonctionnelle comme contrat

Tout ce qui précède produit un livrable tangible : une spécification
fonctionnelle qui porte la compréhension partagée. Elle contient les
faits observés, les insights tirés, les recommandations retenues, le
langage omniprésent sur lequel on s'est accordé, et les scénarios
exécutables qui le testent.

Ce document n'est pas une liste de souhaits. C'est un contrat : entre
le métier et l'ingénierie, et contre votre propre futur. Quand l'équipe
change ou que le produit évolue, la spec est ce qui protège
l'intention d'origine contre sa réécriture silencieuse par celui qui se
trouve dans la pièce ensuite.

Une bonne spécification est courte. Elle est précise sur ce qui est
dans le périmètre, honnête sur ce qui en est exclu, et claire sur ce à
quoi ressemble le succès. Elle est éditable, versionnée, et relue comme
du code.

## Comment je l'applique

Un engagement de cadrage, quand j'en mène un, a toujours la même forme.
Je m'assois avec trois ou quatre parties prenantes, en séances
séparées, et je leur demande de me raconter leur travail. J'écoute les
mots qu'elles emploient, les moments où elles hésitent, les
contournements dont elles s'excusent. Je prends des notes uniquement
dans la couche des Faits.

Entre les séances, j'écris les Insights. Des motifs apparaissent. Deux
parties prenantes utilisent le même mot pour des choses différentes, ou
des mots différents pour la même chose. Le modèle mental que l'équipe a
de son propre processus se révèle troué.

Au moment où je propose des recommandations, le métier a fait
l'essentiel du travail de convergence lui-même, en entendant ses
propres Faits relus devant lui. Les recommandations sont rarement le
goulot. Le cadrage, si.

Les outils open source qui encodent cette méthode sont dans le
[Labo]({{ '/labo/' | relative_url }}).
