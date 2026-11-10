# Veille sécurité — Travail demandé

> Titre professionnel **CDA — RNCP 37873** · Module *Actualiser et partager ses compétences*
> Atelier : **Veille sur des tendances technologiques** (thème : **cybersécurité / développement sécurisé**) puis **Partage de connaissances**.

Ce dossier contient **les documents que vous devez produire et faire vivre**. Ils sont pré-remplis avec un exemple (pile Spring Boot / React / PostgreSQL / Docker) : **remplacez les exemples par votre propre contexte**.

Avant de commencer, lisez le guide : [`../guide/`](../guide/01-pourquoi-une-veille-securite.md).

## Livrables

| # | Document | Ce qu'il faut faire | Quand |
|---|---|---|---|
| 1 | [`01-plan-de-veille.md`](01-plan-de-veille.md) | Définir pile technique, objectifs, sources, routine | Jour 1 de l'atelier |
| 2 | [`../Abonnements_en_cours.md`](../Abonnements_en_cours.md) | Lister et configurer **réellement** vos abonnements (RSS, alertes, Dependabot…) | Jour 1 |
| 3 | [`02-journal-de-veille.md`](02-journal-de-veille.md) | Une ligne par information lue et triée | En continu |
| 4 | [`fiches/`](fiches/) | **Au moins 5 fiches** de veille (modèle : [`_MODELE-fiche.md`](fiches/_MODELE-fiche.md)) | 1 par semaine minimum |
| 5 | [`03-synthese-mensuelle.md`](03-synthese-mensuelle.md) | Synthèse d'une page diffusable à une équipe | Fin de chaque mois |
| 6 | [`04-synthese-dossier-projet.md`](04-synthese-dossier-projet.md) | Partie « veille sécurité » de votre dossier de projet | Avant le dépôt du dossier |
| 7 | [`05-atelier-partage.md`](05-atelier-partage.md) | Support d'une présentation de 10 min à la promo | Atelier « Partage de connaissances » |

## Contraintes

- **Format** : Markdown, versionné dans un dépôt Git (un commit par session de veille).
- **Sources** : au moins **2 sources institutionnelles** (CERT-FR, ANSSI, CNIL, NVD…), **1 source OWASP**, **1 source anglophone**.
- **Fiches** : rédigées **avec vos mots**, sources citées et datées, impact sur *votre* projet explicité.
- **Répartition des 5 fiches minimum** :
  - 2 vulnérabilités concrètes (CVE) — idéalement liées à votre pile ;
  - 1 catégorie de l'OWASP Top 10 (ou API Security Top 10) ;
  - 1 bonne pratique ou un outil de développement sécurisé ;
  - 1 sujet libre (supply chain, IA, réglementation, incident marquant…).

## Grille d'auto-évaluation

| Critère | ✅ |
|---|---|
| Le périmètre de veille correspond à ma pile technique réelle | ☐ |
| Mes abonnements sont réellement configurés (captures ou preuves possibles) | ☐ |
| Ma veille est régulière (historique Git, dates du journal) | ☐ |
| Mes sources sont fiables, variées, dont anglophones | ☐ |
| Chaque fiche indique si mon projet est concerné et l'action menée | ☐ |
| Au moins une action concrète dans mon code découle de ma veille | ☐ |
| Je sais présenter ma démarche en 1 minute à l'oral | ☐ |
| Je sais expliquer en détail au moins 2 vulnérabilités de mes fiches | ☐ |
