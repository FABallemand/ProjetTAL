# Projet TAL

## 🎬 Description
L'objectif du projet est de réaliser un système de recherche d’information dans une collection de descriptions de films publiées sur Allociné.  
Le projet se décompose en deux parties:  
- Prédiction du genre des films par TAL
- Visualisation des résultats

## 🛠 Usage
- Le dossier **notebooks** contient les fichiers consacrés à l'analyse des données et au TAL.
- Le dossier **solr-8.3.0** contient une installation de Solr modifiée pour répondre aux besoins du projet.
- Le dossier **rapport** contient le rapport détaillé du projet.

### 🐍 Notebooks Python
Les notebooks Python contiennent les commandes pour analyser et traiter les données, entraîner et tester différents modèles mais aussi effectuer des prédictions avec le modèle final choisi. Ils sont à considérer dans l'ordre suivant:
- Analyse_donnees.ipynb
- Methodes_basiques.ipynb
- CNN.ipynb
- BILSTM.ipynb
- Transformers.ipynb (très difficile à exécuter avec un ordinateur lambda)

**Remarque:** les fichiers dont le nom commencent par **test_** sont des fichiers de test.

### 🔎 Solr
- Depuis la racine de Solr (**solr-8.3.0**):
    - Lancer le serveur Solr:
    ```bash
    ./bin/solr start
    ```
    - Charger les données:
    ```bash
    curl http://localhost:8983/solr/allocine/update/csv --data-binary @../data/test_results.csv -H 'Content-type:text/plain; charset=utf-8'
    curl "http://localhost:8983/solr/allocine/update?commit=true"
    ```
    - Arrêter le serveur Solr:
    ```bash
    ./bin/solr stop
    ```
- Depuis la barre de recherche d'un navigateur web:
    - Accéder à l'interface de gestion de Solr:
    ```url
    localhost:8983
    ```
    - Effectuer une requête sur le mot "star" (deux méthodes, browse permet d'avoir une interface plus travaillée):
    ```url
    http://localhost:8983/solr/allocine/select?q=titre%3Astar
    http://localhost:8983/solr/allocine/browse?q=titre%3Astar
    ```

## 📎 Ressources

### 📦 Bibliotèques Python
- [Pandas](https://pandas.pydata.org/)
- [Numpy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Scikit-Learn](https://scikit-learn.org/stable/)
- [Imbalanced-Learn](https://imbalanced-learn.org/stable/)
- [Tensorflow](https://www.tensorflow.org/?hl=fr)

### 📚 Ressources TAL
- [Hugging Face](https://huggingface.co/models)

### 🔎 Ressources Solr
- [ri_atexte](https://git.unistra.fr/ruizfabo/ri_atexte)

## 👥 Equipe
- ALLEMAND Fabien
- LEBOT Samuel

## 📝 To Do list
- [x] Relancer modèles pour mettre à jour rapport

## 📊 Résultats
Précision pendant l'entraînement:
- Méthodes basiques -- 12% (Baseline)
- Méthodes basiques -- 59% (Mutinomial NB)
- Méthodes basiques -- 58% (CART)
- Méthodes basiques -- 73% (LR)
- Méthodes basiques -- 69% (Random Forest)
- CNN (avec oversampling) -- 75.29 (+- 0.77)
- LSTM -- 76.60%
- Transformer -- ???%

Le modèle qui donne les meilleurs résultats est le CNN (le LSTM donne des résultats similaires mais avec un temps de calcul nettement supérieur). On obtient une **précision de 51% sur le jeu de test**.