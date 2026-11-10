# Liste des abonnements pour ce sujet de veille : sécurité des applications

> Cochez la colonne « Actif » **uniquement** quand l'abonnement est réellement configuré.
> Revoir cette liste chaque mois : supprimer les sources jamais lues, ajouter celles qui manquent.

## Cercle 1 — Alertes sur ma pile technique (push, quotidien)

| Source | Type | Comment s'abonner | Actif |
|---|---|---|---|
| CERT-FR — Alertes | RSS / e-mail | [cert.ssi.gouv.fr](https://www.cert.ssi.gouv.fr/) → flux RSS « Alertes » | ☐ |
| CERT-FR — Avis | RSS | Flux RSS « Avis » (filtrer sur ses mots-clés dans l'agrégateur) | ☐ |
| OpenCVE | E-mail | [opencve.io](https://www.opencve.io/) → s'abonner aux éditeurs/produits de sa pile | ☐ |
| GitHub Dependabot | Alerte dépôt | *Settings → Code security* → activer *Dependabot alerts* et *security updates* | ☐ |
| GitHub Advisory Database | Web / RSS | [github.com/advisories](https://github.com/advisories), filtrer par écosystème | ☐ |
| Advisories de mon framework | RSS / e-mail | Ex. [spring.io/security](https://spring.io/security), [symfony.com/blog/category/security-advisories](https://symfony.com/blog/category/security-advisories), [nodejs.org/en/blog/vulnerability](https://nodejs.org/en/blog/vulnerability) | ☐ |
| CISA KEV | RSS / e-mail | [cisa.gov/known-exploited-vulnerabilities-catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | ☐ |

## Cercle 2 — Développement sécurisé (hebdomadaire)

| Source | Type | Lien | Actif |
|---|---|---|---|
| OWASP Top 10 / API Security Top 10 | Référentiel | [owasp.org/Top10](https://owasp.org/Top10/), [owasp.org/API-Security](https://owasp.org/API-Security/) | ☐ |
| OWASP Cheat Sheet Series | Référentiel | [cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/) | ☐ |
| ANSSI — guides et recommandations | Web | [cyber.gouv.fr](https://cyber.gouv.fr/) | ☐ |
| CNIL — Guide RGPD de l'équipe de développement | Web | [cnil.fr](https://www.cnil.fr/) (rechercher « guide développeur ») | ☐ |
| PortSwigger Web Security Academy | Cours / labs | [portswigger.net/web-security](https://portswigger.net/web-security) | ☐ |
| tl;dr sec | Newsletter (EN) | [tldrsec.com](https://tldrsec.com/) | ☐ |

## Cercle 3 — Culture cyber (hebdomadaire)

| Source | Langue | Lien | Actif |
|---|---|---|---|
| Cybermalveillance.gouv.fr — actualités | FR | [cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/) | ☐ |
| LeMagIT — Sécurité | FR | [lemagit.fr](https://www.lemagit.fr/) | ☐ |
| NoLimitSecu (podcast) | FR | [nolimitsecu.fr](https://www.nolimitsecu.fr/) | ☐ |
| BleepingComputer | EN | [bleepingcomputer.com](https://www.bleepingcomputer.com/) | ☐ |
| The Hacker News | EN | [thehackernews.com](https://thehackernews.com/) | ☐ |
| Krebs on Security | EN | [krebsonsecurity.com](https://krebsonsecurity.com/) | ☐ |

## Outils

| Outil | Rôle | Configuré |
|---|---|---|
| _Inoreader / Feedly_ | Agrégateur RSS (dossiers Cercle 1/2/3) | ☐ |
| _Google Alerts_ | Requêtes : `"<framework>" vulnerability`, `"<framework>" CVE` | ☐ |
| _npm audit / Dependency-Check / Trivy_ | Audit dans la CI | ☐ |
