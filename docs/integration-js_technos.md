# Pourquoi nous avons choisi SolidJS ?

Certaines fonctionnalités de l’application nécessitent une interactivité locale, notamment pour des **tableaux modifiables**, des formulaires dynamiques ou des composants nécessitant des mises à jour fréquentes de l’état.

Pour répondre à ces besoins spécifiques sans alourdir inutilement l’ensemble de l’application, nous avons choisi **SolidJS**, intégré via le système des *Astro Islands*.

## Nos motivations principales

| Critère                      | Observation                      | Avantage                                           |
| ---------------------------- | -------------------------------- | -------------------------------------------------- |
| **Performance runtime**      | Réactivité fine sans Virtual DOM | Expérience utilisateur fluide et instantanée       |
| **Poids du bundle**          | Framework très léger             | Interactivité sans compromettre la vitesse globale |
| **Simplicité d’intégration** | Compatibilité native avec Astro  | Aucun surcoût de configuration                     |
| **API moderne et familière** | Syntaxe proche de React          | Courbe d’apprentissage rapide pour l’équipe        |

SolidJS n’est chargé que **là où il est strictement nécessaire**. Le reste du site demeure statique et optimisé, ce qui nous permet de **minimiser la quantité de JavaScript envoyée au client**, tout en conservant une expérience utilisateur moderne, réactive et cohérente.
