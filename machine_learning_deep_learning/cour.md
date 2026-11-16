
# MACHINE LEARNING

## 1. DÉFINITION

**Le machine learning** est la branche de l'IA qui permet à un ordinateur d'apprendre par lui-même à partir d'exemples.

Les domaines d'application du machine learning sont :

- **finance :** détection de transactions frauduleuses ; score de crédit dans l'octroi de prêts.
- **vente et retail :** prédire la demande en fonction des habitudes des clients (données de consommation).

## 2. TYPES DE MACHINE LEARNING

En fonction du mode d'apprentissage, on distingue 3 types de machine learning, à savoir :

- **L'apprentissage supervisé :** il consiste à entraîner un modèle de machine learning à partir de données étiquetées, c'est-à-dire que, pour chaque ligne du jeu de données, on connaît la valeur de la cible *y* qu'on veut prédire.
  - **Classification :** la cible est une classe (ex. : fraude / pas fraude).
  - **Régression :** la cible est une valeur numérique (ex. : montant d'un prêt).
  - **Individu (objet, unité statistique) :** c'est une ligne du jeu de données (un client, une transaction) qu'on étudie.
  - **Classe d'appartenance :** c'est la catégorie à laquelle l'individu appartient, autrement dit la valeur qu'un modèle de classification cherche à prédire.
- **L'apprentissage non supervisé :** ici, le modèle est entraîné sur des données non étiquetées, c'est-à-dire qu'on ne connaît pas la cible. L'idée est que le modèle trouve lui-même des structures dans les données :
  - des **groupes** : regrouper les données en fonction de leur ressemblance (clusters homogènes) ;
  - des **axes** : réduire le nombre de variables (réduction de dimension) ;
  - des **anomalies** : repérer les individus qui sortent du lot.
- **L'apprentissage par renforcement :** il consiste à entraîner un modèle (un agent) à prendre des décisions dans l'environnement dans lequel il évolue. À chaque décision, il reçoit une récompense ou une pénalité, et il s'ajuste par essai-erreur pour maximiser ses récompenses.

## 3. LES ÉTAPES DE DÉVELOPPEMENT D'UN MODÈLE DE MACHINE LEARNING

- **Étape 1 – définition du problème :** il faut expliquer de manière claire pourquoi je veux développer ce modèle de machine learning, préciser l'objectif et le résultat attendu ; bref, bien définir la problématique.
- **Étape 2 – la collecte de données :** sans données, pas de machine learning ; il faut donc identifier les sources de données. Plusieurs méthodes sont possibles : extraire depuis une API, depuis une base de données, depuis la golden source.
- **Étape 3 – le traitement des données :** si les données utilisées pour l'entraînement sont fausses, alors les prédictions en sortie seront fausses ; on parle de *garbage in, garbage out*. Cette étape est très importante, car elle permet de garantir la qualité et la fiabilité des données. Elle consiste à traiter les valeurs aberrantes, les valeurs manquantes, les doublons, et bien d'autres choses.
  - **Attention à la fuite de données :** on découpe les données (train / validation / test) avant d'ajuster les traitements qui apprennent des données (imputation, normalisation), et on les ajuste sur le train uniquement.
- **Étape 4 – sélectionner les caractéristiques (variables) pertinentes** afin de répondre à la problématique. Pour cela, on effectue des analyses univariées et bivariées pour voir les différents liens entre les variables.
- **Étape 5 – sélectionner les modèles les plus intéressants pour notre problématique et les entraîner :** on choisit généralement plusieurs modèles, qu'on entraîne sur les données d'entraînement (train) puis qu'on compare sur les données de validation (ou par validation croisée). On divise donc les données en trois parties : train, validation et test.
- **Étape 6 – choisir le modèle approprié :** on se base sur le niveau de performance en validation, sur l'écart entre train et validation (sur-apprentissage / sous-apprentissage) et sur la complexité du modèle ; à performance égale, on garde le plus simple.
- **Étape 7 – validation du modèle :** on évalue le modèle choisi une seule fois sur le jeu de test, qu'il n'a jamais vu, pour savoir s'il généralise bien (ex. : MAE, RMSE, R² en régression).
- **Étape 8 – mise en production du modèle :** on effectue les tests unitaires au préalable, puis on surveille ses performances dans le temps.
## 4. LES PREREQUIS
confert le cour sur la datascince()