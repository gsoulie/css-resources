[< Back to main Menu](https://github.com/gsoulie/Mobile-App-Development)    

# Css

* [Convention BEM](#convention-de-nommage-BEM)     
* [Sticky navbar](https://github.com/gsoulie/css-resources/blob/master/css-sticky-navbar.md)     
* [Collection de layout / pattern prêt à l'emploi](https://csslayout.io/) / https://codyhouse.co/nuggets     
* [Css défensif](https://defensivecss.dev/)      
* [Tooltip](https://github.com/gsoulie/css-resources/blob/main/resources/tooltip.md)      
* [Checkbox animations](https://getcssscan.com/css-checkboxes-examples)     
* [Créer des formes avec clip-path](#créer-des-formes-avec-clip-path)       
* [Animations](https://github.com/gsoulie/css-resources/blob/main/css-animation.md)     

## Convention de nommage BEM

Les trois concepts clés de BEM (Block Element Modifier)

**Block** (bloc) : le bloc est un composant autonome qui peut être réutilisé. Il peut être vu comme un « conteneur » qui regroupe des éléments et des modificateurs. Par exemple, un bloc pourrait être une barre de navigation, un bouton ou une section de contenu.

**Element** (élément) : un élément est une partie d'un bloc qui a une signification sémantique par rapport à son bloc parent. Les éléments sont représentés par deux traits de soulignement. Par exemple, dans une barre de navigation, chaque élément de la liste de navigation serait un élément de la barre de navigation.

**Modifier** (modificateur) : un modificateur est une variation de l'apparence ou du comportement d'un bloc ou d'un élément. Les modificateurs sont représentés par deux tirets. Par exemple, un bouton peut avoir un modificateur pour sa taille ou sa couleur.

````css
.block {}
.block__element {}
.block--modifier {}
````

**Quelques exemples**

````html
<nav class="navbar">
  <ul class="navbar__list">
    <li class="navbar__list-item navbar__list-item--active">Accueil</li>
    <li class="navbar__list-item">À propos</li>
    <li class="navbar__list-item">Contact</li>
  </ul>
</nav>
````

````css
.title-h1 { color: black; }
.article__title-h1 { color: red; }
.navigation__title-h1 { color: blue; }

.product-card__price
.product-card__like-button
````

## Première lettre en majuscule

````css
.title {
  color: black;
  font-size: 1.25em;
  margin: 10px 0;

}
.title::first-letter {
  text-transform: uppercase !important;
}
````
## Animation underline sur un lien

````html
<p>
  <a class="anim-underline-fx" href="#0">How to create an underline fill effect in CSS</a>
</p>
````

````css
.anim-underline-fx {
  color: darkblue;
  text-decoration: none;
  background-image: linear-gradient(to right, darkblue 50%, lightsteelblue 50%);
  background-size: 200% 3px;
  background-repeat: no-repeat;
  background-position: 100% 100%;
  transition: background-position .3s;
}

.anim-underline-fx:hover {
  background-position: 0% 100%;
}

p {
  max-width: 480px;
  margin: 0px auto;
  font-size: 2rem;
}
````

## Créer des formes avec clip-path

Outil : https://bennettfeely.com/clippy/      

Tutorial : https://css-tricks.com/the-shapes-of-css/

Exemple de création d'un pentagone

*html*
````html
<div class="shield-wrapper">
  <div class="shield"></div>
</div>
````


*css*
````scss
.shield-wrapper {
      width: 70px;
      height: 80px;
    }
.shield {
  width: 100%;
  height: 100%;
  display: inline-block;
  font-size: initial;

  /*(haut centre[v, h], droite haut [h, v] , droite bas [h, v],
  gauche bas [h, v], gauche haut [h, v])*/
  /*clip-path: polygon(50% 90%, 80% 65%, 80% 15%, 20% 15%, 20% 65%);*/
  clip-path: polygon(50% 100%, 100% 65%, 100% 0%, 0% 0%, 0% 65%);
  background: rgb(49, 120, 60);
  background: linear-gradient(
    90deg,
    rgba(49, 120, 60, 1) 0%,
    rgba(145, 210, 152, 1) 30%,
    rgba(145, 210, 152, 1) 70%,
    rgba(49, 120, 60, 1) 100%
  );
}
````

## Changement couleur globale de tous les champs

````css
html {
  accent-color: hsla(180, 100%, 70%, 1);
}
