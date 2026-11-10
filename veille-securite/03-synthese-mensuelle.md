# Synthèse mensuelle de veille sécurité — _[Mois AAAA]_

> **Auteur** : _Prénom Nom_ · **Destinataires** : _équipe projet / promotion_ · **Période** : _du JJ/MM au JJ/MM_
> Une page maximum. Exemple ci-dessous à remplacer par votre propre synthèse.

## 🔎 En bref

- _5 informations retenues sur 40 triées · 3 fiches rédigées · 2 actions dans le projet._

## 🔴 Ce qui nous concerne directement

| Sujet | Gravité | Statut |
|---|---|---|
| _Alerte Dependabot sur une dépendance front (déni de service)_ | _CVSS 7.5_ | ✅ _Corrigé (PR #__)_ |
| _OWASP A01 : 2 endpoints sans contrôle de propriétaire_ | _Élevée_ | ✅ _Corrigé + tests ajoutés_ |

## 🟡 Bonnes pratiques à adopter

- _**Mots de passe** : l'OWASP recommande Argon2id ; notre bcrypt reste acceptable, migration planifiée._ → [fiche](fiches/exemple-stockage-mots-de-passe.md)
- _**Scripts tiers** : ajout d'une CSP `script-src 'self'` suite à l'étude du cas polyfill.io._ → [fiche](fiches/exemple-polyfill-io-supply-chain.md)

## ⚪ Pour la culture

- _**xz-utils** : une porte dérobée introduite après deux ans d'ingénierie sociale dans un projet open source._ → [fiche](fiches/exemple-xz-utils-backdoor.md)

## 📅 Le mois prochain

- _Étudier OWASP A03 (Supply chain) et A05 (Injection) ; mettre en place Trivy dans la CI ; supprimer 2 flux RSS jamais lus._

## 📚 Sources principales du mois

_CERT-FR, OWASP, GitHub Advisory Database, Sansec, Openwall._
