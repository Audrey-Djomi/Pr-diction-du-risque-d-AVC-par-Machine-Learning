# Jour 1: Création du dépôt GitHub.
- Mise en place de l'architecture du projet, 
- Initialisation de l'environnement de développement,
- Définition des objectifs du projet,
- Préparation de la documentation,
- Choix du dataset: nous garderons le dataset stroke de notre projet 2.

# Jour 2: Mettre en place un environnement de développement propre et commencer l'exploration des données.
- Correction du problème d'authentification GitHub.
- Vérification de la configuration Git (user.name, user.email, remote).
- Suppression de l'ancien environnement virtuel créé dans un dossier mal nommé.
- Création d'un nouvel environnement virtuel .venv.
- Réinstallation des dépendances à partir du fichier requirements.txt.
- Mise en place d'un .gitignore adapté à un projet Python.

# Jour 3: Début Exploration et compréhension des données (EDA)
- vérifier la structure de nos datasets 
- importer les librairies
- télécharger nos datasets afin d'explorer et de comprendre les données
- exploration de notre dataset raw et comparaison avec le dataset processed
    - Début de l'exploration des données
    - Premières observations :
    5110 observations
    12 variables
    Variables numériques : age, avg_glucose_level, bmi
    Variables catégorielles : gender, ever_married, work_type, Residence_type, smoking_status
    Variables binaires : hypertension, heart_disease, stroke

    Première anomalie détectée :
    201 valeurs manquantes dans la variable BMI (3,93 %)
    Aucun autre champ ne présente de valeurs manquantes.

## Difficultés rencontrées et ce que j'ai appris jusqu'ici:

- Conflit d'authentification GitHub résolu.
- Restructuration de l'environnement virtuel afin d'adopter une organisation plus professionnelle.
- Utiliser un fichier requirements.txt,
- Mettre en place un .gitignore,
- Structurer un projet Machine Learning selon les bonnes pratiques.

## Réflexion
Les premières observations montrent que le jeu de données est relativement propre. La seule variable présentant des valeurs manquantes est l'IMC (bmi), avec environ 3,9 % de données absentes. Avant d'entraîner un modèle de Machine Learning, il sera nécessaire de déterminer la stratégie la plus adaptée pour traiter ces valeurs manquantes afin de limiter leur impact sur les performances du modèle.

# Jour 4: Fin EDA et Début Analyse orientée Machine Learning
- Analyse des valeurs manquantes,
- Recherche de doublons,
- comparer avec notre dataset processed
- Analyse des distributions : Contrairement au Projet 2, l'exploration est réalisée dans une logique de préparation des données pour l'entraînement des modèles.
Les premières analyses ont porté sur :

l'étude de la variable cible (stroke),
la mise en évidence du fort déséquilibre entre les classes,
l'identification des variables numériques et catégorielles,
la définition des futurs prétraitements (encodage, standardisation, aucune action),
la réalisation d'une première matrice de corrélation des variables numériques.
- Premières visualisations
- Étude des corrélations

## Difficultés rencontrées
- Comprendre la différence entre une analyse exploratoire classique et une exploration orientée Machine Learning.
- Réfléchir aux prétraitements nécessaires avant l'entraînement des modèles.

# Jour 5 : début analyse des variables numériques et des variables catégorielles
- visualisations des variables numériques: distribution et boxplot
- visualisations des variables catégorielles: histogrammes 

# Jour 6: Interprétation des résultats d'analyses des variables 
Cette première exploration orientée Machine Learning met en évidence plusieurs caractéristiques importantes du jeu de données. 

- La variable cible présente un fort déséquilibre entre les classes, ce qui nécessitera l'utilisation de techniques adaptées lors de l'entraînement des modèles. 

- Les variables numériques présentent des distributions asymétriques et plusieurs valeurs extrêmes, cohérentes avec un contexte médical, qui seront conservées. 

- Les variables catégorielles sont globalement bien représentées, bien que certaines modalités très rares devront être examinées lors du prétraitement. 

Cette étape nous a permis de définir les transformations nécessaires avant la construction des modèles prédictifs.

# Jour 7: Prétraitement

- Importation des bibliothèques nécessaires au prétraitement,
- Chargement du jeu de données brut,
- Suppression de la colonne id, considérée comme un identifiant sans valeur prédictive,
- Séparation des variables explicatives (X à 80 %) et de la variable cible (y à 20 %) à l'aide de train_test_split,
- Conservation de la proportion des classes grâce au paramètre stratify, afin de préserver le déséquilibre initial entre les patients avec et sans AVC,
- Vérification des dimensions des jeux de données,
- Identification des variables numériques, catégorielles et binaires pour préparer les futurs traitements,
- Gestion des valeurs manquantes de la variable bmi par imputation de la médiane calculée uniquement sur le jeu d'entraînement, puis application de cette valeur au jeu de test afin d'éviter toute fuite d'information (data leakage),
- Vérification de l'absence de valeurs manquantes après l'imputation.

Nous avons observé que nous avions toujours les données manquantes dans notre dataset,
Rappelons que nous travaillons sur notre dataset brut et pas celui néttoyé qui provient de notre projet 2.

Compétences développées

Compréhension de l'importance du découpage Train/Test,
Prévention des fuites d'information lors du prétraitement,
Organisation des variables selon leur nature pour préparer les transformations adaptées,
Application des bonnes pratiques de préparation des données en Machine Learning.

# Jour 8: Suite Prétraitement

- Choix du One-Hot Encoding afin d'éviter la création d'un ordre artificiel entre les catégories,
- Apprentissage des catégories uniquement sur le jeu d'entraînement (fit), puis application de la transformation au jeu de test (transform) afin d'éviter toute fuite d'information,
- Conversion des variables catégorielles en variables numériques binaires (0/1),
- transformation de nos données encodées en dataframe,
- Fusion des variables numériques, binaires et catégorielles encodées afin de constituer le jeu de données final destiné à l'entraînement des modèles,
- Vérification des dimensions et de la cohérence du dataset final,
- Standardisation des variables numériques (age, avg_glucose_level, bmi) avec StandardScaler,
- Apprentissage du scaler sur le jeu d'entraînement uniquement (fit_transform) puis application au jeu de test (transform) afin d'éviter toute fuite de données,
- Vérification de la transformation des variables numériques.


Compétences développées

- Compréhension des techniques d'encodage des variables catégorielles,
- Distinction entre fit et transform,
- Construction d'un jeu de données entièrement numérique adapté aux algorithmes de Machine Learning.
- Compréhension de l'importance de la mise à l'échelle des données
- Préparation des données pour des modèles sensibles à l'échelle des variables

# Jour 9: Fin prétraitement 

- Analyse du déséquilibre des classes de la variable cible (stroke),
- Utiliser la technique SMOTE pour équilibrer les classes du jeu d'entraînement,
- Vérification de la nouvelle distribution des classes après rééchantillonnage,
- Finalisation du pipeline de prétraitement des données.

Compétences développées

- Gestion des jeux de données déséquilibrés.
- Utilisation de la bibliothèque imbalanced-learn.
- Compréhension de la différence entre sur-échantillonnage classique et génération synthétique d'observations,
- Construction d'un pipeline complet de préparation des données.



## Pour la suite 
Les prochaines étapes consisteront à préparer les données pour l'entraînement des modèles de Machine Learning.

