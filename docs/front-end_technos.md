# Pourquoi nous avons choisi Astro ?

Astro s’est rapidement imposé comme une solution particulièrement pertinente pour notre projet, notamment grâce à son approche orientée **performance par défaut** et sa philosophie *content-first*.

Contrairement aux frameworks SPA traditionnels, Astro privilégie le rendu HTML statique et limite drastiquement l’envoi de JavaScript au navigateur. Cette caractéristique correspond parfaitement à notre besoin principal : afficher efficacement une grande quantité de contenu, tout en conservant la possibilité d’ajouter de l’interactivité de manière ciblée.

## Analyse par critères

| Critère                      | Observation                                                           | Impact sur le projet                                           |
| ---------------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Performance initiale**     | Rendu HTML statique, 0 JavaScript par défaut                          | Temps de chargement ultra rapide dès le premier affichage      |
| **Poids du bundle**          | JavaScript chargé uniquement pour les composants interactifs          | Réduction du coût réseau et amélioration significative de l’UX |
| **Simplicité du code**       | Structure claire et séparation nette entre contenu, styles et logique | Maintenance facilitée et meilleure lisibilité                  |
| **SEO et accessibilité**     | Pré-rendu HTML natif                                                  | Référencement naturel optimisé et meilleure accessibilité      |
| **Facilité d’intégration**   | Support hybride de multiples frameworks                               | Intégration fluide avec notre stack existante                  |
| **Écosystème en croissance** | Plugins officiels, documentation complète, communauté active          | Pérennité de la solution et évolutions à long terme            |

Nous avons retenu Astro car il permet de **livrer une application extrêmement performante dès le premier rendu**, tout en restant suffisamment flexible pour intégrer des composants dynamiques grâce au concept des *Astro Islands*.

Cette approche dite **« content-first »**, qui priorise l’affichage rapide des données et du contenu, correspond parfaitement à notre cas d’usage : une majorité de pages statiques enrichies par quelques zones interactives ciblées.
