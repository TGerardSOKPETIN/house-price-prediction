# Prédiction du prix de vente de biens immobiliers

## À propos

Ce projet a été réalisé dans un premier temps dans le cadre de ma certification **Data Scientist Associate** chez **DataCamp**.

Compte tenu de la richesse du cas étudié et de sa portée métier, j’ai choisi de reprendre ce travail dans une démarche plus approfondie et plus professionnalisante. Cette nouvelle version intègre des éléments complémentaires de structuration, d’analyse exploratoire, d’interprétation métier et de restitution orientée décision.

L’objectif n’est donc plus uniquement de répondre à un exercice de certification, mais de transformer ce cas en **projet de data science appliquée**, mettant en lumière à la fois :
- la rigueur analytique,
- la construction de modèles prédictifs,
- et la manière dont ces résultats peuvent soutenir une **décision business** dans le secteur immobilier.

## Vue d’ensemble

Ce projet de data science a été conçu pour aider une agence immobilière à estimer plus finement le prix de vente de maisons à partir de leurs caractéristiques.  
L’objectif est de construire un outil d’aide à la décision capable de soutenir la stratégie de tarification, de limiter les erreurs de positionnement prix et de contribuer à une mise en vente plus efficace des biens.

## Contexte métier

RealAgents est une agence immobilière opérant sur une zone métropolitaine et commercialisant différents types de maisons.  
Dans ce contexte, une mauvaise estimation du prix de vente peut avoir plusieurs conséquences :

- un prix trop élevé peut allonger le temps de mise sur le marché,
- un prix trop faible peut entraîner une perte de valeur,
- une tarification incohérente peut nuire à la performance commerciale.

L’enjeu du projet est donc de prédire le prix de vente d’un bien à partir de variables comme la ville, la surface, le nombre de chambres, le type de maison et la durée de mise en vente.

## Problématique

Comment prédire le prix de vente d’un bien immobilier à partir de ses caractéristiques structurelles et de sa localisation, afin d’améliorer la pertinence du pricing immobilier ?

## Objectifs du projet

Ce projet poursuit quatre objectifs principaux :

1. nettoyer et préparer les données immobilières ;
2. analyser les facteurs associés au prix de vente ;
3. construire un modèle de base puis un modèle de comparaison ;
4. identifier l’approche la plus pertinente pour améliorer la précision des estimations.

## Données utilisées

Le jeu de données contient des informations historiques sur des ventes de maisons.

### Variables principales

- `house_id` : identifiant unique du bien
- `city` : ville dans laquelle se situe le bien
- `sale_price` : prix de vente final
- `sale_date` : date de la dernière vente
- `months_listed` : nombre de mois durant lesquels le bien est resté sur le marché
- `bedrooms` : nombre de chambres
- `house_type` : type de maison
- `area` : surface du bien en m²

## Démarche méthodologique

Le projet a été structuré en cinq étapes :

### 1. Nettoyage des données
Les données ont été nettoyées afin de corriger les valeurs manquantes, harmoniser les formats et produire une base exploitable pour la modélisation.

### 2. Analyse exploratoire
Une analyse exploratoire a été menée pour comprendre la distribution des prix, identifier les variables les plus influentes et faire émerger des premières lectures métier.

### 3. Feature engineering
Les variables ont été transformées pour être adaptées aux modèles :
- dérivation de composantes temporelles à partir de la date,
- encodage des variables catégorielles,
- construction d’une base prête pour le machine learning.

### 4. Modèle de base
Un modèle de régression linéaire a été construit afin d’obtenir un benchmark simple, interprétable et robuste.

### 5. Modèle de comparaison
Un modèle Random Forest a été entraîné afin d’évaluer l’apport d’une approche non linéaire plus flexible.

## Principaux enseignements exploratoires

L’analyse des données met en évidence plusieurs résultats structurants :

- la surface est fortement liée au prix de vente ;
- le nombre de chambres est associé à une hausse du niveau de prix ;
- la localisation joue un rôle important dans la valorisation ;
- le marché semble structuré autour d’un segment central de prix ;
- la durée de mise en vente apporte davantage une lecture commerciale qu’un moteur direct de valorisation.

## Résultats des modèles

### Modèle de base — Régression linéaire
- **RMSE** : 22 309
- **MAE** : 16 960
- **R²** : 0,962

### Modèle de comparaison — Random Forest
- **RMSE** : 16 630
- **MAE** : 11 301
- **R²** : 0,979

### Validation croisée du Random Forest
- **RMSE moyen CV** : 15 718
- **R² moyen CV** : 0,983

## Interprétation des résultats

Le modèle Random Forest améliore sensiblement les performances du modèle de base.  
Cette amélioration suggère que la formation du prix ne suit pas uniquement une logique linéaire et que certaines interactions ou non-linéarités sont mieux captées par un modèle plus flexible.

La validation croisée confirme par ailleurs la robustesse du modèle, avec des performances élevées et stables sur plusieurs sous-échantillons.

## Lecture métier

D’un point de vue business, les résultats montrent que :

- la surface, la localisation et le type de bien sont les principaux leviers de valorisation ;
- un modèle prédictif peut soutenir la fixation du prix de mise en vente ;
- un meilleur pricing peut contribuer à réduire les erreurs de positionnement ;
- l’agence peut s’appuyer sur le modèle comme outil d’aide à la décision, en complément de l’expertise métier.

## Recommandations

À partir de cette étude, plusieurs pistes d’usage peuvent être envisagées :

- utiliser le modèle pour produire une estimation de référence lors de la mise en vente ;
- segmenter les biens selon leurs caractéristiques clés ;
- identifier les cas atypiques nécessitant une expertise complémentaire ;
- approfondir l’analyse sur les segments haut de gamme, où la dispersion des prix est plus forte.

## Structure du projet

```text
house-price-prediction/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_nettoyage_donnees.ipynb
│   ├── 02_analyse_exploratoire.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_modele_de_base.ipynb
│   └── 05_modele_de_comparaison.ipynb
├── outputs/
│   └── figures/
├── src/
├── README.md
├── requirements.txt
└── .gitignore