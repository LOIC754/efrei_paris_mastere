# Roadmap Data Science

ma roadmap personalisé

---

### Phase 0 — Consolider les outils 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **NumPy** : tableaux, broadcasting, vectorisation
- **Pandas avancé** : `groupby`, `merge`, `pivot_table`, `apply`, dates, valeurs manquantes
- **Visualisation** : Matplotlib et Seaborn , puis Plotly
- **Environnement** : Jupyter, uv ou poetry, Git
- **Projet** : l'analyse exploratoire (EDA) complète du Titanic 

### Phase 1 — Maths et statistiques pour la data 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Statistiques descriptives** : moyenne, médiane, variance, quantiles, corrélation de Pearson et de Spearman
- **Probabilités** : lois normale, binomiale et de Poisson, théorème central limite
- **Statistiques inférentielles** : intervalles de confiance, tests (t-test, χ², ANOVA), p-value
- **Algèbre linéaire** : vecteurs, matrices, produit scalaire 
- **Optimisation** : dérivées, gradient, descente de gradient
- **Ressources** : StatQuest (YouTube), 3Blue1Brown pour l'algèbre linéaire, Khan Academy pour les stats
- **Projet** : des tests statistiques sur le dataset d'immatriculations data.gouv (par exemple, la part d'électriques varie-t-elle selon la région ?)

### Phase 2 — Machine learning classique 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Méthode** : train/test split, validation croisée, surapprentissage, compromis biais/variance
- **Préparation des données** : encodage (one-hot, ordinal, target), normalisation, gestion des valeurs aberrantes, `Pipeline` et `ColumnTransformer`
- **Régression** : linéaire, Ridge, Lasso. Métriques : MAE, RMSE, R²
- **Classification** : régression logistique, KNN, arbres de décision. Métriques : précision, rappel, F1, ROC-AUC, matrice de confusion
- **Ensembles** : Random Forest, Gradient Boosting, XGBoost, LightGBM
- **Non supervisé** : K-Means, DBSCAN, ACP
- **Optimisation des hyperparamètres** : GridSearch, RandomSearch, Optuna
- **Interprétabilité** : importance des variables, SHAP
- **Ressources** : *Hands-On Machine Learning* d'Aurélien Géron, la documentation de scikit-learn, Kaggle Learn
- **Projet phare** : la **prédiction du prix des voitures d'occasion**, avec EDA, feature engineering, comparaison de 4 ou 5 modèles et analyse SHAP

### Phase 3 — Sujets avancés du ML 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Données déséquilibrées** : SMOTE, poids de classes, choix de métrique
- **Séries temporelles** : stationnarité, ARIMA, Prophet, features de décalage (lag) avec LightGBM
- **Scoring et risque** : scoring de crédit, détection de fraude. 
- **Projet** : la prévision mensuelle des immatriculations, plus un modèle de scoring de crédit (dataset Kaggle *Home Credit* ou *German Credit*)

### Phase 4 — Deep learning 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Réseaux de neurones** : perceptron, rétropropagation, fonctions d'activation, optimiseurs
- **PyTorch** : tenseurs, `Dataset` et `DataLoader`, boucle d'entraînement
- **CNN** pour l'image, **RNN et LSTM** pour les séquences
- **Transformers et NLP** : embeddings, fine-tuning avec Hugging Face
- **Ressources** : fast.ai, le cours Hugging Face, la spécialisation Deep Learning d'Andrew Ng
- **Projet** : la classification de textes (par exemple des réclamations clients)

### Phase 5 — IA générative et LLM 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Prompt engineering**, API LLM (Gemini, Claude, OpenAI)
- **RAG** : embeddings, base vectorielle (FAISS, pgvector), chunking
- **Agents**, MCP
- **Projet** : un assistant RAG sur de la documentation réglementaire (BCBS239, par exemple). 

### Phase 6 — MLOps et mise en production 

Progression : `[░░░░░░░░░░░░░░░░░░░░] 0 %`

- **Suivi des expériences** : MLflow
- **Servir un modèle** : FastAPI, Docker, Cloud Run
- **Pipelines ML** : Airflow, Vertex AI Pipelines
- **Monitoring** : dérive des données (Evidently), réentraînement
- **Feature store**, BigQuery ML
- **Projet** : déployer le modèle de prix voiture sur GCP, avec une API sur Cloud Run, un réentraînement planifié et un monitoring
