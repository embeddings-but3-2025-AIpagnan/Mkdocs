# Démarches de test

Dans l'optique de tester les algorithmes d'embedding, nous avons mis en place un protocole de test, celui-ci consiste à établir un corpus de synonymes, d'antonymes, d'holonymes et de mots associés et d'ainsi calculer la proximité entre chacun des éléments par le modèle ollama afin de calculer la moyenne de chaque échantillon pour permettre de vérifier l'éfficacité du modèle.
Théoriquement, les synonymes devrait avoir le meilleur résultats conntrairement aux antonymes. 

## Échantillion du corpus de synonymes

* `à,chez,dans,parmi
abaca,chanvre,chènevière,filasse,jute
abaissable,abattable,inclinable
abaissant,avilissant,humiliant,mortifiant,dégradant,vexant,honteux,écrasant,blessant
abaissé,avili,rabaissé,déconsidéré,diminué,déchu,disqualifié,discrédité,dévalorisé,dévalué
abaisse-langue,spatule,manche`