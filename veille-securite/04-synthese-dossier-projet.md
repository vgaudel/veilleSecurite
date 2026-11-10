# Veille sur les vulnérabilités de sécurité — texte pour le dossier de projet

> Texte **modèle** à adapter à votre projet et à votre veille réelle (environ une page).
> Vérifiez la place et le format attendus de cette partie dans le Référentiel d'Évaluation du titre CDA (RNCP 37873) en vigueur et auprès de votre formateur.
> ⚠️ Ne citez que ce que vous avez **réellement fait** : le jury vous interrogera dessus.

---

## Veille sur les vulnérabilités de sécurité

### Démarche

Tout au long du projet, j'ai mené une veille sur les vulnérabilités de sécurité ciblée sur la pile technique de l'application : _React, Spring Boot, PostgreSQL, Nginx et Docker_. J'ai organisé cette veille en trois niveaux :

1. **Alertes sur mes composants**, en mode push : flux RSS des alertes et avis du **CERT-FR**, abonnement **OpenCVE** aux produits utilisés, et alertes **Dependabot** activées sur le dépôt GitHub.
2. **Bonnes pratiques de développement sécurisé** : étude hebdomadaire d'une catégorie de l'**OWASP Top 10** et de l'**OWASP API Security Top 10**, appuyée sur les *OWASP Cheat Sheets*.
3. **Culture sécurité et réglementation** : actualité (sources francophones et anglophones), recommandations **CNIL** et **ANSSI**.

Les informations sont centralisées dans un agrégateur (_Inoreader_), puis triées selon une grille de priorisation (composant concerné, score CVSS, exploitation active). Chaque sujet retenu fait l'objet d'une fiche de veille en Markdown versionnée dans un dépôt Git, avec une synthèse mensuelle. _J'y consacre environ 10 minutes par jour et 45 minutes chaque semaine._

### Exemples et impacts sur le projet

- **Contrôle d'accès défaillant (OWASP A01)** : en étudiant cette catégorie, j'ai audité les endpoints de l'API et identifié _deux routes qui vérifiaient l'authentification mais pas la propriété de la ressource_ (vulnérabilité de type IDOR). J'ai corrigé les requêtes pour filtrer par propriétaire et ajouté des tests d'intégration vérifiant qu'un utilisateur ne peut pas accéder aux réservations d'un autre.
- **Dépendances vulnérables** : _une alerte Dependabot a signalé une vulnérabilité de déni de service (CVSS 7.5) dans une dépendance front-end_. Après lecture de l'advisory, j'ai mis à jour la dépendance et vérifié l'absence de régression. L'étude du cas **Log4Shell** m'a également conduit à vérifier l'arbre de dépendances Maven et à intégrer **OWASP Dependency-Check** à la CI.
- **Attaques sur la chaîne d'approvisionnement** : l'analyse du détournement du CDN **polyfill.io** m'a conduit à n'utiliser aucun script tiers et à configurer une **Content Security Policy** restrictive dans Nginx.
- **Stockage des mots de passe** : la consultation de l'*OWASP Password Storage Cheat Sheet* m'a permis de valider l'utilisation de bcrypt et de planifier une migration vers Argon2id.

### Bilan et axes d'amélioration

Cette veille m'a permis de corriger des failles réelles avant la mise en production et d'acquérir des réflexes de développement sécurisé. Ses limites : _le temps disponible restreint l'étude approfondie, et certaines alertes génèrent du bruit_. Pour progresser, je prévois _d'automatiser davantage (scan d'images Docker avec Trivy, analyse statique avec SonarQube) et de partager régulièrement une synthèse avec l'équipe_.

*Sources principales : cert.ssi.gouv.fr, owasp.org, cheatsheetseries.owasp.org, github.com/advisories, nvd.nist.gov, cnil.fr.*
