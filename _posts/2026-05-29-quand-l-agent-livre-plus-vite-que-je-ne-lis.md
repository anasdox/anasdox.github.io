---
title: "Quand l'agent livre plus vite que je ne lis"
date: 2026-05-29
translation_key: agent
topic: validation
tags: [agentic, specification, cognitive-load]
description: "Les agents de code ont réduit la construction à quelques minutes. Spécifier, valider et relire n'ont pas bougé. Pourquoi je relis désormais le comportement, pas le code."
---

L'échange se passe en général comme ça. Je décris une fonctionnalité
en deux paragraphes. L'agent revient dix minutes plus tard avec trois
mille lignes de code, un diff propre, des tests au vert et une
description de PR mieux écrite que celle que j'aurais rédigée.

Je fais défiler. Je fais encore défiler. Les tests passent. La
structure a l'air raisonnable. Le nommage respecte les conventions.
J'ai dix autres choses à faire aujourd'hui.

J'approuve.

C'est à ce moment-là que j'ai cessé d'être l'ingénieur pour devenir
le spectateur de ma propre base de code. L'agent n'a pas d'astreinte,
pas d'impact client, pas de post-mortem à redouter. Le risque n'a pas
bougé. Il est toujours à moi. Mais ma capacité à le voir vient de
chuter d'un ordre de grandeur, parce que je relis du code que je n'ai
pas écrit, contre une architecture que l'agent a déduite, dans un
budget de temps qui, lui, n'a pas changé.

J'ai commencé à le remarquer au bout de quelques mois. La première
fois, j'ai haussé les épaules. La troisième fois, mon ego l'a senti
passer.

### Le centre de gravité s'est déplacé

Le logiciel a quatre phases qui prenaient à peu près le même temps :
spécifier, construire, valider, relire. Les agents de code génératifs
ont réduit la construction à quelques minutes. Les trois autres n'ont
pas changé. Ce sont des phases humaines. Elles demandent du temps
humain, de l'attention humaine, de la bande passante humaine.

Résultat : le goulot d'étranglement a bougé, et nous non. Nous livrons
du code que personne n'a entièrement compris pendant son écriture,
dans des bases de code que personne n'a entièrement comprises en
train de l'absorber. La description honnête de ce qui se passe
ensuite, c'est : *on approuve et on passe à la suite*. Le coût d'une
approbation sans compréhension reste invisible jusqu'à l'incident.

### Le problème n'est plus «&nbsp;comment coder&nbsp;»

Le problème, c'est «&nbsp;comment garder le contrôle&nbsp;». L'agent sait
générer. Il ne peut pas endosser la responsabilité. Si c'est moi
qu'on appelle le dimanche matin, c'est moi qui dois à la base de code
un niveau d'attention que l'agent est incapable de fournir à ma place.

Écrit comme ça, ça paraît évident. Ça l'est beaucoup moins quand la
PR est au vert et que l'agent attend le prompt suivant.

### Relire le comportement, pas le code

Le changement qui a marché pour moi est celui que le Behavior-Driven
Development attendait patiemment de faire. Avant les agents
génératifs, écrire des spécifications exécutables avant le code
ressemblait à un surcoût. Les équipes écrivaient les scénarios, mais
lentement, et seulement quand la fonctionnalité était assez grosse
pour justifier la cérémonie. La discipline s'effondrait au premier
sprint sous tension.

Les agents génératifs inversent l'économie. Le code ne coûte plus
rien. La spécification du comportement est le seul artefact dont je
dois encore absorber le sens. Lire un scénario Gherkin prend trente
secondes. Lire les trois mille lignes qui l'implémentent prend une
demi-journée que je n'ai pas.

L'unité de relecture est donc remontée d'un niveau. Je consacre
désormais mon attention à cinq à dix scénarios à la fois, écrits dans
le langage omniprésent (*ubiquitous language*) du projet, validés par
les personnes qui vivront avec la fonctionnalité. L'agent implémente
ensuite, lance les tests, itère jusqu'à ce qu'ils passent, montre le
résultat, et attend.

La charge cognitive baisse, parce que les artefacts que je lis sont
courts et porteurs de sens. Le contrôle augmente, parce que rien
n'atteint la base de code sans avoir survécu à un contrat de
comportement que j'ai réellement compris. La qualité augmente, parce
que le contrat est aussi la suite de non-régression.

### À quoi ressemble la boucle

La forme de la boucle est toujours la même. J'écris une description
de fonctionnalité avec trois à dix scénarios au format
Given-When-Then. L'agent génère l'échafaudage de tests à partir des
scénarios, et je relis cet échafaudage. L'agent génère le code de
production qui fait passer les tests. Je relis le résultat au regard
des scénarios, pas du diff ligne à ligne. L'agent montre le
comportement en fonctionnement. Je valide, ou j'affine les scénarios
et on repart pour un tour.

{::nomarkdown}
<div class="mermaid">
flowchart TD
  Start(["Description, 3 à 10 scénarios"]) --> Scaffold["Agent : échafaudage de tests"]
  Scaffold --> ReviewSpec{"Humain : les tests reflètent les scénarios ?"}
  ReviewSpec -- non --> Start
  ReviewSpec -- oui --> Implement["Agent : code de production"]
  Implement --> Run["Agent : lance les tests, itère"]
  Run --> Demo["Agent : montre le comportement"]
  Demo --> Validate{"Humain : comportement correct ?"}
  Validate -- non --> Start
  Validate -- oui --> Done(["Validation"])
</div>
{:/nomarkdown}

Ce que je fais dans cette boucle, c'est ce que j'ai toujours fait
comme ingénieur : décider de ce que «&nbsp;correct&nbsp;» veut dire pour ce
logiciel, dans une langue qu'une partie prenante peut lire. Ce qui a
changé, c'est que j'ai cessé de passer l'essentiel de ma journée dans
l'éditeur qui produit le code, pour la passer dans le document qui
décide de ce que le code doit faire.

L'agent a livré l'implémentation. J'ai livré le contrat. C'est la
division du travail que je veux pour les bases de code dont je serai
responsable dans deux ans.

Le modèle de dépôt que j'utilise comme point de départ est sur
[github.com/anasdox/bdd-with-ai](https://github.com/anasdox/bdd-with-ai).
L'explication plus longue de la place centrale des spécifications de
comportement dans ma façon de travailler est sur la page
[Méthode]({{ '/methode/' | relative_url }}).
