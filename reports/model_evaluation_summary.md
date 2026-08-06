# Résultats de la modélisation

## Objectif

L'objectif de ce projet est de prédire le risque d'Accident Vasculaire Cérébral (AVC) à partir de données médicales de patients en comparant plusieurs modèles de Machine Learning.

---

# Modèles évalués

Les modèles suivants ont été entraînés et comparés :

* Régression Logistique
* Decision Tree
* Random Forest
* XGBoost
* Régression Logistique optimisée (GridSearchCV)
* XGBoost optimisé (RandomizedSearchCV)

---

# Comparaison des performances

| Modèle                          | Accuracy | Precision | Recall   | F1-score |
| ------------------------------- | -------- | --------- | -------- | -------- |
| Régression Logistique           | 71.4 %   | 13 %      | 82 %     | 0.22     |
| Decision Tree                   | 88.7 %   | 14 %      | 26 %     | 0.18     |
| Random Forest                   | 92.3 %   | 13 %      | 10 %     | 0.11     |
| XGBoost                         | 93.2 %   | 21 %      | 14 %     | 0.17     |
| Régression Logistique optimisée | 71.1 %   | 13 %      | **84 %** | 0.22     |
| XGBoost optimisé                | 79.6 %   | 15 %      | 70 %     | **0.25** |

---

# Analyse

Les modèles présentant la meilleure Accuracy (Random Forest et XGBoost avant optimisation) ne sont pas les plus adaptés au contexte médical, car ils détectent une faible proportion des patients ayant réellement subi un AVC.

Dans cette problématique, le **Recall** constitue la métrique la plus importante puisqu'il mesure la capacité du modèle à identifier les patients réellement à risque.

L'optimisation des hyperparamètres a permis d'améliorer significativement les performances de XGBoost, dont le Recall est passé de 14 % à 70 %.

La Régression Logistique optimisée obtient le meilleur Recall (84 %) et constitue le modèle le plus adapté pour une stratégie de dépistage.

---

# Modèle retenu

**Régression Logistique optimisée**

### Justification

* meilleur Recall (84 %)
* limitation des faux négatifs
* modèle simple et interprétable
* particulièrement adapté au dépistage médical

---

# Modèle alternatif

**XGBoost optimisé**

Ce modèle présente le meilleur compromis entre Accuracy, Precision, Recall et F1-score. Il constitue une excellente alternative lorsque l'objectif est d'obtenir un équilibre entre les différentes métriques de performance.

---

# Conclusion

Ce projet montre qu'en Machine Learning, le modèle ayant la meilleure Accuracy n'est pas nécessairement le plus pertinent. Le choix d'un modèle doit toujours être guidé par le contexte métier.

Dans le cadre du dépistage du risque d'AVC, la Régression Logistique optimisée est retenue comme modèle principal grâce à sa capacité à détecter un maximum de patients à risque, tandis que XGBoost optimisé représente une alternative offrant un meilleur compromis global.
