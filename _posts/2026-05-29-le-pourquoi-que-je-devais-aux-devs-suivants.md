---
title: "Le pourquoi que je devais aux devs suivants"
date: 2026-05-29
translation_key: why
topic: discovery
tags: [specification]
description: "Ce que je devais aux développeurs qui liraient mes specs, et pourquoi Faits, Insights, Recommandations est la structure à laquelle je confie le pourquoi."
---

Pendant la première moitié de ma carrière, j'étais le développeur en
bout de chaîne. Une fonctionnalité atterrissait sur mon bureau, avec
une spec, une échéance, parfois un ticket Jira et un lien Figma. Ce
qu'elle n'apportait jamais, c'était la réponse à la question que je
posais sans cesse : *pourquoi est-ce qu'on construit ça ?*

Je ne parle pas du «&nbsp;quel problème business ça résout&nbsp;» sous la forme
polie qui finit sur une slide. Je parle de : qui souffre, qu'est-ce
qu'ils ont réellement dit, qu'est-ce qu'on a observé, qu'est-ce qui
nous a fait choisir cette option plutôt que les trois autres.
L'information qui m'aurait permis de réagir quand un cas limite du
design contredisait discrètement l'intention apparente.
L'information qui m'aurait permis de trancher un petit arbitrage sans
escalader.

Chaque fois que je creusais pour trouver cette information, l'une de
deux choses s'avérait vraie. Soit le problème avait été mal identifié
en amont, et la spec était le produit poli d'une conversation floue
dont personne ne se souvenait vraiment. Soit l'information existait,
quelque part : dans la tête d'un product manager, dans la marge d'un
deck, dans le compte rendu d'une réunion à laquelle je n'avais pas
accès. Et y accéder coûtait plus de capital politique que la question
n'en valait.

Alors je construisais la fonctionnalité avec le signal dont je
disposais. La plupart du temps elle était livrée, utilisée, et ça
allait. Parfois, un an plus tard, on découvrait qu'on avait construit
précisément la mauvaise chose, et personne n'arrivait vraiment à
reconstituer comment on en était arrivé là.

---

Des années plus tard, j'ai changé de côté. Je suis devenu architecte
solutions en avant-vente : dans la salle avec le client, à cadrer le
problème, concevoir la réponse, puis passer la main à l'équipe de
delivery pour la construire. Pour la première fois, c'était moi qui
écrivais la spec que le dev suivant lirait.

J'avais une promesse très précise à tenir : ne pas faire à ces devs
ce qu'on m'avait fait.

Cette promesse paraît évidente. En pratique, elle est plus difficile
qu'elle n'en a l'air. La pression sur l'architecte pousse à
compresser : une recommandation nette, un effort estimé, un schéma
propre. Elle pousse à retirer le bruit, les contradictions, les
non-dits de la discovery, parce que la proposition doit paraître
décidée. Chaque gramme de compression rend la vie du dev suivant plus
difficile.

Il me fallait une discipline qui me permette de compresser la
conclusion sans compresser la piste.

---

La discipline vers laquelle j'ai convergé s'appelle FIR : Faits,
Insights, Recommandations. Chaque couche est écrite séparément, et
chaque conclusion d'une couche doit citer les éléments de la couche
du dessous.

**Les Faits** sont ce qui a réellement été dit ou observé pendant la
discovery. Les mots mêmes de l'utilisateur. La capture d'écran du
reçu cassé. Le chiffre sur le tableau de bord. Aucune paraphrase.

**Les Insights** sont ce que signifient les Faits quand on en lit
plusieurs ensemble. Des motifs, des contradictions, des manques.
Chaque Insight référence les Faits qu'il interprète. Un second
lecteur peut ne pas être d'accord, et ce désaccord est fondé.

**Les Recommandations** sont ce qu'il faut faire. Chaque
Recommandation référence les Insights dont elle découle.

L'intérêt de la structure n'est pas son élégance. L'intérêt, c'est
que le dev qui reprend la spec six semaines plus tard, dans un autre
fuseau horaire, peut remonter d'une recommandation à l'insight qui la
porte, et de cet insight à une phrase que quelqu'un a réellement
prononcée. Le pourquoi n'est plus dans la tête de l'architecte. Il est
dans la chaîne.

La variante que j'utilise aujourd'hui au quotidien s'appelle Atomic
Research. Mêmes trois couches, mais les expériences qui produisent
les faits (entretiens, sessions d'observation, sondages, données
brutes) y sont traitées comme des objets à part entière de la
structure. J'ai formalisé cette méthodologie pour la pratique de
discovery de mon employeur actuel, pour que la piste ne dépende pas
de ma présence ou non en réunion.

---

Ce que je n'ai pas compris pendant des années, c'est que la structure
ne survit pas à un document ordinaire. Les slides inversent la
hiérarchie : la recommandation en titre, les faits en note de bas de
page. Les tables Notion laissent tout atterrir dans une seule colonne
Notes. Excel pardonne toutes les colonnes qu'on n'utilise pas. Les
trois couches survivent à la première séance. Elles ne survivent pas
à la troisième.

Alors j'ai construit [factly](https://github.com/anasdox/factly), un
petit espace de travail où les colonnes ne sont pas optionnelles. Les
entrées à gauche, puis les Faits, puis les Insights, puis les
Recommandations, puis les livrables. Chaque élément pointe vers ce
dont il dépend. Un Insight sans Fait n'existe pas dans la grille. Une
Recommandation sans Insight n'existe pas dans la grille. Le dev qui
lit le livrable peut suivre le fil jusqu'à l'observation d'origine.
La discipline devient mécanique, et c'est la seule façon pour elle de
survivre à un long trimestre.

---

Je ne suis pas naïf. Beaucoup d'engagements livrent encore une
recommandation soignée et très peu de piste. Mais sur ceux où la
piste a survécu, les devs suivants ont posé des questions plus
tranchantes, pris de meilleures décisions locales, et contesté des
choses que le cadrage d'origine avait mal comprises. C'est le seul
résultat qui comptait pour moi depuis le jour où j'ai changé de côté.

La méthode complète est sur la page
[Méthode]({{ '/methode/' | relative_url }}). La version que je relis
en tête de chaque restitution est plus courte :

> Passer plus de temps à comprendre le problème qu'à concevoir la solution.
