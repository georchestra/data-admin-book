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
* mettre en place trigger \(voir implications sur GS\)
* Se poser la question : vue faite dans postgre ou vue faite dans GS ?
* données volumineuses avec géométries complexes : pré-généralisation \(détailler les constantes\)
* wfs-t : publication sur GS de la table postgis \(sans passer par requête sql\) indispensable, sinon passer systématiquement par une vue
* éditer une liste des requêtes SQL efficace

### Avantages :

* avoir des données avec dimensions ou données temporelles

* possibilité de créer des visualiseurs temporels

* gestion graphiques facilitée \(cf. hydro\)

## FICHIERS RASTER

La préparation de données Raster est fonction de compromis entre espace disque disponible, des outils à disposition et des attentes du public ciblé \(performance et qualité de rendu\).

Une donnée livrée est rarement directement prête pour être servie de manière optimisée en flux pour trois raisons :

* Les volumétries des données brutes peuvent se révélées très importantes et les espaces disques serveurs onéreux

* Les zones de bordure peuvent nécessiter une préparation particulière pour un affichage propre \(canal alpha de transparence, footprint, nodata ou sld\)

* Modifier des paramètres avancés tels que le tuilage interne \(inner tiling\), les aperçus \(overview\) ou la taille des dalles \(merge\) influence les temps de réponse.

Il va donc falloir faire des choix par rapport à la compression \(DEFLATE, JPEG, LZW...\) au rééchantillonnage \(bilinear, lanczos, bicubique...\) à la taille des mailles, aux overviiews et au format de sortie \(TIFF, JP2 ...\).

#### Quelle compression?

La première question à se poser est "est-ce que je peux me permettre une compression avec perte ou pas ?".

Ensuite, certaines compressions sont efficaces sur certains types d'images et pas pour d'autres. Le choix de la compression doit donc se faire en prenant en compte les caractéristiques des images, les contraintes techniques et le besoin.

Pour les compressions avec perte, il faut bien s'assurer de ne l'appliquer qu'à la dernière étape de la chapine de traitement car les pertes peuvent se cumuler.

A titre d’exemple ci-dessous les variations en volumétrie d’une ortho RVB à 20cm de résolution :

| Format | Taille proportion | Volume sur 1 département |
| :--- | :--- | :--- |
| tif \(livraison brute\) | 100% | 412Go |
| tif tiling overview | 142% | 585Go |
| tif lzw tiling overview | 137% | 565Go |
| tif deflate tiling overview | 110% | 453Go |
| tif deflate alpha tiling overview | 119% | 490Go |
| tif jpeg tiling overview | 27% | 111Go |
| tif jpeg alpha tiling overview | 40% | 165Go |

L’option PREDICTOR en horizontal ou floating donne de meilleurs résultats \(gain de place\) mais semble mal gérée par Geoserver 2.8 \(edit d'après la liste Geoserver : predictor=3 n'est pas supporté du tout et type=2 ne supporte pas les 32 bit data\).

#### Quel rééchantillonnage?

Rééchantillonnage CUBIC  
![](https://lh4.googleusercontent.com/d558Uac2xPqBjlKSmGuK3eCEl8NY-HCOzHG-TGMSJYDYMBzDKbj23nyod0jO4McSblajicrTVLYncYWRjcrp1XRPl9qQT8jPqOgsWQ_GchcSsIByK0NrZioFUMMCCx0RmaHzexY)

Rééchantillonnage CUBICSPLINE

![](https://lh5.googleusercontent.com/KzYbOos1W4V_9ApIpbC7a8Zo5T1llqAcKWHt-vf-GFMbL7ti6daiyjB1yfuVtbE6l_FpfMvOpK9Tz2hzoz0WjsF3gUwT-yCpKSt0KP7R4epLLDQVRFv46OgbqpMdQreX91OvcnQ)

|  | Rééchantillonnages |  |  |
| :--- | :--- | :--- | :--- |
| Échelles de zoom | Cubic & Bicubic | Cubicspline | Lanczos |
| Grandes échelles | Effet poivre et sel en milieu urbain | Légèrement dégradée et floue en milieu urbain | Fine |
| Petites échelles | Nette et pixellisée | Floue et bruitée | Fine et moins pixellisée |

En plus de cette analyse, nous avons constaté des différences notables entre les niveaux de zoom notamment en mixant les ré-échantillonages: par exemple cubicspline dans les grandes échelles et lanczos dans les petites échelles.

Finalement nous avons jugé plus intéressant d'utiliser le lanczos comme algorithme de ré-échantillonange avec un rendu plus fin, agréable sur les hautes résolutions, et moins bruité ensuite pour l'orthophoto de Rennes Métropole.

Illustration des différents modes de rééchantillonnage de GDAL et donc pourquoi certains algorithmes sont plus adaptés à certains types d'images ou à certains types de rendus.

[https://gis.stackexchange.com/questions/10931/what-is-lanczos-resampling-useful-for-in-a-spatial-context](https://www.google.com/url?q=https://gis.stackexchange.com/questions/10931/what-is-lanczos-resampling-useful-for-in-a-spatial-context&sa=D&ust=1513783705182000&usg=AFQjCNG1-vFfZbDCikNjcs2WHzV8P0eIqw)  
Notez que Lanczos produit des artefacts : certains les considéreront comme gênants et d'autres comme améliorant la lisibilité de l'image.

#### Traiter les contours noirs

Plusieurs possibilités

* Bande alpha \(rajoute 10% de volume\)
* Footprints
* Affecter le dstnodata dans les dalles de manière à avoir un nodata value=0 sur chaque bande puis input transparent color à 000000 dans Geoserver

#### **Une formule qui marche \(© GéoBretagne 2013\)**

`gdal_retile.py -v -r bilinear -co TILED=TRUE -co COMPRESS=LZW -ps 4096 4096 -s_srs EPSG:2154 -co BLOCKXSIZE=256 -co BLOCKYSIZE=256 -levels 7 -targetDir pyramid ortho-56-2010.vrt`

Actuellement DEFLATE a tendance à remplacer LZW

#### Des ressources:

* GDAL[ http://www.gdal.org/](http://www.gdal.org/)

* Geotiff[ http://www.gdal.org/frmt\_gtiff.html](http://www.gdal.org/frmt_gtiff.html)

* Geoserver [http://docs.geoserver.org/latest/en/user/data/raster/index.html](http://docs.geoserver.org/latest/en/user/data/raster/index.html)

* Guides geosolutions [http://geoserver.geo-solutions.it/edu/fr/raster\_data/processing.html ](http://geoserver.geo-solutions.it/edu/fr/raster_data/processing.html)[https://www.slideshare.net/geosolutions/geoserver-on-steroids-foss4g-2015](https://www.slideshare.net/geosolutions/geoserver-on-steroids-foss4g-2015)

#### Comment chosir entre mosaique ou pyramide ?

Conseil Geosolution:

> Taille &lt; 2 Go =&gt; GeoTiff unique, tuilé + overviews
>
> 2Go &lt; Taille &lt; 500 Go =&gt; Mosaïque de GeoTiffs tuilés + overviews
>
> Taille &gt; 500 Go =&gt; Pyramide

Cependant les plateformes ont tendance à recourir à la pyramide en deça de ce seuil. Par ex Géopicardie publie les ortho agglo décimétriques en mosaique et sur une étendue plus importante en pyramide.

#### FICHIERS RASTER MOSAIQUE

Avantages:

* On peut combiner avec du BigTiff pour des performances optimales à grande échelle



Inconvénients:

* Si on veut faire de la mosaique avec du BigTiff la métodologie est assez lourde à mettre en oeuvre \(fusion des dalles, couche shape pour spécifier le nodata...\)

* Moins bonnes performances sur de la petite échelle

* Rendu intermédiaire moyen en mosaïque \(pb de reprojection des overviews\)

* Gestion des overviews. Geoserver supporte mal les aperçus externes Pour les aperçus internes de GeoTIFF \(ou les aperçus externes au format GeoTIFF\), notez que -clean ne réduit pas le fichier. Une exécution ultérieure de gdaladdo avec des niveaux d'aperçu entraînera l'extension du fichier plutôt que la réutilisation de l'espace des vues précédentes supprimées. Si vous souhaitez simplement modifier la méthode de rééchantillonnage sur un fichier qui a déjà des aperçus calculés, vous n'avez pas besoin de nettoyer les aperçus existants.\)

#### FICHIERS RASTER PYRAMIDE

Avantages:

* Meilleure qualité \(rendu et performance\) sur les échelles intermédiaires
* Chaine de production plus simple

Inconvénients:

* footprints pas possible

* Nécessite plus de paramètrage Geoserver

* Un peu plus volumineux si on ne veut pas utiliser de compression à perte

* Input transparent pour les contours retourne des artefacts en compression JPEG

## FICHIERS kml



