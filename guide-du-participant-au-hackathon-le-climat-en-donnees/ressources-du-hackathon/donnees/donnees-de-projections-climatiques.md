---
cover: ../../../.gitbook/assets/Rectangle.png
coverY: 0
---

# Données de projections climatiques

Pour vos projets, Météo-France met à votre disposition de nouvelles données de projections climatiques.

## SOCLE Métropole (France hexagonale et Corse)

### Accès aux données

Les données sont disponibles ici ⤵️

{% embed url="https://www.data.gouv.fr/datasets/projections-climatiques-pour-le-hackathon-2025-socle-metropole" %}

### Description des données

Un seul type de données :&#x20;

* Variables descendues en échelle et ajustées statistiquement = sortie des simulations réalisées avec des  méthodes de descente d’échelle (RCM, CPRCM ou EMULATEUR) plus un ajustement statistique par rapport à des jeux de données climatiques de référence (REF ou parfois aussi appelé REAanalyse), via la méthode CDFt (Michelangeli et al. 2009, [https://github.com/yrobink/SBCK](https://github.com/yrobink/SBCK)).

{% hint style="danger" %}
**Avertissement : Ces données sont encore en cours d’évaluation et de validation, à la fois par les équipes de modélisation européennes et par celles de Météo-France. Des erreurs peuvent subsister, et l’un des objectifs du hackathon est justement de les identifier.**
{% endhint %}

<table><thead><tr><th width="119.1927490234375">Nom court </th><th width="246.578125">Nom long</th><th width="98.3802490234375">Unités</th><th>Commentaires</th></tr></thead><tbody><tr><td>tas</td><td>Température moyenne de l’atmosphère à 2 mètres</td><td>K</td><td>Cette variable est reconstruite comme la demi-somme de tasmin et tasmax après correction sauf pour l’Emulateur où tas est une variable produite par cette approche</td></tr><tr><td>tasmin</td><td>Température minimale de l’atmosphère à 2 mètres</td><td>K</td><td>Idem que tas mais pour le minimum de la journée. Ce minimum est calculé au pas de temps du modèle</td></tr><tr><td>tasmax</td><td>Température maximale de l’atmosphère à 2 mètres</td><td>K</td><td>Idem que tas mais pour le maximum de la journée. Ce maximum est calculé au pas de temps du modèle</td></tr><tr><td>pr</td><td>Précipitation moyenne</td><td>kg/m2/s</td><td>Cette variable est issue d’un cumul des précipitations sur 1 heure pour la fréquence horaire et sur 1 jour pour la fréquence quotidienne. Cette variable inclut pluie et neige</td></tr><tr><td>rsds</td><td>Rayonnement solaire incident (descendant) en surface</td><td>W/m2</td><td>Cette variable est issue d’un cumul sur la journée. Elle inclut le rayonnement direct et le rayonnement diffus</td></tr><tr><td>rlds</td><td>Rayonnement infrarouge incident (descendant) en surface</td><td>W/m2</td><td>Cette variable est issue d’un cumul sur la journée.</td></tr><tr><td>huss</td><td>Humidité spécifique moyenne de l’atmosphère à 2 mètres</td><td>sans unité (kg/kg)</td><td>Cette variable est un diagnostic du modèle reconstruit à partir d’autres variables dont l’humidité du niveau le plus bas du modèle et la stabilité de l’atmosphère. C’est une variable instantanée à la fréquence horaire et une moyenne des 24 données horaires pour la fréquence quotidienne</td></tr><tr><td>sfcWind</td><td>Vitesse du vent moyen à 10 mètres</td><td>m/s</td><td>Cette variable est reconstruite à partir des diagnostics quotidiens de vent de surface zonal (uas) et méridional (vas) avant correction</td></tr></tbody></table>

#### **1. Données quotidiennes à 8 km de résolution**

* **Données issues de modèles régionaux de climat ou Regional Climate Model (RCM)**

<table><thead><tr><th width="406.41668701171875">Description</th><th width="145.3228759765625">Période couverte</th><th width="107.895751953125">Période de calibration pour l’ajustement statistique</th><th width="105.630126953125">Résolution spatiale</th><th width="99.052001953125">Résolution temporelle</th><th width="171.864501953125">Nombre de variables</th><th>Nombre de simulations</th></tr></thead><tbody><tr><td><p>Projections climatiques régionales issues de l’ensemble EURO-CORDEX, basées sur 4 modèles régionaux (RCM) à ~ 12 km de résolution, forcés par différents modèles globaux (GCM) CMIP6. <br></p><p>Les données finales sont à 8 km de résolution, après ajustement statistique par rapport à la référence ANASTASIA-SAFRAN pour les températures et SAFRAN pour les autres variables.</p></td><td><p></p><ul><li>historique : 1950-2014</li><li>scénarios : 2015-2100</li></ul></td><td>1985-2014</td><td>8 km</td><td>1 jour</td><td>8 (tas, tasmin, tasmax, pr, rsds, rlds, huss, sfcWind)</td><td>17 historiques, 17 ssp370, 4 ssp585</td></tr></tbody></table>

\[RCM / GCM : nombre de réalisations (ou membres) par scénario]

* CNRM-ALADIN64E1 / CNRM-ESM2-1 : 3 historiques (membres r1, r14, r15), 3 ssp370 (membre r1, r14, r15), 1 ssp585
* CNRM-ALADIN64E1 / NorESM2-MM : 1 historique, 1 ssp370, 1 ssp585
* CNRM-ALADIN64E1 / CMCC-CM2-SR5 : 1 historique, 1 ssp370
* HCLIM43-ALADIN / IPSL-CM6A-LR : 1 historique, 1 ssp370
* HCLIM43-ALADIN / NorESM2-MM : 1 historique, 1 ssp370
* HCLIM43-ALADIN / CNRM-ESM2-1 : 1 historique, 1 ssp370
* HCLIM43-ALADIN / MIROC6 : 1 historique, 1 ssp370
* HCLIM43-ALADIN / EC-Earth3-Veg : 1 historique, 1 ssp370
* HCLIM43-ALADIN / MPI-ESM1-2-HR : 1 historique, 1 ssp370
* ICON-CLM-202407-1-1 / MPI-ESM1-2-HR : 1 historique, 1 ssp370
* RACMO23E / CNRM-ESM2-1 : 1 historique, 1 ssp370
* RACMO23E / EC-Earth3 : 1 historique, 1 ssp370, 1 ssp585
* RACMO23E / EC-Earth3-Veg : 1 historique, 1 ssp370, 1 ssp585
* RACMO23E / MPI-ESM1-2-HR : 1 historique, 1 ssp370
* RACMO23E / NorESM2-MM : 1 historique, 1 ssp370

***

* **Données issues d’un modèle régional de climat kilométrique, ou Convection-Permitting Regional Climate Model (CPRCM)**

<table><thead><tr><th width="380.2344970703125">Description</th><th width="161.2864990234375">Période couverte</th><th width="271.09375">Période de calibration pour l’ajustement statistique</th><th width="174.6510009765625">Résolution spatiale</th><th width="192.416748046875">Résolution temporelle</th><th width="192.6666259765625">Nombre de variables</th><th width="200.2137451171875">Nombre de simulations</th><th>[CPRCM / GCM : nombre de réalisations (ou membres) par scénario]</th></tr></thead><tbody><tr><td><p>Projection climatique régionale issue du modèle kilométrique à convection résolue (CPRCM) CNRM-AROME46t1 à 2,5 km de résolution, forcé par la simulation CNRM-ALADIN64E1 / CNRM-ESM2-1.<br></p><p>Cette simulation est distribuée pour deux grilles différentes et à deux fréquences temporelles différentes (cf. section 2 et 3)<br></p><p>Données à 8 km de résolution, après ajustement statistique par rapport à la référence ANASTASIA-SAFRAN pour les températures et SAFRAN pour les autres variables.</p></td><td><p></p><ul><li>historique : 1990-2014</li><li>scénarios : 2015-2100</li></ul></td><td>1991-2020</td><td>8 km</td><td>1 jour</td><td>8 (tas, tasmin, tasmax, pr, rsds, rlds, huss, sfcWind)</td><td>1 historique, 1 ssp370</td><td>CNRM-AROME46t1 / CNRM-ESM2-1 : 1 historique, 1 ssp370</td></tr></tbody></table>

* **Données issues d’un émulateur de modèle régional de climat à base IA (EMULATEUR)**

<table><thead><tr><th width="398.1876220703125">Description</th><th width="156.484375">Période couverte</th><th width="117.21875">Période de calibration pour l’ajustement statistique</th><th width="98.9114990234375">Résolution spatiale</th><th width="93.697998046875">Résolution temporelle</th><th width="123.3853759765625">Nombre de variables</th><th width="119.177001953125">Nombre de simulations</th><th>[EMUL / GCM : nombre de réalisations (ou membres) par scénario]</th></tr></thead><tbody><tr><td><p>Projections climatiques régionales obtenues par descente d’échelle d’un ensemble de 10 simulations (10 membres) du GCM MPI-ESM1-2-LR (CMIP6), à partir d’un émulateur à base IA (CNRM-ALADIN63-emul-CNRM-UNET11-tP22). <br><br>L’émulateur est basé sur un réseau de neurones construit pour reproduire la fonction de descente d’échelle du RCM CNRM-ALADIN63 (12 km) appartenant à la  génération EURo-CORDEX-CMIP5.<br></p><p>Les données finales sont à 8 km de résolution, après ajustement statistique par rapport à la référence ANASTASIA-SAFRAN pour les températures et la référence SAFRAN pour les autres variables. </p></td><td><p></p><ul><li>historique : 1850-2014</li><li>scénarios : 2015-2100</li></ul></td><td>1985-2014</td><td>8 km</td><td>1 jour</td><td>2 - température moyenne (tas, pr)</td><td></td><td>CNRM-ALADIN63-emul-CNRM-UNET11-tP22 / MPI-ESM1-2-LR : 10 historiques, 10 ssp126, 10 ssp245, 10 ssp370, 10 ssp585</td></tr></tbody></table>

#### **2. Données de température quotidiennes à 3 km de résolution**

* **Données issues d’un modèle régional kilométrique (CPRCM)**

<table><thead><tr><th width="399.46881103515625">Description</th><th width="160.09375">Période couverte</th><th>Période de calibration pour l’ajustement statistique</th><th width="114.473876953125">Résolution spatiale</th><th width="98.1771240234375">Résolution temporelle</th><th width="154.203125">Nombre de variables</th><th>Nombre de simulations</th><th>[CPRCM / GCM : nombre de réalisations (ou membres) par scénario]</th></tr></thead><tbody><tr><td><p>Projection climatique régionale issue du modèle kilométrique à convection résolue (CPRCM) CNRM-AROME46t1 à 2,5 km de résolution, forcé par la simulation CNRM-ALADIN64E1 / CNRM-ESM2-1.<br><br></p><p>Les données finales sont à 2,5 km de résolution, après ajustement statistique par rapport à la référence ANASTASIA interpolée sur la grille du modèle CNRM-AROME46t1.</p></td><td><p></p><ul><li>historique : 1990-2014</li><li>scénarios : 2015-2100</li></ul></td><td>1991-2100</td><td>2,5 km</td><td>1 jour</td><td>3 (tas, tasmin, tasmax)</td><td></td><td>CNRM-AROME46t1 / CNRM-ESM2-1 : 1 historique, 1 ssp370</td></tr></tbody></table>

#### **3. Données de précipitations horaires à 3 km de résolution**

* **Données issues d’un modèle régional kilométrique (CPRCM)**

<table><thead><tr><th width="403.33856201171875">Description</th><th width="152.3958740234375">Période couverte</th><th>Période de calibration pour l’ajustement statistique</th><th>Résolution spatiale</th><th>Résolution temporelle</th><th>Nombre de variables</th><th>Nombre de simulations</th><th>[CPRCM / GCM : nombre de réalisations (ou membres) par scénario]</th></tr></thead><tbody><tr><td><p>Projection climatique régionale issue du modèle kilométrique à convection résolue (CPRCM) CNRM-AROME46t1 à 2,5 km de résolution, forcé par la simulation CNRM-ALADIN64E1 / CNRM-ESM2-1.<br></p><p>Les données finales sont à 2,5 km de résolution, après ajustement statistique par rapport à la référence COMEPHORE interpolée sur la grille du modèle CNRM-AROME46t1.</p></td><td><p></p><ul><li>historique : 1990-2014</li><li>scénarios : 2015-2100</li></ul></td><td>1997-2020</td><td>2,5 km</td><td>1 heure</td><td>1 (pr)</td><td></td><td><ul><li>CNRM-AROME46t1 / CNRM-ESM2-1 : 1 historique, 1 ssp370</li></ul></td></tr></tbody></table>

### Liste des simulations

{% hint style="info" %}
ALL = tas, tasmax, tasmin
{% endhint %}

<table><thead><tr><th width="116.4375">variable</th><th>domain</th><th>gcm</th><th>experiment</th><th>member</th><th>institute</th><th>rcm</th><th>version</th><th>timestep</th><th>date_beg</th><th>date_end</th><th>données brutes sur socle</th><th>données corrigées</th></tr></thead><tbody><tr><td>ALL</td><td>EUR-12</td><td>CMCC-CM2-SR5</td><td>historical</td><td>r1i1p1f1</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>historical</td><td>r14i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>historical</td><td>r15i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>historical</td><td>r1i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>historical</td><td>r1i1p1f1</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>IPSL-CM6A-LR</td><td>historical</td><td>r1i1p1f1</td><td>HCLIMcom-DMI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>historical</td><td>r1i1p1f1</td><td>HCLIMcom-METNo</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>historical</td><td>r1i1p1f2</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3-Veg</td><td>historical</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MIROC6</td><td>historical</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>historical</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>historical</td><td>r1i1p1f1</td><td>CLMcom-DWD</td><td>ICON-CLM-202407-1-1</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>historical</td><td>r1i1p1f2</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3</td><td>historical</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3-Veg</td><td>historical</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>historical</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>historical</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>19500101</td><td>20141231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CMCC-CM2-SR5</td><td>ssp370</td><td>r1i1p1f1</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp370</td><td>r14i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp370</td><td>r15i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp370</td><td>r1i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp585</td><td>r1i1p1f2</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>ssp370</td><td>r1i1p1f1</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>ssp585</td><td>r1i1p1f1</td><td>CNRM-MF</td><td>CNRM-ALADIN64E1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>IPSL-CM6A-LR</td><td>ssp370</td><td>r1i1p1f1</td><td>HCLIMcom-DMI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>ssp370</td><td>r1i1p1f1</td><td>HCLIMcom-METNo</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp370</td><td>r1i1p1f2</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3-Veg</td><td>ssp370</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MIROC6</td><td>ssp370</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>ssp370</td><td>r1i1p1f1</td><td>HCLIMcom-SMHI</td><td>HCLIM43-ALADIN</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>ssp370</td><td>r1i1p1f1</td><td>CLMcom-DWD</td><td>ICON-CLM-202407-1-1</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>CNRM-ESM2-1</td><td>ssp370</td><td>r1i1p1f2</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3</td><td>ssp370</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3</td><td>ssp585</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3-Veg</td><td>ssp370</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>EC-Earth3-Veg</td><td>ssp585</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>MPI-ESM1-2-HR</td><td>ssp370</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr><tr><td>ALL</td><td>EUR-12</td><td>NorESM2-MM</td><td>ssp370</td><td>r1i1p1f1</td><td>KNMI</td><td>RACMO23E</td><td>v1-r1</td><td>day</td><td>20150101</td><td>21001231</td><td>✅</td><td>✅</td></tr></tbody></table>

## SOCLE Outre-Mer

### Accès aux données

Les données sont disponibles ici ⤵️

{% embed url="https://www.data.gouv.fr/datasets/projections-climatiques-pour-le-hackathon-2025-socle-outre-mer" %}

### Description des données

Deux types de données :

* **Variables corrigées** = sortie de modèles climatiques + ajustement statistique par rapport aux observations

Caractéristiques des variables corrigées (idem pour tous les territoires)

Nombre de variables : 4&#x20;

* température moyenne (tas)
* température minimale (tasmin)
* température maximale (tasmax)
* précipitations (pr)

Résolution spatiale : \~  3 km

Résolution temporelle : quotidienne

* **Indicateurs** = calculés à partir des variables corrigées, sur des fréquences temporelles mensuelles, saisonnières, annuelles et moyennés sur des périodes de 20 années pour les niveaux de réchauffement, et 30 années pour la référence (ex : nombre de jours de fortes chaleurs).

Liste d’indicateurs (idem pour tous les territoires) : [https://www.drias-climat.fr/accompagnement/sections/431](https://www.drias-climat.fr/accompagnement/sections/431)

{% hint style="warning" %}
Remarque : Ces données sont disponibles sur le portail Drias - les futurs du climat , accompagnées de la documentation décrivant leur contenu : la liste des modèles sélectionnés par territoire, les méthodes de correction de biais et les jeux de référence utilisés, ainsi que les périodes et scénarios disponibles : [https://www.drias-climat.fr/accompagnement/sections/305](https://www.drias-climat.fr/accompagnement/sections/305)
{% endhint %}

#### **1. Données sur La Réunion**

<table><thead><tr><th width="423.81256103515625">Description</th><th>Période couverte</th><th width="109.520751953125">Produit de référence pour l'ajustement statistique</th><th width="113.625">Période de calibration pour l’ajustement statistique</th><th width="108.9427490234375">Résolution spatiale</th><th width="148.0260009765625">Types de données disponibles</th><th>Nombre de modèles disponibles</th><th width="113.3228759765625">Nombre de simulations (membres) par modèle</th><th>Scénarios</th></tr></thead><tbody><tr><td><p>Projections climatiques issues de modèles globaux et d’un modèle régional.<br></p><p>Les données finales sont à ~ 3 km de résolution, après ajustement statistique par rapport aux observations de référence, via la méthode CDFt.</p></td><td>1981-2100</td><td>BRIO</td><td>1981-2014</td><td>0.03° (~ 3 km)</td><td><p></p><ul><li>variables corrigées </li><li>indicateurs</li></ul></td><td><p></p><ul><li>17 GCM</li><li>1 RCM</li></ul></td><td>1</td><td><p></p><ul><li>ssp126</li><li>ssp585</li></ul></td></tr></tbody></table>

Plus d’informations: [https://www.drias-climat.fr/accompagnement/sections/338](https://www.drias-climat.fr/accompagnement/sections/338)

#### 2. Données sur Mayotte

<table><thead><tr><th width="429.328125">Description</th><th width="119.4947509765625">Période couverte</th><th width="102.0416259765625">Produit de référence pour l'ajustement statistique</th><th>Période de calibration pour l’ajustement statistique </th><th>Résolution spatiale</th><th width="148.8021240234375">Types de données disponibles</th><th>Nombre de modèles</th><th>Nombre de simulations (membres) par modèle</th><th>Scénarios</th></tr></thead><tbody><tr><td><p>Projections climatiques issues de modèles globaux et régionaux.<br></p><p>Les données finales sont à ~ 3 km de résolution, après ajustement statistique par rapport aux observations de référence, via les méthodes CDFt pour les température et quantiles-quantiles pour les précipitations.</p></td><td>1989-2100</td><td>AROBS</td><td>1990-2024</td><td>0.03° (~ 3 km)</td><td><p></p><ul><li>variables corrigées </li><li>indicateurs</li></ul></td><td><p></p><ul><li>20 GCM</li><li>4 RCM</li></ul></td><td>1</td><td>ssp585 ou rcp85</td></tr></tbody></table>

Plus d’informations: [https://www.drias-climat.fr/accompagnement/sections/466](https://www.drias-climat.fr/accompagnement/sections/466)

#### 3. Données sur la Guyane

<table><thead><tr><th width="432.13543701171875">Description</th><th width="119.2864990234375">Période couverte</th><th width="96.421875">Produit de référence pour l'ajustement statistique</th><th width="108.088623046875">Période de calibration pour l’ajustement statistique</th><th width="139.9947509765625">Résolution spatiale</th><th width="138.432373046875">Types de données disponibles</th><th>Nombre de modèles</th><th>Nombre de simulations (membres) par modèle</th><th>Scénarios</th></tr></thead><tbody><tr><td><p>Projections climatiques issues de modèles globaux et régionaux.<br></p><p>Les données finales sont à ~ 3 km de résolution, après ajustement statistique par rapport aux observations de référence, via les méthodes CDFt pour les température et quantiles-quantiles pour les précipitations.</p></td><td>1989-2100</td><td>AROBS</td><td>1990-2024</td><td>0.03° (~ 3 km)</td><td><p></p><ul><li>variables corrigées </li><li>indicateurs</li></ul></td><td><p></p><ul><li>6 GCM</li><li>4 RCM</li></ul></td><td>1</td><td>ssp585 ou rcp85</td></tr></tbody></table>

Plus d’informations: [https://www.drias-climat.fr/accompagnement/sections/474](https://www.drias-climat.fr/accompagnement/sections/474)

#### 4. Données sur la Nouvelle-Calédonie

<table><thead><tr><th width="398.9375">Description</th><th>Période couverte</th><th width="82.661376953125">Produit de référence pour l'ajustement statistique</th><th width="110.145751953125">Période de calibration pour l’ajustement statistique</th><th width="147.7603759765625">Résolution spatiale</th><th>Type de données disponibles</th><th>Nombre de modèles </th><th width="79.479248046875">Nombre de simulations (membres) par modèle</th><th>Scénarios</th></tr></thead><tbody><tr><td><p>Projections climatiques issues de modèles globaux et régionaux.<br></p><p>Les données finales sont à ~ 3 km de résolution, après ajustement statistique par rapport aux observations de référence, via les méthodes CDFt pour les température et quantiles-quantiles pour les précipitations.</p></td><td>1989-2100</td><td>AROBS</td><td>1990-2024</td><td>0.03° (~ 3 km)</td><td>variables corrigées</td><td><p></p><ul><li>22 GCM</li><li>18 RCM</li></ul></td><td>1</td><td>ssp585 ou ssp370</td></tr></tbody></table>

Plus d’informations: [https://www.drias-climat.fr/accompagnement/sections/485](https://www.drias-climat.fr/accompagnement/sections/485)

### Vue d'ensemble des données

| Nom du jeu de données                                 | Domaine géographique | Résolution spatiale | Couverture temporelle                                             | Fréquence                   | Variables / indicateurs                  | Scénario        |
| ----------------------------------------------------- | -------------------- | ------------------- | ----------------------------------------------------------------- | --------------------------- | ---------------------------------------- | --------------- |
| La Réunion – Variables corrigées                      | La Réunion           | 0,03°               | 1981 - 2100                                                       | quotidienne                 | <p>tasmin<br>tasmax<br>tas<br>precip</p> | ssp585 / ssp126 |
| La Réunion - Indicateurs                              | La Réunion           | 0,03°               | Aux horizons de réchauffement de la TRACC (ref, +1.5, +2, +2.9)   | saisonnière, annuel         |                                          |                 |
| Mayotte – Variables corrigées                         | Mayotte              | 0.025°              | 1989 - 2100                                                       | quotidienne                 | <p>tasmin<br>tasmax<br>tas<br>precip</p> | ssp585 / rcp85  |
| Mayotte - Indicateurs                                 | Mayotte              | 0.025°              | Aux horizons de réchauffement de la TRACC (ref, +1.5, +2, +3)     | mensuel,saisonnière, annuel |                                          |                 |
| Guyane - variables corrigées                          | Guyane               | 0.025°              | 1989-2100                                                         | quotidienne                 | <p>tasmin<br>tasmax<br>tas<br>precip</p> | ssp585 / RCP85  |
| Guyane - Indicateurs                                  | Guyane               | 0.025°              | Aux horizons de réchauffement de la TRACC (ref, +1.7, +2.3, +3.5) | mensuel,saisonnière, annuel |                                          |                 |
| Nouvelle Calédonie - variables corrigées              | Nouvelle-Calédonie   | 0.025°              | 1989-2100                                                         | quotidienne                 | <p>tasmin<br>tasmax<br>tas<br>precip</p> | ssp370 / ssp585 |
| Produit de ref precipitations La Réunion              | Réunion              | 0,03°               | 1979-2024                                                         |                             |                                          |                 |
| Produit de ref température La Réunion                 | Réunion              | 0,03°               | 2000-2024                                                         |                             |                                          |                 |
| produit ref Mayotte précipitations                    | Mayotte              | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |
| produit ref Mayotte température (tas, tasmin, tasmax) | Mayotte              | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |
| produit ref Guyane précipitations                     | Guyane               | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |
| produit ref Guyane température (tas,tasmin,tasmax     | Guyane               | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |
| produit ref Nouvelle-Calédonie précipitations         | Nouvelle-Calédonie   | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |
| produit ref Nouvelle-Calédonie température            | Nouvelle-Calédonie   | 0.025°              | 1990-2024                                                         | quotidienne                 |                                          |                 |

## Autres

Vous avez également à votre disposition toutes les données disponibles sur :

* [meteo.data.gouv.fr](http://meteo.data.gouv.fr) ;
* [le portail DRIAS](https://www.drias-climat.fr/).

## Bibliographie

Besson, F., Dubuisson, B., Etchevers, P., Gibelin, A.-L., Lassegues, P., Schneider, M., and Vincendon, B., 2019. Climate monitoring and heat and cold waves detection over France using a new spatialization of daily temperature extremes from 1947 to present, Adv. Sci. Res., 16, 149–156, https://doi.org/10.5194/asr-16-149-2019.

Michelangeli, P.-A., Vrac, M., and Loukos, H., 2009. Probabilistic downscaling approaches: Application to wind cumulative distribution functions. Geophysical Research Letters, 36, L11708, doi:10.1029/2009GL038401

Vidal, J.-P., Martin, E.,  Franchisteguy, L., Baillon, M. and Soubeyroux, J.-M., 2010. ‘A 50-Year High-Resolution Atmospheric Reanalysis over France with the Safran System’. International Journal of Climatology 30 (11): 1627–44. https://doi.org/10.1002/joc.2003.

## Remerciements

Météo-France remercie l’ensemble des acteurs qui ont contribué à la production des données et l’organisation de ce hackathon :

* le comité scientifique des projets SOCLE-Métropole et SOCLE-Outremer, dont les échanges et recommandations ont inspiré l’organisation de ce hackathon,
* les centres de modélisation européens qui ont produit et mis à disposition les projections EURO-CORDEX, parfois avant leur publication officielle :
* les équipes du CNRM, de Météo-France, et de l’IRD  pour les simulations avec ALADIN, AROME et l’EMULATEUR sur les domaines Métropole et Outremer
* le Norwegian Meteorological Institute (MetNo), le Swedish Meteorological (SMHI) et le Danish Meteorological Institute (DMI) pour les simulations HCLIM43-ALADIN,
* le Deutscher Wetterdienst (DWD) pour les simulations ICON-CLM-202407-1-1,
* le Royal Netherlands Meteorological Institute (KNMI) pour les simulations RACMO23E
* le Jülich Center pour l’infrastructure de stockage ayant permis le partage des données.
* les équipes du LSCE (en particulier Y. Robin) qui développe le package d’ajustement statistique des données (XSBCK, CDF-t), dont le support a été déterminant.
* les projets IMPETUS4CHANGE, CLIPSSA, BRIO et TRACCS dont les financements ont permis en partie la production des simulations climatiques
* le projet TRACCS (M. Huot-Royer) pour son soutien essentiel à l’organisation du hackathon.
* les équipes de Météo-France impliquées dans les projets SOCLE-Métropole et SOCLE-Outremer, qui ont travaillé dans des délais très contraints pour respecter les échéances.

_Ce travail a bénéficié d’une aide de l’État gérée par l’Agence Nationale de la Recherche au titre de France 2030 portant les références ANR-22-EXTR-0011 ANR-22-EXTR-0004, ANR-22-EXTR-0003, ANR-22-EXTR-0002._

_Funded by the European Union through the HORIZON-EUROPE IMPETUS4CHANGE project. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union. Neither the European Union nor the granting authority can be held responsible for them._
