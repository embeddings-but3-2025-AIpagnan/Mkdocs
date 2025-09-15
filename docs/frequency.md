# Embeddings basés sur la fréquence (Frequency-Based Embeddings)
Ces méthodes utilisent des statistiques de concurrence des mots dans un corpus.


Elles reposent sur des matrices qui comptent le nombre de fois où des mots apparaissent ensemble dans des fenêtres de texte.


## Exemples :


* `Count Vector` : vecteur basé sur le nombre d’occurrences de chaque mot dans un document.


* `TF-IDF (Term Frequency-Inverse Document Frequency)` : pondère les mots en fonction de leur fréquence dans le document et dans le corpus.


* `LSA (Latent Semantic Analysis)` :utilise la décomposition SVD pour extraire des concepts latents à partir d’une matrice terme-document.


## Avantages : 
simples, interprétables.


## Inconvénients : 
matrices très grandes et creuses, peu efficaces pour capturer des liens sémantiques complexes.
