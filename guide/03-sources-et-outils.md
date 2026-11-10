# 03 — Sources et outils de veille sécurité

## 1. Pull ou push ?

| Méthode | Principe | Avantages | Inconvénients |
|---|---|---|---|
| **Pull** | Je vais chercher l'info (recherches, navigation) | Ciblé, sérendipité | Chronophage, irrégulier |
| **Push** | L'info vient à moi (RSS, alertes, newsletters, bots) | Régulier, automatisé | Risque de surcharge |

👉 Pour la sécurité : **push pour le cercle 1** (alertes sur ma pile), **mix pull/push** pour les cercles 2 et 3. Les deux méthodes ne sont pas exclusives.

## 2. Sources de référence

### Institutionnelles (fiabilité maximale)

| Source | Contenu | Accès |
|---|---|---|
| **CERT-FR** (ANSSI) | Alertes, avis de sécurité, bulletins d'actualité, en français | [cert.ssi.gouv.fr](https://www.cert.ssi.gouv.fr/) — flux RSS disponibles |
| **ANSSI** | Guides et recommandations (sécurité des applications web, des API, de Docker…) | [cyber.gouv.fr](https://cyber.gouv.fr/) |
| **CNIL** | RGPD, guide du développeur, sécurité des données | [cnil.fr](https://www.cnil.fr/) — notamment le *Guide RGPD de l'équipe de développement* |
| **Cybermalveillance.gouv.fr** | Actualité grand public, menaces en cours | [cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/) |
| **NVD (NIST)** | Base de données des CVE avec score CVSS | [nvd.nist.gov](https://nvd.nist.gov/) |
| **CVE Program** | Référentiel officiel des identifiants CVE | [cve.org](https://www.cve.org/) |
| **CISA KEV** | Catalogue des vulnérabilités **activement exploitées** | [cisa.gov/known-exploited-vulnerabilities-catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) |
| **ENISA** | Agence européenne, rapports sur les menaces | [enisa.europa.eu](https://www.enisa.europa.eu/) |

### Communautaires / développement sécurisé

| Source | Contenu |
|---|---|
| **OWASP** | Top 10, API Security Top 10, Top 10 LLM, ASVS, Cheat Sheet Series — **incontournable** ([owasp.org](https://owasp.org/), [cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/)) |
| **GitHub Advisory Database** | Vulnérabilités par écosystème (npm, Maven, PyPI, Composer, NuGet…) ([github.com/advisories](https://github.com/advisories)) |
| **OSV.dev** | Base agrégée de vulnérabilités open source, interrogeable par paquet ([osv.dev](https://osv.dev/)) |
| **OpenCVE** | Abonnement aux CVE par éditeur/produit avec alertes mail ([opencve.io](https://www.opencve.io/)) |
| **PortSwigger Web Security Academy** | Cours + labs gratuits sur les vulnérabilités web ([portswigger.net/web-security](https://portswigger.net/web-security)) |
| **Blogs sécurité des éditeurs** | Spring, Symfony, Node.js, Django, etc. publient leurs propres *security advisories* |

### Actualité (cercle 3)

- **Français** : Le Monde Informatique (rubrique sécurité), ZDNet.fr, LeMagIT, Zataz, podcast *NoLimitSecu*
- **Anglais** : BleepingComputer, The Hacker News, Krebs on Security, The Record, podcast *Darknet Diaries*, *Risky Business*

> 💡 L'anglais est indispensable : les advisories et la documentation sont publiées en anglais en premier. C'est aussi une compétence évaluée au titre.

## 3. Outils

### Agréger

| Outil | Usage |
|---|---|
| **Feedly**, **Inoreader**, **Netvibes** | Agrégateurs RSS (dossiers par cercle, filtres par mots-clés) |
| **Google Alerts** | Alertes par mot-clé (ex. `"Spring Boot" vulnerability`) |
| **Newsletters** | tl;dr sec, Snyk, Cybermalveillance, CERT-FR… |
| **Mastodon / LinkedIn / Bluesky** | Suivre chercheurs et éditeurs (avec modération du temps passé !) |
| **Discord / Slack** | Communautés techniques (canaux #security) |

### Automatiser la détection dans *son propre code* (veille « active »)

| Outil | Rôle |
|---|---|
| **Dependabot** / **Renovate** | Alertes + PR automatiques de mise à jour des dépendances vulnérables |
| `npm audit`, `composer audit`, `pip-audit`, `mvn dependency-check` (OWASP Dependency-Check) | Audit des dépendances en local ou en CI |
| **Trivy**, **Grype** | Scan d'images Docker et de dépendances |
| **OWASP ZAP** | Scan dynamique (DAST) de l'application en fonctionnement |
| **SonarQube / SonarCloud**, **Semgrep**, **CodeQL** | Analyse statique (SAST) |
| **Gitleaks**, **GitHub secret scanning** | Détection de secrets commités |

> Ces outils transforment la veille en action : une CVE lue dans un flux RSS **et** détectée par Dependabot sur votre projet, c'est un excellent exemple pour le jury.

### Capitaliser

| Outil | Usage |
|---|---|
| **Markdown + Git** (ce dépôt !) | Simple, versionné, partageable |
| **Notion**, **Obsidian**, **Confluence** | Base de connaissances, tags, liens |
| **Zotero**, **Raindrop.io**, **Pocket**-like | Sauvegarde et annotation de liens |

## 4. Évaluer la fiabilité d'une source (méthode rapide)

Pour chaque source, se demander :

1. **Qui** publie ? (organisme officiel, éditeur, chercheur identifié, blog anonyme)
2. **Quand** ? (date de publication et de mise à jour)
3. **Sources citées** ? (lien vers la CVE, l'advisory officiel, le commit de correctif)
4. **Recoupement** : l'info est-elle confirmée par une source officielle (CERT-FR, éditeur, NVD) ?
5. **Ton** : sensationnaliste (« la faille qui va tout détruire ») ou factuel ?

## 5. Lire une vulnérabilité : le vocabulaire minimum

| Terme | Signification |
|---|---|
| **CVE** | *Common Vulnerabilities and Exposures* — identifiant unique (ex. `CVE-2021-44228`) |
| **CWE** | *Common Weakness Enumeration* — type de faiblesse (ex. `CWE-89` injection SQL) |
| **CVSS** | Score de gravité de 0 à 10 (Faible < 4 ≤ Moyen < 7 ≤ Élevé < 9 ≤ Critique) |
| **EPSS** | Probabilité d'exploitation dans les 30 jours (0 à 1) |
| **KEV** | Vulnérabilité connue comme exploitée activement (catalogue CISA) |
| **Advisory** | Bulletin publié par l'éditeur ou un CERT décrivant faille + correctif |
| **0-day** | Faille exploitée avant qu'un correctif n'existe |
| **PoC** | *Proof of Concept* — code démontrant l'exploitation |
| **Supply chain attack** | Attaque via une dépendance, un outil de build ou un fournisseur |
