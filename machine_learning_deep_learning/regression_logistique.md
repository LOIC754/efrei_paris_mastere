# Régression logistique — l'essentiel

---

## DÉFINITION

**La régression logistique** est un modèle supervisé de machine learning utilisé pour de la classification.<br>
Il permet de répondre à une question du style « OUI/NON » ou « accepter/refuser » à partir de la prédiction d'un pourcentage sous forme de score.<br>

## PRINCIPE DE FONCTIONNEMENT DE LA RÉGRESSION LOGISTIQUE

Le principe de fonctionnement de la régression logistique tourne autour de 3 axes, à savoir :

- **Le scoring linéaire :** c'est une fonction linéaire qui permet de regrouper toutes les variables en un seul nombre qui dit plutôt « oui » ou plutôt « non ». On la définit ainsi : `z = w·x + b` avec :
  - **w** étant le poids : c'est la pente, elle permet de savoir de combien le score z change quand la variable x augmente de 1, donc à quel point elle pousse vers OUI ou vers NON.
  - **b**, en régression logistique, est la tendance de départ vers OUI ou vers NON, avant de regarder les variables. Il permet d'empêcher un score de 0 (on aurait z = 0), par exemple dans le cas où toutes les variables valent 0 : alors la droite serait obligée de passer par l'origine, ce qui fausse le modèle.
  - **x** la variable principale ; les variables sont combinées comme une somme pondérée, c'est-à-dire que chaque variable compte plus ou moins selon son poids w.
  - **z** la variable cible, bref c'est le score dans ce cas, ou la tendance finale vers oui ou vers non.

- **La probabilité et l'erreur :** on passe le score z (ensemble des variables regroupées en une valeur) dans une sigmoïde pour obtenir une probabilité entre 0 et 1, puis on mesure l'erreur quadratique MSE (combien on se trompe).
  - Une sigmoïde : c'est une fonction mathématique en forme de S. Elle prend n'importe quel nombre en entrée et rend un nombre entre 0 et 1.
  - La sigmoïde a pour rôle de transformer le score z en probabilité tel que : `σ(z) = 1 / (1 + e^(−z))` avec σ la probabilité.
  - À la fin de cette étape, on a une probabilité, mais cette probabilité ne répond pas directement à la question de départ, à laquelle on essaie de répondre par oui ou par non.

- **La décision :** elle transforme une probabilité en réponse OUI/NON ; pour cela, elle compare la probabilité avec le seuil.
  - L'entraînement sert justement à trouver les w et b qui rendent z positif pour les vrais admis et négatif pour les vrais refusés. Sans lui, la décision n'utilise aucune information sur l'étudiant.

**But de la régression logistique** : prédire une probabilité à partir d'un classement (OUI / NON).

## LES ÉTAPES POUR CONSTRUIRE UN MODÈLE LOGISTIQUE

1. **Besoin** : poser la question OUI/NON et coder la cible y en 0 ou 1.
2. **Données** : choisir les variables X (ex. heures, moyenne).
3. **Séparer** : 75 % pour l'apprentissage, 25 % pour le test, avec `stratify=y`. Le modèle ne voit jamais le test pendant l'apprentissage.
4. **Standardiser** X (moyenne 0, écart-type 1) pour que la descente de gradient avance bien.
5. **Score** : `z = w₁·x₁ + w₂·x₂ + b`.
6. **Probabilité** : `p = σ(z) = 1 / (1 + e^(−z))`.
7. **Erreur** : la log loss, `−moyenne(y·log(p) + (1−y)·log(1−p))`. Elle punit fort les erreurs « sûres d'elles ». La référence à battre est 0,693, le score d'un modèle qui répond toujours p = 0,5.
8. **Apprentissage** : la descente de gradient, `w ← w − α × moyenne((p − y) × x)`. On vérifie que la courbe d'apprentissage descend puis s'aplatit.
9. **Décision** : 1 si p ≥ seuil (0,5 par défaut).
10. **Évaluer** sur le test : matrice de confusion, précision, rappel. On ajuste le seuil selon le coût métier de chaque erreur.

| Étape          | Formule / outil                                      |
|----------------|------------------------------------------------------|
| Score          | `z = w·x + b`                                        |
| Probabilité    | `p = σ(z) = 1 / (1 + e^(−z))` → entre 0 et 1         |
| Décision       | classe 1 si p ≥ seuil (0,5 par défaut)               |
| Erreur         | log loss = `−moy(y·log(p) + (1−y)·log(1−p))`         |
| Apprentissage  | `w ← w − α × moy((p − y)·x)` ; `b ← b − α × moy(p − y)` |
| Évaluation     | matrice de confusion, précision, rappel              |

**Repères**

- σ(0) = 0,5 · σ(4) ≈ 0,98 · σ(−4) ≈ 0,02
- Log loss « je ne sais pas » (p = 0,5) = 0,693 → à battre
- α trop petit = lent · α trop grand = diverge
- Standardiser X avant la descente de gradient
- Précision = TP / (TP + FP) → « quand je dis oui, ai-je raison ? »
- Rappel = TP / (TP + FN) → « est-ce que je trouve tous les oui ? »
- Monter le seuil : précision ↑, rappel ↓
- Seuil = décision métier, pas technique

# TP1 : L'ALGORITHME DE DESCENTE DE GRADIENT

**Pipeline scikit-learn**

```
train_test_split → StandardScaler → LogisticRegression → .fit → .predict_proba → seuil → confusion_matrix
```