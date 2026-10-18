<div align="center">

# 🇫🇷 Monitor Budget

**Moniteur open source des données budgétaires publiques françaises — en un seul fichier HTML.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub last commit](https://img.shields.io/github/last-commit/gunout/monitor-budget)](https://github.com/gunout/monitor-budget/commits)
[![GitHub issues](https://img.shields.io/github/issues/gunout/monitor-budget)](https://github.com/gunout/monitor-budget/issues)
[![GitHub stars](https://img.shields.io/github/stars/gunout/monitor-budget?style=social)](https://github.com/gunout/monitor-budget/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/gunout/monitor-budget?style=social)](https://github.com/gunout/monitor-budget/network/members)

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![API](https://img.shields.io/badge/API-data.gouv.fr-000091)](https://www.data.gouv.fr/api)
[![Backend](https://img.shields.io/badge/backend-none-success)](#)
[![DSFR](https://img.shields.io/badge/design-DSFR-000091)](https://www.systeme-de-design.gouv.fr/)

[🚀 Démarrage](#-démarrage-rapide) · [✨ Fonctionnalités](#-fonctionnalités) · [🏷️ Catégories](#️-catégories-intégrées) · [🛠️ Stack](#️-stack-technique) · [📄 Licence](#-licence)

</div>

---

## 📖 À propos

**Monitor Budget** est un tableau de bord **mono-fichier** qui interroge directement l'[API publique de data.gouv.fr](https://www.data.gouv.fr/api) et affiche en temps réel les jeux de données liés au **budget de l'État français**, toutes années confondues.

Aucun backend, aucun build, aucune dépendance npm. Un fichier HTML, un navigateur, et c'est parti.

> Conçu pour les journalistes, chercheurs, citoyens et agents publics qui veulent **explorer et surveiller** les données budgétaires sans écrire une ligne de code.

---

## ✨ Fonctionnalités

- 🏷️ **7 catégories budgétaires** prêtes à l'emploi (PLF, Budget vert, Collectivités, etc.)
- 📅 **Filtre temporel** : 2021 → 2026
- 🔀 **Tri avancé** : plus récents · plus anciens · populaires
- 📄 **3 vues** : Résultats · JSON brut · Timings
- 📥 **Exports** CSV / JSON côté client
- 📊 **Panneau Intelligence** : latence API, uptime session, activité récente
- 🎨 **Design DSFR** (Système de Design de l'État)
- 📱 **Responsive** : mobile, tablette, desktop
- 🌐 **0 dépendance** à l'exécution (hors CDN DSFR)

---

## 🚀 Démarrage rapide

### Option 1 — Cloner le dépôt

    git clone https://github.com/gunout/monitor-budget.git
    cd monitor-budget

### Option 2 — Télécharger directement

    curl -O https://raw.githubusercontent.com/gunout/monitor-budget/main/budget-monitor.html

### Ouvrir le moniteur

    # Linux
    xdg-open budget-monitor.html

    # macOS
    open budget-monitor.html

    # Windows
    start budget-monitor.html

Ou simplement **double-cliquer** sur `budget-monitor.html` dans ton explorateur de fichiers.

> ℹ️ L'API `data.gouv.fr/api/2` autorise les requêtes cross-origin (CORS `*`) — **aucun serveur local n'est nécessaire**.

---

## 🧭 Utilisation

| Action | Résultat |
|---|---|
| Cliquer sur une **catégorie** (sidebar) | Filtre la recherche sur ce thème |
| Choisir une **année** | Ajoute `2026` / `2025`… à la requête |
| Changer le **tri** | Réordonne par date ou popularité |
| `Entrée` dans la barre de recherche | Lance la recherche |
| **📥 Export CSV/JSON** | Télécharge les résultats affichés |
| **🗑️ Effacer** | Réinitialise l'état |

### Exemples de requêtes

    budget vert 2026
    PLF 2025
    budget commune 2024
    dépenses fiscales
    comptes publics 2023

---

## 🏷️ Catégories intégrées

| Catégorie | Requête injectée | Source typique |
|---|---|---|
| 🏛️ PLF / Budget de l'État | `PLF` | Direction du Budget |
| 🌿 Budget vert | `budget vert` | Ministère de la Transition écologique |
| 🏘️ Collectivités locales | `budget collectivité` | DGCL |
| 🏙️ Communes | `budget commune` | DGFiP |
| 💸 Dépenses fiscales | `dépenses fiscales` | DGFiP |
| 📊 Comptes publics | `comptes publics` | Cour des comptes |
| 🏗️ Investissement local | `investissement public local` | Banque des Territoires |

---

## 🛠️ Stack technique

| Composant | Technologie |
|---|---|
| **Frontend** | HTML5 + CSS3 (variables, grid, flexbox) |
| **Logique** | JavaScript vanilla (ES2020) |
| **API** | data.gouv.fr/api/2 |
| **Design** | DSFR 1.11.2 (CDN) |
| **Exports** | Blob API native |
| **Zéro build** | Aucun npm, webpack, ou transpileur |

---

## 📁 Structure du projet

    monitor-budget/
    ├── budget-monitor.html   ← l'application complète (HTML + CSS + JS)
    ├── README.md             ← ce fichier
    └── LICENSE               ← MIT

---

## 🔧 Personnalisation

### Changer les catégories

Ouvre `budget-monitor.html`, cherche le bloc `const CATEGORIES` et modifie-le :

    const CATEGORIES = [
      { id: "plf", nom: "PLF", icon: "🏛️", color: "#000091", query: "PLF" },
      // Ajoute tes propres catégories ici
    ];

### Changer l'API

Par défaut, le moniteur utilise l'API v2. Pour basculer sur l'API v1 (plus stable) :

    const API_V2 = 'https://www.data.gouv.fr/api/1/datasets/';

### Changer le tri par défaut

    <select id="sortSelect">
      <option value="recent" selected>📅 Plus récents</option>
      <!-- ... -->
    </select>

---

## ⚠️ Limites connues

- L'API v2 de data.gouv.fr est **en beta** — son schéma peut évoluer sans préavis.
- L'API applique un **ET strict** : `budget 2026` ne renvoie que les datasets contenant *les deux* mots.
- Pas de cache persistant : chaque recherche refait un appel réseau.
- Les exports sont limités aux résultats actuellement affichés (pas d'export « tout »).

---

## 🗺️ Roadmap

- [x] **v1.0** — Moniteur mono-fichier avec catégories
- [ ] **v1.1** — Vue graphique (Chart.js) — datasets budget par année
- [ ] **v1.2** — Filtre par organisation (Direction du Budget, DGFiP, etc.)
- [ ] **v1.3** — Mode comparaison (2024 vs 2025 vs 2026)
- [ ] **v2.0** — Version PWA (offline + installable)
- [ ] **v2.1** — Backend FastAPI optionnel pour cache + exports massifs

---

## 🤝 Contribution

Les contributions sont **les bienvenues** !

1. Fork le projet
2. Crée une branche (`git checkout -b feature/ma-fonctionnalite`)
3. Commit tes changements (`git commit -m 'Ajout de ma fonctionnalité'`)
4. Push (`git push origin feature/ma-fonctionnalite`)
5. Ouvre une Pull Request

### Signaler un bug

Ouvre une [issue](https://github.com/gunout/monitor-budget/issues) en précisant :

- Le navigateur et sa version
- Les étapes pour reproduire
- Le comportement attendu vs observé

---

## 📄 Licence

Distribué sous licence **MIT**. Voir `LICENSE` pour plus d'informations.

Les **données** affichées proviennent de [data.gouv.fr](https://www.data.gouv.fr) et sont soumises à leur propre licence (majoritairement [Licence Ouverte 2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence)).

---

## 🙏 Remerciements

- [data.gouv.fr](https://www.data.gouv.fr) — pour l'API publique
- [Etalab](https://www.etalab.gouv.fr) — pour l'ouverture des données
- [DSFR](https://www.systeme-de-design.gouv.fr) — pour le design system de l'État
- [Shields.io](https://shields.io) — pour les badges

---

<div align="center">

**⭐ Si ce projet t'est utile, mets-lui une étoile ! ⭐**

[Signaler un bug](https://github.com/gunout/monitor-budget/issues) · [Proposer une fonctionnalité](https://github.com/gunout/monitor-budget/issues) · [Contribuer](https://github.com/gunout/monitor-budget/pulls)

Fait avec 🇫🇷 pour les données publiques françaises.

</div>
