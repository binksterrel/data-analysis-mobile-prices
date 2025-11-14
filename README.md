# Analyse Corrélation Prix vs. Specs Mobiles – Projet Data Analyse

Ce dépôt contient l'analyse complète et l'audit d'un jeu de données public sur les prix des téléphones mobiles (`Global_Mobile_Prices_2025_Extended.csv`).

L'objectif était de déterminer les facteurs influençant le prix, mais l'analyse a révélé que le jeu de données était **factuellement et statistiquement incohérent.**

**Compétences démontrées :** `Python`, `Pandas`, `Seaborn`, `Analyse de Données`, `EDA (Exploratory Data Analysis)`, `Data Audit`, `Data Visualization`

---

## 🎯 Problématique

L'objectif initial de ce projet était de répondre à une question simple : **"Comment les caractéristiques techniques (RAM, Stockage, Caméra...) influencent-elles le prix des téléphones ?"**

Dans un jeu de données logique, on s'attendrait à une corrélation positive. Ce projet sert d'audit pour vérifier si le jeu de données `Global_Mobile_Prices_2025_Extended.csv` est fiable pour une telle analyse.

---

## 🕵️ Méthodologie et Découvertes Clés

Mon analyse s'est déroulée en trois étapes critiques, menées dans le notebook `analyse_finale.ipynb`.

### 1. Découverte d'Incohérences Factuelles (La Preuve Principale)
Après un nettoyage de base, un audit approfondi des données a révélé des absurdités logiques qui invalident le jeu de données :

* **Incohérences OS/Processeur :** J'ai trouvé des "iPhones" listés avec des processeurs Android (ex: `Dimensity`, `Snapdragon`) et inversement, des téléphones "Android" avec des processeurs Apple (`A18 Pro`).
* **Incohérences Specs/Prix :** J'ai identifié des téléphones haut de gamme (ex: 12GB RAM, 128GB Stockage) vendus à des prix dérisoires (moins de 400 $), et des téléphones bas de gamme (ex: 4GB RAM) vendus à plus de 1000 $.

### 2. Confirmation Statistique (La Corrélation Nulle)
Pour confirmer **statistiquement** que l'ensemble du jeu de données était aléatoire (comme le suggéraient les preuves factuelles), j'ai calculé la matrice de corrélation (`.corr()`).

Les résultats ont confirmé cette hypothèse :
* Corrélation `price_usd` vs. `ram_gb` : **-0.02**
* Corrélation `price_usd` vs. `storage_gb` : **0.00**

Un score de 0 prouve mathématiquement qu'il n'y a **AUCUNE** relation linéaire entre ces variables.

### 3. Confirmation Finale (L'Absurdité des Marques)
Enfin, une analyse `groupby()` pour comparer le prix moyen par marque a révélé un classement illogique :
* **Marque la plus "chère" :** Infinix (839$)
* **Marque la 2e moins "chère" :** Samsung (791$)
* L'écart de prix entre toutes les marques était de toute façon minime, confirmant le caractère aléatoire des données.

---

## 🏁 Conclusion

Ce projet n'est pas une analyse de marché, mais un **audit de données**.

J'ai prouvé que le jeu de données `Global_Mobile_Prices_2025_Extended.csv` est **inutilisable pour une analyse prédictive**, et ce, par deux moyens :
1.  **Preuve Factuelle :** Le jeu de données contient des absurdités techniques (iPhones avec processeurs Android).
2.  **Confirmation Statistique :** Les données ne montrent aucune corrélation logique (score de 0.0) ni aucune structure de prix de marché réaliste.

Ce projet démontre ma capacité à **ne pas faire aveuglément confiance à un jeu de données** et à utiliser les outils statistiques (Pandas, Seaborn) pour **valider la qualité des données** avant de tirer des conclusions.

---

## 🚀 Comment l'exécuter

Ce projet est contenu dans un notebook Jupyter.

**Fichiers dans ce dépôt :**
* `analyse_finale.ipynb` : Le notebook contenant tout le code et les conclusions.
* `Global_Mobile_Prices_2025_Extended.csv` : Le jeu de données brutes.

**Installation :**
Pour exécuter l'analyse vous-même, clonez ce dépôt et installez les dépendances nécessaires :
```bash
# Il est recommandé de créer un environnement virtuel
pip install pandas matplotlib seaborn jupyter
