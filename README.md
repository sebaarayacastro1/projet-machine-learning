# Estimation du rendement des réseaux de distribution d’eau potable

## Contexte

Le rendement d'un réseau d'eau potable est un indicateur de performance de la distribution. L'objectif du projet est d'étudier si des **caractéristiques descriptives des réseaux** permettent d'estimer leur rendement.

## Problématique

**Est-il possible de prédire le rendement d'un réseau de distribution d'eau potable à partir de ses caractéristiques géographiques, de son volume d'eau et de son mode de gestion ?**

## Données

- **Source :** Agence de l'eau Seine-Normandie, [Réseaux de distribution en eau potable — Performances](https://www.data.gouv.fr/datasets/reseaux-de-distribution-en-eau-potable-performances).
- **Fichier :** `data/reseaux-performances-2014-2022.csv`.
- **Volume :** 13 647 lignes et 25 colonnes dans le fichier étudié.
- **Cible :** `Rendement` (valeur numérique généralement exprimée en pourcentage).
- **Unité d'observation :** une ligne de données relative à un réseau et à une année ; cette unité sera vérifiée car certaines combinaisons réseau-année se répètent.

Les années et les régions présentes sont celles couvertes par la source, sans représentativité nationale garantie. Ce fichier ne contient pas de réseaux des départements du Nord (59) et du Pas-de-Calais (62).

## Objectifs

1. Explorer les observations, les valeurs manquantes et les anomalies.
2. Étudier les enregistrements multiples par identifiant de réseau et année.
3. Définir des variables explicatives disponibles indépendamment du rendement : localisation, catégorie d'exploitant, année et, si pertinent, caractéristiques techniques après vérification.
4. Séparer les **réseaux** en ensembles d'entraînement et de test avec `train_test_split` afin d'éviter qu'un même réseau figure dans les deux ensembles.
5. Comparer une référence simple, la régression linéaire, Ridge et éventuellement KNN.
6. Utiliser `StandardScaler`, `Pipeline`, `cross_val_score` et `GridSearchCV` sur l'entraînement ; mesurer la MAE et le R² sur le test.
7. Interpréter les résultats et documenter les limites ainsi que l'utilisation de l'IA générative.

## Précautions méthodologiques

- `Rendement` et les champs qui le reconstituent directement ne doivent pas entrer dans les variables explicatives.
- Les répétitions par réseau et année doivent être examinées, pas supprimées aveuglément.

## Structure

```text
projet-machine-learning/
├── data/
│   └── reseaux-performances-2014-2022.csv
├── notebooks/
│   └── 01_exploration.ipynb
├── .gitignore
├── requirements.txt
└── README.md
```

## Installation et exécution

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Ouvrir `notebooks/01_exploration.ipynb` dans VS Code et sélectionner le noyau de `.venv`. Le notebook cherche le fichier CSV dans `../data/` ou `data/` selon le dossier de lancement.

## Avancement

- [x] Choix d'un sujet et d'un jeu de données
- [x] Initialisation du dépôt et du notebook exploratoire
- [ ] Analyse des observations répétées et des anomalies
- [ ] Sélection justifiée des variables explicatives
- [ ] Séparation par réseau et préparation des données
- [ ] Modélisation et validation croisée
- [ ] Évaluation, discussion et export HTML

## Usage de l'intelligence artificielle générative

Les interventions d'une IA générative dans la préparation du projet seront explicitées et vérifiées de manière critique dans le rendu final.
