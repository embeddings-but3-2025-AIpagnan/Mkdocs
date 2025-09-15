# Embeddings contextualisés (Contextualized Word Embeddings)
Ces embeddings tiennent compte du contexte dans lequel le mot apparaît.


Le même mot peut donc avoir plusieurs représentations différentes selon la phrase (ex : “bark” en anglais peut désigner un aboiement ou une écorce).


Utilisent des architectures avancées comme les réseaux LSTM bidirectionnels ou les Transformers.


## Exemples :


* `ELMo `: produit un vecteur pour chaque mot en tenant compte de toute la phrase, via des LSTM bidirectionnels.


* `BERT : modèle basé sur les Transformers `; produit des vecteurs contextuels riches pour chaque mot.


* `GPT, RoBERTa, XLNet, etc. `: d’autres variantes de modèles préentraînés de type Transformer.


## Avantages : 
très performants, capturent le sens réel du mot dans son contexte.


## Inconvénients : 
lourds à entraîner et à déployer, difficilement interprétables.
