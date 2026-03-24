---
description: Liste des transformations opérées sur nos indicateurs
---

# Transformations

### Cogification au dernier millésime

Grâce aux [tables de références](https://app.gitbook.com/o/w6D6SnLwCXQaMMSzcTvp/s/K56ETHxhBea8DHmbPCgt/~/changes/3/ecologie.data.gouv.fr/indicateurs/publier-un-indicateur/methodes-de-traitements-des-indicateurs/tables-de-references) nous passons tous nos indicateurs au dernier millésime publié par l'INSEE, actuellement le millésime est 2025.

Nous enrichissons aussi tous nos indicateurs à l'ensemble des mailles géographique disponibles.

Nous excluons l'historique des communes ayant connu une scission de nos indicateurs car nous ne pouvons pas attribuer la valeur de l'indicateur aux communes résultantes les données.&#x20;

### Passage aux mailles supérieures

#### Données à la maille communale

Lorsque la donnée source d'un indicateur est disponible à la maille communale, nous faisons l'enrichissement et les agrégations nécessaires pour mettre à disposition l'indicateur aux mailles supérieures: epci, départementales, régionales

#### Données à la maille EPCI uniquement

Lorsque la donnée source d'un indicateur n'est disponible qu'à la maille EPCI, nous ne pouvons partager que les données à cette maille géographique.

Cela est dû au fait qu'il existe des EPCIs qui appartiennent à plusieurs départements et à plusieurs régions. Nous ne pouvons donc pas passer à partir de données disponibles à la maille EPCI à des mailles supérieures.

#### Données aux maille EPCI et Departementales

Lorsque la données existe dans plusieurs sources à la maille EPCI et départementale, nous mettons à dispotion l'indicateur aux mailles rendues disponibles par ces sources.&#x20;

La maille départementale permet de passer ainsi à la maille régionale.
