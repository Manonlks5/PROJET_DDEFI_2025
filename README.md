# Prédiction des Prix et Actifs du S&P 500 avec Machine Learning

## Contexte
Ce projet vise à prédire les prix et rendements des actifs du S&P 500 en utilisant des modèles de machine learning. Le projet applique des techniques avancées d'analyse de séries temporelles, de modélisation prédictive et d'évaluation des performances. 

## Objectifs
1. Collecter et préparer les données financières (prix historiques, indicateurs macroéconomiques).
2. Développer des modèles prédictifs en utilisant plusieurs algorithmes.
3. Évaluer les performances des modèles avec des métriques standards.
4. Interpréter les résultats pour proposer des recommandations d'investissement.

---

## Structure du projet

### 1. Collecte et Préparation des Données
- **Source des données :** Yahoo Finance (données historiques sur 5 ans).
- **Étapes réalisées :**
  - Nettoyage des données (gestion des valeurs manquantes et des doublons).
  - Transformation des prix en rendements logarithmiques.
  - Analyse de stationnarité avec le test ADF.
  - Création d'indicateurs techniques (Moyennes mobiles, RSI, MACD).

### 2. Modèles Implémentés
#### Modèle 1 : Régression Linéaire
- **Description :** Modèle simple pour prédire les rendements en fonction des indicateurs techniques.
- **Résultats :**
  - **MAE :** 0.0076
  - **RMSE :** 0.0099
- **Visualisation :**
  ![Régression linéaire](path_to_regression_plot.png)

#### Modèle 2 : ARIMA
- **Description :** Modèle ARIMA pour capturer les dépendances temporelles des séries stationnaires.
- **Ordre optimal :** (1, 1, 1) (après validation croisée).
- **Résultats :**
  - **MAE :** 0.0076
  - **RMSE :** 0.0099
  - **Précision directionnelle :** 46.36%
- **Visualisation :**
  ![Modèle ARIMA](path_to_arima_plot.png)

### 3. Méthodologie
#### Entraînement et Validation
- **Partitionnement :** Données divisées en 80% pour l'entraînement et 20% pour le test.
- **Validation croisée :** Validation par fenêtre glissante (rolling window).

#### Évaluation
- **Métriques utilisées :**
  - MAE (Mean Absolute Error)
  - RMSE (Root Mean Squared Error)
  - Précision directionnelle (hausse/baisse)

### 4. Analyse des Résultats
- Les prédictions des deux modèles capturent des tendances générales mais diffèrent dans la capture de l'intensité des pics.
- **Points d'amélioration potentiels :**
  - Incorporation de modèles non linéaires comme Random Forest ou Gradient Boosting.
  - Exploration de modèles avancés comme LSTM pour capturer des dépendances à long terme.

---

