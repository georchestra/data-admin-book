# Vérifier/valider la cohérence des données et des métadonnées - sdi-consistence-check

Cet outil n'est pas inclu dans GeoNetwork, mais nécéssite une installation àcôté. Il destiné a générer des rapports mesurant le degré de cohérence entre les données et les métadonnées d’une infrastructure de données spatiales, qu’elle soit basée sur geOrchestra ou non. L'objectif de faciliter la gestion de la qualité de diffusion de la donnée, en fournissant un rapport de conformité entre les données présentes sur la base de données \(services WMS, WFS\) et les métadonnées du catalogue \(service CSW\).

[https://github.com/georchestra/sdi-consistence-check](https://github.com/georchestra/sdi-consistence-check) \(licence GPL v3\)

3 types de rapports sont disponibles via une url consultable par un navigateur web :

* via le flux WMS : verifie dans le flux getCapabilities du WMS l'association aux metadonnées 
* via le flux WFS : de même que le WMS mais pour le WFS 
* via le flux CSW : vérifie la disponibilitée d'un service WMS ou WFS pour chaque métadonnée présente dans le CSW. 



Pour chaque couche son niveau de conformité : “ok” si la donnée et la métadonnée sont bien conformes, ou un message d'erreur détaillé dans le cas contraire.

```
#4  
  Layer: georhena:Centres_Zentren_Planif_Planung_2016
  Error: No metadata defined for layer georhena:Centres_Zentren_Planif_Planung_2016

#5
  Layer: georhena:ChefsLieux_Hauptorte OK
```

Cette application vérifie \(pour le WMS et le WFS\) du côté de la base de données si la donnée a une métadonnée associée et si celle-ci est accessible. Pour le CSW du catalogue, l’application vérifie qu’une donnée a été associée dans la fiche de métadonnées.

Les rapports sont effectués sur la base des flux CSW, WFS et WMS de la plateforme, et sont actualisés toutes les heures.

cf. mettre lien vers 

