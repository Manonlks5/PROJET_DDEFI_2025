# 📊 DDEFI 2025 - Analyse de Sentiment et Prédiction du S&P 500 📈

## 🔍 Contexte

Dans un marché financier en constante évolution, comprendre le sentiment des investisseurs est crucial pour affiner la précision des modèles prédictifs.
Ce projet a pour but de créer un indice Fear & Greed basé sur des sources variées (actualités, Twitter, Google Trends, etc.) et de l’intégrer dans un modèle Machine Learning pour améliorer les prévisions du S&P 500.

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

Reddit API : Extraction des discussions financières sur r/wallstreetbets  
Google Trends API : Volume de recherche pour des termes financiers  
Actualités financières : Récupération via GDELT API  
Twitter API (si possible) : Extraction des tweets mentionnant le S&P 500  

📌 2. Extraction & Prétraitement des Données

📥 Collecte

Web Scraping pour récupérer des articles de presse et discussions Reddit  
API Calls automatisés pour la récupération des tweets et des indicateurs économiques  
Nettoyage des textes avec NLP (suppression des stopwords, stemming, lemmatisation)  

📊 Feature Engineering

Analyse de sentiment NLP (classification des articles en positif, neutre ou négatif)  
Agrégation journalière du score Fear & Greed  
Fusion avec les données du S&P 500 pour créer un dataset prêt à être modélisé  

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
