---
date: 2026-01-12
description: "Work in progress..."
image: '/image/Galaxy.webp'
lastmod: 2026-01-13
showTableOfContents: true
categories: [ "formation", "stage"]
tags: ["JS", "VueJS","NodeJS", "TypeScript", "Docker"]
title: "Stage Diluz"
cover: '/image/Galaxy.webp'
type: "post"
--- 
# Diluz

> Diluz est une ESN (entreprise de services numériques), affiliée au groupe Toadenn, lui-même partie du réseau Talenz, un groupe d'expertise comptable.
>
> Ce stage a pour objectif de découvrir le monde professionnel, notamment les différents environnements de travail, afin de me préparer au métier de développeur (full stack & DevOps), tout en renforçant mes compétences nécessaires à l'obtention de mon BTS SIO.


## Contexte de la mission
<!-- à placer : 
    Réalisation d’un PDF en back-end avec récupération des datas en BDD  au préalablement enregistrés via un formulaire sur le front  (forumlaire d’annexe juridique)  
    Evolution ont eu un impact sur les différents composants de l’architecture. 
    Création propre pour l’annexe juridique donc pas d’impact sur d’autres modules 
-->
> L'entreprise a développé sa propre application web interne, `MyToadenn`, permettant aux différents pôles (juridique, économique, etc.) de recenser les informations relatives aux clients.
>
> Exemple : la coopérative U, dont les données juridiques et financières sont centralisées par les experts de Talenz Toadenn.
>
> L'application dispose d'une section dédiée au pôle juridique, où les experts renseignent un formulaire d'`Annexe juridique` contenant les informations sur les missions d'une structure.
>
> Cependant, cette annexe avait un __problème__ :
>
> Les données saisies ne pouvaient pas être exportées en PDF. Les experts devaient donc ressaisir manuellement ces informations dans un document Word pour pouvoir les imprimer.

> Ma mission a donc consisté à :
> - Créer un bouton d'export PDF du formulaire d'annexe juridique.
> - Générer ce PDF côté back-end en `TypeScript`, à l'aide des librairies `jsPDF` et `jsPDF-autotable`.
> - Stocker le PDF en base de données et permettre son téléchargement via le navigateur (l'envoi direct depuis le back-end n'étant pas possible).

> Les premières semaines ont été consacrées à la mise en place du poste et de l'environnement de développement de `MyToadenn`. Sans cet environnement, certaines journées ont nécessité de la programmation "à l'aveugle", sans accès au front-end ni aux données.

> Une fois l'environnement opérationnel, j'ai pu commencer efficacement à identifier les bons attributs des tables en base de données en fonction de la structure du formulaire d'annexe juridique.


## Stack technique de `MyToadenn`

### Front-end
- VueJS (Framework JavaScript)
- NuxtJS (Framework de VueJS)

### Back-end
- NodeJS
- TypeScript
- Framework ExpressJS
- ORM Sequelize
- Librairies jsPDF (pour la création du PDF)

### Base De Données
- Postgresql (managé avec DBeaver)

### Données supplémentaires
- `MyToadenn` est hébergée sur GitLab (dépôts, branches, commits, merge requests, CI). Aucun ticket ni milestone n'était utilisé dans le projet.

- L'application est organisée sous la forme :

    >Front -> Back (Contrôleurs -> Modèles -> Services -> DAO) -> BDD

## Structuration de l'annexe juridique

> L'annexe juridique, sous la forme d'un formulaire, est divisée en 3 grandes parties :
>
> - Les informations des dirigeants, associés et administrateurs
> - Les conventions réglementées (comptes courants, contrats intragroupe, CAC, CSE, etc.)
> - L'affectation du résultat (bénéfice, perte, etc. — volet financier de la mission)


## Structuration de la mission : 

- 2 premières semaines : mise en place de l'environnement et réalisation de la partie 1 de l'annexe
- 2 semaines suivantes : réalisation de la partie 2, correction de bugs, optimisation du code et personnalisation du PDF
- 2 dernières semaines : réalisation de la partie 3, déploiement sur la branche Dev et finitions de la génération du PDF