# OWASP Top 10 — A01 : Contrôle d'accès défaillant (Broken Access Control)

> 📌 **Fiche d'exemple** — catégorie OWASP.

| Champ | Valeur |
|---|---|
| **Date de la fiche** | _AAAA-MM-JJ_ |
| **Type** | Catégorie OWASP |
| **Identifiants** | OWASP Top 10 A01 · CWE-284, CWE-285, CWE-639 (IDOR), CWE-862 · OWASP API Security API1 (BOLA) |
| **Gravité** | 1re place du Top 10 2021, maintenue en tête dans l'édition 2025 |
| **Priorité pour mon projet** | 🟠 P2 |
| **Tags** | #owasp #controle-acces #idor #api #spring-security |

## Sources

1. [OWASP Top 10 — A01 Broken Access Control](https://owasp.org/Top10/)
2. [OWASP API Security Top 10 — API1 Broken Object Level Authorization](https://owasp.org/API-Security/)
3. [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)

## Résumé

Le contrôle d'accès garantit qu'un utilisateur ne peut agir **que dans les limites de ses droits**. Il est défaillant quand un utilisateur peut consulter, modifier ou supprimer des données d'un autre utilisateur, ou accéder à des fonctions d'administration. C'est la catégorie la plus fréquemment rencontrée lors des tests d'applications.

## Explication technique

Cas le plus courant en API REST : **IDOR / BOLA** — on vérifie que l'utilisateur est *authentifié*, mais pas qu'il est *propriétaire* de la ressource.

```java
// ❌ Vulnérable : tout utilisateur connecté peut lire n'importe quelle réservation
@GetMapping("/reservations/{id}")
public Reservation get(@PathVariable Long id) {
    return repository.findById(id).orElseThrow();
}

// ✅ Corrigé : la requête est restreinte au propriétaire
@GetMapping("/reservations/{id}")
public Reservation get(@PathVariable Long id, @AuthenticationPrincipal Utilisateur user) {
    return repository.findByIdAndProprietaireId(id, user.getId())
                     .orElseThrow(() -> new ResponseStatusException(HttpStatus.NOT_FOUND));
}
```

Autres formes : élévation de privilèges (rôle modifiable dans le corps de requête), routes d'admin seulement cachées côté front, CORS trop permissif, JWT non vérifié ou modifiable.

## Impact sur mon projet

- Revue des 12 endpoints de l'API : _2 endpoints ne vérifiaient que l'authentification_ (`GET /reservations/{id}`, `DELETE /reservations/{id}`).
- Les routes `/admin/**` sont bien protégées par `hasRole('ADMIN')` côté serveur.

## Action menée

- [x] Correction des 2 endpoints (requête filtrée par propriétaire).
- [x] Ajout de tests d'intégration : « l'utilisateur B reçoit 404 sur la réservation de A ».
- Lien : _PR #__

## Ce que j'en retiens

- **Refuser par défaut** (deny by default) et contrôler côté serveur, jamais seulement dans le front.
- Pour chaque endpoint, se poser la question : *« Et si je change l'identifiant dans l'URL ? »*
- Les tests de contrôle d'accès font partie du plan de tests.
