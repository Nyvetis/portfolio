---
date: 2026-05-03
description: "Veille Cyber sécurité"
image: '/image/Galaxy.webp'
lastmod: 2026-01-13
showTableOfContents: true
categories: [ "formation", "stage"]
tags: ["Cyber"]
title: "Veille Cyber"
cover: '/image/Galaxy.webp'
type: "post"
--- 

# Les 5 dernières actualités dans le monde de la Cyber

## 1. Fuite massive sur l'ANTS — Réaction du gouvernement
**Source :** LCP / 30 avril 2026

Le Premier ministre Sébastien Lecornu a annoncé une "doctrine de protection" des données numériques de l'État, évoquant une "situation assez grave". Ces annonces font suite à la cyberattaque du 15 avril ayant touché près de 12 millions de comptes sur le portail de l'Agence nationale des titres sécurisés (ANTS), qui gère les demandes de pièces d'identité.

## 2. Fuite du code source de Claude Code sur npm
**Source :** Anthropic / 31 mars 2026

Le 31 mars 2026, Anthropic a accidentellement publié l'intégralité du code source de **Claude Code** sur npm — son outil de codage IA en ligne de commande. Une erreur de configuration a entraîné l'inclusion d'un fichier source map de 59,8 Mo contenant ~513 000 lignes de TypeScript sur 1 906 fichiers, révélant toute l'architecture interne de l'agent. Anthropic a confirmé qu'il s'agissait d'une "erreur humaine de packaging" et qu'aucune donnée client ni identifiant n'avait été exposé.

En quelques heures, le code a été mirroré sur GitHub, atteignant 50 000 étoiles et 41 500 forks avant les demandes de retrait DMCA. La fuite révèle notamment des fonctionnalités non encore publiées, dont un mode daemon autonome baptisé **KAIROS** permettant à Claude Code de travailler en arrière-plan même quand l'utilisateur est inactif.

## 3. Compromise du paquet npm Axios
**Source :** npm Security / 31 mars 2026

Le 31 mars 2026, le paquet npm **Axios** (70M+ téléchargements/semaine) a été compromis via le compte du mainteneur principal, piégé par du social engineering. Les versions malveillantes ont injecté une dépendance cachée qui déployait automatiquement un **RAT multiplateforme** (Remote Access Trojan) sous Windows, macOS, et Linux, dès l'installation, en se connectant à un serveur C2 nord-coréen. Les versions corrompues sont restées en ligne environ 3 heures avant d'être retirées.

## 4. Trois exploits zero-day contre Microsoft Defender
**Source :** Chercheur anonyme / Avril 2026

Un chercheur anonyme a publié trois exploits zero-day ciblant **Microsoft Defender** :
- **BlueHammer** : élévation de privilèges via la logique de remédiation de fichiers
- **RedSun** : exploitation du rollback de fichiers cloud pour obtenir les droits SYSTEM
- **UnDefend** : perturbation silencieuse du pipeline de mises à jour

BlueHammer a été patché par Microsoft le 14 avril (CVE-2026-33825, CVSS 7.8) et ajouté au catalogue KEV de la CISA avec une deadline au 6 mai. RedSun et UnDefend restent **non patchés**, laissant tous les systèmes Windows à jour exposés.

## 5. Intrusion chez Trellix — Accès au code source
**Source :** Trellix / 2 mai 2026

Le 2 mai 2026, **Trellix** — éditeur majeur de solutions de sécurité endpoint et XDR — a confirmé une intrusion ayant permis un accès non autorisé à une partie de son dépôt de code source interne. L'entreprise a immédiatement mandaté des experts forensiques externes et notifié les autorités. Trellix précise n'avoir trouvé aucune preuve que son code source ait été modifié ou exploité, ni que son processus de distribution ait été compromis. L'incident est particulièrement sensible : accéder au code source d'un éditeur de sécurité revient à obtenir le plan technique de ses outils de protection, permettant à un attaquant d'y chercher des vulnérabilités de manière ciblée. L'enquête est toujours en cours, l'identité des attaquants n'ayant pas encore été divulguée.