## Gestion des contextes

Accessibles depuis le menu espace de travail, les contextes sont au format WMC. Ils peuvent être créés en sauvegardant la carte en cours.

![](/assets/contextes.PNG)

## Administrer les contextes

Après création des WMS, les enregistrer dans le data\_dir/mapfishapp/contexts.

Dans le répertoire images, on enregistre les visuels des contextes qui devront porter le même nom que les contextes au format png.

Exemple :

contexte 01.wmc     image 01.png

On veillera à bien renseigner les mots clés \(menu en haut à droite\) soit au moment de la création du WMC ou en l'éditant dans un éditeur de texte.



Extrait WMC :



> `  <General>  
>     <Window width="1600" height="950" />  
>     <BoundingBox minx="-552897.5948454746" miny="6012350.199226545" maxx="-167648.9843393778" maxy="6258886.822406981" SRS="EPSG:3857"/>  
>     <Title>Fond style Bing, photos</Title>  
>         <KeywordList>  
>             <Keyword>GEOBRETAGNE</Keyword>  
>             <Keyword>BRETAGNE</Keyword>  
>             <Keyword>OPENSTREETMAP</Keyword>  
>     </KeywordList>  
>     <Abstract>Un fond OpenStretMap contrasté avec toponymes, routes et bâtiments; les scan IGN; les photographies aériennes</Abstract>  
>     <DescriptionURL>  
>         <OnlineResource xlink:type="simple" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="http://www.geobretagne.fr/"/>  
>     </DescriptionURL>  
>     <Extension>  
>         <ol:maxExtent xmlns:ol="http://openlayers.org/context" minx="-1376846.9183907886" miny="4965405.476539082" maxx="652449.1653438079" maxy="6920373.037782215"/>  
>     </Extension>  
>   </General>`



