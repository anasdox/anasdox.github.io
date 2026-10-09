---
title: "L'IA produit le code en dix minutes. Votre CI a-t-elle suivi ?"
date: 2026-10-09
translation_key: ci-cadence
topic: validation
tags: [agentic, shipping, specification]
description: "Les agents accélèrent le code. Le cycle de livraison ne raccourcit que si la chaîne de validation absorbe la cadence. Sinon, la file d'attente se déplace."
---

Un problème en production. Pour comprendre ce qui se passe, il faut
ajouter des logs. Quelques lignes, qu'un agent écrit en une minute.

Sauf qu'ajouter des logs, c'est modifier le code. Modifier le code,
c'est relancer les tests fonctionnels. Et les tests fonctionnels ne
tournaient pas en parallèle : une heure de CI. Une heure pendant
laquelle la production reste bloquée, sans le moindre indice
supplémentaire.

L'autre option était de sauter la CI. Ce n'est pas mieux : c'est
exactement comme ça qu'on crée une régression en essayant de réparer
un incident.

Le code était prêt en une minute. La confiance dans ce code coûtait
une heure. Faites le compte sur votre propre chaîne : la revue qui
attend le lendemain, le déploiement réservé au jeudi matin, de
préférence quand Mercure n'est pas rétrograde. L'agent gagne des
heures sur l'implémentation. Le cycle complet, lui, ne bouge pas.

### Le goulot a encore changé de place

Dans [un article précédent]({{ '/quand-l-agent-livre-plus-vite-que-je-ne-lis/' | relative_url }}),
j'écrivais que les agents ont réduit la construction à quelques
minutes, et que le goulot était passé à la relecture. Puis que
[le BDD]({{ '/les-agents-ont-rendu-le-bdd-rentable-pas-delegable/' | relative_url }})
permet de définir ce qui doit être vrai, et de relire des scénarios
plutôt que des diffs.

La suite est mécanique. Si le code coûte moins cher et que le contrat
est clair, la question devient : en combien de temps peut-on vérifier
que le code respecte le contrat, et le mettre en production sans
risque ? C'est le travail de la CI/CD. Et elle n'a pas été conçue pour
cette cadence.

L'IA accélère la production du code. La CI/CD doit accélérer la
confiance. Si elle ne le fait pas, l'accélération reste en amont, sous
forme de branches qui attendent.

### Une chaîne déterministe autour d'une production probabiliste

Un agent ne produit pas deux fois le même code pour la même demande.
C'est sa nature, et ce n'est pas un défaut tant que quelque chose de
reproductible juge le résultat. Ce quelque chose, c'est la chaîne de
validation.

Elle doit vérifier, de la même façon à chaque passage :

- les comportements attendus, c'est-à-dire les scénarios ;
- les invariants critiques, ceux qui ne doivent jamais casser ;
- l'absence de régression ;
- la sécurité ;
- la qualité de l'artefact produit.

L'agent propose. La chaîne atteste. L'humain décide de ce que la
chaîne ne peut pas attester. C'est la séparation que j'explore avec
[workline]({{ '/labo/' | relative_url }}) : ce qu'une machine peut
prouver seule, et ce qui doit rester une décision.

### La couverture ne suffit pas

Un pourcentage de couverture élevé dit que des lignes ont été
exécutées. Il ne dit pas qu'un test aurait échoué si le comportement
avait disparu. Un test qui n'affirme rien couvre ses lignes et passe
au vert.

Avec un agent, le risque grandit : il sait écrire des tests qui
passent, et il est récompensé quand ils passent. Les vérifications qui
comptent sont celles qui cherchent activement à faire échouer le code :

- les **scénarios métier**, qui disent ce qui doit être vrai ;
- le **property-based testing**, qui cherche le contre-exemple au lieu
  de vérifier trois cas choisis à la main ;
- le **fuzzing**, sur tout ce qui parse une entrée extérieure ;
- le **mutation testing**, qui modifie le code et vérifie qu'au moins
  un test le remarque. C'est la seule mesure qui répond à la question
  «&nbsp;mes tests peuvent-ils échouer ?&nbsp;» ;
- quelques **tests d'intégration ciblés**, là où les mocks mentent.

### Paralléliser la validation

Quand la production de code accélère, une suite qui tourne en
séquence devient une file d'attente. Ajouter des tests sans réfléchir
à leur ordre allonge chaque cycle de la même durée, pour chaque
changement.

La suite doit s'organiser comme un graphe, pas comme une liste : par
dépendances, par niveau de risque, et selon ce que le changement
touche réellement. Un changement dans la documentation ne relance pas
les tests d'intégration. Un changement dans le module de paiement les
relance tous. Les vérifications rapides et décisives passent en
premier, pour échouer tôt. L'heure de CI de mon incident n'était pas
une fatalité : c'était une suite de tests fonctionnels qui attendaient
leur tour les uns derrière les autres.

### Arrêter de tout mettre dans l'assiette

L'autre façon d'allonger une CI, c'est d'y empiler tout ce qui peut
se vérifier. L'orthographe des spécifications. La syntaxe des
diagrammes Mermaid. Le formatage du Markdown. Chacune de ces
vérifications est raisonnable prise seule. Sur un dépôt qui contient
beaucoup de fichiers, leur somme coûte des minutes à chaque passage,
et elle bloque des changements qui n'ont rien à voir.

Je pose la question autrement : qu'est-ce que cette vérification
protège ? Une faute de frappe dans une spécification ne change pas le
comportement du système. Un humain la lit sans buter, et un LLM la
comprend sans difficulté. Une régression fonctionnelle, elle, part en
production.

Ces vérifications ont leur place dans l'éditeur, dans un hook local,
ou dans une tâche qui ne bloque rien. Pas dans le chemin critique qui
sépare un correctif de la production. Une CI qui fait tourner vite de
bons tests fonctionnels et d'acceptation, avec une vraie couverture du
comportement, vaut mieux qu'une CI exhaustive qui livre en retard des
spécifications sans faute.

### Produire un artefact de confiance

Le même artefact, construit une fois et versionné, doit traverser
tous les environnements. Pas une reconstruction à chaque étape, avec
des dépendances résolues à des moments différents et un résultat que
personne n'a réellement testé.

Ce que la CI a validé doit être exactement ce qui part en production.
Sinon, la validation porte sur un objet qui n'existe plus.

### Le rollback fait partie du déploiement

Un rollback jamais testé est un espoir écrit en YAML.

Quand le rythme de livraison augmente, le nombre de mises en
production augmente avec lui, et donc le nombre de fois où l'une
d'elles se passe mal. La réponse n'est pas de ralentir. C'est de
limiter le rayon d'explosion de chaque livraison :

- des **feature flags**, pour séparer le déploiement de l'activation ;
- des **déploiements progressifs**, sur une fraction du trafic
  d'abord ;
- une **observabilité** qui dit en minutes si le comportement en
  production correspond au comportement attendu ;
- un **retour arrière** qui fait partie du chemin normal, exercé
  régulièrement, et pas une procédure d'urgence qu'on découvre le
  jour où on en a besoin.

### Accélérer la confiance

Les agents ont rendu le code bon marché. Ils n'ont rendu bon marché
ni la vérification, ni la mise en production, ni le retour arrière.
Si ces trois-là gardent leur rythme d'avant, le cycle de livraison
garde le sien aussi, et l'accélération se transforme en stock de
changements qui attendent.

La question à poser à votre chaîne n'est donc pas «&nbsp;à quelle
vitesse produit-on du code ?&nbsp;». C'est «&nbsp;à quelle vitesse
peut-on avoir confiance dans ce qu'on livre ?&nbsp;».
