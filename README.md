```markdown
# DUDA CohortScore v1

Le **DUDA CohortScore** est le MVP d'une Webapp Streamlit d'analyse de cohortes, réalisé pour le DU Sorbonne Data Analytics 2024-2025 par **Alexandre Cameron BORGES** & **Alioune DIOP**. L'outil segmente la clientèle Instacart via l'analyse RFM (Récence, Fréquence, Montant), explore les habitudes d'achat et génère un WordCloud à partir d'un texte importé.

### 📋 Table des matières

1. [Objectifs](#✨-objectifs)  
2. [Démo rapide](#🚀-démo-rapide)  
3. [Jeux de données](#📊-jeux-de-données)  
4. [Méthodologie](#🧠-méthodologie)  
5. [Architecture de l'application](#🏗️-architecture-de-lapplication)  
6. [Installation & Exécution](#⚙️-installation--exécution)  
7. [Auteurs](#🙋-auteurs)  


## ✨ Objectifs
- Segmenter les clients selon le modèle RFM (Récence, Fréquence, Montant).
- Visualiser les tendances d'achat : top produits, heatmaps temporelles.
- Explorer dynamiquement via des filtres : jour, heure, rayon, cluster.
- Générer un WordCloud à partir d'un fichier texte lié au e-commerce.

## 🚀 Démo rapide
### WebApp hébergée
Visitez la démo en ligne :
> https://acb-dudacohortscore.streamlit.app/

### Exécution locale
```bash
# 1. Cloner le dépôt et se positionner dans le dossier
git clone https://github.com/alexandre-cameron-borges/duda_cohortscore.git
cd duda_cohortscore

# 2. Créer et activer l’environnement virtuel
# macOS/Linux
env python -m venv .venv && source .venv/bin/activate
# Windows
venv\\Scripts\\activate

# 3. Installer les dépendances
pip install --upgrade pip
pip install -r requirements.txt

# 4. Lancer l’application
streamlit run app.py
````

> **Note** : L'application s'attend à trouver `data/instacart_sample_1m.parquet`. Ajustez le chemin dans `app.py` si nécessaire.

## 📊 Jeux de données

| Fichier                       | Lignes    | Description                                                                                                  |
| ----------------------------- | --------- | ------------------------------------------------------------------------------------------------------------ |
| `instacart_sample_1m.parquet` | 1 000 000 | Échantillon de commandes Instacart (2017) : utilisateurs, produits, rayons, départements, détails de panier. |

**Structure des données** :

* **Orders** : détails de chaque commande (ID utilisateur, jour de la semaine, heure, délai depuis la dernière commande).
* **Products** : catalogue de \~50 000 produits avec noms et rayons.
* **Aisles** : 134 rayons (ex : "légumes frais", "fromages emballés").
* **Departments** : 21 départements (ex : "œufs laitiers", "boissons").
* **Order\_products** : produits dans chaque commande et ordre d'ajout.

*Source : Kaggle – Analyse du panier d'épicerie en ligne Instacart.*

## 🧠 Méthodologie

1. **EDA & nettoyage** (`data_and_finetuning_cohort.py`)

   * Détection et traitement des NaN, doublons et typage.
   * Création de variables : `order_dow_name`, totaux par client, indicateurs RFM.
2. **Segmentation RFM**

   * Standardisation des indicateurs.
   * Détermination du nombre de clusters (méthode du coude).
   * Application de KMeans.
3. **Visualisations**

   * Bar charts, heatmap temporelle, pairplot, vue 3D.
4. **Exploration de texte**

   * Nettoyage, tokenisation, suppression de stop words.
   * Génération de WordCloud depuis un fichier texte.

## 🏗️ Architecture de l'application

```
duda_cohortscore/
├── app.py                          # Application Streamlit
├── data_and_finetuning_cohort.py  # EDA, nettoyage & création de variables
├── requirements.txt                # Dépendances Python
├── data/
│   ├── instacart_sample_1m.parquet # Échantillon de travail
│   └── instacart_cleaned.csv       # Jeu nettoyé final
└── README.md                       # Ce document
```

## ⚙️ Installation & Exécution

Voir la section **Démo rapide** ci-dessus pour les commandes pas-à-pas.

## 🙋 Auteurs

* **Alexandre Cameron BORGES** – [LinkedIn](https://www.linkedin.com/in/alexandre-cameron-borges)
* **Alioune DIOP** – [LinkedIn](https://www.linkedin.com/in/aliounediop)

```
```



