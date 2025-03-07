# 📊 DDEFI 2025 - Analyse de Sentiment et Prédiction du S&P 500 📈 - TrendX

## 🔍 Contexte

Dans un marché financier en constante évolution, comprendre le sentiment des investisseurs est crucial pour affiner la précision des modèles prédictifs.
Ce projet a pour but de créer un indice Fear & Greed basé sur des sources variées (actualités, Reddit, Google Trends, etc.) et de l’intégrer dans un modèle Machine Learning pour améliorer les prévisions du S&P 500.
Cet indice a pour but de prévoir des mouvements de retournements potentiels du marché. En effet, une peur extrême indique souvent une sous-évaluation des actifs et donc des opportunités d'achat. Au contraire, une cupidité excessive suggère un marché suracheté et donc un potentiel retournement baissier. 

## 💼 À qui s'adresse TrendX ?

📌 Fonds d’investissement & Hedge Funds – Pour affiner leurs stratégies basées sur l'analyse de sentiment  
📌 Traders indépendants & Analystes – Pour anticiper les tendances du S&P 500 grâce à l’IA  
📌 Startups Fintech – Pour intégrer un indice Fear & Greed intelligent dans leurs solutions  

---

## 🎯 Objectifs du Projet

✅ Développer un indice Fear & Greed personnalisé à partir de données d'actualités et de médias sociaux

✅ Tester l’impact de cet indice sur la précision des modèles de prédiction du S&P 500

✅ Automatiser la collecte et l’analyse des données à l’aide d’APIs et de pipelines de données

✅ Industrialiser la solution via CI/CD, Docker, et Cloud Deployment

---

## 📌 1. Sources de Données

📈 Données du marché  

YahooFinance API : Données historiques du S&P 500    
Macroéconomie : Indicateurs FRED API (inflation, taux d’intérêt, chômage)  

📢 Données de sentiment
 
Actualités financières : Récupération via GDELT API  ==> récupération de titres d'articles liés à l'actualité financière.       
Google Trends API : Volume de recherche pour des termes financiers    
Twitter API (si possible) : Extraction des tweets mentionnant le S&P 500, bloqués malheureusement il fallait payer pour    
collecter les données.   
Reddit API : Extraction des discussions financières sur r/wallstreetbets   

## 1ère approche Google Trends :  


## 📌 2. Extraction & Prétraitement des Données

📥 Collecte

Web Scraping pour récupérer des articles de presse ==> mots-clés : " S&P 500 " pour collecter les articles pouvant influencer son prix
[Télécharger le fichier Excel](SP500_Fear_Greed_Articles_finale.xlsx)
Récupération uniquement des titres des articles et leurs liens url.   
==> Catégorisation des articles en Fear, Greed ou Neutral grâce à des mots-clés.  
Nettoyage des textes avec NLP (suppression des stopwords, stemming, lemmatisation)    

⚠️ Difficultés survenues : Collecte de nombreux tweets sur Reddit mais unqiuement les plus récents et donc impossible pour tester avec du Machine learning afin de prédire le prix. On pouvait récupérer que les 2 derniers jours.  

📊 Feature Engineering

Analyse de sentiment NLP : Scoring des titres d'articles pour créer notre index   
Agrégation hebdomadaire du score Fear & Greed 📥 [Télécharger le fichier Excel](sp500_with_scores_7_days-2.xlsx)  
Fusion avec les données du S&P 500 📥 [Télécharger le fichier Excel](https://github.com/votre-repo/votre-projet/blob/main/fichier.xlsx)
pour créer un dataset prêt à être modélisé.
Visualisation du prix du S&P500 avec le scoring créé.

![Graphique du SP&500 et du scoring en fonction du temps](GraphiqueS&P-Fear&Greed.png)  

## 📌 3. Modélisation Machine Learning

🛠️ Modèles testés :

✅ XGBoost (modèle performant pour les séries temporelles)  
 
🎯 Évaluation des modèles

Backtest sur des périodes historiques pour mesurer la fiabilité :    

On a d'abord essayé de corréler les log des rendements du S&P500 et le scoring sur 7 jours de nos titres d'articles afin d'entraîner notre modèle. XGBoost a donc construit des prédictions de baisse ou de hausse du S&P500 en se basant sur le passé. On a fait du 70-30.  

![Graphique de la prediction d'un potentiel retournement haussier ou baissier](PrédictionML.png)

Comparaison des performances avec et sans l’indice Fear & Greed  

Visualisation des prédictions avec Matplotlib & Seaborn  
![Prédiction du S&P500 avec notre modèle](Prédiction_prix_S&P500.png)

Cette prédiction est meilleure que le prix réel car il y a un manque d'information ce qui entache la précision. Si on fait un test de notre modèle on obtient : 

## 2️⃣ Résultats du Modèle

📌 Performance Générale

Métrique	Valeur  
Accuracy	51,66%  
Macro Avg Precision	51%  
Macro Avg Recall	51%  
Macro Avg F1-Score	51%  

📌 Rapport de Classification

### 📊 Rapport de Classification

| Classe | Précision | Rappel | F1-score | Support |
|--------|------------|--------|-----------|---------|
| **0 (Baisse du marché)** | 0.49 | **0.47** | 0.48 | 144 |
| **1 (Hausse du marché)** | 0.54 | **0.56** | 0.55 | 158 |
| **Global** | 0.52 | 0.52 | 0.52 | 302 |

📌 Matrice de Confusion 

### 🔎 Matrice de Confusion

|   | Prédit **0** | Prédit **1** |
|---|-------------|-------------|
| **Réel 0** | 67 (✅ Vrais négatifs) | **77 (❌ Faux positifs)** |
| **Réel 1** | **69 (❌ Faux négatifs)** | 89 (✅ Vrais positifs) |

## 3️⃣ Analyse des Résultats

🔴 Le modèle fait encore trop d’erreurs : 77 faux positifs, 69 faux négatifs  
🟢 Le modèle est équilibré entre les classes   
⚠️ Problème principal : Le modèle ne capte pas encore bien les signaux du marché.  

## 📌 4. Déploiement et Conlusion

🚀 Automatisation

✅ Pipeline de collecte et transformation des données (ETL)  
✅ Mise à jour quotidienne des prédictions  


📊 Résultats et Insights

📌 Corrélation entre le sentiment et le S&P 500 

Il y a une certaine forme de décorrélation entre l'indice Fear&Greed et le cours du S&P500 dans les mouvements à hautes volatilités car la cupidité ou la peur deviennent extrêmes et le cours va se retourner et commencer à chuter.  
Par contre sur des ranges du S&P500 les deux indices sont corrélés. 

📌 Amélioration de la précision du modèle avec l’analyse de sentiment  

Collecte de beaucoup plus d'articles afin d'augmenter en précision et pour tester plus correctement notre ML. Créer un poids spécifique par articles en fonction de leur popularité afin d'avoir une meilleure représentation de l'index et du sentiment générale de marché. Par exemple si le New York Times plublie un article positif sur le S&P500 on sera sûrement sur de la cupidité extrême.

📌 Détection de retournements de marché basés sur Fear & Greed  

La principale utilité est donc la détection de retournement de marché, surtout quand l'indice Fear&Greed est fort ( dans les deux sens, peur ou cupidité). C'est donc un indicateur majeur pour les banques,traders,fonds d'investissements pour savoir à quel moment acheter ou vendre. 
