[< Back to main Menu](https://github.com/gsoulie/css-resources/tree/main)     

## Utilisation de l'instruction if

Une nouvelle instruction officiellement en mode **experimental** (juil. 2025) mais déjà supportée par *chrome* et *edge* vient de voir le jour.

> [Documentation MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/if)    

Voici quelques exemples d'utilisation :

En partant du code suivant : 
````css
.box {
	width: 300px;
	height: 300px;
	background-color: red;
}
@media (width <= 1000px) {
	.box {
		background-color: blue;
	}
}
@media (width <= 600px) {
	.box {
		background-color: green;
	}
}
````

On peut désormais écrire

````css
.box {
	width: 300px;
	height: 300px;
	background-color: if(
		media(width <= 600px): green;	
		media(width <= 1000px): blue;
		else: red;
	);
}
````
> **Important** l'ordre des media queries est important, il faut placer la taille la plus petite en premier

Pour aller plus loin en utilisant une variable css pour stocker la dimension : 

````css
:root {
	--bp: if(
		media(width <= 600px): "sm";
		media(width <= 1024px): "md";
		else: "lg";		
	)
}

.box {
	width: 300px;
	height: 300px;
	background-color: if(
		style(--bp: "sm"): green;
		style(--bp: "md"): blue;
		style(--bp: "lg"): red;
		else: black;
	);
}
````

Autre exemple d'utilisation avec ````@container````

````css
:root {
	--test: "hi";
}

.box {
	width: 300px;
	height: 300px;
	background-color: if(
		style(--test: "hi"): green;
		else: red;
	);
}

@container(style(--test: "hi")) {
	.box {
		color: yellow;
	}
}
````

## Attribut attr

https://www.youtube.com/watch?v=WcNWf6edIcc&ab_channel=WebDevSimplified

````html
<div class="box" data-status="loading">
	...
</div>
````

````css

.box {
	--status: attr(data-status)

	width: 300px;
	height: 300px;
	background-color: if(
		style(--status: "loading"): green;
		style(--status: "loaded"): blue;
		style(--status: "error"): red;
		else: black;
	);
}
````

Utiliser un attribut pour fixer une couleur

````css
.box {
	background-color: attr(data-color type(<color>), red);
	width: attr(data-width px);  // l'unité peut être exprimée en em, rem, px, vm, % etc...
	height: 300px;
}
````

* ````data-color```` : nom de l'attribut dans le html
* ````type(<color>)```` : cast de la valeur récupérée. Css attend une valeur de type *<color>*, hors la valeur récupérée est une string. Cette dernière ne peut pas être utilisée en tant que telle.
* dernier paramètre : valeur fallback si l'attribut n'est pas renseigné côté html
