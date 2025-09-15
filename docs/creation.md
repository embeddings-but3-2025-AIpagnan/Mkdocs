# Comment les embeddings sont créés
Les embeddings sont généralement appris automatiquement à partir de grands corpus de texte, en utilisant des techniques d’apprentissage automatique ou d’apprentissage profond.


L’objectif principal est de trouver une représentation numérique pour chaque mot (ou phrase, ou document) qui capture ses relations avec les autres mots dans le langage.


 Étapes générales de création d’un embedding
## 1. Préparation des données :

Un grand corpus de texte est collecté (par exemple : Wikipedia, livres, articles...).
Le texte est nettoyé, découpé en phrases, puis en mots (tokenisation)
Une "fenêtre de contexte" est définie : par exemple, on peut regarder les 5 mots autour de chaque mot cible.


## 2. Construction d’un objectif d’apprentissage :

On choisit un objectif à optimiser. Par exemple :
Prédire un mot cible à partir de son contexte (CBOW).
Prédire le contexte à partir d’un mot cible (Skip-gram).
Ou bien apprendre une fonction qui approxime les relations de cooccurrence entre mots (GloVe).
Ce sont des tâches simples, mais qui forcent le modèle à comprendre les relations entre mots pour réussir.


## 3. Entraînement d’un modèle :

On utilise un petit réseau de neurones (dans Word2Vec) ou une architecture plus complexe (LSTM pour ELMo, Transformer pour BERT).
Le modèle ajuste progressivement les vecteurs associés à chaque mot, de manière à minimiser une fonction de perte (par exemple : erreur de prédiction du mot).
Pendant cet entraînement, chaque mot est associé à un vecteur qui évolue à chaque itération pour mieux refléter ses usages dans le corpus.


## 4. Extraction des vecteurs appris :


Une fois l’entraînement terminé, chaque mot a un vecteur numérique stable : c’est son embedding.
Ces vecteurs peuvent ensuite être utilisés dans d’autres modèles pour différentes tâches (analyse de sentiments, traduction automatique, résumé de texte, etc.).
