[< Back to main Menu](https://github.com/gsoulie/Mobile-App-Development)    

# Css

* [Tailwind CSS - NextJS / Angular](https://github.com/gsoulie/css-resources/blob/main/css-tailwind.md)
* [Bonnes pratiques](https://github.com/gsoulie/css-resources/blob/main/css-best-practices.md)     
* [Convention BEM](#convention-de-nommage-BEM)
* [Première lettre en majuscule](#première-lettre-en-majuscule)     
* [Sticky navbar](https://github.com/gsoulie/css-resources/blob/master/css-sticky-navbar.md)     
* [Collection de layout / pattern prêt à l'emploi](https://csslayout.io/) / https://codyhouse.co/nuggets     
* [Css défensif](https://defensivecss.dev/)      
* [Tooltip](https://github.com/gsoulie/css-resources/blob/main/resources/tooltip.md)      
* [Checkbox animations](https://getcssscan.com/css-checkboxes-examples)     
* [Créer des formes avec clip-path](#créer-des-formes-avec-clip-path)       
* [Animations](https://github.com/gsoulie/css-resources/blob/main/css-animation.md)     
* [Css doodle](https://css-doodle.com/)
* [Eviter le redimenssionnement d'une div de taille fixe avec application d'un padding](#eviter-le-redimenssionnement-dune-div-de-taille-fixe-avec-application-dun-padding)
* [Désactiver le style hover sur un élément disabled](#désactiver-le-style-hover-sur-un-élément-disabled)
* [Header qui disparaît lors du scroll](#header-qui-disparaît-lors-du-scroll)
* [Inifinite image shadow](https://codepen.io/t_afif/pen/XWoNdGK)
* [Gérer les états d'un bouton avec color-mix](#gérer-les-états-d-un-bouton-avec-color-mix)
* [griser une image ou un logo](#griser-une-image-ou-un-logo)
* [Ajouter un effet de blur](#ajouter-un-effet-de-blur)     

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
````

## Eviter le redimenssionnement d'une div de taille fixe avec application d'un padding

<details>
  <summary>comprendre l'attribut box-sizing</summary>

Par défaut, chaque paramètre de *box-sizing* d'élément est défini sur ````content-box````. Ce qui signifie que si vous définissez la largeur d'un élément sur **200px**, puis ajoutez un padding de **20px** aux deux extrémités horizontales, cela entraînerait une largeur totale de **240px** pour cet élément.

pour résoudre ce problème, il vous suffit de mettre à jour le paramètre ````box-sizing````

````css
* {
     box-sizing : border-box
  }
````

Cela indique au navigateur de prendre en compte toute bordure et tout remplissage dans les valeurs que vous spécifiez pour la largeur et la hauteur d'un élément.

Ainsi, pour un élément défini sur border-box avec une largeur de 200 px et un remplissage de 20 px des deux côtés, sa largeur totale resterait toujours de 200 px (160 px comme zone de contenu et 40 px comme remplissage).

</details>

## Désactiver le style hover sur un élément disabled

<details>
  <summary></summary>

````
.btn-std {
  height: 47px;
  padding: 13px 30px;
  background-color: transparent;
  border: none;
  border-radius: 6px;
  font-size: 14px;
  line-height: 21px;
  transition: 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;


  &:disabled {
    background-color: var(--color-disabled-button);
    pointer-events: none;
  }
}

.fill-dark-blue {
  background-color: var(--color-dark-blue);
  color: white;
  fill: white;

  &:hover:enabled {
    background-color: rgba(#014093, 0.7);
  }
}

<button class="btn-std fill-dark-blue">Bouton</button>
<button class="btn-std fill-dark-blue" disabled>Bouton</button>
````
</details>

## Header qui disparaît lors du scroll

<details>
  <summary>Exemple sous React</summary>


````typescript
export const RouteLayout = () => {
  const [showHeader, setShowHeader] = useState(true);

  useEffect(() => {
    let prevScrollPos = window.pageYOffset;

    const handleScroll = () => {
      const currentScrollPos = window.pageYOffset;
      const shouldShowHeader =
        currentScrollPos < prevScrollPos || currentScrollPos <= 200; // currentScrollPos === 0 ajuster la variable pour le seuil de déclenchement

      setShowHeader(shouldShowHeader);
      prevScrollPos = currentScrollPos;
    };

    window.addEventListener("scroll", handleScroll);

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  }, []);

  return (
    <>
      <div className={`header ${showHeader ? "" : "hidden"}`}>
        <HeaderWrapper />
      </div>
	</>
  )
}
````

*HeaderWrapper.tsx*

````typescript
import './HeaderWrapper.scss'
import { MainMenu } from '../mainMenu/MainMenu';

export const HeaderWrapper = () => {


  return (
    <>      
      <div className="header">
        <Toolbar />
        <Navigation handleClick={showMenu} />
      </div>
    </>
  );
}
````

*HeaderWrapper.scss*

````css
.header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;  
  position: fixed;
  top: 0;
  left: 0;
  transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
  transform: translateY(0);
  opacity: 1;
}
.header.hidden {
  transform: translateY(-100%);
  opacity: 0;
}
@media
(prefers-reduced-motion: no-preference) {
  html {
    scroll-behavior: smooth;
  }
}
````
</details>

## Gérer les états d'un bouton avec color mix

Css introduit la fonctionnalité *mix* qui permet de fusionner des couleurs, ceci peut-être utiles pour faciliter la gestion des styles dans les différents états (hover, active etc...)

<details>
	<summary>Implémentation color mix</summary>

````css
:root {
  --primary: #126df7;
}

button {
  transition: all .3s;
  padding: 1rem 2rem;
  border: none;
  border-radius: 0.75rem;
  cursor: pointer;

  color: var(--primary);
  background: color-mix(in lch, var(--primary) var(--mix, 15%), transparent);
  
  &:hover {
    --mix: 25%;
  }
  
  &:active {
    --mix: 35%;
  }
}
````
 
</details>

## griser une image ou un logo

<details>
	<summary></summary>


````css
element.style {
	filter: saturate(200%) grayscale(1);
}
````
 
</details>

## Ajouter un effet de blur

<details>


````css
.container:after {
	content: "";
	width: 100%;
	height: 100%;
	top: 0;
	position: absolute;
	// ---> blur
	background: inherit;
	filter: blur(20px);
	z-index: -1;
}
````
</details>

