# Premières expériences

## Choix des technologies

Pour commencer, il nous a fallu choisir une technologie à utiliser. Comme nous n'arrivions pas à faire fonctionner Word2Vec (pour des raisons techniques), nous avons initialement choisi d'utiliser un modèle basé sur des transformers, facile à lancer n'importe où grâce à Ollama. Nous avons ensuite réussi à faire fonctionner Word2Vec, et nous avons donc initialement décidé de comparer les deux.

Pour Word2Vec, nous avons utilisé le corpus text8, qui contient le premier milliard de caractères de Wikipedia. L'autre modèle que nous avons utilisé est MiniLM, qui est basé sur une architecture BERT (qui est elle-même basée sur une architecture de transformers).

## Tests sémantiques sur MiniLM

Nous avons commencé par faire des tests pour voir s'il était possible de se baser sur la proximité (distance scalaire) pour trouver des relations entre les mots. Nous avons donc calculé la distance moyenne entre des groupes de synonymes, antonymes, mots associés et holonymes (relation de tout à partie).  
Pour les synonymes, nous avons trouvé un corpus de 36 000 groupes de synonymes. Nous n'avons pas trouvé de corpus pour les autres types de mots, nous les avons donc générés par IA.

Voici les résultats:

- Synonymes
    - Proximité moyenne: 0.637
    - Proximité minimale: 0.484 pour épistaxis, saignement de nez
    - Proximité maximale: 0.976 pour scintigramme, scintillogramme
- Antonymes
    - Proximité moyenne: 0.665
    - Proximité minimale: 0.565 pour aube, crépuscule
    - Proximité maximale: 0.907 pour visible, invisible
- Associés
    - Proximité moyenne: 0.640
    - Proximité minimale: 0.554 pour lion, crinière
    - Proximité maximale: 0.794 pour pluie, parapluie
- Holonymes
    - Proximité moyenne: 0.653
    - Proximité minimale: 0.537 pour organe, corps
    - Proximité maximale: 0.854 pour graine, fruit

À notre grande déception, tous les types de mots ont une proximité similaire. Après réflexion, cela paraît logique, car même si la relation entre les mots est différente, ils restent proches sémantiquement.

## Récupération de synonymes via Word2Vec

Contrairement à MiniLM, Word2Vec permet de récupérer la liste des mots qui sont proches d'un vecteur. Nous avons donc testé de trouver des synonymes avec la méthode suivante : on part d'un (ou plusieurs) mot(s), on les embed (c'est-à-dire les convertit en vecteur), on fait la moyenne des vecteurs obtenus, puis on récupère la liste des mots les plus proches de ce vecteur.

Voici les résultats (la proximité au vecteur est entre parenthèses):

- Avec les mots: home, residence, house
    - house (`0.802`)
    - residence (`0.788`)
    - home (`0.749`)
    - palace (`0.693`)
    - mansion (`0.678`)
    - manor (`0.661`)
    - castle (`0.631`)
    - windsor (`0.628`)
    - edinburgh (`0.625`)
    - hotel (`0.620`)
- Avec les mots: button, zipper, latch
    - button (`0.989`)
    - buttons (`0.829`)
    - hook (`0.781`)
    - stick (`0.769`)
    - punch (`0.763`)
    - notch (`0.762`)
    - pedal (`0.754`)
    - tray (`0.751`)
    - window (`0.749`)
    - keyboard (`0.748`)
- Avec les mots: penalty, sanction, sentence
    - penalty (`0.861`)
    - sentence (`0.849`)
    - defendant (`0.712`)
    - felony (`0.683`)
    - manslaughter (`0.669`)
    - procedure (`0.666`)
    - punishment (`0.652`)
    - offence (`0.634`)
    - conviction (`0.634`)
    - wrongful (`0.628`)
- Avec les mots: ruby, emerald, sapphire
    - sapphire (`0.856`)
    - ruby (`0.855`)
    - microcebus (`0.836`)
    - plum (`0.829`)
    - moth (`0.825`)
    - bean (`0.823`)
    - ginger (`0.820`)
    - cabbage (`0.819`)
    - emerald (`0.817`)
    - marmoset (`0.805`)

Comme on peut le voir, la qualité des mots est plutôt mauvaise, et les scores ne permettent pas de filtrer les meilleurs mots. En plus de cela, Word2Vec ne supporte pas le contexte (c'est-à-dire qu'on ne peut embedder qu'un seul mot à la fois). Même si nous avons simulé du contexte en faisant la moyenne de plusieurs mots, c'est tout de même moins qualitatif qu'un modèle qui permet d'utiliser du contexte.

Au vu du manque d'efficacité de cette méthode, nous avons décidé de changer de méthode pour déterminer les synonymes d'un mot.
