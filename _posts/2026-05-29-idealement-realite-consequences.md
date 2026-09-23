---
title: "Idéalement, Réalité, Conséquences"
date: 2026-05-29
translation_key: irc
topic: specification
tags: [discovery]
description: "Trois sections obligatoires dans chaque epic, et aucune n'a le droit de contenir une solution. Pourquoi le mur entre problème et solution protège l'ingénieur en aval."
---

Chaque epic que mon équipe écrit porte une description en trois
sections obligatoires, et un petit linter la rejette quand l'une
manque. Les sections sont toujours les mêmes, toujours dans le même
ordre : Idéalement, Réalité, Conséquences. Aucune des trois n'a le
droit de contenir une solution.

Cette dernière règle est tout l'enjeu. Le pattern n'est pas un modèle
pour écrire des tickets plus vite. C'est une contrainte qui force le
problème à exister sur la page avant que quiconque ait le droit de
concevoir contre lui.

### À quoi sert chaque section

**Idéalement**, c'est le monde tel qu'il devrait être. L'état qu'on
observerait si le problème n'existait pas. *«&nbsp;Tout serveur qui échoue
à un contrôle réseau automatique est réalloué sans qu'un humain y
touche.&nbsp;»* C'est la description d'une destination, écrite au présent,
sans aucune référence à la façon d'y arriver.

**Réalité**, c'est le monde tel qu'il est aujourd'hui. L'écart.
*«&nbsp;Aujourd'hui le contrôle se déclenche, mais la réallocation bloque
sur une validation manuelle que personne ne porte, donc les serveurs
restent non attribués quatre jours en moyenne.&nbsp;»* C'est la section
qui doit pouvoir être vérifiée contre les faits. Si la Réalité est
floue, le problème n'est pas encore compris, et aucune conception de
solution ne le rattrapera.

**Conséquences**, c'est ce que coûte l'écart. Le «&nbsp;et alors ?&nbsp;».
*«&nbsp;Quatre jours de matériel inutilisé par incident, une escalade
récurrente vers l'astreinte, et un SLA de livraison client que nous
ratons discrètement deux fois par mois.&nbsp;»* Sans cette section, tous
les problèmes paraissent aussi urgents et rien ne peut être priorisé.
Avec elle, le lecteur peut dimensionner la chose avant d'y consacrer
une seule journée.

Trois sections, et la solution n'apparaît dans aucune. Elle vient
plus tard, dans un champ séparé, écrite par quelqu'un qui a lu les
trois.

### Pourquoi l'ordre, et pourquoi le mur

L'ordre n'est pas décoratif. On ne peut pas écrire honnêtement les
Conséquences tant que la Réalité n'est pas précise, et on ne peut pas
écrire la Réalité sans s'être engagé sur un Idéalement assez précis
pour mesurer l'écart. Chaque section porte la suivante. Sautez
Idéalement, et la Réalité devient une liste de plaintes. Sautez la
Réalité, et les Conséquences deviennent une peur.

Le mur entre le problème et la solution est la partie à laquelle les
gens résistent. Il paraît inefficace. L'auteur arrive généralement
avec une réponse déjà en main, et les trois sections ressemblent à
une cérémonie qui se dresse entre lui et le moment de l'écrire.

Mais c'est précisément le mur qui protège l'ingénieur en aval.

### Le mode d'échec qu'il empêche

Donnez à un ingénieur un ticket qui contient déjà une solution, et il
construira cette solution. Ce n'est pas de la paresse. C'est la
réponse rationnelle à une consigne claire. Le problème, c'est qu'une
solution rédigée comme un énoncé de problème n'a ni écart ni coût
attaché, donc l'ingénieur n'a rien pour la vérifier. Là où la consigne
se tait, son propre jugement comble le vide, et ce jugement est la
subjectivité d'une autre personne que celle qui a écrit le ticket. Le
résultat a l'air conforme et il est discrètement faux.

J'ai vu ça se produire assez souvent pour faire davantage confiance
au pattern qu'à ma propre discipline. Un ingénieur qui reçoit
Idéalement, Réalité, Conséquences reçoit le problème au lieu de la
réponse. Il voit la destination, l'écart et l'enjeu. Il peut alors
faire ce que j'attends vraiment de lui : concevoir la bonne réponse,
ou revenir me dire que le problème tel qu'il est formulé n'est pas le
vrai. Un ticket qui commence par une solution ferme les deux portes.

### La même discipline, un autre artefact

C'est la même règle que je retrouve dans toutes les formes de
discovery. En entretien, elle prend la forme de questions sans
solution : on interroge le problème, la douleur, le contournement,
jamais son idée. Dans une restitution écrite, elle prend la forme
Faits avant Insights avant Recommandations, la conclusion ayant
interdiction de contaminer les éléments. Dans un epic Jira, elle
prend la forme Idéalement, Réalité, Conséquences, la solution restant
hors des trois.

Des artefacts différents, un seul principe : garder le problème et la
solution dans des compartiments séparés, et écrire le problème
d'abord. Le mur entre les compartiments est bon marché à construire
et coûteux à sauter. Chaque heure passée à rendre la Réalité précise
est une heure que l'équipe ne passe pas à construire quelque chose de
précis et d'inutile.

La méthode complète est sur la page
[Méthode]({{ '/methode/' | relative_url }}). La version qui la
surplombe est plus courte :

> Passer plus de temps à comprendre le problème qu'à concevoir la solution.
