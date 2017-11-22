# Qu'est-ce qu'un addon?

# 

# Gérer la liste des addons Mapfishapp

Les addons disponibles sont stockés dans le datadir georchestra. Un répertoire dédié existe pour chaque addon dans mapfishapp/addons/.

Exemple avec l'addon cadastre : mapfishapp/addons/cadastre

Le paramétrage, le préchargement ou la désactivation de chaque addon se fait dans le fichier config.json de chaque addon présent à la racine de chaque addon.

Exemple de fichier config.json

```
[{
            "id": "geob_coordinates_0",
            "name": "geob_coordinates",
            "enabled": "true",            
            "title": {
                "en": "Coordinates",
                "es": "Coordonnées",
                "fr": "Coordonnées xyz"
            },
            "preloaded": "true",
            "description": {
                "fr": "Récupérer les coordonnéeses x, y, z en un point"
            },
            "options": {
                "placement": "bottom",
                "showintoolmenu": false,
                "autoactivate": true
            },
            "thumbnail": "img/thumbnail.png"
        }]
```

# Configurer les addons préexistants

Todo



## Addons disponibles

* [annotation](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/annotation/README.md)  qui permet de récolter les retours utilisateurs ou “feedback” pour une amélioration continue et collaborative des données.

* [cadastre](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/cadastre/README.md) which allows users to locate a feature \(typically a parcel\) based on cascading drop downs \(eg: state, then city, then borough\).
* [extractor](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/extractor/README.md) which relies on the services offered by the [extractorapp](https://github.com/georchestra/georchestra/blob/master/extractorapp/README.md) geOrchestra module.
* [magnifier](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/magnifier/README.md) which allows one to explore a map area with configured imagery.
* [openls](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/openls/README.md) which allows one to locate an address on the map.
* [quicksearch](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/quicksearch/README.md) is an all-in-one search tool.
* [streetview](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/streetview/README.md)... obviously based on the Google Street View Image API.
* [osm2geor](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/osm2geor/README.md) display vector data from OSM \(got from the Overpass API\) into a vector layer.
* [measure](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/measure/README.md) to perform simple distance and area measurements \(that cannot be printed\).
* [measurements](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/measurements/README.md) to perform advanced distance and area measurements \(which can be printed 
  &
   exported to KML\).
* [locateme](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/locateme/README.md) allows users to track their location on the map.
* [fullscreen](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/fullscreen/README.md) to \(obviously\) make the map fullscreen.
* [notes](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/notes/README.md) to report map issues.
* [atlas](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/atlas/README.md) allows users to print PDF with one feature per page.
* [coordinates](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/coordinates/README.md) to let the user copy location coordinates.
* [goto](https://github.com/georchestra/georchestra/blob/master/mapfishapp/src/main/webapp/app/addons/goto/README.md) allows users to recenter the map on a location, given its coordinates. 



