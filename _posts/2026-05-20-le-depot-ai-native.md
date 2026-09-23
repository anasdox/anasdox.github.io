---
title: "Le dépôt AI-native"
date: 2026-05-20
translation_key: context-repo
topic: context
tags: [agentic]
description: "Les assistants de code IA échouent moins à cause du modèle qu'à cause du dépôt. Ce que doit contenir le contrat de contexte posé à la racine d'un repo."
---

La plupart des ingénieurs avec qui je parle d'assistants de code IA
décrivent le même arc : quelques démos impressionnantes, puis une
longue traîne de frustration. Le modèle hallucine une fonction qui
n'existe pas, suggère une API dépréciée, ou réécrit un fichier qui
marchait avec une version légèrement moins bonne de lui-même.

La réponse habituelle est d'accuser le modèle. Je pense que le modèle
va généralement bien. C'est le dépôt qui pose problème.

### Le dépôt comme contexte

Un grand modèle de langage n'a pas accès à l'intuition de votre
équipe. Il n'a aucun souvenir de la revue d'architecture du trimestre
dernier, aucune idée de l'abstraction qui porte la charge, aucun
indice que `customfield_12320` signifie «&nbsp;Acceptance Criteria&nbsp;» dans
votre instance Jira. Chaque interaction démarre à froid.

Si vous voulez que le modèle soit utile, vous devez écrire cette
intuition. Pas sous forme de commentaires éparpillés dans le code,
mais comme un contrat de premier niveau que le modèle peut lire d'une
traite. Dans mes propres dépôts, il vit dans un fichier appelé
`CLAUDE.md`, placé par convention à la racine. C'est la première
chose que lit le modèle, et c'est la différence entre un modèle qui
aide et un modèle qui livre du code cassé.

### Ce qu'on y met

Trois choses, par ordre d'importance :

1. **La posture.** Qui est l'utilisateur, ce qu'il cherche à
   accomplir, et quelle voix le modèle doit adopter pour lui
   répondre. Pas du vernis sur le ton : de vrais garde-fous. «&nbsp;Fais
   remonter les risques clairement. Propose des décisions, pas des
   constats. Bref, direct.&nbsp;»

2. **Les conventions.** Les choses non évidentes. Où vivent
   réellement les critères d'acceptation. Quels champs sont
   modifiables par quelle API. Quels types de liens sont de vraies
   dépendances et lesquels sont des anti-patterns. Chaque morceau de
   savoir tribal qu'un nouvel ingénieur apprendrait pendant son
   premier mois.

3. **Les anti-patterns à refuser.** Les erreurs que j'ai vu le modèle
   faire deux fois. Pas comme des suggestions, comme des règles.
   «&nbsp;N'affiche jamais un lien Jira sous la forme `Blocks <- X`, le
   sens est ambigu. Rends toujours le verbe complet, du point de vue
   du ticket interrogé.&nbsp;»

Ce fichier est modifié chaque fois que le modèle se trompe d'une
nouvelle façon. Au fil des mois, il prend la même texture que la
mémoire de travail d'un ingénieur senior, sauf qu'elle est partagée,
versionnée, et rechargée à chaque prompt.

### Le levier

Le levier, ce n'est pas que le modèle écrive plus de code. C'est
qu'il écrive du code qui s'intègre. Les pull requests rétrécissent.
Les revues accélèrent. Ce qui demandait un échange Slack de quinze
minutes se règle désormais dans le prompt lui-même.

Je n'appellerais pas ça un gain de productivité. J'appellerais ça une
montée en gamme de la collaboration.
