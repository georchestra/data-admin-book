# Configurer le bandeau \(header\)



\#\# Description



Le bandeau \(module header\) est un bloc horizontal affiché sur toutes les applications intégrées dans geOrchestra. Il permet de naviguer entre ces applications. Le bandeau se présente différemment selon le profil de l'utilisateur.



\#\#\# Utilisateur anonyme



Pour un utilisateur anonyme, le bandeau présente de gauche à droite :



\* un logo de la plateforme. Un clic sur le logo permet d'accéder à xxxxxxxxxx.

\* un bouton catalogue qui affiche la page d'accueil du catalogue

\* un bouton visualiseur qui affiche l'interface du visualiseur avancé

\* un bouton services qui affiche la page d'accueil de GeoServer



A droite, un bouton \`\`\`connexion\`\`\` permet à l'utilisateur de se connecter.



Note : si l'utilisateur souhaite créer un compte, il doit utiliser le bouton \`\`\`connexion\`\`\` puis le lien \`\`\`s'inscrire\`\`\`





\#\#\# Utilisateur authentifié \(non administrateur\)



Une fois l'utilisateur connecté, le bouton \`\`\`connexion\`\`\` se change en deux boutons pour accéder au profil de l'utilisateur et pour se déconnecter.



\#\#\# Administrateur



Le bouton \`\`\`administration\`\`\` est ajouter. Il permet d'alterner entre les boutons d'application utilisateurs et les boutons d'applications d'administration.



\#\# Personnalisation



Le bandeau peut être partiellement personnalisé à partir de \`\`\`\`datadir/header\`\`\`.



\#\#\# Modifier le logo



Il suffit de déposer une image \`\`\`logo.png\`\`\` dans le répertoire headers. Le logo doit avoir une hauteur de 50px, une hauteur différente sera automatiquement redimensionnée à 50px.



\#\# Modifier le lien du logo



Je ne sais pas !



\#\# Modifier les couleurs du bandeau



La configuration ne le permet actuellement pas.



