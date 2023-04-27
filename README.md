# Projet TAL

## 🎬 Description
L'objectif du projet est de réaliser un système de recherche d’information dans une collection de descriptions de films publiées sur Allociné.  
Le projet se décompose en deux parties:  
- Prédiction du genre des films par TAL
- Visualisation des résultats

## 📎 Ressources

### 📦 Bibliotèques Python
- [Pandas](https://pandas.pydata.org/)
- [Numpy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Scikit-Learn](https://scikit-learn.org/stable/)
- [Imbalanced-Learn](https://imbalanced-learn.org/stable/)
- [Tensorflow](https://www.tensorflow.org/?hl=fr)

### 📚 Articles

## 👥 Equipe
- ALLEMAND Fabien
- LEBOT Samuel

## 📝 To Do list
- [ ] Vérifier l'encodage
- [ ] https://fasttext.cc/docs/en/crawl-vectors.html
- [ ] Tokénisation données = tokénisation plongement (mot hors vocabulaire)

## Usage

### Solr Commands
> ./bin/solr create -c allocine # only first use
> ./bin/solr start
> curl http://localhost:8983/solr/allocine/update/csv --data-binary @../data/test_results.csv -H 'Content-type:text/plain; charset=utf-8'
> curl "http://localhost:8983/solr/allocine/update?commit=true"
> http://localhost:8983/solr/allocine/select?q=titre%3Astar
> http://localhost:8983/solr/allocine/browse?q=titre%3Astar
> ./bin/solr stop


## Résultats
- Basic methode -- 66% of accuracy with random forest
- CNN -- 72.91% of accuracy
- LSTM -- 74.51% of accuracy