## Personnalisation de la liste des catalogues interrogeables

Accès à la liste des catalogues : depuis le menu Ajouter des couches.

![](/assets/listing_csw.PNG)

Prérequis : le catalogue doit fournir un service CSW compatible version 2.0

Le fichier de configuration a modifier GEOR\_custom.js est dans le datadir/mapfishapp/js dans la rubrique CATALOGS :

CATALOGS: \[  
        \['https://geobretagne.fr/geonetwork/srv/fre/csw', 'GéoBretagne'\],  
        \['http://geowww.agrocampus-ouest.fr/geonetwork/srv/fre/csw', 'Agrocampus Ouest'\]  
\]

Dans ce même fichier, on pourra personnaliser le contexte par défaut, le maximun de fiches retournées par une recherche, l'impression, les applications de partage...

## Personnalisation de la liste des serveur OGC

Accès à la liste des services OGC : depuis le menu Ajouter des couches onglet Serveur OGC

![](/assets/listing_wms.PNG)

Prérequis : le service WMS doit être en version xx et le service WFS en xx.

Le fichier de configuration a modifier est dans le datadir/mapfishapp/wms.server.json ou wfs.server.json ou wmts.server.json

Voici un exemple pour WMS :

{"servers": \[  
    {"name": "GéoBretagne - Altimétrie", "url": "https://geobretagne.fr/geoserver/alti/wms"},  
    {"name": "GéoBretagne - Cadastre", "url": "https://geobretagne.fr/geoserver/cadastre/wms"},  
    {"name": "GéoBretagne - OpenStreetMap", "url": "https://geobretagne.fr/geoserver/osm/wms"},  
    {"name": "GéoBretagne - Photographies", "url": "https://geobretagne.fr/geoserver/photo/wms"},  
    {"name": "GéoBretagne - IGN", "url": "https://geobretagne.fr/geoserver/ign/wms"}  
\]}

## Ajouter un thésaurus

Accès à la liste des services OGC : depuis le menu Ajouter des couches onglet Thesaurus

![](/assets/listing_thesaurus.PNG)

