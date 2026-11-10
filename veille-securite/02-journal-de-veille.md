# Journal de veille

> Une ligne par information **triée** (pas besoin de noter ce que vous ignorez au premier coup d'œil).
> Priorités : 🔴 P1 · 🟠 P2 · 🟡 P3 · ⚪ P4 (voir [plan de veille](01-plan-de-veille.md#7-grille-de-priorisation)).
> Les lignes ci-dessous sont des **exemples** : remplacez-les par votre propre veille.

| Date | Sujet | Source | Cercle | Concerné ? | Priorité | Suite donnée |
|---|---|---|---|---|---|---|
| _AAAA-MM-JJ_ | Rappel Log4Shell (CVE-2021-44228) — cas d'école | CERT-FR, NVD | 1 | Vérifié : non (Logback par défaut avec Spring Boot) | ⚪ | [Fiche](fiches/exemple-log4shell.md) |
| _AAAA-MM-JJ_ | OWASP Top 10 — A01 Broken Access Control | owasp.org | 2 | Oui | 🟠 | [Fiche](fiches/exemple-owasp-a01-controle-acces.md) + ticket « vérifier contrôle propriétaire sur /reservations/{id} » |
| _AAAA-MM-JJ_ | Porte dérobée dans xz-utils (CVE-2024-3094) | CERT-FR, Openwall | 3 | Non (image de base non concernée) | ⚪ | [Fiche](fiches/exemple-xz-utils-backdoor.md) |
| _AAAA-MM-JJ_ | Détournement du CDN polyfill.io | BleepingComputer, Sansec | 3 | Vérifié : aucun script externe | ⚪ | [Fiche](fiches/exemple-polyfill-io-supply-chain.md) |
| _AAAA-MM-JJ_ | OWASP Password Storage Cheat Sheet — Argon2id | OWASP | 2 | Oui (BCrypt actuellement) | 🟡 | [Fiche](fiches/exemple-stockage-mots-de-passe.md) |
| _AAAA-MM-JJ_ | Alerte Dependabot sur une dépendance front | GitHub | 1 | Oui | 🟠 | PR de mise à jour fusionnée |
