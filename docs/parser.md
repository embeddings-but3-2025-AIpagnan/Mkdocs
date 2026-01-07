# Parser
La suite de la SAE se concentrera sur de l'analyse de code, c'est donc pour cela qu'il est nécessaire de détenir ce qui s'appelle un parser.
L'action de parser se réfère à l'analyse syntaxique, c'est-à-dire mettre en évidence la structure d'un texte. Cela est utilisé dans de nombreux domaines, que ce soit dans les langues, les maths ou bien ce qui nous intéresse, la programmation.
Dans notre cas, cela consiste à extraire les mots clés non inhérents aux langages donc définis par les utilisateurs pour ensuite relever les occurrences.

Après avoir effectué des tests en utilisant les expressions régulières, ceux-ci se sont révélés non concluants car trop complexes et pas assez fiables.

Nous sommes donc passés sur la bibliothèque **tree-sitter** permettant de réaliser notre besoin d'une manière assez simple en définissant simplement, pour chaque langage ciblé, le type de mot clé que nous souhaitons récupérer.

C'est donc comme cela que nous avons pu réaliser des fonctions Python placées dans le back-end permettant de prendre un dossier de code, dans un premier temps uniquement en Java, et d'en extraire les termes métier triés par le nombre d'occurrences et donc leur probable importance. Implémentés dans l'application, cela permet de créer une base afin de remplir un glossaire.