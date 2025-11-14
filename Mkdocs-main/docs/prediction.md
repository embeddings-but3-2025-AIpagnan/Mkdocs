# Embeddings prédictifs (Prediction-Based Embeddings)
Ces modèles apprennent les vecteurs en prévoyant un mot à partir de son contexte ou l’inverse.


Utilisent des réseaux de neurones simples pour créer des représentations distribuées.


## Exemples

### Word2Vec

* `Skip-gram` : prédit les mots du contexte à partir du mot cible.


* `CBOW` (Continuous Bag of Words) : prédit le mot cible à partir du contexte.


* `GloVe` : combine approche de cooccurrence et apprentissage prédictif ; s’appuie sur la probabilité relative de cooccurrence entre mots.


## Avantages

efficaces, rapides à entraîner, bonnes performances sur les similarités sémantiques.


## Inconvénients

un seul vecteur par mot, pas de prise en compte du contexte (un mot a toujours le même vecteur, quel que soit son sens dans la phrase).
