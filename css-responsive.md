
# Astuces pour bien gérer le responsive


## Responsive sans @media queries

````css
.container {
	padding: 5em;
}
@media(max-width: 700px) {
	.container {
		padding: 2em
	}
}
````

Peut être remplacé par : 

````css
.container {
	padding: min(5em, 8%); // La première valeur est la valeur par défaut. La seconde valeur est une unité responsive
}
````

## Font responsive

Il est fortement conseillé d'utiliser une taille de font en ````rem```` (root element font-size) qui est une unité relative par rapport à l'élément root.

*Valeur par défaut* : **1rem = 16px**

Donc 1.5rem =  16px * 1.5 = 24px

Pour bien gérer le responsive sur les fonts, il faut tenir compte de trois choses :

* valeur préférée
* taille max pour les grands écrans
* taille min pour les petits écrans (mobiles)

Pour ce faire il existe la fonction ````clamp(min, preferred, max)````

````css
h1 {
	font-size: clamp(1.8rem, 10vw, 5rem); // 10vw = 10% de la taille de la largeur de la vue
}
````

Cependant l'utilisation de l'unité ````vw```` pose un problème en cas de zoom car elle est calculée uniquement sur la taille de la vue, peut-importe si l'on zoome ou non.

*Version améliorée*

````css
h1 {
	font-size: clamp(1.8rem, calc(7vw + 1rem), 5rem); 
}
````

## Images responsives

Conserver un affichage propre en fonction de la dimension et de l'image :

````css
img {
	max-width: 100%;
	height: auto;
	aspect-ratio: 1 / 1;
	object-fit: cover;
}
````

## Eviter 100vh

L'unité ````100vh```` fonctionne bien sur desktop, cependant, cela devient problématique sur mobile. En effet les browser mobile, prévoient un espace en haut pour la barre de navigation, et cet espace n'est pas pris en compte pas ````vh````.

Il faut donc préférer l'unité ````dvh```` (dynamic viewport height)

Pour une couverture totale, il est même possible de fournir les deux unités. Le browser choisira celle qui est approprié 

````css
.container {
	height: 100vh;
	height: 100dvh;
}
````



## Flexbox vs Grid

https://www.youtube.com/watch?v=aEj6k-gi9-s

> **Flexbox** implique de modifier les éléments enfants pour ajuster le layout

> **Grid** se focalise sur la div parent pour  ajuster le layout

Dans quel cas utiliser un layout de type Grid ?

* si le layout d'un composant doit toujours être vertical alors utiliser **Grid** car il utilise l'affichage colonne par défaut
* layouts réguliers et homogènes (plus rigides) : affichage en colonne ou ligne, menu, grille produit parfaite etc...
* besoin d'avoir des éléments enfants qui ont tous la même taille
* pour les layout *complexes* (structure globale d'une application), il est préférable d'utiliser Grid car Flexbox ne peut pas être à la fois en mode colonnes et en mode ligne. Voir **grid-template-areas**

Dans quel cas utiliser un layout de type Flexbox ?

* si le layout d'un composant doit pouvoir passer d'un mode horizontal à vertical en fonction du form factor (changement du flex-direction) alors utiliser **Flexbox**
* liste d'éléments nécessitant un affichage de type wrap ajusté. Possible en Grid mais les items auront tous la même taille.
* nécessité d'avoir des container enfants flexibles

**Cas d'école** : Le layout avec une navbar, un content qui doit prendre toute la hauteur, puis un footer

Ici le **Grid** layout est encore le plus aproprié. Ce type de layout est généralement ennuyeux à régler avec Flexbox, alors que Grid gère ça très simplement avec

````css

body {
	display: grid;
	grid-template-rows: auto 1fr auto;
}
nav {
	background: blue;
	gap: 1em;
	display: flex;
}
footer {
	background: black;
	gap: 1em;
	display: flex;
}
````

````html
<nav></nav>
<body></body>
<footer></footer>
````
