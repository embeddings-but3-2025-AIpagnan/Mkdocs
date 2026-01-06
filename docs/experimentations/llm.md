# LLM

Afin de résoudre les problèmes de la méthode précédente, nous avons complètement changé d'approche. Nous avons décidé d'utiliser un LLM traditionnel (similaire à ChatGPT par exemple). En l'occurence, notre choix s'est porté sur **Qwen3**, car il est haut dans les leaderboards (comme on peut le voir [ici](https://llm-stats.com/leaderboards/open-llm-leaderboard)), et qu'il y a des versions compressées, moins intelligentes, mais suffisamment légères pour être utilisées localement.  
Un avantage majeur d'utiliser un LLM est sa grande flexibilité: il suffit de modifier le prompt pour générer différents types de contenus.

En l'occurence, pour générer des synonymes, nous sommes arrivés à ce prompt grâce à des tests itératifs rapides:

```
In a ubiquitous language glossary named "<nom du glossaire>" and with the following description:
<description du glossaire>

The glossary currently contains the following words: <mots du glossaire>

Find synonyms of the word "<mot>" as defined by:
<définition du mot>

Already known synonyms for the correct sense of the word: <liste des synonymes déjà présents>

Your response MUST be in the original word's language.
Respond ONLY with the synonyms, separated by commas. Do not include any other text in your response.
```

Il suffit ensuite de nettoyer la réponse donnée par l'IA en appliquant ces étapes:

- Suppression de certains caractères que l'IA utilise parfois (`'`, `"`, `.`)
- Passage en minuscules de tous les mots
- Déduplication des mots, incluant les pluriels

Même si les résultats ne sont pas parfaits (par exemple, l'IA génère souvent des réponses en anglais même lorsque le glossaire est en français), à cause des capacités limitées des petits modèles, ils restent globalement de bonne qualité.  
C'est donc cette méthode qui a été retenue pour l'application finale.