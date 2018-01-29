# BASICS FOR RUBY ON RAILS
Description des concepts essentiels pour Ruby on Rails


* [Site statique / Site dynamique](https://github.com/dacoloma/Rails_initiation#site-statique--site-dynamique)
* [Model View Controller (MVC)](https://github.com/dacoloma/Rails_initiation#model-view-controller-mvc)
* [Les routes](https://github.com/dacoloma/Rails_initiation#les-routes)
* [Bases de Données](https://github.com/dacoloma/Rails_initiation#bases-de-donn%C3%A9es)
* [GET / POST](https://github.com/dacoloma/Rails_initiation#get--post)
* [Migration](https://github.com/dacoloma/Rails_initiation#migration)
* [Les relations entre les models des BDD](https://github.com/dacoloma/Rails_initiation#les-relations-entre-les-models-des-bdd)
* [CRUD](https://github.com/dacoloma/Rails_initiation#crud)

## Site statique / Site dynamique
Lorsqu'un site est défini comme étant statique, cela signifie que le lien sur lequel on se trouve nous renverra toujours les mêmes données (ex: http://motherfuckingwebsite.com/). L'affichage renvoyée sera toujours identique, quelque soit le nombre de visites.

Pour un site dynamique, l'URL d'une page peut envoyer un affichage différent selon l'internaute. (ex: mon fil d'actualités Facebook et celui de mon voisin). Pour notre exemple, l'affichage sera différent après quelques rafraichissement de la page car de nouvelles actualités apparaissent au cours du temps.

ATTENTION : si vous pensez qu'un site qui contient des animations (GIF, vidéos, ou musiques) est forcément un site dynamique, VOUS VOUS TROMPEZ. Un site statique peut très bien contenir des animations, mais elles resteront les mêmes, peu importe votre nombre de fois que vous visitez la page.
## Model View Controller (MVC)
L'architecture MVC sert à structure votre code sous 3 fichiers. Le but de cette architecture est de rendre plus lisible votre code au lieu d'avoir un seul fichier où il est facile de s'y perdre.

On retrouve cette structure dans chaque application Rails, dans un dossier app/, où nous allons retrouver des sous-dossiers models, views, controllers.

<p align="center">
  <img src="/images/mvc.png">
</p>

Grossièrement:
- le Model est le fichier qui va permettre d'aller récupérer des données de la BDD
- le View contient le code HTML, c'est la partie qui s'occupera de l'interface Homme/Machine
- le Controller contient le code logique et fait la passerelle entre ces 2 fichiers et l'utilisateur

### Model
C'est dans ce fichier que seront stockées toutes les requêtes vers votre Base de Données.

### View
C'est ici que se trouve le code HTML de votre site web. C'est donc cette partie qui va s'occuper de mettre les données sous forme HTML récupérées de la BDD.

### Controller
Lorsqu'un utilisateur se trouve face à son navigateur, l'utilisateur adresse ses requêtes au Controller. Chaque requête renvoie vers une action (fonction) dans le Controller. Chaque action va donc transmettre une requête vers le Model. Après réponse du Model, les données vont être envoyées vers le View pour la mise en forme.

Pour chaque action du Controller il existera donc un fichier View qui contiendra le code HTML correspondant)

## Les routes
Les routes d'un site sont représenter dans l'URL avec des '/' comme pour les chemin en terminal.
Ex : J'ai crée www.mon-site.fr et je dispose de 3 links : Accueil, Historique, Contact.
Si je tape dans la barre d'adresse de mon navigateur www.mon-site.fr/accueil, cela me renverra vers la page Accueil (en supposant que j'ai crée un fichier HTML correspondant).

Le principe des routes pour Rails consiste à rediriger un utilisateur vers l'action correspondante dans le Controller (puis ensuite refaire le parcours MVC)
## Bases de Données
C'est un ensemble de données organisé autour d'un thème, activité, etc.
Ex: Amazon contient une énorme BDD qui contient les infos de chaque utilisateurs (noms, prénoms, ville, moyen de paiement, etc.), les infos des articles à vendre (nom, prix, descriptif, etc.), etc.
## GET / POST
GET : va aller appeler la méthode du Controller lié à l'URL rentré par l'utilisateur.
Ex: l'utilisateur tape dans son navigateur monsite.com/welcome  => il sera renvoyé vers la méthode index situé dans le Controller appelé 'welcome'
```ruby
Rails.application.routes.draw do
    get 'welcome', to: 'welcome#index'
end
```
POST : sert à soumettre un formulaire. Par exemple, si on a site qui affiche la liste de toutes les bières dans le monde. On souhaiterait ajouter une nouvelle marque de bière. On passera donc par la méthode POST qui va renvoyer vers une méthode create dans le Controller.

## Migration
La migration est une classe qui permet de créer une table de BDD, de la modifier ou de la supprimer.
```
$ rails g migration CreateTestTable title:string content:text
```
Dès la création du fichier de migration, le site est devenu inaccessible et vous renverra une erreur pour dire qu'une migration est en attente. Il est nécessaire d'effectuer une mise à jour de la BDD avant de pouvoir rentre le site opérationnel.
```
$ rails db:migrate
```
Si une mise à jour a été faite mais que vous désirez revenir en arrière, il suffit de taper cette commande :
```
$ rails db:rollback
```

## Les relations entre les models des BDD


## CRUD
Acronyme informatique anglais qui correspond à 4 fonctions nécessaires pour gérer une base de données  :
- Create
- Read
- Update
- Delete
