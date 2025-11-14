# Architecture retenue

Notre architecture front-end se découpe en deux niveaux :

1. **Astro** : gère le rendu statique, le routage, la structure globale et le SEO.  
2. **Solid (Islands)** : prend en charge les zones interactives ciblées au sein des pages Astro.

Cette approche hybride nous permet de bénéficier du **meilleur des deux mondes** :  
- la **vitesse d’un site statique**,  
- et la **souplesse d’un framework réactif** là où c’est utile.