# Création de visites virtuelles et contenus pédagogiques en VR libres et gratuits

*Version 1*

> Auteurs:
> - **Maxime Renauld**, élève en TPRO SN RISC au lycée Louis de Cormontaigne, Metz
> - **Solenne Mvutu Mbeya**,  élève en TPRO SN RISC au lycée Louis de Cormontaigne, Metz
> - **Yanis Maafa**,  élève en TPRO SN SSIHT au lycée Louis de Cormontaigne, Metz
> - **Matthieu Farcot**, encadrement et validation, lycée Louis de Cormontaigne, Metz

## Objectif du document:
Expliquer comment créer et mettre en ligne des visites virtuelles incluant des éléments pédagogiques diversifiés. La technologie utilisée doit être entièrement gratuite et sous licence libre - y inclut l'hebergement. La technologie doit permettre une navoigation compatible avec les spécificités de multiples appareils, y inclut la navigation en VR 

Ce document doit inclure toutes les étapes de la réalisation, des prises de vue à l'édition du code en passant par l'hébergement. Le tout doit être écrit de la manière la plus simple et didactique possible, en procédant étape par étape.

La cible du document est le grand public *sans connaissances techniques préalables*.

## Introduction
Bienvenue sur notre page dédiée à la réalisation de panoramas 360° pour l’éducation en utilisant les bibliothèques A-Frame.

La réalité virtuelle a le potentiel de transformer l’éducation, en offrant des expériences d’apprentissage immersives et interactives. Les panoramas 360°, en particulier, peuvent permettre aux lycéens et étudiants de découvrir de nouveaux environnements et concepts d’une manière visuellement riche et engageante.

A-Frame, une bibliothèque JavaScript pour la création d’expériences de réalité virtuelle, rend cette technologie accessible à tous, même à ceux qui n’ont pas de connaissances approfondies en programmation. Avec A-Frame, vous pouvez consulter des panoramas 360° interactifs et immersifs directement dans votre navigateur web, ce qui est idéal pour une utilisation en classe ou à distance.

Sur cette page, nous vous guiderons à travers les étapes de la création de votre propre panorama 360° en utilisant A-Frame, spécifiquement adapté à un contexte éducatif. Nous commencerons par les bases, comme la configuration de votre environnement de développement et la prise de photos panoramiques, puis nous vous montrerons comment utiliser A-Frame pour assembler ces photos en une expérience de réalité virtuelle interactive.

Que vous soyez un enseignant cherchant à intégrer la réalité virtuelle dans votre salle de classe, un développeur web cherchant à créer des ressources éducatives interactives, ou simplement quelqu’un qui est curieux de la technologie de panorama 360°, nous espérons que vous trouverez cette page informative et utile. Bonne création !

# [Partie 1 - Matériel préparatoire et prises de vues](https://maximer37.github.io/VR-Markdown/guide1/partie1/index.html)

## En amont : La plannification

La plannification, définissant l'objet de la visite et le contenu qui devra s'afficher, est essentielle en amont de toute production. Ceci est plus simple à dire qu'à faire, mais il est essentiel de définir l'objectif de la visite et d'avoir une idée claire de *ce qui doit être montré*.

Dans notre cadre, nous allons réaliser une viste virtuelle simple du terrain de sport de lycée Louis de Cormontaigne à Metz, se basant sur deux panoramas à 360°. Cette visite devra inclure des informations textuelles, des images, des vidéos, et des objets en 3 dimensions qui s'insèrent naturellement dans un panorama en 360°. Pour simplifier l'exemple, nous allons lier deux panoramas 360° entre eux pour permettre de simuler une ballade. Suivant la logique de navigation entre panoramas, l'orientation de l'utilisateur dans un panorama va avoir un impact: il est plus naturel quand on se déplace d'un point A à un point B que la vue lors de l'arrivée au point B suive une ligne droite issue du point A, afin de faire comprendre l'idée du mouvement. De même, l'ensemble des panoramas seront enrichis avec du contenu pédagogique sous diverses formes. Ce contenu doit s'afficher *à sa place* dans le panorama (par exemple le texte qui donne des information sur un batiment doit flotter uniquement au dessus de ce batiment).

Ceci explique l'importance d'une reflexion en amont, afin d'être sûr d'avoir toutes les images requises. Prendre une prise de vue manquante dans un deuxième temps risque expose l'opération à des changement brutaux de conditions de navigation (lumière ou météo différente par exemple) qui vont nuire à l'immersion.

## Matériel nécéssaire

- Une caméra 360° (nous utiliserons une caméra Insta 360 pour cet exemple).
- Un pied pour appareil photo (afin d'avoir une hauteur de prise de vue fixe entre les différents panoramas)
- Un ordinateur, avec les logiciels suivants
  - Un environnement de développement (ici VS Codium)
  - Un logiciel d'édition et de retouche d'image (ici GIMP)
  - Un compte GitHub (nous utiliserons cette plateforme pour l'hebergement des scènes, et nous nous assurerons que vous puissiez retrouver les fichiers issus de ce document)

### Prise des vues 360°

Il est utile de bien plannifier en amont de toutes prises de vues les endroits où seront réalisés les photos.
En exterieur, des outils comme google earth sont particulièrement utiles.

![plannification](<partie2/resources/image/plan.jpg>)

L'importation des images est le moment ideal pour mofier la résolution  modifier la resolution de l'image de 2880 pixel par 1440 pixel avec le logiciel de la caméra puis j'ai flouté le visage pour par la suite les importer 

on va utiliser le code suivant pour importer l'image 360 sur le navigateur:
```
<!DOCTYPE html>
<html>
  <head>
    <script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-sky src="./images/panorama1.jpg"></a-sky>
    </a-scene>
  </body>
</html>
```
*... et c'est tout!*

Nous créons donc un document html à la racine de notre compte Github intitullé index.html


## Création d’un compte GitHub :


Pour commencer à utiliser GitHub, vous devez créer un compte personnel gratuit sur GitHub.com.


Suivez les invites pour créer votre compte personnel Assurez-vous d’utiliser un mot de passe fort et unique.


Vérifiez votre adresse e-mail lors de l’inscription. Sans adresse e-mail vérifiée, certaines tâches de base sur GitHub, comme la création d’un référentiel, ne seront pas possibles.


### Création d’un dépôt pour votre site :


Vous pouvez créer un nouveau dépôt ou utiliser un dépôt existant pour votre site.


Pour créer un nouveau dépôt :
Cliquez sur le bouton “+” dans le coin supérieur droit de n’importe quelle page, puis sélectionnez “Nouveau référentiel”.


Choisissez un nom pour votre référentiel (par exemple, <votre-nom-d'utilisateur>.github.io).


Sélectionnez “Public” comme visibilité du dépôt.
Cochez l’option “Initialize this repository with a README” (Initialiser ce dépôt à l’aide d’un fichier LISEZMOI).


Cliquez sur “Créer le dépôt”.


### Création de votre site :


Accédez au dépôt de votre site sur GitHub.


Configurez une source de publication pour votre site. Vous pouvez choisir entre différentes options, comme une branche dédiée ou un workflow GitHub Actions personnalisé.


Créez le fichier d’entrée pour votre site (par exemple, un fichier HTML, Markdown, etc.).


Publiez votre site en poussant vos fichiers vers le dépôt sur GitHub.


Votre site sera accessible via l’URL https://<votre-nom-d'utilisateur>.github.io.


Remarque : Les sites GitHub Pages sont disponibles publiquement sur Internet, même si leur dépôt est privé. Assurez-vous de ne pas inclure de données sensibles dans votre dépôt avant la publication

## Explication du code

Ce code est un exemple simple d’une page Web qui utilise la bibliothèque JavaScript A-Frame pour afficher une image à 360 degrés. Voici une explication détaillée de chaque partie :

`<!DOCTYPE html>` : Cette déclaration doit être la première ligne du document. Elle informe le navigateur que le document est une page HTML.

`<html>` : C’est la racine de la page HTML.

`<head>` : Cette balise contient des métadonnées sur le document HTML, qui ne sont pas affichées sur la page Web elle-même. Ici, elle contient une balise <script>.

`<script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>` : Cette balise importe la bibliothèque A-Frame, qui est une bibliothèque JavaScript pour la création d’expériences de réalité virtuelle.

`<body>` : Cette balise contient le contenu principal de la page Web, qui est affiché dans le navigateur.

`<a-scene>` : C’est une balise spécifique à A-Frame qui crée une scène 3D où vous pouvez placer des objets.

`<a-sky src="./images/3601.jpg"></a-sky>` : Cette balise spécifique à A-Frame crée un ciel autour de la scène avec comme texture l’image spécifiée. Dans ce cas, l’image est "3601.jpg" qui se trouve dans le répertoire "images".


`<a-scene>` est l’élément principal qui contient tous les objets 3D de la scène scène A-Frame.


`<a-assets>` est utilisé pour précharger les ressources, comme l'image de panorama.


`<img id="panorama-image" src="chemin_vers_votre_image.jpg">` définit une image que vous utiliserez pour le panorama. Remplace "chemin_vers_votre_image.jpg" par le chemin vers ton image de panorama.

`<a-sky src="#panorama-image"></a-sky>` crée le panorama en utilisant l’image que vous avez définie. Il utilise l’ID de l’image comme source.

N’oublie pas de remplacer "chemin_vers_votre_image.jpg" par le chemin réel vers ton image de panorama. Attention: l’image doit être au format equirectangular pour qu’elle s’affiche correctement comme un panorama 360°.


En résumé, ce code crée une scène de réalité virtuelle avec un ciel texturé par une image à 360 degrés. Vous pouvez interagir avec cette scène en utilisant la souris pour regarder autour de vous.



<!-- <a href="https://maximer37.github.io/VR-Markdown/"> -->

<img src="partie2/resources/image/panorama1.jpg" alt="premier panorama" height="auto" width="850">


# [Partie 2 - Navigation entre deux panorama 360](https://maximer37.github.io/VR-Markdown/guide1/partie2/index.html)

<img src="partie2/resources/image/panorama2.jpg" alt="premier panorama" height="auto" width="850">

Dans un premier temps j'ai ajouter un template dans mon code qui va me permettre de gagner du temps sur la création de fonction, on va aussi crée une page javascript du nom de index.js qui va me permetre d'utiliser des variable et des fonction propre a javascript, on va crée deux page html que l'on va ranger dans un dossier spécifique dans l'arboraissance ./partie2/Pages-Index/default.html et dans le dossier ./partie2/Pages-Index/1.html. Dans c'est index on peut y trouver les du code pour inserer un object qui est notre fleche, qui permet de naviger d'un panorama a l'autre. 

## Changer la couleur d'un object

Pour commencer il faut activer l'inspecteur avec la combinaisson de touche  `ctrl` + `Alt` + `I` 

<img src="partie2/resources/image/imagegenerique/presentationinspecteur.png" alt="mode inspecteur" height="auto" width="850">

A votre gauche on y trouve les element qui compose la page (le panorama,la camera...)

On va selectionner a gauche l'element ***MainScene*** puis dans la partie dérouler on selectionne l'entiter ***fleche*** 

<img src="partie2/resources/image/imagegenerique/selection.png" alt="selection" height="auto" width="250">

Puis maintenant notre fleche est selectionner on peut alors acceder au menu de modification des different element ici ce qui nous 
interesse c'est la couleur

A votre droite un menu c'est ouvert a fin de modifier la fleche, on va selection le menu deroulant ***Add composant*** on chercher ***Material***

<img src="partie2/resources/image/imagegenerique/ajoutcomposant.png" alt="ajout composant" height="auto" width="200">

ensuite on peut cliquer sur ***Material*** une ligne avec idiquer ***color*** va nous permetre de changer la couleur, on clique sur le carré blanc et a l'aide du curseur on va selectionner la couleur que l'on veut.

<img src="partie2/resources/image/imagegenerique/color.png" alt="changement de couleur" height="auto" width="850">

Enfin on peut copier extraire les modification pour les transformer en code a implementer dedans 

<img src="partie2/resources/image/imagegenerique/copiecode.png" alt="copie code" height="auto" width="200" >

on recherche la ligne du code qui fais reference a la ***fleche*** et on peut coller le nouveau code 

<img src="partie2/resources/image/imagegenerique/selectioncode.png" alt="selection code" height="auto" width="850">

# [Partie 3 - Animer un objet et inserer un texte](https://maximer37.github.io/VR-Markdown/guide1/partie3/index.html)

Dans un deuxieme temps on va animer notre fleche qui vas aller du haut vers le bas pour mieux indiquer ou va aller l'utilisateur Pour realiser cela on va utiliser un composant du nom de animation on vas lui indiquer le type d'animation  mais aussi inserer des texte pour mieux guider l'utilisateur dans son parcours.Pour cela on rajoute un composant poiur le texte qui va fonctionner avec une frise qui est au nveau du sol dans le but que le texte  regarde toujours vers l'utilisateur qui se base sur un morceau de code en javascript 

````
AFRAME.registerComponent('lamo', {
    schema: {
      angle: {type: 'int', default: 0},
      Y: {type: 'int', default: 1}
    },
  
    init: async function() {
      this.update = this.update.bind(this)
    },
  
````

# [Partie 4 - Implémentation d'une vidéo](https://maximer37.github.io/VR-Markdown/guide1/partie4/index.html)

Pour tout demarage de fichier video ou de fichier audio il faut obligatoirement une interaction qui permet de demmarer c'est dernier. tout cela est la causse de soucis deconomie de bande passance 

<!-- 
````
<a-entity id="printer" scene-changer="" obj-model="obj: ./resources/fleche.obj" position="-28.26659 0.24929 -16.91649" class="raycastable" rotation="-90 0 0" 


animation="property: position; dir: alternate; to: -28.2 -.4 -16.9; loop: true; dur: 1000"></a-entity>
````-->