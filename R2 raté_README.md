# 📅 EPS — Emploi du Temps · Collège Pasteur Villemomble

Application web autonome de visualisation des emplois du temps EPS, déployable en un seul fichier HTML sur GitHub Pages.

---

## ✨ Fonctionnalités

- **Vue semaine** — grille complète Lundi → Vendredi avec tous les créneaux (M1 à S4)
- **Vue par enseignant** — grille dédiée par prof, n'affiche que les jours travaillés
- **Vue récap** — compteur de créneaux + fiches synthétiques par enseignant
- **Filtre par enseignant** — isolation visuelle depuis la sidebar
- **Tooltip au survol** — affiche enseignant, classe et note (piscine, AS…)
- **Icônes spéciales** : 🏊 piscine · ⭐ AS · ♿ ULIS
- **Zéro dépendance** — un seul fichier HTML, Google Fonts en seule ressource externe

---

## 👩‍🏫 Équipe EPS

| Enseignant | Couleur | Particularités |
|------------|---------|----------------|
| Clément    | 🔴 Rouge  | Accompagnement piscine mardi & jeudi |
| Anne       | 🔵 Bleu   | Accompagnement piscine mardi |
| Pauline    | 🟢 Vert   | Accompagnement piscine mardi & jeudi · ULIS vendredi |
| Steven     | 🟠 Orange | Accompagnement piscine jeudi |
| Louis      | 🟣 Violet | AS Gymnastique & Tennis de table |

---

## 🕐 Créneaux horaires

| Créneau | Horaire |
|---------|---------|
| M1 | 08h25 – 09h20 |
| M2 | 09h25 – 10h20 |
| M3 | 10h35 – 11h30 |
| M4 | 11h35 – 12h30 |
| — | Pause méridienne |
| S1 | 13h30 – 14h25 |
| S2 | 14h30 – 15h25 |
| S3 | 15h30 – 16h25 |
| S4 | 16h30 – 17h25 |

Les créneaux doubles (ex. M3&M4) sont affichés comme un seul bloc.

---

## 📂 Structure du projet

```
/
├── EPS_Emploi_du_Temps.html   # Application complète (fichier unique)
└── README.md                  # Ce fichier
```

---

## 🚀 Déploiement GitHub Pages

1. Pousser `EPS_Emploi_du_Temps.html` à la racine du dépôt (ou dans `/docs`)
2. Activer GitHub Pages dans les paramètres du dépôt
3. Accéder via `https://louisodilonschneider-web.github.io/<repo>/EPS_Emploi_du_Temps.html`

---

## 🛠️ Modifier les données

Toutes les données d'emploi du temps se trouvent dans l'objet `SCHEDULE` dans la balise `<script>` du fichier HTML.

### Structure d'un créneau

```js
SCHEDULE = {
  clement: {
    Mardi: {
      M1: { classe: '6ème A (piscine)', isPool: true, double: true, note: 'Accompagnement piscine' },
      M3: { classe: '3ème E' },
      // ...
    }
  }
}
```

### Propriétés disponibles

| Propriété | Type | Description |
|-----------|------|-------------|
| `classe` | string | Nom de la classe affichée |
| `double` | boolean | Créneau de 2h (occupe 2 lignes) |
| `isPool` | boolean | Affiche l'icône 🏊 |
| `isAS` | boolean | Affiche l'icône ⭐ (Association Sportive) |
| `isULIS` | boolean | Affiche l'icône ♿ |
| `note` | string | Note affichée dans le tooltip et la chip |

### Ajouter un enseignant

1. Ajouter une entrée dans l'objet `TEACHERS` avec `name`, `color` et `cls`
2. Définir la variable CSS correspondante `--c-prenom`
3. Ajouter les règles CSS `.chip-prenom`
4. Ajouter les données dans `SCHEDULE`
5. Ajouter le bouton dans la sidebar HTML

---

## 🎨 Design

- **Fond** : blanc (`#ffffff`)
- **Barre d'outils** : bleu marine (`#1d4e89`)
- **Typographie** : DM Serif Display (titres) · DM Sans (texte)
- **Palette enseignants** : rouge · bleu · vert · orange · violet

---

## 📋 AS — Associations Sportives

| Enseignant | AS | Horaire |
|------------|----|---------|
| Clément | Foot | Mercredi 13h30–16h30 |
| Anne | Danse | Mercredi 13h30–16h30 |
| Pauline | Basket | Mercredi 13h30–16h30 |
| Steven | Foot féminin | Lundi S1 |
| Steven | Tennis de table | Mardi S1 |
| Steven | Foot féminin | Jeudi S1 |
| Louis | Tennis de table | Lundi S1 |
| Louis | Gymnastique | Mercredi 13h–14h · Jeudi S1 |

---

*Projet EPS — Collège Pasteur · Villemomble · louisodilonschneider-web*
