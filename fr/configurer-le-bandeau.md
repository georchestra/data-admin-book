# Bandeau \(header\)

Le bandeau \(module header\) est un bloc horizontal affiché sur toutes les applications intégrées dans geOrchestra.

![](/assets/index.png)

Il permet de naviguer entre ces applications. Le bandeau se présente différemment selon le profil de l'utilisateur.

### Bandeau pour utilisateur anonyme

Pour un utilisateur anonyme, le bandeau présente de gauche à droite :

* un logo de la plateforme. Un clic sur le logo permet d'accéder à la racine du site \(adresse `/` \).
* un bouton catalogue qui affiche la page d'accueil du catalogue \(adresse `/geonetwork/` \)
* un bouton visualiseur qui affiche l'interface du visualiseur avancé \(adresse `/mapfishapp/` \)
* un bouton services qui affiche la page d'accueil de GeoServer \(adresse `/geoserver/web`\)

* à droite, un bouton `connexion` permet à l'utilisateur de se connecter.

> Si l'utilisateur souhaite créer un compte, il doit utiliser le bouton `connexion` puis le lien `s'inscrire`

### Bandeau pour utilisateur authentifié \(non administrateur\)

Une fois l'utilisateur connecté, le bouton `connexion` se change en deux boutons pour accéder au profil de l'utilisateur et pour se déconnecter.

La destination des boutons utilisateurs est fabriquée à partir du paramètre `ldapAdminPublicContextPath`dans `header/header.properties` .

Si l'utilisateur a, dans son profil, le droit d'accéder à des applications filtrées, les boutons correspondant apparaîssent.

### Bandeau pour administrateur

Le bouton `administration` est ajouté. Il permet d'alterner entre le bandeau utilisateur et le bandeau  des applications d'administration.

## Personnalisation du bandeau

Le bandeau peut être partiellement personnalisé à partir de la configuration datadir.

#### Modifier la hauteur

La hauteur est configurable dans les fichiers suivants :

`cas/cas.properties:header.height=90      
catalogapp/catalogapp.properties:headerHeight=90                  
geowebcache/geowebcache.properties:header.height=90                  
ldapadmin/ldapadmin.properties:headerHeight=90`

Cette configuration n'agira pas sur le header lui-même, ni sur les applications dont le bandeau n'est pas configurable \(en particulier GeoServer et GeoNetwork\).

#### Modifier le logo

Copier une image png dans l'emplacement `header/logo.png`. L'image doit avoir une hauteur de 50px. Une image sera automatiquement redimensionnée à une hauteur de 50px.

#### Modifier le lien du logo

Le logo est associé à l'adresse "/" donc à la racine du domaine. Pour rediriger vers une ressource il faut mettre en place une redirection dans le reverse proxy.

#### Modifier les couleurs du bandeau

La configuration ne le permet actuellement pas.

#### Changer la langue

Paramètre `language`dans `header/header.properties`

