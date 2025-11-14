# Pourquoi nous avons choisi Astro ?

Astro s’est rapidement imposé pour plusieurs raisons stratégiques :

| Critère | Observation | Impact sur le projet |
|----------|--------------|----------------------|
| **Performance initiale** | Rendu HTML statique, 0 JS par défaut | Temps de chargement ultra rapide |
| **Poids du bundle** | Très faible (JS uniquement sur les composants interactifs) | Réduction du coût réseau et meilleure UX |
| **Simplicité du code** | Structure claire, séparation nette contenu / logique | Maintenance facilitée |
| **SEO et accessibilité** | Excellent grâce au pré-rendu HTML | Meilleur référencement naturel |
| **Facilité d’intégration** | Support hybride et partiel | Intégration fluide avec notre stack existante |
| **Écosystème en croissance** | Plugins officiels et communauté active | Améliorations et support à long terme |

Nous avons retenu Astro car il permet de **livrer un site ultra performant dès le premier rendu**, tout en restant suffisamment flexible pour intégrer des composants dynamiques grace à astro islands.  
C’est une approche “**content-first**”, c'est à dire priorisant l'affichage de données, qui correspond parfaitement à notre besoin : beaucoup de contenu statique, enrichi par quelques zones interactives.
