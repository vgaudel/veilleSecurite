# Porte dérobée dans xz-utils — attaque sur la chaîne d'approvisionnement

> 📌 **Fiche d'exemple** — incident / supply chain.

| Champ | Valeur |
|---|---|
| **Date de la fiche** | _AAAA-MM-JJ_ |
| **Date de l'information** | 2024-03-29 |
| **Type** | Incident · Vulnérabilité (CVE) |
| **Identifiants** | CVE-2024-3094 · CWE-506 (code malveillant intégré) |
| **Gravité** | CVSS 10.0 (Critique) |
| **Composants concernés** | xz-utils / liblzma **5.6.0 et 5.6.1** — principalement des versions de développement de distributions Linux (ex. Debian unstable, Fedora Rawhide / 40 bêta) |
| **Priorité pour mon projet** | ⚪ P4 (vérifié non concerné) |
| **Tags** | #supply-chain #open-source #linux #ssh #ingenierie-sociale |

## Sources

1. [Message initial d'Andres Freund — oss-security (Openwall)](https://www.openwall.com/lists/oss-security/2024/03/29/4)
2. [NVD — CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094)
3. [CERT-FR — bulletins et avis de la période](https://www.cert.ssi.gouv.fr/)

## Résumé

Un contributeur (pseudonyme « Jia Tan ») a gagné la confiance du projet open source xz-utils pendant environ **deux ans**, jusqu'à en devenir co-mainteneur, puis a dissimulé une porte dérobée dans les **archives de publication** (pas directement dans le code visible du dépôt). Sur certaines distributions, elle visait le serveur SSH et aurait pu permettre une prise de contrôle à distance. Elle a été découverte **par hasard** par un ingénieur intrigué par une lenteur de connexion SSH de ~500 ms, avant d'atteindre les versions stables des grandes distributions.

## Explication technique

- Le code malveillant était caché dans des fichiers de test binaires et activé par le script de build présent uniquement dans les tarballs publiés.
- `liblzma` était chargée indirectement par `sshd` via `libsystemd` sur certaines distributions, ce qui permettait de détourner l'authentification.
- L'attaque est avant tout **humaine** : pression sur le mainteneur épuisé, faux comptes réclamant un nouveau mainteneur.

## Impact sur mon projet

- Image Docker de base : _eclipse-temurin sur Ubuntu LTS_ → xz-utils en version 5.4.x / 5.2.x non concernée.
- Vérification :

  ```bash
  docker run --rm <mon-image> sh -c "xz --version"
  ```

## Action menée

- [x] Vérification de la version dans l'image (non concernée).
- [x] Ajout d'un scan Trivy de l'image dans la CI.

## Ce que j'en retiens

- La sécurité de l'open source dépend de **personnes**, souvent bénévoles et surchargées.
- Le code publié (artefacts) peut différer du code source du dépôt : intérêt des **builds reproductibles**, des signatures et des SBOM.
- Éviter les versions de développement / *rolling* en production.
