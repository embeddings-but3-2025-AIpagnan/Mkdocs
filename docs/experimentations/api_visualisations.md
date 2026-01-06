# API & Visualisations

## Nouvelle méthode

La nouvelle méthode fonctionne comme suit:

![](../images/pipeline-ia.png)

On commence par récupérer les synonymes du mot depuis des API, puis on embède le mot (avec son contexte) ainsi que les synonymes. On classe ensuite les synonymes selon leur proximité avec l'embedding du mot et on ne garde que les meilleurs. On peut aussi faire la même chose avec des antonymes.

## Comparaison MiniLM et Word2Vec

Pour déterminer quel était le meilleur modèle pour cette tâche, nous avons créé une visualisation afin de voir lequel rapprochait le mieux les différents synonymes. Dans cette visualisation, 4 groupes de 3 mots sont affichés, en anglais et en français (sauf pour Word2Vec, dont le corpus utilisé est exclusivement anglais).

**Word2Vec (mots anglais)**

![](../images/visualisation_word2vec_en.png)

**MiniLM (mots anglais)**

![](../images/visualisation_minilm_en.png)

**MiniLM (mots français)**

![](../images/visualisation_minilm_fr.png)

On peut voir que, pour Word2Vec deux groupes (« gems » et « button ») sont bien regroupés, mais pas les deux autres. Pour MiniLM, les groupes sont bien regroupés en anglais, mais pas en français.  
Au vu de ces résultats, nous avons décidé d'abandonner complètement Word2Vec et d'utiliser MiniLM pour la suite.

## Stratégie d'embedding

À l'origine, nous utilisions la même stratégie pour embedder les mots avec MiniLM qu'avec Word2Vec: chaque mot du contexte (tous des synonymes les uns des autres lors des tests) était embeddé individuellement, puis la moyenne des vecteurs était utilisée comme résultat (méthode 1). Nous avons décidé de comparer cette méthode avec une autre, plus adaptée à un modèle qui prend en compte le contexte: concaténer tous les mots du contexte, séparés par des virgules, puis embedder le tout d'un coup (méthode 2).

Pour comparer les deux méthodes, nous avons lancé la recherche de synonymes sur 4 groupes de 3 mots:

- Groupe 1: *home*, *residence*, *house*  
- Groupe 2: *button*, *zipper*, *latch*  
- Groupe 3: *penalty*, *sanction*, *sentence*  
- Groupe 4: *ruby*, *emerald*, *sapphire*

Pour chaque groupe, on récupère la liste des synonymes et on les affiches avec leur score et leur nombre d'occurrences (le même synonyme peut apparaître dans plusieurs API, et plusieurs fois dans la même API). Voici les résultats:

**Groupe 1**
<table>
	<thead>
		<tr>
			<th colspan="3" style="text-align: center;">Méthode 1</th>
			<th colspan="3" style="text-align: center;">Méthode 2</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
		</tr>
		<tr>
			<td>abidance</td>
			<td>0.7958</td>
			<td>1</td>
			<td>abidance</td>
			<td>0.9731</td>
			<td>1</td>
		</tr>
		<tr>
			<td>enclose</td>
			<td>0.7688</td>
			<td>2</td>
			<td>manse</td>
			<td>0.9287</td>
			<td>1</td>
		</tr>
		<tr>
			<td>rezidentura</td>
			<td>0.7639</td>
			<td>1</td>
			<td>enclose</td>
			<td>0.9095</td>
			<td>2</td>
		</tr>
		<tr>
			<td>menage</td>
			<td>0.7485</td>
			<td>2</td>
			<td>menage</td>
			<td>0.9082</td>
			<td>2</td>
		</tr>
		<tr>
			<td>manse</td>
			<td>0.7222</td>
			<td>1</td>
			<td>rezidentura</td>
			<td>0.8941</td>
			<td>1</td>
		</tr>
		<tr>
			<td>sign</td>
			<td>0.6891</td>
			<td>1</td>
			<td>sign</td>
			<td>0.8894</td>
			<td>1</td>
		</tr>
		<tr>
			<td>base</td>
			<td>0.6771</td>
			<td>1</td>
			<td>firm</td>
			<td>0.8893</td>
			<td>1</td>
		</tr>
		<tr>
			<td>accommodate</td>
			<td>0.6673</td>
			<td>2</td>
			<td>theater</td>
			<td>0.8865</td>
			<td>1</td>
		</tr>
		<tr>
			<td>firm</td>
			<td>0.6666</td>
			<td>1</td>
			<td>accommodate</td>
			<td>0.8775</td>
			<td>2</td>
		</tr>
		<tr>
			<td>tenement</td>
			<td>0.6593</td>
			<td>2</td>
			<td>harbor</td>
			<td>0.8652</td>
			<td>2</td>
		</tr>
		<tr>
			<td>harbor</td>
			<td>0.6489</td>
			<td>2</td>
			<td>base</td>
			<td>0.8589</td>
			<td>1</td>
		</tr>
		<tr>
			<td>theater</td>
			<td>0.6380</td>
			<td>1</td>
			<td>harbour</td>
			<td>0.8277</td>
			<td>2</td>
		</tr>
		<tr>
			<td>harbour</td>
			<td>0.6236</td>
			<td>2</td>
			<td>tenement</td>
			<td>0.8241</td>
			<td>2</td>
		</tr>
		<tr>
			<td>domicile</td>
			<td>0.6151</td>
			<td>3</td>
			<td>shop</td>
			<td>0.8083</td>
			<td>4</td>
		</tr>
		<tr>
			<td>shop</td>
			<td>0.5999</td>
			<td>4</td>
			<td>put up</td>
			<td>0.7819</td>
			<td>2</td>
		</tr>
		<tr>
			<td>put up</td>
			<td>0.5895</td>
			<td>2</td>
			<td>store</td>
			<td>0.7787</td>
			<td>2</td>
		</tr>
		<tr>
			<td>store</td>
			<td>0.5737</td>
			<td>2</td>
			<td>host</td>
			<td>0.7711</td>
			<td>2</td>
		</tr>
		<tr>
			<td>host</td>
			<td>0.5590</td>
			<td>2</td>
			<td>domicile</td>
			<td>0.7245</td>
			<td>3</td>
		</tr>
		<tr>
			<td>abode</td>
			<td>0.5245</td>
			<td>4</td>
			<td>abode</td>
			<td>0.6901</td>
			<td>4</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>homeward</td>
			<td>0.6206</td>
			<td>2</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>residency</td>
			<td>0.5429</td>
			<td>2</td>
		</tr>
	</tbody>
</table>

**Groupe 2**
<table>
	<thead>
		<tr>
			<th colspan="3" style="text-align: center;">Méthode 1</th>
			<th colspan="3" style="text-align: center;">Méthode 2</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
		</tr>
		<tr>
			<td>endpin</td>
			<td>0.7081</td>
			<td>1</td>
			<td>push</td>
			<td>0.9102</td>
			<td>1</td>
		</tr>
		<tr>
			<td>adjuster</td>
			<td>0.6553</td>
			<td>1</td>
			<td>endpin</td>
			<td>0.9008</td>
			<td>1</td>
		</tr>
		<tr>
			<td>push</td>
			<td>0.6520</td>
			<td>1</td>
			<td>blow</td>
			<td>0.8806</td>
			<td>1</td>
		</tr>
		<tr>
			<td>slide fastener</td>
			<td>0.6389</td>
			<td>3</td>
			<td>adjuster</td>
			<td>0.8092</td>
			<td>1</td>
		</tr>
		<tr>
			<td>blow</td>
			<td>0.6132</td>
			<td>1</td>
			<td>clit</td>
			<td>0.7725</td>
			<td>1</td>
		</tr>
		<tr>
			<td>clit</td>
			<td>0.5455</td>
			<td>1</td>
			<td>slide fastener</td>
			<td>0.7202</td>
			<td>3</td>
		</tr>
		<tr>
			<td>zip fastener</td>
			<td>0.5384</td>
			<td>2</td>
			<td>zip</td>
			<td>0.6318</td>
			<td>2</td>
		</tr>
		<tr>
			<td>endbutton</td>
			<td>0.5212</td>
			<td>1</td>
			<td>zip up</td>
			<td>0.6314</td>
			<td>1</td>
		</tr>
		<tr>
			<td>zip up</td>
			<td>0.5019</td>
			<td>1</td>
			<td>endbutton</td>
			<td>0.5855</td>
			<td>1</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>zip fastener</td>
			<td>0.5750</td>
			<td>2</td>
		</tr>
	</tbody>
</table>

**Groupe 3**
<table>
	<thead>
		<tr>
			<th colspan="3" style="text-align: center;">Méthode 1</th>
			<th colspan="3" style="text-align: center;">Méthode 2</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
		</tr>
		<tr>
			<td>embargo</td>
			<td>0.7105</td>
			<td>1</td>
			<td>embargo</td>
			<td>0.8740</td>
			<td>1</td>
		</tr>
		<tr>
			<td>estoppel</td>
			<td>0.7021</td>
			<td>1</td>
			<td>estoppel</td>
			<td>0.8688</td>
			<td>1</td>
		</tr>
		<tr>
			<td>boycott</td>
			<td>0.6608</td>
			<td>1</td>
			<td>boycott</td>
			<td>0.8348</td>
			<td>1</td>
		</tr>
		<tr>
			<td>interdiction</td>
			<td>0.6523</td>
			<td>1</td>
			<td>interdiction</td>
			<td>0.8293</td>
			<td>1</td>
		</tr>
		<tr>
			<td>taboo</td>
			<td>0.6287</td>
			<td>1</td>
			<td>taboo</td>
			<td>0.7957</td>
			<td>1</td>
		</tr>
		<tr>
			<td>countenance</td>
			<td>0.6153</td>
			<td>1</td>
			<td>countenance</td>
			<td>0.7884</td>
			<td>1</td>
		</tr>
		<tr>
			<td>injunction</td>
			<td>0.5889</td>
			<td>1</td>
			<td>proscription</td>
			<td>0.7777</td>
			<td>1</td>
		</tr>
		<tr>
			<td>proscription</td>
			<td>0.5875</td>
			<td>1</td>
			<td>authority</td>
			<td>0.7736</td>
			<td>1</td>
		</tr>
		<tr>
			<td>punition</td>
			<td>0.5458</td>
			<td>2</td>
			<td>punition</td>
			<td>0.7174</td>
			<td>2</td>
		</tr>
		<tr>
			<td>authority</td>
			<td>0.5444</td>
			<td>1</td>
			<td>injunction</td>
			<td>0.6887</td>
			<td>1</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>ban</td>
			<td>0.6302</td>
			<td>1</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>verdict</td>
			<td>0.6016</td>
			<td>2</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>condemn</td>
			<td>0.5701</td>
			<td>1</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>sentence</td>
			<td>0.5591</td>
			<td>2</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>pass sentence</td>
			<td>0.5417</td>
			<td>1</td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td></td>
			<td>conviction</td>
			<td>0.5352</td>
			<td>3</td>
		</tr>
	</tbody>
</table>

**Groupe 4**
<table>
	<thead>
		<tr>
			<th colspan="3" style="text-align: center;">Méthode 1</th>
			<th colspan="3" style="text-align: center;">Méthode 2</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
			<th>Synonyme</th>
			<th>Score</th>
			<th>Occurrences</th>
		</tr>
		<tr>
			<td>smaragd</td>
			<td>0.7336</td>
			<td>2</td>
			<td>smaragd</td>
			<td>0.8328</td>
			<td>2</td>
		</tr>
		<tr>
			<td>minionette</td>
			<td>0.7200</td>
			<td>2</td>
			<td>minionette</td>
			<td>0.7985</td>
			<td>2</td>
		</tr>
		<tr>
			<td>chromatic</td>
			<td>0.6947</td>
			<td>2</td>
			<td>azure</td>
			<td>0.7662</td>
			<td>1</td>
		</tr>
		<tr>
			<td>azure</td>
			<td>0.6637</td>
			<td>1</td>
			<td>agate</td>
			<td>0.7341</td>
			<td>3</td>
		</tr>
		<tr>
			<td>ruddy</td>
			<td>0.6277</td>
			<td>1</td>
			<td>chromatic</td>
			<td>0.7321</td>
			<td>2</td>
		</tr>
		<tr>
			<td>agate</td>
			<td>0.6240</td>
			<td>3</td>
			<td>ruddy</td>
			<td>0.7072</td>
			<td>1</td>
		</tr>
		<tr>
			<td>crimson</td>
			<td>0.6023</td>
			<td>1</td>
			<td>crimson</td>
			<td>0.6362</td>
			<td>1</td>
		</tr>
		<tr>
			<td>carmine</td>
			<td>0.5153</td>
			<td>1</td>
			<td>rubi</td>
			<td>0.6085</td>
			<td>2</td>
		</tr>
		<tr>
			<td>rubi</td>
			<td>0.5029</td>
			<td>2</td>
			<td>carmine</td>
			<td>0.5928</td>
			<td>1</td>
		</tr>
	</tbody>
</table>

On voit rapidement que la méthode 2 a tendance à attribuer des scores plus élevés aux synonymes, ce qui n'est pas grave: on peut simplement augmenter le seuil minimal requis pour qu'un synonyme soit retenu (lors des tests, tous les synonymes avec un score supérieur à 0.5 étaient retenus). On remarque aussi que les scores fournis par la méthode 2 sont globalement meilleurs. Nous avons donc choisi d'utiliser cette méthode.

## Problèmes

Malheureusement, après avoir fait plus de tests, la qualité des synonymes laissait à désirer, principalement parce que les API ne renvoyaient pas des synonymes de qualité en premier lieu, problème que le filtrage ne suffisait pas à résoudre. La dépendance à des API est aussi problématique car elle nécessite une connexion internet et suppose que les API soient fonctionnelles. Nous avons donc décidé de changer de méthode, comme présenté dans la partie suivante.