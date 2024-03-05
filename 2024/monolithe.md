# Le monolithe est mort, vive le monolithe !

# [Official slides](https://github.com/confooca/2024/blob/main/2024-02-23/Le_monolithe_est_mort_vive_le_monolithe-Sebastien_Ballange.pdf)

## Introduction

- Quelle archi pour un nouveau projet ?
  - Taille de l'équipe
  - Dateline
  - Budget
  - Volume d'utilisateur
  - Expérience de l'équipe
- Monolithe quasiment tout le temps, microservices, il faut se poser la question de l'utilité (si on ne sait pas pourquoi, il ne faut pas le faire)

## Inconvénients

- Couplage étroit et complexité
  - Interdépendances entre les composants
  - Longs cycles de développements
- Augmenter les resources de certaines fonctionnalités n'est pas possible, tout est concerné
- Un ralentissement d'une section peut se propager au reste
- Obstacle à l'adoption de nouvelles technologies / innovation moins facile
- Courbe d'apprentissage complexe (haut volume d'infos à absorber)
- Large domaine à tester
- Collaboration entre équipes : + de problèmes de communication et risque accru de briser le travail des autres

## Avantages

- Dév et déploiements plus simples : une seule unité à coder et déployer
- One codebase
- Pas de communication entre services plus complexes
- Développement local plus simple, rien de très complexe à orchestrer
- Cohérence améliorée entre les fonctionnalités :
  - Même modèle de données et même BDD
  - Cohérence des données entre les différentes fonctionnalités
  - Transactions avec plusieurs fonctionnalités sont plus faciles
- Débug et tests plus faciles : nature unifiée
- Tracer les problèmes à travers l'ensemble du système sans barrière de communication
- Outils et processus pour architecture monolithique sont bien établis
- Avantages en termes de performance dans certains cas
- Moins d'accès au réseau
- Il y a des cas d'utilisation idéaux où le monolithe s'impose logiquement
- Mettre rapidement des MVP sur le marché en étant rapide et flexible 

## Middle ground

- Regrouper la logique en services spécialisés et compartimentés
- Plus facile à maintenir et à tester
- Raisonner en API: API platform basé sur Symfony
- Performances
- Monolithe ou citadelle: monolithe au centre avec des avant-postes
  - https://signalvnoise.com/svn3/the-majestic-monolith-can-become-the-citadel/
- Analysez la situation, être pragmatique
- La complexité est notre pire ennemi
- https://grugbrain.dev/
