# 📊 DDEFI 2025 - Analyse de Sentiment et Prédiction du S&P 500 📈

## 🔍 Contexte

Dans un marché financier en constante évolution, comprendre le sentiment des investisseurs est crucial pour affiner la précision des modèles prédictifs.
Ce projet a pour but de créer un indice Fear & Greed basé sur des sources variées (actualités, Reddit, Google Trends, etc.) et de l’intégrer dans un modèle Machine Learning pour améliorer les prévisions du S&P 500.
Cet indice a pour but de prévoir des mouvements de retournements potentiels du marché. En effet, une peur extrême indique souvent une sous-évaluation des actifs et donc des opportunités d'achat. Au contraire, une cupidité excessive suggère un marché suracheté et donc un potentiel retournement baissier. 

🎯 Objectifs du Projet

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

📌 2. Extraction & Prétraitement des Données

📥 Collecte

Web Scraping pour récupérer des articles de presse ==> mots-clés : " S&P 500 " pour collecter les articles pouvant influencer son prix  
Récupération uniquement des titres des articles et leurs liens url.    
Nettoyage des textes avec NLP (suppression des stopwords, stemming, lemmatisation)    

📊 Feature Engineering

Analyse de sentiment NLP : Scoring des titres d'articles pour créer notre index   
Agrégation hebdomadaire du score Fear & Greed  
Fusion avec les données du S&P 500 📥 [Télécharger le fichier Excel](https://github.com/votre-repo/votre-projet/blob/main/fichier.xlsx)
pour créer un dataset prêt à être modélisé.
Visualisation du prix du S&P500 avec le scoring créé.![Graphique du SP&500 et du scoring en fonction du temps](GraphiqueS&P-Fear&Greed.png)  

📌 3. Modélisation Machine Learning

🛠️ Modèles testés :

✅ XGBoost (modèle performant pour les séries temporelles)  
✅ LSTM (Deep Learning) (pour capturer les tendances complexes du marché)  
✅ Régression linéaire (benchmark simple)  

🎯 Évaluation des modèles

Comparaison des performances avec et sans l’indice Fear & Greed  
Backtest sur des périodes historiques pour mesurer la fiabilité  
Visualisation des prédictions avec Matplotlib & Seaborn  

📌 4. Industrialisation & Déploiement

🚀 Automatisation
✅ Pipeline de collecte et transformation des données (ETL)
✅ Mise à jour quotidienne des prédictions

📦 Containerisation & API
✅ Docker pour garantir la portabilité du projet
✅ FastAPI pour exposer les prédictions sous forme d’API

☁️ Déploiement Cloud
✅ CI/CD avec GitHub Actions (tests et mise en production automatisés)
✅ Déploiement sur AWS / GCP / Azure (accessible en ligne)

📊 Résultats et Insights
📌 Corrélation entre le sentiment et le S&P 500
📌 Amélioration de la précision du modèle avec l’analyse de sentiment
📌 Détection de retournements de marché basés sur Fear & Greed
