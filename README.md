# Prévision de l'inflation au Maroc à partir de son évolution passée

## 📌 Problématique

> **Comment peut-on prévoir l'inflation au Maroc à partir de son évolution passée ?**

Ce projet a pour objectif de prédire le **taux d'inflation mensuel au Maroc en glissement annuel (%)** à partir de l'évolution historique de l'**Indice des Prix à la Consommation (IPC)** publié par le **Haut-Commissariat au Plan (HCP)**.

## 🎯 Objectif du projet

L'objectif est de construire un modèle de **Machine Learning supervisé** capable d'anticiper l'inflation du mois suivant en utilisant uniquement les valeurs passées de l'inflation.

## 📊 Données utilisées

- **Source :** Haut-Commissariat au Plan (HCP) — Royaume du Maroc
- **Site officiel :** https://www.hcp.ma/Indicateurs-mensuels-de-l-indice-des-prix-a-la-consommation_a681.html
- **Indicateur :** Indice des Prix à la Consommation (IPC), série mensuelle nationale
- **Période :** Janvier 2010 – Décembre 2025
- **Fréquence :** Mensuelle
- **Nombre d'observations :** 192
- **Fichier de données :** `data/raw/ipc_maroc_2010_2025.csv`

### Variables

| Variable | Description | Type | Unité |
|---|---|---|---|
| `date` | Mois d'observation | Datetime | Mois / Année |
| `ipc` | Indice des Prix à la Consommation | Numérique | Indice |
| `inflation_yoy` | Taux d'inflation en glissement annuel | Numérique | % |

La variable cible est **`inflation_yoy`**.

## 🧠 Méthodologie

Le travail suit les étapes suivantes :

1. Formulation du problème
2. Compréhension et exploration des données
3. Nettoyage des données
4. Création de variables retardées (*lags*)
5. Création de moyennes mobiles
6. Découpage chronologique Train / Test
7. Entraînement d'un modèle de Machine Learning
8. Évaluation et comparaison avec un modèle naïf
9. Interprétation des résultats

## 🤖 Algorithme retenu

L'algorithme principal utilisé est le **Random Forest Regressor**.

Il a été comparé à un **modèle naïf de persistance** défini par :

\[
\hat{y}_t = y_{t-1}
\]

## 📏 Métriques d'évaluation

Les performances du modèle sont évaluées à l'aide de :

- **MAE** : Mean Absolute Error
- **RMSE** : Root Mean Squared Error
- **R²** : coefficient de détermination

Objectif fixé avant entraînement :

> **MAE < 0,30 point de pourcentage**

## 🗂️ Structure du projet

```text
projet_inflation_maroc_FXX/
│
├── README.md
├── requirements.txt
├── .gitignore
├── DECLARATION_IA.md
├── data/raw/
├── docs/
├── notebooks/
├── figures/
├── rapport/
└── presentation/
