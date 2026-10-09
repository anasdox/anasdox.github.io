---
title: "Les agents ont rendu le BDD rentable. Pas délégable."
date: 2026-10-09
topic: specification
tags: [agentic, validation]
description: "Le BDD mourait de son coût d'écriture et de maintenance. Les agents l'ont effondré. Le seul geste qu'ils ne font pas à votre place : signer le scénario."
---

En montant [bdd-with-ai](https://github.com/anasdox/bdd-with-ai), un
dépôt où des agents travaillent à partir de scénarios de comportement,
j'ai vu deux choses qui semblaient se contredire.

La première : un agent m'a proposé un scénario d'erreur auquel
personne n'avait pensé. Un vrai cas, que nous aurions découvert en
production.

La seconde : un agent dont le code ne passait pas un scénario n'a pas
corrigé son code. Il a modifié le scénario. Les tests sont passés au
vert.

Ce sont les deux faces du même constat. Les agents rendent le BDD
enfin abordable. Ils peuvent aussi le vider de son sens en une
modification.

### Pourquoi le BDD mourait

Le Behavior-Driven Development n'a jamais eu de problème d'idée.
Décrire le comportement attendu avant d'écrire le code, dans une
langue que le métier peut relire : personne ne conteste le principe.

Il avait un problème d'addition. Écrire les scénarios prenait du
temps. Écrire le code de liaison entre les phrases Gherkin et le
système en prenait davantage. Et surtout, il fallait tout maintenir :
chaque évolution du produit cassait des étapes, dupliquait des
phrases, laissait des scénarios décrire un comportement qui n'existait
plus.

Je l'ai vu de près. La discipline tenait tant que l'équipe avait du
temps. Au premier
sprint sous tension, les scénarios passaient en «&nbsp;on rattrapera
après&nbsp;». On ne rattrapait pas. Le dossier `features/` devenait un
musée.

### Ce que les agents changent dans l'addition

Presque toutes les lignes de cette addition sont du travail qu'un
agent fait bien et vite :

- rédiger un premier jet de scénarios à partir d'un besoin décrit en
  quelques paragraphes ;
- proposer les cas que personne n'a écrits, en particulier les
  chemins d'erreur ;
- générer et maintenir le code de liaison des étapes ;
- repérer les phrases dupliquées et les scénarios qui se recouvrent ;
- remettre les étapes d'aplomb quand le système évolue.

Prenons un scénario simple :

```gherkin
Feature: Import de réservations

  Scenario: Les lignes valides sont enregistrées
    Given un fichier de 3 000 réservations dont 12 invalides
    When l'opératrice dépose le fichier
    Then les 2 988 lignes valides sont enregistrées
    And les 12 lignes invalides sont signalées
```

Demandez à un agent ce qui manque, il revient avec des questions
utiles. Que se passe-t-il si le même fichier est déposé deux fois ?
Si toutes les lignes sont invalides ? Si le fichier est vide ? Chacune
est un scénario que l'équipe aurait dû écrire, et qu'elle découvrait
d'habitude en production.

Le coût marginal d'un scénario s'est effondré. L'argument «&nbsp;on n'a
pas le temps&nbsp;» ne tient plus. C'est la bonne nouvelle, et elle est
réelle.

### Le piège : le contrat qui se signe tout seul

La tentation suivante est logique : si l'agent écrit les scénarios, le
code de liaison et l'implémentation, pourquoi ne pas lui laisser toute
la chaîne ? On décrit le besoin, l'agent produit le reste, les tests
passent.

À ce moment-là, le BDD ne sert plus à rien. Un scénario n'a de valeur
que parce qu'il est écrit **indépendamment** du code qu'il juge. Si la
même main rédige la règle et ce qui la satisfait, le vert ne prouve
qu'une chose : l'agent est d'accord avec lui-même. Il vous a fallu une
minute pour obtenir un contrat circulaire.

C'est pire qu'un manque de tests, parce que ça y ressemble. La colonne
est remplie, les scénarios sont bien écrits, le rapport est vert. Rien
de tout ça ne dit si le comportement est celui que le métier attendait.

### Proposer n'est pas décider

La répartition qui tient est simple à énoncer :

- **L'agent propose.** Premier jet, cas manquants, reformulations,
  détection de doublons. Il est meilleur que moi pour l'exhaustivité.
- **L'humain décide.** Je relis les scénarios, je tranche les
  questions ouvertes avec les personnes qui vivront avec la
  fonctionnalité, et je fige le contrat avant que l'implémentation
  commence.
- **Le contrat ne bouge plus pendant l'implémentation.** Si l'agent a
  besoin de modifier un scénario pour faire passer son code, c'est un
  signal d'alerte, pas une correction. Soit le scénario était faux, et
  c'est une décision humaine de le changer. Soit le code est faux, et
  le scénario vient de faire son travail.

Concrètement, ça veut dire que les scénarios et le code n'arrivent pas
dans la même relecture. Les scénarios sont relus et validés d'abord,
sur leur propre changement. Le code vient ensuite, et se juge contre
eux.

### Documentation vivante, à une condition

On dit souvent que les fichiers Gherkin deviennent une documentation
qui ne pourrit plus, puisque l'agent peut la tenir à jour. C'est vrai
à une condition : que chaque scénario puisse **échouer** le jour où le
comportement disparaît. Un scénario dont les étapes ne vérifient rien
documente une intention, pas le système. Il est même plus dangereux
qu'une page obsolète, parce qu'il est vert.

L'agent rend la maintenance gratuite. Il ne rend pas la vérification
automatique. C'est à vous de vous assurer que le vert veut encore dire
quelque chose.

### Ce qui a changé, et ce qui n'a pas changé

Ce qui a changé : écrire et maintenir des scénarios ne coûte presque
plus rien. Le BDD n'a plus d'excuse économique pour être abandonné.

Ce qui n'a pas changé : quelqu'un doit dire ce que «&nbsp;correct&nbsp;»
veut dire pour ce logiciel, et en répondre. Ce geste-là ne se délègue
pas. Les agents ont rendu le BDD rentable. Ils l'ont rendu plus
important à signer, pas plus facile à abandonner.

La boucle que j'utilise au quotidien est décrite dans
[Quand l'agent livre plus vite que je ne lis]({{ '/quand-l-agent-livre-plus-vite-que-je-ne-lis/' | relative_url }}),
et la place du BDD dans le cadrage d'un problème sur la page
[Méthode]({{ '/methode/' | relative_url }}). Le modèle de dépôt est sur
[github.com/anasdox/bdd-with-ai](https://github.com/anasdox/bdd-with-ai).
