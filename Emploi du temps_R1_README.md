# 📅 EPS Emploi du Temps — Collège Pasteur

> Application web standalone de génération et gestion des emplois du temps de l'équipe EPS du Collège Pasteur (Villemomble).

---

## 🚀 Démarrage rapide

1. Ouvrez `emploi_du_temps_eps.html` dans votre navigateur (Chrome, Firefox, Edge recommandés)
2. Configurez les **journées libres** de chaque enseignant (onglet *Enseignants*)
3. Ajustez les **disponibilités des installations** (onglet *Installations*)
4. Choisissez l'**option piscine** (onglet *Contraintes*)
5. Cliquez sur **⚡ Générer l'EDT**
6. Vérifiez les conflits (onglet *Vérification*)

Aucune installation serveur requise. Tout fonctionne en local, avec persistance via `localStorage`.

---

## 👩‍🏫 Équipe EPS

| Enseignant | Heures min. | Particularités |
|---|---|---|
| Clément | 22h | — |
| Steven | 22h | — |
| Anne | 20h | Évite 4ème et 3ème (configurable) |
| Pauline | 20h | — |
| Louis | 18h | — |

---

## 🎓 Structure des classes

| Niveau | Nb classes | Volume horaire | Sessions |
|---|---|---|---|
| 6ème | 7 | 2h/semaine | 1 session de 2h |
| 5ème | 6 | 3h/semaine | 1 session de 2h + 1 session de 1h |
| 4ème | 6 | 3h/semaine | 1 session de 2h + 1 session de 1h |
| 3ème | 6 | 3h/semaine | 1 session de 2h + 1 session de 1h |
| ULIS | 1 | 1h/semaine | 1 session de 1h |

**Total : 26 classes — 72 heures EPS hebdomadaires**

---

## ⏰ Créneaux horaires

| Créneau | Horaire | Notes |
|---|---|---|
| M1 | 08h25 – 09h20 | |
| M2 | 09h25 – 10h20 | |
| M3 | 10h35 – 11h30 | |
| M4 | 11h35 – 12h30 | ⚠️ Déconseillé pour les 6ème |
| S1 | 13h00 – 13h55 | ⚠️ Déconseillé pour tous |
| S2 | 14h00 – 14h55 | |
| S3 | 15h10 – 16h05 | |
| S4 | 16h10 – 17h05 | |

> Le mercredi après-midi (S1–S4) est automatiquement exclu.

---

## 🏊 Créneaux piscine (6ème)

Les 7 classes de 6ème bénéficient de créneaux piscine dédiés. Deux options au choix :

### Option 1 (4+3)
- **Mardi M1+M2** : 4 classes de 6ème
- **Jeudi M3+M4** : 3 classes de 6ème

### Option 2 (3+3+1 sans piscine)
- **Mardi M1+M2** : 3 classes de 6ème
- **Jeudi M3+M4** : 3 classes de 6ème
- 1 classe de 6ème sans créneau piscine (EPS classique)

> La sélection se fait dans l'onglet **Contraintes** avant génération.

---

## 📋 Règles et contraintes appliquées

### Règle des 24h
Deux cours d'une même classe ne peuvent être programmés à moins de 24 heures d'intervalle. Par exemple, si la 6eB a cours le lundi M1 (8h25), son prochain cours ne peut être planifié avant le mardi M2 (9h25 au plus tôt — soit après 10h35).

### Journée + demi-journée libres
Chaque enseignant dispose d'une journée entière libre et d'une demi-journée libre (matin ou après-midi), configurables individuellement dans l'application. Ces contraintes sont strictement respectées lors de la génération.

### Heures minimales
- Clément & Steven : ≥ 22h
- Anne & Pauline : ≥ 20h
- Louis : ≥ 18h

### 1 classe de 6ème minimum par enseignant
Chaque enseignant se voit attribuer au minimum une classe de 6ème.

### Créneaux interdits / déconseillés
- **Interdit** : cours de 2h sur S3+S4 (15h10–17h05)
- **Déconseillé** : M4 pour les 6ème
- **Déconseillé** : S1 pour tous les niveaux

---

## 🏟️ Gestion des installations

L'application gère la disponibilité hebdomadaire de chaque installation :

| Installation | Capacité par défaut |
|---|---|
| Gymnase 1 | 2 groupes simultanés |
| Gymnase 2 | 1 groupe |
| Salle polyvalente | 1 groupe |
| Stade / Terrain ext. | 2 groupes (fermé mercredi) |
| Piscine | 2 groupes (créneaux fixes) |

Chaque installation dispose d'une **grille de disponibilité** modifiable créneau par créneau. Les cases vertes signifient "disponible", les rouges "indisponible". Les créneaux piscine (Mardi M1+M2, Jeudi M3+M4) sont fixes et non modifiables.

---

## 🖥️ Fonctionnalités de l'application

### Onglets
| Onglet | Fonctionnalité |
|---|---|
| 📊 Tableau de bord | Vue globale : heures par enseignant, classes planifiées, conflits |
| 👩‍🏫 Enseignants | Journée libre, demi-journée libre, préférences de niveaux |
| 🏟️ Installations | Grille de disponibilité cliquable par installation |
| ⚙️ Contraintes | Option piscine, rappel des règles |
| 📅 Emploi du Temps | Grille hebdomadaire interactive, vue par enseignant |
| ⚠️ Vérification | Détection automatique des conflits et violations |

### Génération algorithmique
- L'algorithme respecte toutes les contraintes dans l'ordre de priorité suivant :
  1. Créneaux piscine fixés
  2. Journées/demi-journées libres
  3. Disponibilités des installations
  4. Règle des 24h
  5. Heures minimales (équilibrage automatique)
  6. Préférences de niveaux
  7. Évitement des créneaux déconseillés

- Chaque génération produit un résultat différent (randomisation), permettant de comparer plusieurs options.

### Modification manuelle
Cliquez sur n'importe quel créneau dans la vue **Emploi du Temps** pour :
- Changer l'enseignant affecté
- Changer l'installation
- Supprimer le créneau

### Persistance et export
- Les données sont **sauvegardées automatiquement** dans `localStorage` (persistance entre sessions)
- **Export JSON** : bouton "📤 Exporter" → fichier horodaté
- **Import JSON** : bouton "📥 Importer" → rechargement complet
- **Impression** : bouton 🖨️ dans la sidebar de l'onglet EDT

---

## 🔄 Workflow recommandé

```
1. Configurer les enseignants (journées libres + préférences)
   ↓
2. Configurer les installations (disponibilités)
   ↓
3. Choisir l'option piscine
   ↓
4. Générer l'EDT (⚡)
   ↓
5. Vérifier les conflits (onglet ⚠️)
   ↓
6. Ajuster manuellement si besoin (clic sur créneaux)
   ↓
7. Exporter ou imprimer
```

---

## 🛠️ Informations techniques

- **Fichier unique** : tout en HTML/CSS/JS, aucune dépendance externe sauf Google Fonts
- **Compatibilité** : Chrome 90+, Firefox 88+, Edge 90+, Safari 14+
- **Stockage local** : clé `eps_edt_v1` dans `localStorage`
- **Déploiement** : compatible GitHub Pages (simple upload du fichier HTML)

---

## 📁 Structure du projet

```
emploi_du_temps_eps.html    ← Application complète
README.md                   ← Ce fichier
```

---

## 📝 Notes réglementaires (Éducation Nationale — 2nd degré)

- **Dotation horaire 6ème** : 4h EPS/semaine réglementaires → organisation en 2h hebdomadaires de cours + créneaux piscine
- **Dotation 5ème/4ème/3ème** : 3h EPS/semaine (2h + 1h)
- **Service enseignant** : 18h réglementaires (ORS) ; les heures supplémentaires (HSA) sont intégrées pour Clément (22h) et Steven (22h)
- **ULIS** : 1h d'EPS adaptée hebdomadaire

---

*Développé pour le Collège Pasteur, Villemomble — Équipe EPS*
