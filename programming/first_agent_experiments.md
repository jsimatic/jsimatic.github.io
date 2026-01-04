# 🌿 First Agent Experiments (FR)

## Motivation: L'ingénieur face au développement des IAs génératives

Il y a quelques mois, les IAs génératives offraient à peine plus qu'une autocomplétion basée sur l'analyse formelle du code. Aujourd'hui, elles semblent capables de développer des applications complètes. On s'attend à ce que ces capacités se développent encore exponentiellement.

Face à cette croissance, je me pose des questions à la fois comme ingénieur et comme CTO de comment intégrer ces outils dans notre quotidien. Il s'agit tout d'expérimenter, pour limiter la part de fantasme dans les discussions, pour apprécier en direct l'interaction avec ces outils. Faute de temps, il s'agit d'une expérimentation partielle dont je n'espère pas tirer une conclusion définitive ou scientifiquement rigoureuse, mais j'espère tirer une tendance.

## Expérience 1: Script Python et algorithmie

L'idée est d'utiliser l'IA pour répondre à une question de dénombrement: calculer la probabilité de bombes (carré ou suite de carte de même couleur) dans le jeu de Tichu. Pour cela, j'ai utilisé Antigravity et Gemini 3 Flash

Mon prompt était le suivant:

> create a python script managed by UV that computes the probability of a given card combination. The cards are numbered from 2 to 10, J, D, K, A and there are 4 colours: Spades, Hearts, Diamonds and clover, with 4 jokers. A bomb is combination with 4 cards of the same value (e.g. 3 of hearts, 3 of diamond, 3 of spades, 3 of clover) or 5 or move consecutive cards of the same colour. Given that all cards are dealt randomly, what is the probability of the number of bombs in the game ?

L'outil a généré un plan:

1. Initialize project with uv
2. Define the deck and card values
3. Implement bomb detection logic: Quad detection then Straight flush detection
4. Implement Monte Carlo simulation
5. Verify results and format output

L'exécution du plan a donné un code fonctionnel et un tableau de probabilité de bombes dans le jeu de Tichu. La lecture du code était claire, sauf pour la partie sur les bombes de suite de cartes où la logique était un peu obscure. J'ai donc demandé à l'IA de vérifier cette partie.

A ma grande surprise, l'IA n'a pas fourni d'explication sur le code mais a déclaré avoir détecté une erreur de logique: le fait que son code comptait comme plusieurs bombes des bombes qui partagaient les mêmes cartes et le fait qu'une suite de 10+ cartes était considérée comme une bombe alors qu'elle pouvait constituer plusieurs bombes.

Le code corrigé était encore plus obscur, avec notamment une fonction récursive pour trouver les ensembles disjoints. Que faire alors pour s'assurer du fonctionnement ? J'ai demandé d'ajouter des tests.

Après une passe de refactoring pour utiliser pytest au lieu de unittest, il s'est avéré que les tests étaient incorrects. J'ai préféré manuellement les corriger pour m'assurer de la cohérence. En revanche, je n'ai pas investigué l'implémentation de la logique de comptage de bombes.

J'ai lancé un nouveau planning pour ajouter le calcul dans le cas du jeu à 6.

> Add an option to the script to evaluate a 6 player deck. We add for each value 2 cards. Suits are alternated so that we add hearts and clovers for even cards (2, 4, 6, 8, 10, D, A) and diamonds and spades for odd cards (3, 5, 7, 9, J, K)

A nouveau, surprise, l'IA m'a demandé de clarifier le nombre de cartes données aux joueurs. En effet, ayant oublié de lui préciser qu'on ajoutait 2 jokers, on se retrouvait soit à donner un nombre inégal de cartes entre les joueurs soit à devoir laisser des cartes non-distribuées.

Une fois l'information donnée, la génération du code s'est passée sans encombre. J'ai rajouté à la main les tests pour tester l'absence de couleurs répétées dans les bombes de 4 cartes.

Leçons:

1. Les capacités de réflexion et de génération m'ont agréablement surpris. L'IA a été capable de relever des cas limites non triviaux (bien que pas forcément compliqués).
2. Intégrer l'écriture de tests dans le plan initial et bien relire les tests.
3. Le code généré peut devenir vite complexe et donc difficile à adapter par un humain.

Un tel code a clairement sa place en tant que prototype, mais c'est plus tangeant pour un code en production à maintenir et à faire évoluer. En effet, pour faire évoluer un tel code, on serait soit contraints de recourir à l'IA soit de dépenser un effort conséquent pour comprendre l'implémentation. Dans les deux cas, une série de test sur le domaine de validité des entrées semble de mise alors que lors d'une écriture manuelle, cette réflexion est souvent intégrée dans l'implémentation (bien que souvent implicite).

## Expérience 2: Application web

Cette fois, je m'intéresse à la création d'un application web par l'IA. Remarque préliminaire: je n'ai pas de connaissance en développement web (à part quelques notions).

Après plusieurs essais d'outils, je me suis à nouveau rabattu sur Antigravity:

1. Zed n'arrivait plus à se lancer après l'installation de l'extension Mistral.
2. VS Code avec le plugin Continue.dev semblait produire des plans intéressants mais le mode d'exécution n'était peut-être pas bien compatible avec Devstral.
3. Mistral Vibe CLI était trop lent, rien que pour initialiser un projet. Cela dit, c'était peut-être dû au faible débit de ma connexion au moment des tests.

Mon objectif était de créer une application permettant de noter des scores de Tichu. Mon premier
prompt décrivait les différentes vues que j'imaginais de l'application (page de score par parties, leaderoard, etc.). L'IA a proposé un plan d'application sur lequel je l'ai lancée sans trop réfléchir.

Le résultat était étonnamment bon: L'application était relativement fonctionnelle. Mais lorsque j'ai souhaité faire des changements qui me semblaient relativements mineurs comme ne pas afficher le leaderboard sur la page d'accueil, l'IA a eu du mal à faire les modifications sans casser l'application (le debug visuel du rendu du navigateur, bien qu'impressionnant reste assez lent).

L'approche qui a fonctionné après plusieurs essais similaires a été:

1. De spécifier les contraintes (comme les règles du jeu) dans un fichier plutôt que dans le prompt. Cela permettait notamment de ne pas avoir à le réécrire à chaque fois.
2. De planifier une architecture d'application et de demander à l'IA de l'implémenter au fur et à mesure: en commençant par exemple par le backend avant de passer au frontend. Sur le frontend, je me suis appuyé sur les explications de l'IA pour essayer de palier mon manque de connaissance avant de lancer une implémentation.

L'IA a faillit se perdre à un moment, une modification qui me semblait simple a déclenché l'ajout d'un endpoint. Peut-être que passer à un modèle plus performant aurait pu accélérer la reprise en main.

Au final, faute de temps, l'application est à 80% finie. Il manque quelques fonctionnalités et je n'aurai aucune confiance à la déployer en l'état. 

Je tire de cette expérience le sentiment que les pratiques d'ingénierie logicielle sont essentielles pour que l'IA puisse être utile. Il reste (aujourd'hui) un fort besoin de cadrage et de supervision humaine.

## Bilan: Productivité et souveraineté

A suivre ...

Un large merci à Logic Inc. pour leur article [Codex is a Slytherin, Claude is a Hufflepuff](https://bits.logic.inc/p/codex-is-a-slytherin-claude-is-a?utm_source=tldrnewsletter) qui m'a poussé à écrire ce billet.