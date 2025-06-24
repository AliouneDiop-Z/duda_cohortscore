# duda_cohortscore
UDA CohortScore v1
Le DUDA CohortScore est le MVP d'une Webapp Streamlit d'analyse de cohortes, réalisé pour le DU Sorbonne Data Analytics 2024-2025 par Alexandre Cameron BORGES & Alioune DIOP. L'outil segmente la clientèle Instacart via l'analyse RFM (Récence, Fréquence, Montant), explore les habitudes d'achat et génère un WordCloud à partir d'un texte importé.

Dépôt GitHub Python

· 1️⃣ ✨ Objectif
Segmenter les clients selon le modèle RFM.
Visualiser les tendances d'achat (top produits, heatmaps temporelles).
Explorer dynamiquement via des filtres (jour, heure, rayon, cluster).
Générer un WordCloud à partir d'un fichier texte lié au e-commerce.
· 2️⃣ 🚀 Démo rapide
Ouvrez la WebApp hébergée → https://acb-dudacohortscore.streamlit.app/

ou

Cloner le dépôt et installer les dépendances (cf. §6).

Lancer l'application :

streamlit run app.py
Dans l'interface :

Sélectionner le fichierdata/instacart_sample_1m.parquet
Appliquer des filtres (jour, heure, rayon, cluster)
Explorer les graphiques (bar charts, heatmap, pairplot, vue 3D)
Charger un texte pour générer un WordCloud
· 3️⃣ 📊 Jeux de données
Tableau	Lignes	Description
instacart_sample_1m.parquet	1 000 000	Cet échantillon de jeu de données provient d'Instacart, une plateforme américaine de livraison d'épicerie en ligne. L'original contient des informations anonymisées sur plus de 3 millions de commandes passées par plus de 200 000 utilisateurs Instacart en 2017.
Contenu principal : Le jeu de données comprend plusieurs fichiers CSV interconnectés :

Commandes : Informations sur chaque commande (ID utilisateur, jour de la semaine, heure, délai depuis la dernière commande)
Produits : Catalogue de ~50 000 produits avec leurs noms et rayons
Allées : Les 134 rayons du magasin (ex : « légumes frais », « fromages emballés »)
Départements : Les 21 départements (ex : "œufs laitiers", "boissons")
Order_products : Détails des produits dans chaque commande avec l'ordre d'ajout au panier
Source : Kaggle – Analyse du panier d'épicerie en ligne Instacart

· 4️⃣ 🧠 Méthodologie
EDA & nettoyage ( data_and_finetuning_cohort.py) :

Détection et traitement des NaN, doublons, typage.
Création de variables :

order_dow_name(jour de la semaine), totaux par client, indicateurs RFM.
Regroupement RFM :

Standardisation, méthode du coude, KMeans.
Visualisations (10 graphiques) :

Graphiques à barres, carte thermique, pairplot, vue 3D.
Exploration de texte :

Nettoyage, tokenisation, suppression de mots vides, génération de WordCloud.
· 5️⃣ 🏗️ Architecture de l'application
duda_cohortscore/
├── app.py                          # Application Streamlit
├── data_and_finetuning_cohort.py  # EDA, nettoyage & création de variables
├── requirements.txt                # Dépendances Python
├── data/
│   ├── [instacart_sample_1m.parquet](https://drive.google.com/file/d/1znbv-o5XfyWLc_5IcnHosrDdgH8JafDp/view?usp=drive_link) # Échantillon de travail
│   └── [instacart_cleaned.csv](https://drive.google.com/file/d/1pRjgJ3X8CXfcaApv_W-QfZiWTHO71HlS/view?usp=drive_link)       # Jeu nettoyé final
└── README.md                       # Ce document
· 6️⃣ ⚙️ Paramètres régionaux d'installation
# 1. Cloner le repo
git clone https://github.com/alexandre-cameron-borges/duda_cohortscore.git
cd duda_cohortscore

# 2. Créer et activer l’environnement
python -m venv .venv && source .venv/bin/activate  # macOS/Linux
# venv\Scripts\activate                            # Windows

# 3. Installer les dépendances
pip install --upgrade pip
pip install -r requirements.txt

# 4. Lancer l’application
streamlit run app.py
Note : l'application s'attend à trouver data/instacart_sample_1m.parquet. Ajustez le chemin dans app.pysi nécessaire.

· 7️⃣ 🙋 Auteurs
Alexandre Cameron BORGES – LinkedIn
Alioune DIOP
