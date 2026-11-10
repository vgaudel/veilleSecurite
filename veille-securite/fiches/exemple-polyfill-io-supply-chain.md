# Détournement du CDN polyfill.io — script tiers devenu malveillant

> 📌 **Fiche d'exemple** — supply chain côté front-end.

| Champ | Valeur |
|---|---|
| **Date de la fiche** | _AAAA-MM-JJ_ |
| **Date de l'information** | 2024-06-25 (alerte publique) |
| **Type** | Incident supply chain |
| **Identifiants** | Pas de CVE unique (compromission d'un service, pas d'une bibliothèque versionnée) |
| **Gravité** | Plus de 100 000 sites incluant le script au moment de l'alerte |
| **Priorité pour mon projet** | ⚪ P4 (vérifié non concerné) |
| **Tags** | #supply-chain #front-end #cdn #javascript #sri #csp |

## Sources

1. [Sansec — Polyfill supply chain attack](https://sansec.io/research/polyfill-supply-chain-attack)
2. [BleepingComputer — couverture de l'incident](https://www.bleepingcomputer.com/)
3. [MDN — Subresource Integrity](https://developer.mozilla.org/fr/docs/Web/Security/Subresource_Integrity)

## Résumé

Le domaine `polyfill.io`, qui servait des *polyfills* JavaScript à des centaines de milliers de sites via une simple balise `<script src="https://cdn.polyfill.io/...">`, a été **racheté** début 2024. Quelques mois plus tard, le service a commencé à injecter du code malveillant redirigeant certains visiteurs (surtout mobiles) vers des sites frauduleux. Tous les sites qui chargeaient ce script ont distribué le code malveillant **sans avoir modifié une ligne de leur propre code**.

## Explication technique

- Un script chargé depuis un domaine tiers s'exécute avec **les mêmes droits** que le code du site (accès au DOM, aux cookies non `HttpOnly`, aux formulaires…).
- Le contenu de polyfill.io était généré dynamiquement selon le navigateur → impossible d'utiliser un hash SRI fixe : la seule vraie protection était d'**héberger soi-même** le code ou de supprimer la dépendance.
- Les navigateurs modernes n'ont souvent plus besoin de ces polyfills.

```html
<!-- ❌ Script tiers non maîtrisé -->
<script src="https://cdn.exemple-tiers.com/lib.js"></script>

<!-- ✅ Si un CDN est indispensable : version figée + SRI -->
<script src="https://cdn.exemple.com/lib@1.2.3/lib.min.js"
        integrity="sha384-…" crossorigin="anonymous"></script>
```

## Impact sur mon projet

- Recherche dans le code : `grep -rn "polyfill.io" src/ public/` → aucun résultat.
- Le front est bundlé par Vite : toutes les dépendances sont servies depuis notre domaine.

## Action menée

- [x] Vérification (non concerné).
- [x] Ajout d'une en-tête **Content-Security-Policy** limitant `script-src` à `'self'` dans la configuration Nginx.

## Ce que j'en retiens

- Chaque script tiers est une **dépendance de confiance** : l'inventorier comme une dépendance npm.
- Préférer l'auto-hébergement ; sinon versions figées + SRI + CSP.
- Un nom de domaine peut changer de propriétaire : la confiance n'est pas éternelle.
