# 02 — Définir ses objectifs et son périmètre de veille

Une veille sans périmètre devient vite un flux ingérable. Première étape : **savoir ce que l'on surveille, et pourquoi**.

## 1. Partir de sa pile technique

Listez tout ce qui compose votre application (projet fil rouge, projet d'entreprise) :

| Couche | Ce que je dois lister | Exemple |
|---|---|---|
| Front-end | Framework, bibliothèques majeures | React 19, Vite, Axios |
| Back-end | Langage, framework, ORM | Java 21, Spring Boot 3, Hibernate |
| Données | SGBD, cache | PostgreSQL 16, Redis |
| Authentification | Mécanisme, bibliothèque | JWT, Spring Security, OAuth2 / OpenID Connect |
| Infrastructure | Conteneurs, serveur web, CI/CD | Docker, Nginx, GitHub Actions |
| Mobile (si concerné) | Framework | Flutter, React Native |

👉 Cette liste devient vos **mots-clés de veille**. Elle est consignée dans le livrable [`veille-securite/01-plan-de-veille.md`](../veille-securite/01-plan-de-veille.md).

## 2. Formuler des objectifs SMART

Mauvais objectif : *« Me tenir au courant de la cybersécurité. »*

Bons objectifs :

- *« Être alerté sous 48 h de toute vulnérabilité critique (CVSS ≥ 9) affectant Spring Boot, PostgreSQL ou Nginx. »*
- *« Lire et résumer une catégorie de l'OWASP Top 10 par semaine pendant 10 semaines. »*
- *« Produire une synthèse mensuelle de veille d'une page pour mon équipe / mon dossier de projet. »*

## 3. Définir trois cercles de veille

```
        ┌──────────────────────────────────────────────┐
        │  Cercle 3 — Culture générale cyber            │  ← 15 min / semaine
        │  (grandes attaques, tendances, réglementation)│
        │   ┌──────────────────────────────────────┐   │
        │   │ Cercle 2 — Bonnes pratiques dév sécu  │   │  ← 30 min / semaine
        │   │ (OWASP, ANSSI, DevSecOps, auth…)       │   │
        │   │   ┌──────────────────────────────┐    │   │
        │   │   │ Cercle 1 — MA pile technique │    │   │  ← alertes en continu
        │   │   │ (CVE, advisories, patchs)    │    │   │
        │   │   └──────────────────────────────┘    │   │
        │   └──────────────────────────────────────┘   │
        └──────────────────────────────────────────────┘
```

- **Cercle 1** : critique, actionnable → alertes automatiques, réaction rapide.
- **Cercle 2** : améliore votre façon de coder → lecture régulière.
- **Cercle 3** : culture, contexte, oral du jury → lecture opportuniste.

## 4. Thèmes de veille recommandés pour un CDA

- **OWASP Top 10** (applications web) et **OWASP API Security Top 10** (API REST)
- **Authentification** : hachage (bcrypt, Argon2), MFA, passkeys/WebAuthn, OAuth2/OIDC, JWT (pièges)
- **Sécurité de la chaîne d'approvisionnement** : dépendances vulnérables, typosquatting, SBOM, signatures
- **Sécurité des conteneurs et de la CI/CD** : images de base, secrets, permissions des pipelines
- **Sécurité et IA** : OWASP Top 10 for LLM Applications (injection de prompt, fuite de données) si votre application intègre un LLM
- **Protection des données** : RGPD, Privacy by Design, chiffrement, journalisation
- **Réglementation** : recommandations CNIL et ANSSI, NIS 2, Cyber Resilience Act

## 5. Checklist de fin d'étape

- [ ] Ma pile technique est listée avec les versions.
- [ ] J'ai 2 à 4 objectifs SMART.
- [ ] J'ai classé mes thèmes dans les 3 cercles.
- [ ] J'ai estimé le temps hebdomadaire que je peux y consacrer (réaliste !).
