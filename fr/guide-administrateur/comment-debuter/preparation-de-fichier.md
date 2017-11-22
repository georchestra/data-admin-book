# Préparation des fichiers 



## FICHIER SHAPEFILES 

* un identifiant unique
* Avant de déposer vos données shapefile sur la pydio, quelques vérifications à faire :

Vérifier que la projection du fichier prj est prise en compte dans la déclaration des services WMS WFS etc ... \(de préférence : 2154, 3857\)

Vérifier que l'encodage du fichier dbf est bien en concordance avec les déclarations du namespace dans GS \(exemple UTF8 encodage international\)

Vérifier que la donnée que vous souhaitez publier n'existe pas à un échelon géographique supra

### Respecter les recommandations en matière de nommage des couches :

* Elles  ne devront pas contenir de caractères spéciaux, ni daccents, ni espaces.
* Le souligné « \_ » remplacera un espace dans le nom\_de\_la\_couche.
* Elles ne devront pas contenir de tiret « - ».
* Elles ne devront pas commencer par un chiffre \(ex: 2015\_nomdelacouche\)
* Dans le nom du fichier le millésime d'une donnée est à utiliser dans les cas d'une série de données historisée \(sinon lors d'une mise à jour le lien est cassé\).
* Eviter les noms des fichiers avec une écriture mixte majuscule-minuscule\).

### Recommandations dans le contenu des fichiers

Vérifier le format de date \(ne doit pas être un entier naturel\)

Le code INSEE ne doit pas être un entier naturel, doit être en caractère ou float

Classer les données par date \(un champ date par ligne\)

exemple :

Préférez cette structure :

|  | Date | Nombre |
| :--- | :--- | :--- |
| logements individuels | 01-01-1950 | 10 |
| logements collectifs | 01-01-1950 | 5 |
| logements collectifs | 01-01-1990 | 12 |
| logements individuels | 01-01-1990 | 6 |

```

```

Plutôt que celle-ci :

|  | 1950 | 1990 |
| :--- | :--- | :--- |
| logements individuels | 10 | 12 |
| logements collectifs | 5 | 6 |



Intérêt : On peut alors utilisé la temporalité sur Géoserver et créer des visualiseurs avec des curseurs temporels

--&gt; mettre un exemple

### liste des choses à ne pas faire

* pb de geometrie \(géométrie multiple, polygone fermé, ...\)
* absence d'attribut
* champs date qui n'en sont pas
* attribut contenant "%"
* données sans repère géographique
* attribut chiffré en format caractère
* copier-coller pdf \(pose problème avec dbf, ne reconnait pas l'encodage\)
* nom des attributs non explicite
* champ contenant uniquement des codes



## FICHIER POSTGRE

* pb géométrie
* projection
* dimension \(dim2, Dim3\)
* Indexation \(pas nécessaire de tout indexer\)
* pas d'espace
* un identifiant unique
* mettre en place tregger \(voir implications sur GS\)
* Se poser la question : vue faite dans postgre ou vue faite dans GS ?
* données volumineuses avec géométries complexes : pré-généralisation \(détailler les constantes\)
* wfs-t : publication sur GS de la table postgis \(sans passer par requête sql\) indispensable, sinon passer systématiquement par une vue
* éditer une liste des requêtes SQL efficace

### Avantages :

* avoir des données avec dimensions ou données temporelles

* possibilité de créer des visualiseurs temporels

* gestion graphiques facilitée \(cf. hydro\)

## FICHIERS RASTER

## 

## FICHIERS RASTER MOSAIQUE

## FICHIERS RASTER PYRAMIDE

## FICHIERS kml



