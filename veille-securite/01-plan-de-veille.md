# Plan de veille sécurité

> **Auteur** : _Prénom Nom_ · **Créé le** : _AAAA-MM-JJ_ · **Dernière révision** : _AAAA-MM-JJ_
> **Projet concerné** : _nom du projet fil rouge / projet en entreprise_

*Les éléments en italique sont des exemples à remplacer.*

## 1. Contexte

_Application web de gestion de réservations pour une association : front-end React, API REST Spring Boot, base PostgreSQL, déploiement Docker sur un VPS, CI GitHub Actions. L'application traite des données personnelles (nom, e-mail, téléphone) → soumise au RGPD._

## 2. Pile technique surveillée (cercle 1)

| Couche | Composant | Version | Mots-clés de veille |
|---|---|---|---|
| Front | _React_ | _19.x_ | _react, react-dom, vite_ |
| Front | _Axios_ | _1.x_ | _axios_ |
| Back | _Java / Spring Boot_ | _21 / 3.x_ | _spring boot, spring security, spring framework_ |
| Back | _jjwt_ | _0.12.x_ | _jwt_ |
| Données | _PostgreSQL_ | _16_ | _postgresql_ |
| Infra | _Docker, image eclipse-temurin_ | _—_ | _docker, temurin, openjdk_ |
| Infra | _Nginx_ | _1.2x_ | _nginx_ |
| CI/CD | _GitHub Actions_ | _—_ | _github actions_ |

## 3. Objectifs

1. _Être alerté sous 48 h de toute vulnérabilité **critique** (CVSS ≥ 9) ou **activement exploitée** touchant un composant ci-dessus._
2. _Étudier une catégorie de l'**OWASP Top 10** par semaine et vérifier mon projet en conséquence._
3. _Rédiger **au moins une fiche de veille par semaine**._
4. _Produire une **synthèse mensuelle** d'une page._

## 4. Thèmes par cercle

| Cercle | Thèmes | Fréquence |
|---|---|---|
| 1 — Ma pile | _CVE et advisories des composants ci-dessus, alertes Dependabot_ | Quotidienne (5–10 min) |
| 2 — Dév sécurisé | _OWASP Top 10 & API Top 10, authentification (JWT, OAuth2, passkeys), sécurité Docker/CI_ | Hebdomadaire (30 min) |
| 3 — Culture cyber | _Grandes attaques, supply chain, sécurité de l'IA, RGPD/CNIL, NIS 2, Cyber Resilience Act_ | Hebdomadaire (15 min) |

## 5. Sources et outils

Liste détaillée et état des abonnements : [`../Abonnements_en_cours.md`](../Abonnements_en_cours.md).

| Étape | Outil retenu |
|---|---|
| Collecte | _Inoreader (dossiers « Cercle 1 / 2 / 3 »), OpenCVE, alertes e-mail CERT-FR_ |
| Détection dans mon code | _Dependabot, `npm audit`, OWASP Dependency-Check, Trivy en CI_ |
| Capitalisation | _Ce dépôt Git (Markdown)_ |
| Diffusion | _Synthèse mensuelle, canal #securite de la promo_ |

## 6. Routine

| Créneau | Activité |
|---|---|
| _Chaque matin, 5 min_ | _Survol alertes cercle 1 + Dependabot ; ligne dans le journal si pertinent_ |
| _Lundi 9 h – 9 h 45_ | _Lecture approfondie, 1 fiche de veille, commit_ |
| _Dernier vendredi du mois, 1 h_ | _Synthèse mensuelle + revue des sources (supprimer / ajouter)_ |

## 7. Grille de priorisation

| Priorité | Condition | Délai d'action |
|---|---|---|
| 🔴 P1 | Me concerne + exploitée activement (KEV) ou CVSS ≥ 9 avec PoC | 24–48 h |
| 🟠 P2 | Me concerne + CVSS ≥ 7 | Sprint en cours |
| 🟡 P3 | Me concerne + CVSS < 7 ou exploitation improbable | Backlog |
| ⚪ P4 | Ne me concerne pas directement | Culture / partage |

## 8. Revue du plan

| Date | Modification | Raison |
|---|---|---|
| _AAAA-MM-JJ_ | _Création du plan_ | _Démarrage atelier_ |
