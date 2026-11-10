# Atelier « Partage de connaissances » — support de présentation

> **Format** : 10 minutes de présentation + 5 minutes de questions, devant la promotion.
> **Sujet** : une notion de sécurité issue de **votre** veille (une de vos fiches).
> Ci-dessous : la consigne, une trame, puis un exemple rédigé.

## Consigne

1. Choisir **une** fiche de veille (vulnérabilité, catégorie OWASP, bonne pratique, incident).
2. Préparer une présentation qui permette à vos collègues de **comprendre** la notion et de **vérifier leur propre projet**.
3. Terminer par une **checklist actionnable** et vos sources.
4. Option : une démo (code vulnérable puis corrigé, outil d'audit, lab PortSwigger).

## Trame (≈ 6 diapositives)

| # | Contenu | Durée |
|---|---|---|
| 1 | **Accroche** : un fait, un incident, une question | 1 min |
| 2 | **De quoi parle-t-on ?** Définition simple + vocabulaire (CVE, CWE, CVSS…) | 2 min |
| 3 | **Comment ça marche ?** Mécanisme, schéma ou code vulnérable | 2 min |
| 4 | **Démo / exemple concret** dans un projet | 2 min |
| 5 | **Comment s'en protéger ?** Code corrigé, configuration, outils | 2 min |
| 6 | **Checklist + sources** + comment j'ai trouvé l'info (ma démarche de veille) | 1 min |

## Exemple : « Changez l'ID dans l'URL » — le contrôle d'accès défaillant

**1. Accroche**
> « Connectez-vous à votre propre application, ouvrez `/api/reservations/12` et remplacez `12` par `13`. Qu'est-ce que vous voyez ? »

**2. De quoi parle-t-on ?**
- OWASP Top 10 — **A01 Broken Access Control** : n° 1 des risques applicatifs web.
- Authentification = *qui es-tu ?* · Autorisation = *as-tu le droit ?*
- IDOR / BOLA : accès à l'objet d'un autre utilisateur via son identifiant.

**3. Comment ça marche ?**
- L'endpoint vérifie le jeton JWT (authentifié ✅) mais pas le propriétaire de la ressource (autorisé ❌).

**4. Démo**
- Deux comptes A et B, requête `curl` avec le jeton de B sur la réservation de A → `200 OK` 😱.

**5. Se protéger**
- Filtrer les requêtes par propriétaire (`findByIdAndProprietaireId`), refuser par défaut, contrôles côté serveur.
- Tests d'intégration « utilisateur B → 404 ».
- Ne pas exposer d'identifiants séquentiels prévisibles quand ce n'est pas nécessaire (UUID) — en complément, **jamais à la place** du contrôle.

**6. Checklist pour vos projets**
- [ ] Chaque endpoint qui prend un `{id}` vérifie le propriétaire ou le rôle.
- [ ] Les routes admin sont protégées côté serveur.
- [ ] Le rôle de l'utilisateur ne peut pas être modifié par le corps de requête.
- [ ] Un test automatisé couvre l'accès croisé entre deux utilisateurs.

*Sources : OWASP Top 10 (A01), OWASP API Security Top 10 (API1), OWASP Authorization Cheat Sheet.*
*Trouvé grâce à : ma routine hebdomadaire « une catégorie OWASP par semaine ».*

## Grille d'évaluation par les pairs

| Critère | 1 | 2 | 3 |
|---|---|---|---|
| La notion est clairement expliquée | ☐ | ☐ | ☐ |
| Un exemple concret / démo illustre le propos | ☐ | ☐ | ☐ |
| Je sais quoi vérifier dans mon propre projet | ☐ | ☐ | ☐ |
| Les sources sont citées et fiables | ☐ | ☐ | ☐ |
| Le temps est respecté | ☐ | ☐ | ☐ |
