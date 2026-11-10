# 04 — Organiser sa veille

La meilleure veille est celle qu'on **tient dans la durée**. Objectif : une routine courte, régulière, et une trace écrite exploitable.

## 1. Le cycle de veille

```
  1. Collecter ──► 2. Trier ──► 3. Analyser ──► 4. Capitaliser ──► 5. Diffuser / Agir
       ▲                                                                   │
       └───────────────────── 6. Ajuster les sources ◄─────────────────────┘
```

| Étape | Action concrète | Outil |
|---|---|---|
| Collecter | Les flux arrivent automatiquement | Feedly / Inoreader, alertes, Dependabot |
| Trier | Lecture des titres, 80 % sont ignorés ou archivés | Agrégateur (marquer lu / sauvegarder) |
| Analyser | Pour les 20 % restants : suis-je concerné ? quelle gravité ? | Grille de priorisation (ci-dessous) |
| Capitaliser | Rédiger une **fiche de veille** | Modèle Markdown |
| Diffuser / Agir | Patch, ticket, message à l'équipe, synthèse mensuelle | Git, Jira/Trello, Slack/Teams |
| Ajuster | Supprimer les sources bruyantes, en ajouter | Revue mensuelle |

## 2. Une routine réaliste

| Fréquence | Durée | Activité |
|---|---|---|
| **Quotidien** | 5–10 min | Survol des alertes (cercle 1) : CERT-FR, Dependabot, OpenCVE |
| **Hebdomadaire** | 30–45 min | Lecture approfondie de 2–3 articles, 1 fiche de veille rédigée |
| **Mensuel** | 1 h | Synthèse mensuelle, mise à jour du plan, nettoyage des sources |

> 💡 Bloquez le créneau dans votre agenda (ex. lundi 9 h–9 h 30). Une veille « quand j'ai le temps » n'existe pas.

## 3. Grille de priorisation

Pour chaque vulnérabilité repérée, répondez à ces questions :

| Question | Si oui → |
|---|---|
| Touche-t-elle un composant **de ma pile** et **dans ma version** ? | Sinon : simple culture, pas d'action |
| Score CVSS ≥ 9 (critique) ? | Priorité haute |
| Présente dans le **catalogue KEV** ou exploitation active signalée ? | Priorité **urgente** |
| EPSS élevé (> 0,1) ou PoC public ? | Priorité haute |
| Composant exposé sur Internet ? | Augmente la priorité |
| Correctif ou contournement disponible ? | Planifier la mise à jour |

Niveaux de priorité proposés :

- 🔴 **P1 – Urgent** : exploitée activement, me concerne → correction sous 24–48 h
- 🟠 **P2 – Élevé** : critique/élevée, me concerne → correction dans le sprint
- 🟡 **P3 – Modéré** : me concerne, faible exploitabilité → backlog
- ⚪ **P4 – Info** : ne me concerne pas directement → culture / partage

## 4. Rédiger une fiche de veille

Une fiche = **une information**, rédigée **avec vos mots**, en **10 minutes maximum**. Modèle : [`veille-securite/fiches/_MODELE-fiche.md`](../veille-securite/fiches/_MODELE-fiche.md).

Contenu minimal :

1. **Titre, date, source(s)** (avec lien)
2. **Résumé** en 3–5 lignes (quoi, qui est concerné, gravité)
3. **Impact pour mon projet** (concerné / pas concerné, pourquoi)
4. **Action** (mise à jour, configuration, rien)
5. **Ce que j'en retiens** (bonne pratique, notion apprise)
6. **Tags** (`#owasp-a03`, `#spring`, `#supply-chain`…)

## 5. Organiser ses fichiers

Arborescence conseillée (celle de ce dépôt) :

```
veille-securite/
├── 01-plan-de-veille.md          ← périmètre, objectifs, routine
├── 02-journal-de-veille.md       ← une ligne par élément lu
├── fiches/                       ← une fiche par sujet analysé
│   ├── _MODELE-fiche.md
│   └── AAAA-MM-JJ-sujet.md
├── 03-synthese-mensuelle.md      ← synthèse diffusable
├── 04-synthese-dossier-projet.md ← texte pour le dossier de projet
└── 05-atelier-partage.md         ← support de l'atelier de partage
```

Conventions :

- Nom de fiche : `AAAA-MM-JJ-mot-cle.md` (tri chronologique automatique).
- Un commit Git par session de veille : `veille: fiche log4shell + MAJ journal`. L'historique Git **prouve** la régularité de votre veille.

## 6. Pièges à éviter

- **Infobésité** : 50 flux RSS non lus = aucune veille. Commencez avec 8–10 sources.
- **Collectionner sans lire** : sauvegarder 100 liens n'est pas faire de la veille.
- **Copier-coller** : une fiche reformulée prouve la compréhension ; un copier-coller, non.
- **Rester passif** : lire une faille sans vérifier si votre projet est concerné.
- **Croire une seule source** : recoupez avec CERT-FR, l'éditeur ou NVD.
- **Négliger l'anglais** : la majorité des sources primaires sont anglophones.
- **Surcharger son agenda** : mieux vaut 20 minutes chaque semaine que 3 heures une fois.
