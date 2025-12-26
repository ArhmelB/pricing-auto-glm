# Pricing Auto – Modélisation GLM

## Contexte
Projet académique de modélisation de la prime pure en assurance automobile,
basé sur une approche fréquence × coût.

L’objectif est la mise en œuvre de modèles GLM
(Poisson / Binomiale négative pour la fréquence, Gamma pour la sévérité).


---

## Données
Les données utilisées proviennent des jeux de données freMTPL2 de la base de données de référence CASdataset.

Elles ne sont pas incluses dans ce dépôt mais sont accessibles aux adresses : "https://github.com/dutangc/CASdatasets/blob/master/data/freMTPL2freq.rda" et "https://github.com/dutangc/CASdatasets/blob/master/data/freMTPL2sev.rda" .

Pour reproduire les résultats: 
- extraire les fichiers csv de R
-  placer les fichiers correspondants
dans un dossier "datasets/" à la racine du projet.

---

## Méthodologie
- Analyse exploratoire des données (EDA) univariée et bivariée (Spearman et êta-carré)

- Modélisation de la fréquence des sinistres par GLM (statmodels)après vérification des hypothèses (surdispersion)

- Modélisation de la sévérité par GLM Gamma (avec sélection de variables)
- Diagnostics des modèles(validation croisée pour le surapprentissage, courbe de Lorenz pour les performance, analyse des résidus.. )
- Calcul de la prime pure

- Discussion des limites et pistes d’amélioration (EVT)

---

## Limites

- La modélisation par GLM ajuste bien le coeur de la distribution mais est moins efficace pour les valeurs extrêmes (voir résidus standardisés par exemple). Une modélisation spécifique des queues (EVT) constituerait une extension naturelle de ce travail.

- Les GLM reposent sur l'hypothèse forte d'une relation linéaire du prédicteur. Le modèle est donc sensible à la multicolinéarité et peine à capter des relations plus subtils (non monotones ou non lisses) entre variables d'où l'utilisation de splines pour les variables age par exemple.

- Les GLM (avec statmodels) sont meilleurs pour l'interprétabilité de la sinistralité. Cependant, les performances prédictives du modèle pourraient  être comparées à des méthodes de machine learning comme les random forest et Grandient Boosting.

---

## Organisation du dépôt
- "notebooks/Pricing EDA.ipynb" : exploration et préparation des données
- "notebooks/Pricing GLM.ipynb" : estimation des modèles GLM
- "requirements.txt" : dépendances Python du projet
- "README.md"
- "rapports" : versions PDFs de résultats

---

## Bibliothèques utilisées
Python, pandas, numpy, matplotlib, seaborn, statsmodels, scipy, scikit-learn

---

## Remarques
Ce projet vise à illustrer une démarche de modélisation actuarielle
plutôt qu’à fournir un modèle de production.
