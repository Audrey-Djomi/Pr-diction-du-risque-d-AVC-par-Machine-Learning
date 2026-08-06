# Prédiction du risque d'AVC par Machine Learning

## Contexte

Les accidents vasculaires cérébraux (AVC) constituent l'une des principales causes de mortalité et de handicap dans le monde. La détection précoce des patients à risque représente un enjeu majeur pour la prévention et la prise en charge médicale.

L'objectif de ce projet est de développer un modèle de Machine Learning capable d'estimer le risque d'AVC à partir de caractéristiques médicales et démographiques.

## Objectif

* Explorer et comprendre le jeu de données,
* Nettoyer et préparer les données,
* Concevoir de nouvelles variables (Feature Engineering),
* Entraîner plusieurs modèles de classification,
* Optimiser leurs hyperparamètres,
* Comparer leurs performances,
* Sélectionner le modèle le plus adapté au contexte médical.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- Scikit-learn
- imbalanced-learn(SMOTE)
- XGBoost
- Joblib
- Git
- GitHub

## Méthodologie

Le projet a été réalisé selon les étapes suivantes :

* Nettoyage des données,
* Analyse exploratoire (EDA),
* Feature Engineering,
* Sélection des variables,
* Encodage et standardisation,
* Rééquilibrage des classes avec SMOTE,
* Entraînement des modèles,
* Optimisation des hyperparamètres,
* Comparaison des performances,
* Sélection du modèle final.

## Modèles étudiés

- Régression Logistique
- Decision Tree
- Random Forest
- XGBoost 
- Régression Logistique optimisée(GridSearchCV)
- XGBoost optimisé(RandomizedSearchCV)

## Évaluation

- Accuracy
- Precision
- Recall
- F1-score
- Matrice de confusion

## Résultats

Le projet montre qu'une Accuracy élevée n'est pas suffisante dans un contexte médical.

Le Recall a été privilégié afin de limiter les faux négatifs et d'identifier un maximum de patients réellement à risque.

## Modèle retenu

 Régression Logistique optimisée

Recall : 84 %
Modèle privilégié pour une stratégie de dépistage.

Alternative

 XGBoost optimisé

Recall : 70 %
Meilleur compromis entre Accuracy, Precision, Recall et F1-score.

## Illustrations

Le dossier reports/figures/ contient :

* graphique comparatif des modèles
![Graphique comparatif des modèles](/reports/figures/comparison_models.png)

* matrices de confusion des modèles retenus.
![Matrice de confusion Regression Logistique optimisée](/reports/figures/confusion_lr.png)

![Matrice de confusion XGBoost optimisé](/reports/figures/confusion_xgb.png)

## Perspectives

Les pistes d'amélioration envisagées sont :

* tester d'autres méthodes de rééquilibrage des classes ;
* enrichir le jeu de données avec de nouvelles variables médicales ;
* expérimenter d'autres algorithmes (LightGBM, CatBoost, réseaux de neurones) ;
* développer une interface Streamlit pour réaliser des prédictions interactives ;
* déployer le modèle sous forme d'API.


---

## 👩 Auteur

**Audrey DJOMI**

Data Analyst | Machine Learning |

GitHub : https://github.com/Audrey-Djomi


## À propos

Projet réalisé dans le cadre de ma reconversion vers les métiers de la Data, avec pour objectif de mettre en pratique une démarche complète de Machine Learning, de la préparation des données jusqu'à l'évaluation et la sélection du modèle.


Projet Terminé
