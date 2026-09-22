# OpenG7 Model Gateway — architecture

## Mission et état

Router les inférences OpenG7 avec gouvernance, quotas et observabilité, indépendamment du fournisseur.
Le dépôt contient actuellement cadrage et gouvernance. Les modules décrits
dans le [README](../README.md) sont une architecture cible, pas du code livré.
Aucun build applicatif n’est disponible avant ajout de ses manifests et sources.

## Frontières

Le gateway possède routes, adaptateurs fournisseurs et minimisation des requêtes. Il ne stocke pas la mémoire canonique et n’orchestre pas les tâches métier des agents.

API compatible et administration → classification/politique → sélection de route → port fournisseur → adaptateur. Observabilité et budgets encadrent tout le flux, sans dépendance fournisseur dans les applications consommatrices.

## Invariants de conception

Appliquer les [invariants du projet](../AGENTS.md#périmètre-local) aux contrats,
aux adaptateurs et à leurs tests; ils restent définis à cet endroit unique.

## Évolution

Garder les contrats de domaine indépendants des fournisseurs et les effets dans
les adaptateurs. Pour matérialiser un module, documenter ses entrées/sorties,
consommateurs, permissions, état d’implémentation et validations disponibles.
Mettre à jour cette frontière si elle change; les consignes d’exécution restent
dans [AGENTS.md](../AGENTS.md), sans recopier une autre stack.
