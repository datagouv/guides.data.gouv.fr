# FAQ

## Comment faire si une recherche d’adresse ne fonctionne pas ? <a href="#comment-faire-si-une-recherche-d-adresse-ne-fonctionne-pas" id="comment-faire-si-une-recherche-d-adresse-ne-fonctionne-pas"></a>

* Vérifier en utilisant l’[autocomplétion](https://adresse.data.gouv.fr/base-adresse-nationale#4.4/46.9/1.7) :
  * Tapez votre adresse. Par exemple, "20 avenue de Ségur". Si le numéro est bien proposé et que la commune est la bonne pour le premier résultat, c’est la manière dont vous avez récupéré l’adresse qui est en cause. Si vous êtes en mode "batch", la première adresse retournée peut être mauvaise et c’est la 2ème ou 3ème adresse que vous attendiez.
  * Imaginons que vous pensiez que le numéro existe, mais ne le trouvez pas dans votre résultat de géocodage. Essayez alors de trouver la rue. Essayons "87 avenue de Ségur". On ne voit que des rues qui sont retournées suite à la recherche. Cliquez sur la rue qui semble correspondre à votre recherche. Cela va zoomer. Vous allez pouvoir voir s’il y a des adresses et lesquelles sont inventoriées.
* La donnée de référence n’est pas présente : c’est un oubli ou personne ne l’a encore produite.&#x20;
* Le résultat est une adresse BAL. Votre commune est entrée dans une démarche de recensement et valorisation de ces adresses.&#x20;
  * Vous pouvez confirmer si l'adresse existe en allant sur [https://adresse.data.gouv.fr/deploiement-bal](https://adresse.data.gouv.fr/deploiement-bal).&#x20;
    * Zoomez sur la carte pour trouver votre commune ou l'organisme qui porte votre BAL, par exemple un intercommunalité.&#x20;
    * Cliquez sur le polygone. Allons par exemple à [la communauté d'agglomération Arles Crau Camargue Montagnette](https://adresse.data.gouv.fr/bases-locales/jeux-de-donnees/601402f5818a575b16081fe3).&#x20;
    * Descendons et recherchons une commune puis cliquons dessus, par exemple [Arles](https://adresse.data.gouv.fr/base-adresse-nationale/13004).&#x20;
    * On peut maintenant chercher par nom de voie ou lieu dit pour vérifier que la voie existe. Prenons [l'allée des Manades](https://adresse.data.gouv.fr/base-adresse-nationale/13004\_2865#15.05/43.66235/4.6205).&#x20;
    * Nous pouvons ensuite vérifier dans la liste l'existence du numéro.
* Adresse IGN vs adresse cadastre vs adresse BAL.&#x20;
* La donnée est présente, mais les termes de recherche ne permettent pas de la trouver.&#x20;

{% hint style="success" %}
Vous êtes un particulier ? Vous pouvez récupérer les coordonnées de votre commune pour lui faire part de vos retours en passant par [https://adresse.data.gouv.fr/contribuer](https://adresse.data.gouv.fr/contribuer) puis en cherchant votre commune.
{% endhint %}

## Que faire lorsqu'on est un gros consommateur de l’API [api-adresse.data.gouv.fr](http://api-adresse.data.gouv.fr/) ? <a href="#gros-consommateurs-de-l-api-api-adresse-data-gouv-fr" id="gros-consommateurs-de-l-api-api-adresse-data-gouv-fr"></a>

Si vous êtes un organisme public, vous pouvez faire une demande pour augmenter les quotas par défaut sur l’API publique [api-adresse.data.gouv.fr](http://api-adresse.data.gouv.fr/).&#x20;

Si ce n’est pas le cas, vous pouvez vous autohéberger.&#x20;

* Dans ce cas, le plus simple est de passer par l’utilisation de Docker : [https://github.com/etalab/addok-docker#readme](https://github.com/etalab/addok-docker#readme).&#x20;
* Il est possible aussi de regarder du côté de Addok, le logiciel open source derrière l’API Adresse si vous avez des besoins plus spécifiques au niveau de votre installation ou de la personnalisation de la recherche : [https://github.com/addok/addok](https://github.com/addok/addok).&#x20;
