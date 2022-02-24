
Il faut mettre à jour le dossier product-list 
qui va afficher une liste de produit utiliserez des données produit prédéfinies 
à partir de products.ts

On a rajouté une boucle for of qui va boucler sur une variable produit qui appelle une liste de produits
elle va répeter sur chaque produit de la liste

{{product-name}} est une déclaration elle va permettre de rendre une valeur au texte

{{product-name}} va charger et afficher le nom dans une liste 

Chaque produit doit être englobé d'un lien <a> 

Pour personnaliser les titres on utlisera les crochets [] a[title]

On rajoute la description du produit avec une balise p 

On met une condition *ngif qui est une condition si il montre ou pas

Le bouton user va permettre de partager le produit avec l'action du bouton click
comme un addevenlistenner 

lorsqu'on clique sur share il y'a un popup qui indique le produit à bien été partager



##Transmettre des données à un composant enfant

On doit ouvrir un nouveau terminal

Dans ce terminal on va copier coller ce code 

ng generate component product-alerts

il va generer ces fichiers : 

product-alerts.component.ts
product-alerts.component.html
product-alerts.component.css

quand on ouvre le fichier ts 
product-alerts.component.ts

@Component() indique la classe qui doit suivre et importe un comportement
identifier les composants par convention on mettra le prefix
app-

Un composant (component) Angular représente un bout d'interface de l'application. 
C'est à vous de décider ce que vous mettez dans un composant ; 
ça peut aller d'un simple bouton à un écran entier. 
On part toujours d'un composant racine, qui représente l'ensemble de l'application

 ProductAlertsComponent importe input de @angular/core.

definit une classe et une propriété nommer produit

@Input() cela correspond à une classe dont les parents sont 
ProductListComponent.

NgModule fournit des métadonnées de configuration. 
qui va declarer ces composants

@NgModule({
  declarations: [
    AppComponent,
    TopBarComponent,
    ProductListComponent,
    ProductAlertsComponent,
  ],


###Transmettre des données à un composant parent

EventEmitter est un module qui permet de partager des données entre les composants à l’aide de méthodes. 

p *ngIf="product && product.price > 700">

C'est une condition si le produit s'affiche avec le prix 700 sinon il
nous retourne que c'est faux
on pourra agir cette action avec une action de clique 
  <button type="button" (click)="notify.emit()">Notify Me</button>

Le onNotify() method ressemble à la methode share

cela mettra à jour le produit cela va notifier que le produit à bien été vendu

