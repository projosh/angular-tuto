
Il faut mettre à jour le dossier product-list 
qui va afficher une liste de produit utiliserez des données produit prédéfinies 
à partir de products.ts

On a rajouté une boucle for of qui va boucler sur une variable produit qui appelle une liste de produit.
elle va répeter sur chaque produit de la liste.

{{product-name}} est une déclaration elle va permettre de rendre 
une valeur au texte

{{product-name}} va charger et afficher le nom dans une liste. 

Chaque produit doit être englobé d'un lien <a> 

Pour personnaliser les titres on utlisera les crochets [] a[title]

On rajoute la description du produit avec une balise <p> 

On met une condition *ngif qui est une condition si il montre ou pas

Le bouton user va permettre de partager le produit avec l'action du bouton click
comme un "addevenlistenner" 

lorsqu'on clique sur share il y'a un popup qui indique le produit à bien été partager.


### Transmettre des données à un composant enfant.

On doit ouvrir un nouveau terminal.

Dans ce terminal on va copier coller ce code.

ng generate component product-alerts

il va generer ces fichiers : 

product-alerts.component.ts
product-alerts.component.html
product-alerts.component.css

Quand on ouvre le fichier ts 
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

cela mettra à jour le produit cela va notifier que le produit à bien été vendu.

On copie colle dans le terminal
ng generate component product-details

le RouteurLink
Lorsqu’il est appliqué à un élément dans un modèle, 
fait de cet élément un lien qui lance la navigation vers un itinéraire
et va generer un id et ainsi personnalisé 

En cliquant on va se trouver sur une autre page

On va importer ActivatedRoute de angular/router

Dans la classe class ProductDetailsComponent
on a injecté un produit 

Le constructor doit être privé pour
qu'il ne soit pas accessible n'importe où

ngOnInit() est une methode qui va extraire le productId 

<div *ngIf="product"> c'est une condition si 
le nom du produit, son prix et sa description 
alors le produit sera affiché. il transforme les chaines 
de caractére et les transformes afin d'afficher le contenu

ng generate service cart
Cela creer des repertoires
cart.service.spec.ts
cart.service.ts

on a importé le composant product et
esporté la class cartservice

items: Product[] = []; cela va permettre de 
ajouter des articles au panier, retourner des articles 
de panier et effacer les articles du panier.

addToCart(product: Product) { 
    this.items.push(product);

cela permet de rajouter un produit

import { CartService } from '../cart.service';

importer le dossier cart.service

on a rajouter un nouveau constructor cartservice en plus 
de activateroute

constructor(
    private route: ActivatedRoute,
    private cartService: CartService

addToCart() va lier l'événement à la méthode 
et l'ajouter au panier 

###nouveau panier


Generer un nouveau composant appeler cart
avec cette ligne de commande 

ng generate component cart et va creer 

ces fichiers : 

CREATE src/app/cart/cart.component.html (19 bytes)
CREATE src/app/cart/cart.component.spec.ts (612 bytes)
CREATE src/app/cart/cart.component.ts (267 bytes)
CREATE src/app/cart/cart.component.css (0 bytes
 
RouterLink 
Permet d'intercepter l'événement click 
sur les liens et de changer de "route" sans recharger toute l'application.

On injecte un nouveau constructor en privé CartService
constructor(
    private cartService: CartService

on rappel notre constructor 
avec cette commande qui va definir notre item
items = this.cartService.getItems();

On injecte ce code dans notre fichier cart.component.html

<h3>Cart</h3>

<div class="cart-item" *ngFor="let item of items">
  <span>{{ item.name }}</span>
  <span>{{ item.price | currency }}</span>
</div>

Cela va permettre de boucler avec une boucle for entre les items
entre les nom et les prix.


Configurer AppModulepour utiliserHttpClient

configurer votre application pour utiliser HttpClientModule.

il va se servir d'un fichier json pour rechercher les informations

on rajoute un nouveau constructor 

  constructor(
    private http: HttpClient
  ) {}

HttpClient est une requête qui va attendre une reponse

On configure cartservice avec les délais de livraison

On utilisera la méthode get pour obtenir les informations 

 getShippingPrices() {
    return this.http.get<{type: string, price: number}[]>

Il retourne la chaine de caractére price 

Copie colle dans le terminal
ng generate component shipping
cela generer un composant shipping

Cela va creer des composant shipping

On rajouter dans le app.module.ts

le chemin est mis automatiquement
{ path: 'shipping', component: ShippingComponent },

et aussi la declarations 
  ShippingComponent

Dans le composant shipping.component.ts

on va rajouter un constructor private cartService

Dans le composant shipping.component.html 

<h3>Shipping Prices</h3>

<div class="shipping-item" *ngFor="let shipping of shippingCosts | async">
  <span>{{ shipping.type }}</span>
  <span>{{ shipping.price | currency }}</span>
</div>

On a une boucle for qui va nous indiquer que tant 
qu'on clique sur buy alors il va boucler sur la variable shipping
de shippingcost

pour les objets (item) on aura aussi une boucle for 
pour nos item name et item price

Importer 
import { FormBuilder } from '@angular/forms';

On va injecter un nouveau constructor formBuilder
 
checkoutForm = this.formBuilder.group({ 

va permet de vérifier le formulaire.

onSubmit est une methode qui va nous envoyer le formulaire 

### creation du formulaire de payement

On injecte ce code : 

<form [formGroup]="checkoutForm">

  <button class="button" type="submit">Purchase</button>

</form>

on va rajouter ngSubmit qui va permettre d'envoyer le formulaire
via angular

