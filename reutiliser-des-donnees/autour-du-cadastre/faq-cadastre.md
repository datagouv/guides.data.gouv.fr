# Foire aux questions - Cadastre (FAQ)

> Si vous avez une autre question sur le cadastre ou sur l'utilisation des données ouvertes du plan cadastral, [**n'hésitez pas à nous l'indiquer ici**](https://tally.so/r/wgdoJl). Nous vous répondrons à travers ce guide et cette foire aux questions.

<details>

<summary>Comment rechercher/connaître un propriétaire ?</summary>

Nous ne disposons pas d'informations sur les propriétaires actuels ou anciens. De ce fait, nous ne pouvons pas les communiquer. Il vous est possible de demander ces informations.
1. Si vous êtes une collectivité, vous pouvez [vous adresser au Service de Publicité Foncière (SPF) dont dépend votre collectivité](http://www2.impots.gouv.fr/contacts/spf/index.htm).
2. Si vous êtes un particulier :
   - Si vous souhaitez connaître le propriétaire d'un bien, vous pouvez obtenir cette information en demandant un extrait de propriété (payant). Les démarches sont indiquées [ici](https://www.service-public.fr/particuliers/vosdroits/F17759).
   - Si vous êtes propriétaire et que vous cherchez certaines informations relatives à votre bien, que vous devez demander des modifications ou chercher des informations sur la mitoyenneté sur le plan ou un droit de passage, il est recommandé de [vous adresser aux impôts en passant par votre espace sécurisé](https://impots.gouv.fr). 

</details>

<details>

<summary>Le fichier du cadastre téléchargé ne correspond pas à ma commune, comment faire ?</summary>

Vous avez peut-être confondu code INSEE et code postal, dans le cadre de votre recherche. Le code INSEE est unique, alors que le code postal correspond à une ou plusieurs communes. Pour retrouver plus facilement ce code INSEE, passez plutôt par "l'aide au téléchargement"  pour [les données PCI (*Edigeo* ou *DXF*)](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise) ou [celle des données Cadastre Etalab (*GeoJSON*/*SHP*)](https://cadastre.data.gouv.fr/datasets/cadastre-etalab) selon le format de fichier souhaité. 

</details>

<details>

<summary>Comment remonter une erreur dans les données de valeurs foncières ?</summary>

Nous vous invitons à lire [la partie Questions fréquentes à ce propos](https://app.dvf.etalab.gouv.fr/faq.html). Si l'information vous paraît toujours erronnée, veuillez contacter le bureau GF-3B de la DGFiP à l'adresse suivante : <a href="mailto:bureau.gf3b-dvf@dgfip.finances.gouv.fr">bureau.gf3b-dvf@dgfip.finances.gouv.fr</a>.

</details>

<details>

<summary>Comment faire retirer les informations de vente dans les données de valeurs foncières ?</summary>

Nous vous invitons à lire la partie [Cadre réglementaire de la publication de ces informations](https://app.dvf.etalab.gouv.fr/faq.html).

</details>

<details>

<summary>Comment s'informer sur la mitoyenneté ?</summary>

Nous vous invitons à consulter [cette page](https://www.service-public.fr/particuliers/vosdroits/F2415). Vous pouvez également consulter le plan avec figuré sur [cadastre.gouv.fr](https://www.cadastre.gouv.fr/). La [page de légende du cadastre](https://www.cadastre.gouv.fr/scpc/pdf/legendes/FR_fr/Legende%20du%20plan%20sur%20internet.pdf#page=3) vous permet de comprendre les figurés liés à la mitoyenneté. Il vous est possible d'avoir plus d'informations si vous êtes propriétaire en vous rapprochant des services concernés en passant par votre espace sécurisé sur [impots.gouv.fr](https://impots.gouv.fr).


</details>

<details>

<summary>J'ai un décalage entre les parcelles cadastrales et des photos aériennes et/ou je constate des chevauchements entre des parcelles,  pourquoi ?</summary>

Contrairement à une croyance commune, **le contour des parcelles n'est pas fiable** : il ne s'agit que d'une représentation graphique imprécise, établie avant que les photos aériennes soient généralisées et de grande précision. **Seuls les actes de vente ont une valeur juridique.**

Il faut aussi noter que les parcelles aux limites entre communes se recoupent ou donnent un "no man land" car historiquement, chaque commune gérait séparément ses parcelles et aucune ne se préoccupait de la limite exacte avec les communes limitrophes de son territoire.

Pour évaluer ce décalage entre les contours des parcelles et le terrain, il est possible d'utiliser la couche "**Décalage de la representation cadastrale**" `CADASTRALPARCELS.HEATMAP` disponible sur [le WMS](https://data.geopf.fr/wms-r/wms) et aussi consultable sur [le Géoportail](https://www.geoportail.gouv.fr/carte?c=-1.0309918634157356,46.551302493795134\&z=6\&l0=ORTHOIMAGERY.ORTHOPHOTOS::GEOPORTAIL:OGC:WMTS\(1\)\&l1=GEOGRAPHICALGRIDSYSTEMS.PLANIGNV2::GEOPORTAIL:OGC:WMTS\(1\)\&l2=CADASTRALPARCELS.HEATMAP::GEOPORTAIL:OGC:WMTS\(0.9\)\&l3=CADASTRALPARCELS.PARCELLAIRE\_EXPRESS::GEOPORTAIL:OGC:WMTS\(1\)\&permalink=yes). Cette couche couvre une grande partie du territoire, mais pas son ensemble.
{% endhint %}

<figure><img src="../../.gitbook/assets/exemple-decalage-parcellaire.png" alt=""><figcaption><p>Un exemple de décalage de parcelles avec différents niveaux de précision</p></figcaption></figure>

</details>

<details>

<summary>Comment rechercher des parcelles anciennes ?</summary>

Pour rechercher des parcelles anciennes, plusieurs solutions se présentent à vous :
- Si vous ne recherchez pas la représentation graphique, vous pouvez consulter [les documents de filiation informatisés (DFI)](https://www.data.gouv.fr/fr/datasets/documents-de-filiation-informatises-dfi-des-parcelles/) qui précisent la parenté ;
- Si les parcelles anciennes que vous recherchez ne figurent pas dans les DFI, nous vous invitons à consulter les remembrements aux archives départementales, ou à contacter le Service de publicité foncière (sans garantie).

Pour retrouver les contours du cadastre de l'époque, vous pouvez vous adresser :
- à la mairie ;
- au Service de publicité foncière, dans les annexes graphiques des actes notariaux.

</details>

<details>

<summary>Comment rechercher des photographies aériennes ?</summary>

Pour rechercher des photographies aériennes, deux options s'offrent à vous :
- [l'outil remonter le temps](https://remonterletemps.ign.fr/) "version facile", en choisissant "cartes" ;
- [l'outil remonter le temps](https://remonterletemps.ign.fr/), en cherchant les clichés. La position exacte et l'orientation ne sont pas toujours satisfaisants car il s'agit de clichés bruts et non calés : ce ne sont pas des ortho-photographies. L'investissement technique peut être élevé. 

</details>

<details>

<summary>Certaines parcelles ne sont pas présentes, pourquoi ?</summary>

A la manière d'un traducteur, le parseur utilisé n'interprète pas toujours parfaitement les points indiqués dans les données pour décrire les contours des parcelles : des erreurs peuvent donc se glisser.

</details>
