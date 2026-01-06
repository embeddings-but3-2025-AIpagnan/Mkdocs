# Notre démarche

## Format

Nous avions initialement envisagé le développement d’une **application web hébergée sur un serveur**, afin de garantir une **accessibilité simple et universelle** depuis n’importe quel terminal. Ce choix facilitait également la maintenance et les mises à jour de l’application.

Cependant, lors des échanges avec notre cliente, des **préoccupations liées à la souveraineté des données** ont été soulevées. L’hébergement distant des données ne répondait pas pleinement aux exigences de sécurité et de maîtrise des informations. Nous avons donc orienté notre réflexion vers une **application de bureau**, permettant un traitement et un stockage des données **en local**.

Dans ce contexte, nous avons étudié plusieurs technologies permettant de transformer une application en solution de bureau multiplateforme. Trois frameworks se sont démarqués : **Flet**, un framework Python basé sur Flutter, **Electron**, une solution JavaScript largement utilisée, et **Tauri**, un framework récent reposant sur Rust.

Notre choix s’est porté sur **Tauri**, principalement en raison de sa **légèreté**, de ses **bonnes performances** et de sa **faible consommation de ressources**. Contrairement à Electron, qui embarque un moteur Chromium complet, Tauri s’appuie sur le moteur web natif du système, ce qui permet de produire des applications plus rapides et plus compactes.

---

## Tableau comparatif des technologies étudiées

| Critère | **Flet** | **Electron** | **Tauri** |
|-------|---------|-------------|----------|
| **Langage principal** | Python | JavaScript / TypeScript | Rust (backend) + Web |
| **Poids de l’application** | Moyen | Élevé | Très faible |
| **Consommation mémoire** | Moyenne | Élevée | Faible |
| **Performances** | Bonnes | Correctes | Excellentes |
| **Sécurité** | Standard | Standard | Élevée |


## Front-End

Dans le cadre du développement du front-end de l’application, notre équipe a pris le temps d’évaluer plusieurs frameworks modernes tels que **React, Vue, Svelte, Solid, Astro, Next.js**, ainsi que d’autres solutions émergentes.

Cette phase d’étude avait pour objectif d’identifier la technologie la plus adaptée à nos contraintes fonctionnelles et techniques. Nous recherchions une solution capable de concilier **performance**, **simplicité de mise en œuvre**, **évolutivité** et **interactivité**, tout en restant cohérente avec la nature du projet : **une application légère, rapide à charger et facile à maintenir sur le long terme**.

À l’issue de cette comparaison, nous avons décidé d’adopter **Astro** comme framework principal pour le rendu et la structure globale, accompagné de **SolidJS** pour gérer les parties interactives via le système des *Astro Islands*.

## Back-End

Concernant le back-end de l’application, l’un de nos prérequis majeurs était l’utilisation du **langage Python**. Nous avons donc évalué plusieurs **frameworks Python** capables d’assurer la communication entre le **front-end** et la logique métier de l’application. Dans un premier temps, notre attention s’est portée sur **Flask**, un framework web **léger, rapide à mettre en œuvre et très simple d’utilisation**. Flask est particulièrement adapté aux projets de petite à moyenne envergure et offre une grande flexibilité grâce à son approche minimaliste.

Après présentation de cette solution à notre cliente. Elle nous a partagé qu'elle considérait Flask comme un framework **relativement ancien**, nécessitant de nombreux modules additionnels pour répondre à des besoins modernes (validation des données, documentation automatique, performances élevées). Suite aux recommandations d’une de ses connaissances, elle nous a suggéré d’envisager l’utilisation de **FastAPI**.

Nous nous sommes donc orientés vers **FastAPI**, un framework Python moderne conçu pour le développement d’**API rapides et performantes**. FastAPI permet une **validation automatique des données**, une **documentation interactive générée automatiquement** et d’excellentes performances, proches de celles de frameworks plus bas niveau. Ces caractéristiques en font une solution particulièrement adaptée à notre projet et aux attentes de notre cliente.

