# 01 — Pourquoi une veille sécurité quand on est CDA ?

> Public : apprenants préparant le titre professionnel **Concepteur Développeur d'Applications (CDA) — RNCP 37873**.
> Module : *Actualiser et partager ses compétences en conception et développement d'applications*.

## 1. La sécurité est au cœur du titre

Les trois activités types du titre CDA portent toutes la mention « **sécurisée** » :

| Activité type | Intitulé |
|---|---|
| AT1 | Développer une application **sécurisée** |
| AT2 | Concevoir et développer une application **sécurisée** organisée en couches |
| AT3 | Préparer le déploiement d'une application **sécurisée** |

Concrètement, le jury attend que vous sachiez :

- identifier les vulnérabilités courantes (injection, contrôle d'accès défaillant, XSS, CSRF, dépendances vulnérables…) ;
- justifier vos choix de sécurité (hachage des mots de passe, gestion des sessions/JWT, validation des entrées, en-têtes HTTP…) ;
- montrer que vous **suivez l'actualité des vulnérabilités** qui touchent *votre* pile technique.

La veille est aussi l'une des compétences transverses du titre (« **Apprendre en continu** ») : elle se prouve par une démarche, pas par une déclaration.

> ⚠️ Les modalités exactes d'évaluation (contenu du dossier de projet, de l'entretien technique, etc.) sont fixées par le **Référentiel d'Évaluation (RE)** et le **Référentiel de Compétences (RC)** en vigueur. Vérifiez-les sur [francecompetences.fr/recherche/rncp/37873](https://www.francecompetences.fr/recherche/rncp/37873/) et auprès de votre formateur. En pratique, le dossier de projet comporte une partie consacrée à **la veille effectuée sur les vulnérabilités de sécurité** : ce guide vous prépare à la rédiger.

## 2. Pourquoi c'est indispensable dans le métier

- **Le paysage bouge en permanence** : plusieurs dizaines de milliers de CVE (vulnérabilités référencées) sont publiées chaque année.
- **Votre code n'est qu'une petite partie de votre application** : 70 à 90 % du code exécuté provient de dépendances (npm, Maven, Composer, pip…). Une faille dans l'une d'elles devient *votre* faille (ex. Log4Shell, 2021).
- **Les attaques sur la chaîne d'approvisionnement** (supply chain) se multiplient : paquets malveillants, mainteneurs compromis, CDN détournés.
- **Obligations légales** : RGPD (sécurité des données personnelles, art. 32), directive NIS 2, Cyber Resilience Act européen pour les produits numériques.
- **Coût d'une faille** : plus elle est découverte tard (en production), plus elle coûte cher à corriger.

## 3. Les trois dimensions de la veille sécurité

| Dimension | Questions qu'on se pose | Exemples |
|---|---|---|
| **Technologique** | Quelles failles touchent mes langages, frameworks, bibliothèques, serveurs ? | CVE sur Spring, Symfony, Express, React, PostgreSQL, Docker… |
| **Méthodologique** | Quelles pratiques de développement sécurisé émergent ? | OWASP Top 10, ASVS, DevSecOps, SAST/DAST, SBOM, passkeys |
| **Réglementaire** | Quelles obligations s'imposent à mon application ? | RGPD, recommandations CNIL/ANSSI, NIS 2, Cyber Resilience Act |

## 4. Ce que vous saurez faire à la fin

1. Définir le **périmètre** de votre veille à partir de votre pile technique ([02](02-definir-objectifs-et-perimetre.md)).
2. Choisir des **sources fiables** et les automatiser en mode *push* ([03](03-sources-et-outils.md)).
3. **Organiser** une routine, trier, qualifier et prioriser l'information ([04](04-organiser-sa-veille.md)).
4. **Exploiter** la veille dans vos projets et la **partager** (dossier de projet, équipe, oral) ([05](05-exploiter-et-partager.md)).
