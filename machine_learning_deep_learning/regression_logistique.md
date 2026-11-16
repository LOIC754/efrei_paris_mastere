# Régression logistique — l'essentiel

----------------
## DEFINITION

**La régression logistique** est un modèle superviser de machine learning utiliser pour de la classification. <br>
Il permet de repondre à une question du style "OUI/NON" ou "accepter/refuser" a partir de la prediction d'un pourcentage sous forme de score.<br>

## PRINCIPE DE FONCTIONEMENT DE LA REGRESSION LOGISTIQUE
Le principe de fonctionement de la regression logistique tourne autour de 3 axes a savoir:

-**le scoring lineaire:** c'est une fonction linaire qui permet de regroupper toutes les variables en un seule nombre qui dit plustot <oui> ou plustot<non> on la definie ainsi: z = w·x + b avec:
    -w étant le poid: c'est la pente, elle permet de savoir de combien le score z change quand la variable x augmente de 1, donc à quel point elle pousse vers OUI ou vers NON
    -b en régression logistique,est la tendance de départ vers OUI ou vers NON, avant de regarder les variables.il permet d'empecher un score de 0(aurait z = 0) par exemple dans le cas ou toutes les variables valent 0 alors  La droite serait obligée de passer par l’origine, ce qui fausse le modèle.
    -x la variable principale ,les variables sont combiner comme une somme pondérée c'est a dire chaque variable compte plus ou moins selon son poids w.
    -z la varible cible , bref c'est le score dans ce cas ou la tendance finale vers oui ou bers non.

-**la probabilite et l'erreur:** on passe le score z (ensembles des variables regroupe en une valeur) dans une sigmoïde pour obtenir une probabilité entre 0 et 1 puis on mesure l'ereur quadratique MSE(combien on se trompe).
    -une sigmoide C’est une fonction mathématique en forme de S. Elle prend n’importe quel nombre en entrée et rend un nombre entre 0 et 1.
    -la sigmoide a pour role de transformer le score Z en probalite tel que: σ(z) = 1 / (1 + e^(−z)) avec σ la probabilité
    -a la fin de cette etape on as une probabilite , mais cette proba ne repond pas directe^ment a la question de depart dont on essaye de repondre par oui ou par non
-**la descision:**Elle transforme une probabilité en réponse OUI/NON pour cela elle compare la probabilité  avec le seuil.
    -L’entraînement sert justement à trouver les w et b qui rendent z positif pour les vrais admis et négatif pour les vrais refusés. Sans lui, la décision n’utilise aucune information sur l’étudiant.

**But de la regression logistique** : est de predit une probabilité a partir d'un classement (OUI / NON)

## Les étapes pour construire un modèle logistique:

etape1 Besoin : poser la question OUI/NON et coder la cible y en 0 ou 1.
etape2 Données : choisir les variables X (ex. heures, moyenne).
etape3 Séparer : 75 % pour l’apprentissage, 25 % pour le test, avec stratify=y. Le modèle ne voit jamais le test pendant l’apprentissage.
etape4 Standardiser X (moyenne 0, écart-type 1) pour que la descente de gradient avance bien.
etape5 Score : z = w₁·x₁ + w₂·x₂ + b.
etape6 Probabilité : p = σ(z) = 1 / (1 + e^(−z)).
etape7 Erreur : la log loss, −moyenne(y·log(p) + (1−y)·log(1−p)). Elle punit fort les erreurs « sûres d’elles ». La référence à battre est 0,693, le score d’un modèle qui répond toujours p = 0,5.
etape7 Apprentissage : la descente de gradient, w ← w − α × moyenne((p − y) × x). On vérifie que la courbe d’apprentissage descend puis s’aplatit.
etape8 Décision : 1 si p ≥ seuil (0,5 par défaut).
etape9 valuer sur le test : matrice de confusion, précision, rappel. On ajuste le seuil selon le coût métier de chaque erreur.

| Étape          | Formule / outil                                  |
|----------------|--------------------------------------------------|
| Score          | z = w·x + b                                      |
| Probabilité    | p = σ(z) = 1 / (1 + e^(−z))  → entre 0 et 1      |
| Décision       | classe 1 si p ≥ seuil (0,5 par défaut)           |
| Erreur         | log loss = −moy(y·log(p) + (1−y)·log(1−p))       |
| Apprentissage  | w ← w − α × moy((p − y)·x) ; b ← b − α × moy(p − y) |
| Évaluation     | matrice de confusion, précision, rappel          |

**Repères**
- σ(0) = 0,5 · σ(4) ≈ 0,98 · σ(−4) ≈ 0,02
- Log loss "je ne sais pas" (p = 0,5) = 0,693 → à battre
- α trop petit = lent · α trop grand = diverge
- Standardiser X avant la descente de gradient
- Précision = TP / (TP + FP) → "quand je dis oui, ai-je raison ?"
- Rappel = TP / (TP + FN) → "est-ce que je trouve tous les oui ?"
- Monter le seuil : précision ↑, rappel ↓
- Seuil = décision métier, pas technique


# TP1 L'ALGORITHME DE DESCENTE DE GRADIEN 
**Pipeline scikit-learn**
train_test_split → StandardScaler → LogisticRegression → .fit → .predict_proba → seuil → confusion_matrix