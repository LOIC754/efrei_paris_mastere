# Processe universelle d'un projet ML

## T1 — Problème métier
- **À faire** : écrire qui décide, quelle décision le modèle aide à prendre, ce que coûte chaque type d'erreur et le critère de succès chiffré. Vérifier aussi qu'il faut vraiment du ML : sans dimension prédictive, une analyse et des visualisations des données historiques suffisent souvent.
- **Livrable** : 5 lignes en Markdown en tête du notebook.

## T2 — Traduction en ML
- **À faire** : choisir le type de ML (régression, classification ou clustering), l'unité d'observation (une ligne = quoi ?), la cible et la métrique principale.
- **Livrable** : une fiche « cible / type / métrique ».

## T3 — Import des données
- **À faire** : `read_csv`, `shape`, `dtypes`, `head`, et un dictionnaire des colonnes (sens, unité, type).
- **Livrable** : un tableau qui décrit chaque colonne.

## T4 — Audit qualité
- **À faire** : chercher les doublons, les valeurs manquantes, les formats incohérents et les valeurs impossibles (âge de 999 ans).
- **Livrable** : un tableau problème / nombre de lignes / décision.

## T5 — Mise de côté du test
- **À faire** : découper en train et test (`stratify`, `random_state`) avant toute statistique qui servira au modèle. Géron insiste sur ce point : mettre un jeu de test de côté et ne jamais le regarder, pour éviter le « data snooping ».
- **Livrable** : `X_train`, `X_test`, `y_train`, `y_test`.

## T6 — Analyse exploratoire (sur le train)
- **À faire** : distribution de la cible (classes équilibrées ou non), histogrammes, lien de chaque variable avec la cible, corrélations.
- **Livrable** : constats et interpretations.

## T7 — Cible et variables
- **À faire** : retirer l'identifiant, les colonnes connues seulement après l'événement (fuite de données) et la cible ; créer des variables dérivées.
- **Livrable** : la liste des variables retenues, avec la raison de chaque choix.

## T8 — Pipeline de préparation
- **À faire** : fonctions de nettoyage, imputation, one-hot, `StandardScaler`, le tout dans un `ColumnTransformer` placé dans un `Pipeline`.
- **Livrable** : un seul objet qui va du CSV brut à la prédiction.

## T9 — Baseline
- **À faire** : `DummyClassifier`, ou la moyenne de la cible en régression.
- **Livrable** : le score à battre.

## T10 — Comparaison de modèles
- **À faire** : au moins 3 modèles, même pipeline, validation croisée à 5 plis (moyenne et écart-type).
- **Livrable** : un tableau comparatif.

## T11 — Réglage
- **À faire** : `GridSearchCV` sur les hyperparamètres, puis choix du seuil de décision d'après le coût des erreurs.
- **Livrable** : le modèle final et son seuil.

## T12 — Évaluation finale
- **À faire** : test utilisé une seule fois ; matrice de confusion ou erreurs de régression, analyse des erreurs, importance des variables.
- **Livrable** : les scores finaux et leur interprétation.

## T13 — Restitution
- **À faire** : recommandation en 3 phrases, chiffres compris, limites assumées.
- **Livrable** : une conclusion ou une soutenance.

## T14 — Mise en service
- **À faire** : prédire sur de nouveaux cas bruts (comme la mission 9 du Challenge), sauvegarder le modèle, écrire un README. En entreprise, on ajoute ensuite la surveillance.
- **Livrable** : un modèle réutilisable.

---

**Sources**
- [DataRobot — Machine Learning Project Checklist](https://datarobot.com/blog/machine-learning-project-checklist)
- [Scribd — ML Checklist (Géron)](https://www.scribd.com/document/494449865/Ml-Checklist-PDF)

# pratique nous allons nous entrainer sur ces jeux de données.

1. [Auto MPG](https://www.kaggle.com/datasets/uciml/autompg-dataset)
2. [Mobile Price Classification](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification)
3. [Vehicle Dataset from CarDekho](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)
4. [Default of Credit Card Clients](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset)
5. [Health Insurance Cross Sell Prediction](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction)