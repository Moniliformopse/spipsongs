SPIPSONGS - Portée Libre
=======
Tout un univers musical contemporain.
Site collaboratif de créations musicales contemporaines.
Conçu pour publier, informer, consulter et partager un répertoire ou acheter un produit.

Adresse du site : http://www.notretribunet.fr/songs/ 

Squelette du projet propulsé par Spip 3 et Thelia

Technologies utilisées
===========

Ce site fonctionne avec le système de publication SPIP -> http://www.spip.net/fr , outil libre de publication web, distribué sous licence GNU / GPL 3 -> http://www.gnu.org/licenses/gpl-3.0.html 

Le support de publication, le code spécifique de ce site et son identité graphique sont redevables aux auteurs de SPIPr -> http://spipr.nursit.com/ 

L’identité graphique de ce site utilise les outils suivants :
- BootStrap -> http://getbootstrap.com/ 
- LESS -> http://lesscss.org/ 
- Layout Gala -> http://blog.html.it/layoutgala/ 

Le schéma de micro-données utilisé sur ce site fait référence à "Schema.org" -> http://schema.org/ 

La typographie du site intègre une base CSS pour le contenu éditorial web : Tiny Typo -> http://tinytypo.tetue.net/ 

La partie marchande de ce site intègre Thelia, une solution e-commerce libre -> http://thelia.net/ 

Le lecteur en page d’accueil s’inspire de Free Art Template -> http://www.softrains.fr/template/ , un thème minimaliste pour Spip 3 distribué sous Licence Art Libre -> http://artlibre.org/licence/lal . Retrouvez le projet et la documentation sur GitHub -> https://github.com/jean-emmanuel/spip-fat/ 

Conception et mise en œuvre
===========

C’est grâce à tous ces outils (librement mis à disposition) que la personnalisation de l’habillage graphique de ce site a été développée pour le plaisir par Moniliformopse -> http://moniliformopse.tiddlyspace.com/ 

Installation
============

- Installer Spip 3 -> http://www.spip.net/fr_download
- Configurer Spip (monsite.fr/ecrire) 
- Copier le contenu du git à la raçine de l'installation de spip dans un repertoire du même nom
- Créer le ficher "mes_options.php" dans le dossier "config" et y ajouter ces lignes :

```
<?php
  $GLOBALS['dossier_squelettes'] = 'NOM_DU_REPERTOIRE';
?>
```

- Modifier/créer le fichier .htaccess dans votre installation de spip, y ajouter ces lignes :
- adapter la ligne "RewriteBase /" à votre installation si le site se trouve dans un repertoire.

```
SetEnv PHP_VER 5
SetEnv REGISTER_GLOBALS 0

RewriteEngine On

RewriteBase /

RewriteCond %{QUERY_STRING} action=rss
RewriteRule spip.php	spip.php?page=rss [QSA,L]
RewriteCond %{QUERY_STRING} action=ical
RewriteRule spip.php	spip.php?page=ical_prive [QSA,L]
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule "." - [skip=100]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule "." - [skip=100]
RewriteRule ^rubrique([0-9]+)(\.html)?$	spip.php?page=rubrique&id_rubrique=$1 [QSA,L]
RewriteRule ^article([0-9]+)(\.html)?$	spip.php?page=article&id_article=$1 [QSA,L]
RewriteRule ^breve([0-9]+)(\.html)?$	spip.php?page=breve&id_breve=$1 [QSA,L]
RewriteRule ^mot([0-9]+)(\.html)?$		spip.php?page=mot&id_mot=$1 [QSA,L]
RewriteRule ^auteur([0-9]+)(\.html)?$	spip.php?page=auteur&id_auteur=$1 [QSA,L]
RewriteRule ^site([0-9]+)(\.html)?$	spip.php?page=site&id_syndic=$1 [QSA,L]
RewriteRule ^(rubrique|article|breve|mot|auteur|site|agenda|backend|backend-breves|distrib|forum|ical|plan|recherche|sommaire|sommaire_texte)\.php3?$	spip.php?page=$1 [QSA,L]
RewriteRule ^resume.php[3]?	spip.php?page=sommaire [QSA,L]
RewriteRule ^page.php[3]?	spip.php [QSA,L]
RewriteRule ^spip_cal\.php3?$	spip.php?page=ical_prive [QSA,L]
RewriteRule ^spip_rss\.php3?$	spip.php?page=rss [QSA,L]
RewriteRule ^([1-9][0-9]*)$     spip.php?action=redirect&type=article&status=301&id=$1 [QSA,L]
RewriteRule ^([\w]+)\.api(/(.*))?$ spip.php?action=api_$1&arg=$3 [QSA,L]

RewriteRule ^([^\.])+(\.html)?$		spip.php?page=sommaire [QSA,E=url_propre:$0,L]

RewriteRule ^(.*/)?\.svn/ - [F]
RewriteRule ^robots[.]txt$      spip.php?page=robots.txt [QSA,L]
RewriteRule ^favicon[.]ico$      spip.php?page=favicon.ico [QSA,L]
RewriteRule ^sitemap[.]xml$      spip.php?page=sitemap.xml [QSA,L]

ErrorDocument 404 /spip.php?page=404

<Files .htaccess>
order allow,deny
deny from all
</Files>

<ifModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
mod_gzip_item_include handler ^cgi-script$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>
```


Configuration
=============

Aller dans l'espace privé (monsite.fr/ecrire)

- Définir l'url et le nom du site dans Configuration / Identité du site. Ignorer les autres options.
- Dans la configuration des fonctions avancées de spip, activer la compression automatique des images (GD2 si possible, nécessaire pour afficher des images compressées en gardant la transparence)
- Créer une rubrique, préciser le titre, le numéro de l'abum bandcamp et le sous titre. Enregistrer.
 - Si la rubrique porte le même nom que le site, son url canonique sera celle du site (monsite.fr au lieu de monsite.fr/marubrique)
 - Numéro d'album bandcamp dans le cadre "Descriptif rapide". On le trouve sur la page de l'album, en affichant le code source (ctrl+U), à la dernière ligne, après "album id".
 - Sous titre dans le cadre "Description de la page (meta) et sous titre";
- Ajouter des liens dans la rubrique, penser à leur attribuer un nom d'icône et à les publier une fois enregistrés. 
 - Pour ajouter un lien, cliquer sur "Référencer un site" depuis la page de rubrique dans l'espace privé
 - Le dernier cadre permet de choisir l'icone du lien ajouté, on y indique une des classes proposées dans la liste ("Liste des Icones")
- Ajouter une image de fond à la rubrique. L'image de fond secondaire (optionnelle) apparaitra par transparence au défilement de la page.
- Créer autant d'articles que nécessaire sans oublier de les publier.
- Télécharger et activer l'ensemble des plugins qui font SPIPr -> http://spipr.nursit.com/telecharger 
- Intégrer Thelia pour SPIP -> http://contrib.spip.net/Thelia 


Intégration dans un article
===========

Bandcamp : 
```  
<bandcamp|id=NUMERO_D'ALBUM>
```

Vimeo : 
```  
<vimeo|id=ID_VIDEO>
```

Youtube : 
```  
<youtube|id=ID_VIDEO>
```

Dailymotion : 
```  
<dailymotion|id=ID_VIDEO>
```

Image :
```  
<imgX|align|nolink|noborder|width>
```
 - align : left / right / center
 - nolink : masque le lien vers l'image d'origine (non réduite)
 - noborder : masque la bordure de l'image (pratique pour les images sur fond transparent)
 - width : redimensionne l'image par la largeur (l'image ne pourra pas dépasser la largeur du texte.
 
Document (affiche le type, la taille et le titre du document) : 
```  
<docX>
```

Gallerie photo : 
```  
<slider|id=ID_ARTICLE|titre=TITRE(OPTIONNEL)>
```
 - Affiche les images ajoutées à l'article pointé par l'identifiant dans un carousel
 - Chaque image peut avoir un texte associé (indiqué dans le champ "Crédits")

Compatibilité 
=============

- Spip 3 (derniere version testée : 3.0.15)
- Bureau : IE 9+ (Accessible IE 7&8), Firefox, Chrome, Safari.
- Mobile : à peu près tous les navigateurs mobiles modernes.

Performances 
=============

Tous les scripts sont chargés en différé pour optimiser le temps de chargement, de même qu’une grande partie du css.
