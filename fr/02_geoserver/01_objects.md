# Définitions

Un **espace de nommage** ou *workspace* permet de classer des objets dans Geoserver. Par exemple http://mon.georchestra.org/geoserver/ws/ows?service=wms&request=getcapabilities va lister uniquement les services wms de mon espace de travail ws.

Un **entrepot** ou *store* donne accès à une source de donnée par exemple un shapefile, un répertoire de shapefile, un schéma postgis, un geotiff, un répertoire de geotiff...

Une **couche** ou *layer* constitue le couple WMS/WFS pour du vecteur, WMS/WCS pour du rasteur. C'est ici que l'on affecte les symbologies, les attributions, que l'on active le WMTS [cf](02_geoserver/02_create_layer.md)...

Une **agrégation de couches** ou *layer group* permet de regrouper les couches comme typiquement l'orthophoto composite de géobretagne (on passe d'une image satellite à un orthophotoplan selon le niveau de zoom)

Un **style** définie le mode de représentation de la couche (trame, seuils d'affichage ...)

Pour plus de détails se référer à http://docs.geoserver.org/stable/en/user/data/webadmin/index.html

# Considérations diverses

Geoserver est organisé par espaces de nommage et laisse la possibilité à l'administrateur de garder l'**endpoint** ouvert ou non.

Il faut savoir que GeoWebCache a besoin de l'endpoint ouvert pour fonctionner (GS 2.8). De plus avec un endpoint fermé, on ne pourra plus monter des couches agrégées venant d'espaces de nommage différents (sauf à devoir les dupliquer).

En cas d'un grand nombre de couches dans Geoserver, un getcapabilities sur l'endpoint peut être lent. Il est néanmoins possible de le garder ouvert sans pour autant utiliser ou communiquer les appels sur l'url globale Geoserver.

Généralement les IDS organisent leurs espaces de nommage par partenaires afin de pouvoir leur déléguer la création des couches et des styles (on parle d'**administration déléguée** [cf](02_geoserver/04_layer_security.md)).

Les **acronymes** choisis pour les espaces de nommage devraient être le plus générique possible étant donné que les appellations changent (typiquement Conseil Général en Conseil Départemental). En cas de changement cette mise à jour n'est pas simple et on peut être amené à devoir recréer tous les entrepôts, les couches et les styles (via gsconfig par exemple). Un resolver pourrait accompagner le changement dans la douceur. En tous cas, il n'est pas conseillé de modifier le datadir à la main sans assurance.

Les styles seraient à organiser par espaces de nommage sauf pour ceux susceptibles d'intéresser d'autres utilisateurs.

Dans le choix des **noms des couches**, il est conseillé de prendre des appellations génériques type ortho67_2015 ce qui aurait l'avantage de pouvoir être réutilisable si au fil du temps on modifie un format de publication par exemple. La stabilité des chemins d'accès aux couches est très importante pour les applications tierces qui consomment les données.
