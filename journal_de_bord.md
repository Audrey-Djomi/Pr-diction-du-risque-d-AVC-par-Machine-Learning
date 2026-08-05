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

# Jour 9: Fin prétraitement  et début construction de notre pipeline dans le fichier feature_engineering

- Analyse du déséquilibre des classes de la variable cible (stroke),
- Utiliser la technique SMOTE pour équilibrer les classes du jeu d'entraînement,
- Vérification de la nouvelle distribution des classes après rééchantillonnage,
- Création d'une copie du jeu de données nettoyé afin de préserver les données d'origine,
- Début de la création de nouvelles variables basées sur des facteurs de risque médicaux (âge, glycémie et risque cardiovasculaire).
- Création de variables dérivées à partir des connaissances métier (senior, high_glucose, cardio_risk), 
- Analyse de la distribution de ces nouvelles variables,
- Évaluation de leur relation avec la variable cible (stroke) par tableaux croisé.

Compétences développées

- Gestion des jeux de données déséquilibrés
- Utilisation de la bibliothèque imbalanced-learn
- Compréhension de la différence entre sur-échantillonnage classique et génération synthétique d'observations,
- Application du Feature Engineering basé sur les connaissances métier
- Création de variables binaires à partir de seuils cliniques
- Analyse de la pertinence de nouvelles variables avant leur intégration au modèle
- Application du Feature Engineering basé sur les connaissances métier
- Création de variables binaires à partir de seuils cliniques
- Analyse de la pertinence de nouvelles variables avant leur intégration au modèle.

# Jour 10: Features Engineering
- Encodage des variables catégorielles,
- Utilisation de la méthode mutual information,
- Calcul du score de chaque variable
- graphique représentatif des variables et leur différents scores
- Analyses de la pertinence d'information de chaque variable sur la cible "stroke"

# Jour 11: Préparation finale des données
- Exportation du df_features dans le fichier 04_model_training
- Après avoir vérifié que le dataset issu du Feature Engineering ne contenait ni valeurs manquantes ni doublons, séparation des données en jeux d'entraînement et de test (80/20), 
- Encodage des variables catégorielles à l'aide de OneHotEncoder (drop="first" et handle_unknown="ignore"), en appliquant fit_transform() sur le jeu d'entraînement et transform() sur le jeu de test afin d'éviter toute fuite de données,
- Vérification de la bonne création des nouvelles variables binaires et de l'absence de valeurs manquantes après l'encodage,
- Préparation finale des données pour l'entraînement des modèles,
- Concaténation des variables catégorielles encodées, des variables continues standardisées et des variables binaires afin d'obtenir un dataset de 18 variables explicatives,
- Application de SMOTE sur le jeu d'entraînement uniquement afin d'équilibrer les classes (3888 observations par classe),
- Début de la phase de modélisation avec l'entraînement d'un premier modèle, la Régression Logistique, qui servira de modèle de référence (baseline) pour les comparaisons futures.

# Jour 12: Entraînement du premier modèle de classification : Régression Logistique.

- Résultats obtenus
    - Accuracy : 71,4 %
    - Recall (classe AVC) : 82 %
    - Precision (classe AVC) : 13 %
    - F1-score (classe AVC) : 22 %

La Régression Logistique détecte correctement la majorité des patients présentant un AVC avec un Recall élevé, ce qui est un point essentiel dans un contexte médical où il est préférable de limiter les faux négatifs. En revanche, la précision reste faible, ce qui traduit un nombre important de faux positifs. 
Ce modèle constitue une baseline qui servira de référence pour comparer les modèles plus avancés tels que Decision Tree, Random Forest et XGBoost.

Difficultés rencontrés

Compréhension de l'interprétation des métriques d'évaluation (Accuracy, Precision, Recall, F1-score) et de leur importance dans un problème médical.

# Jour 13: Entrainement d'autres modèles
### Decision Tree
- Entraînement et évaluation d'un modèle Decision Tree
Les performances montrent une accuracy élevée (88,7 %), mais une analyse détaillée révèle un recall de seulement 26 % sur la classe AVC. Le modèle identifie correctement la majorité des patients sains, mais manque une grande partie des patients réellement victimes d'un AVC (37 faux négatifs sur 50 cas). 
Cette étape confirme l'importance de ne pas se limiter à l'accuracy pour évaluer un modèle sur un jeu de données déséquilibré. 
La comparaison avec la Régression Logistique montre que cette dernière reste plus adaptée au contexte médical grâce à son rappel beaucoup plus élevé, malgré un nombre plus important de faux positifs.

### Random Forest
- Entraînement et évaluation d'un modèle Random Forest. 
Malgré une accuracy élevée de 92,3 %, l'analyse détaillée montre un recall de seulement 10 % sur la classe AVC. Le modèle détecte correctement la majorité des patients sains mais échoue à identifier la plupart des patients réellement victimes d'un AVC (45 faux négatifs sur 50 cas). Cette expérience confirme que l'accuracy seule ne permet pas d'évaluer la qualité d'un modèle dans un contexte de données déséquilibrées. 
Les paramètres par défaut de la Random Forest ne sont pas adaptés à notre problématique, ce qui justifie une future phase d'optimisation des hyperparamètres.

# Jour 14: Suite et Fin entrainement modèle
### eXtreme Gradient Boost (XGBoost)

- Entraînement et évaluation d'un modèle XGBoost
Le modèle obtient la meilleure accuracy parmi les quatre modèles testés (93,2 %), 
Son Recall reste faible (14 %). 
Il identifie correctement la majorité des patients sains mais détecte seulement 7 des 50 patients réellement victimes d'un AVC. 
La Precision atteint 21 %, ce qui signifie que lorsqu'il prédit un AVC, environ un patient sur cinq est effectivement malade. 
Cette étape confirme une nouvelle fois que l'accuracy seule ne permet pas d'évaluer un modèle dans un contexte médical où la détection des patients à risque est prioritaire. 

Une optimisation des hyperparamètres sera nécessaire afin d'améliorer les performances du modèle sur la classe minoritaire.

- Sauvegarde des modèles entraînés au format .pkl à l'aide de joblib,
Ce qui va me permettre de réutiliser les modèles sans avoir à les réentraîner.

- Sauvegarde de l'encoder et du scaler pour garder le format.

# Jour 15 : Optimisation d'hyperparamètres de nos modèles : Regression Logistique et XGBoost 


## Pour la suite 



