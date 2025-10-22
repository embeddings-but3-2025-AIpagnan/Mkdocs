# Pourquoi nous avons Choisi Solid ?

Certaines fonctionnalités de l’application nécessitent une interactivité locale due aux tableaux nécessitant de pouvoir être modifiables.  
Pour ces cas spécifiques, nous avons choisi **SolidJS**, intégré via le système des *Astro Islands*.

## Nos motivations principales :

| Critère | Observation | Avantage |
|----------|--------------|-----------|
| **Performance runtime** | Solid est reconnu pour sa réactivité exceptionnelle | Expérience fluide et instantanée |
| **Poids du bundle** | Très léger | Interactivité sans compromettre la vitesse globale |
| **Simplicité d’intégration** | Compatible nativement avec Astro | Aucun surcoût de configuration |
| **API moderne et familière** | Proche de React mais plus performante | Courbe d’apprentissage rapide pour l’équipe |

Solid n’est chargé que là où c’est nécessaire.  
Le reste du site reste statique et optimisé, ce qui nous permet de **minimiser la quantité de JavaScript envoyée au client**, tout en maintenant une UX moderne et réactive.