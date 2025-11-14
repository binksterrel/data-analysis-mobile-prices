# Analyse Corrélation Prix vs. Specs Mobiles – Projet Data Analyse

Ce dépôt contient l'analyse complète d'un jeu de données public sur les prix des téléphones mobiles (`Global_Mobile_Prices_2025_Extended.csv`). L'objectif était de déterminer les facteurs influençant le prix, mais l'analyse a révélé que le jeu de données était statistiquement incohérent.

**Compétences démontrées :** `Python`, `Pandas`, `Seaborn`, `Analyse de Données`, `EDA (Exploratory Data Analysis)`, `Data Audit`, `Data Visualization`

---

## 🎯 Problématique

L'objectif initial de ce projet était de répondre à une question simple : **"Comment les caractéristiques techniques (RAM, Stockage, Caméra...) influencent-elles le prix des téléphones ?"**

Dans un jeu de données logique, on s'attendrait à une forte corrélation positive (plus de RAM = plus cher). Ce projet sert d'audit pour vérifier si le jeu de données est fiable pour une telle analyse.

---

## 🕵️ Méthodologie et Découvertes Clés

Mon analyse s'est déroulée en trois étapes critiques, menées dans le notebook Jupyter `analyse_finale.ipynb`.

### 1. Nettoyage et Exploration (EDA)
Le jeu de données de 1000 entrées était techniquement "propre" :
* **0** valeur manquante.
* **0** doublon.

Cependant, une première exploration des données (via `df.head()`) a révélé des anomalies logiques (ex: un "iPhone 16 Pro Max" listé à 335$), ce qui a éveillé mon scepticisme.

### 2. La Preuve par Corrélation (Le Cœur de l'Analyse)
Pour quantifier la relation entre le prix et les spécifications, j'ai calculé la **matrice de corrélation** (`.corr()`).

Les résultats ont été la découverte principale du projet :
* Corrélation `price_usd` vs. `ram_gb` : **-0.02**
* Corrélation `price_usd` vs. `storage_gb` : **0.00**

Un score de 0 (ou proche de 0) prouve mathématiquement qu'il n'y a **AUCUNE** relation linéaire entre ces variables. Les graphiques (Heatmap et Regplots) ont confirmé cette absence totale de tendance, contredisant toute intuition visuelle initiale.

### 3. La Confirmation par les Marques
Pour confirmer l'hypothèse d'un jeu de données aléatoire, j'ai mené une analyse `groupby()` pour comparer le prix moyen par marque. Les résultats sont absurdes et confirment l'incohérence :
* **Marque la plus "chère" :** Infinix (839$)
* **Marque la 2e moins "chère" :** Samsung (791$)

---

## 🏁 Conclusion

Ce projet n'est pas une analyse de marché, mais un **audit de données**.

J'ai prouvé que le jeu de données `Global_Mobile_Prices_2025_Extended.csv` est **incohérent, inutilisable pour une analyse prédictive**, et que les prix ont très probablement été générés aléatoirement.

La compétence clé démontrée est la capacité à **ne pas faire aveuglément confiance à un jeu de données** et à utiliser les outils statistiques (Pandas, Seaborn) pour prouver une hypothèse, plutôt que de forcer une analyse erronée.

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
