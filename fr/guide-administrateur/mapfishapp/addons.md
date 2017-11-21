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



