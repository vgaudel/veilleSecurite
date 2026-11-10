# Stockage des mots de passe : recommandations actuelles (Argon2id, bcrypt)

> 📌 **Fiche d'exemple** — bonne pratique.

| Champ | Valeur |
|---|---|
| **Date de la fiche** | _AAAA-MM-JJ_ |
| **Type** | Bonne pratique |
| **Identifiants** | OWASP Password Storage Cheat Sheet · CWE-916 (hachage insuffisant) · OWASP Top 10 « Défaillances cryptographiques » (A02:2021, A04:2025) et « Défaillances d'authentification » (A07) |
| **Priorité pour mon projet** | 🟡 P3 |
| **Tags** | #authentification #hachage #argon2 #bcrypt #spring-security #rgpd |

## Sources

1. [OWASP — Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
2. [CNIL — recommandation relative aux mots de passe (2022)](https://www.cnil.fr/)
3. [Spring Security — Password Storage](https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html)

## Résumé

Un mot de passe ne doit jamais être stocké en clair ni chiffré de façon réversible, ni haché avec un algorithme rapide (MD5, SHA-1, SHA-256 seul). Il faut un algorithme **volontairement lent et salé**. L'OWASP recommande en priorité **Argon2id**, puis scrypt, bcrypt (pour les systèmes existants) ou PBKDF2 (si une conformité FIPS est exigée), avec des paramètres de coût régulièrement réévalués.

## Explication technique

Paramètres minimaux indiqués par l'OWASP (à revérifier lors de chaque veille, ils évoluent) :

| Algorithme | Paramètres minimaux |
|---|---|
| Argon2id | mémoire 19 Mio, 2 itérations, parallélisme 1 |
| bcrypt | facteur de coût ≥ 10 ; attention : entrée limitée à 72 octets |
| PBKDF2-HMAC-SHA256 | 600 000 itérations |

Avec Spring Security, le `DelegatingPasswordEncoder` permet de **migrer progressivement** : les anciens hachés restent vérifiables (préfixe `{bcrypt}`), les nouveaux sont produits avec l'algorithme choisi.

```java
@Bean
PasswordEncoder passwordEncoder() {
    String idParDefaut = "argon2";
    Map<String, PasswordEncoder> encoders = Map.of(
        "argon2", Argon2PasswordEncoder.defaultsForSpringSecurity_v5_8(),
        "bcrypt", new BCryptPasswordEncoder());
    return new DelegatingPasswordEncoder(idParDefaut, encoders);
}
```

## Impact sur mon projet

- Actuel : `BCryptPasswordEncoder` avec le coût par défaut (10) → **acceptable**, pas de faille.
- Amélioration possible : passage à Argon2id pour les nouveaux comptes, re-hachage à la connexion.

## Action menée

- [ ] Ticket backlog « Migration vers Argon2id via DelegatingPasswordEncoder ».
- [x] Ajout d'une limitation du nombre de tentatives de connexion (contre la force brute).

## Ce que j'en retiens

- Hacher ≠ chiffrer. Hachage lent + sel unique par utilisateur (géré automatiquement par ces algorithmes).
- Les « bons » paramètres évoluent avec la puissance de calcul : c'est un **sujet de veille récurrent**.
- La CNIL donne aussi des règles sur la robustesse des mots de passe et le blocage après échecs : point RGPD à citer devant le jury.
