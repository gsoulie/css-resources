[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

* [Tailwind css color generator](https://uicolors.app/create)    
* [Composant Bouton React générique avec styles tailwind](https://github.com/gsoulie/css-resources/tree/main/css-react-compo)     
* [Bonnes pratiques (WIP)](#bonnes-pratiques)
* [Gestion dark et light theme](#gestion-dark-et-light-theme)     

## Bibliothèques de composant basées sur Tailwind	
* [Flowbite](https://flowbite.com/docs/components/accordion/)
* [Merakiui](https://merakiui.com/components)
* [Tailblocks](https://tailblocks.cc/)
* [HyperUI](https://www.hyperui.dev/)    
* [Daisy UI](https://daisyui.com/docs/intro/)
* [preline](https://preline.co/docs/modal.html)     
  
## Présentation 

Tailwind CSS est un framework CSS utilitaire conçu pour rendre le processus de développement de sites web et d'applications web plus rapide et plus efficace. Contrairement aux frameworks traditionnels qui fournissent des composants préconstruits (comme Bootstrap ou Foundation), Tailwind CSS adopte une approche différente en offrant une série de classes utilitaires de bas niveau. Ces classes permettent aux développeurs de construire des interfaces utilisateur directement dans leur HTML, sans avoir à écrire de CSS personnalisé.

**Principales caractéristiques de Tailwind CSS**

* **Classes Utilitaires** : Tailwind CSS propose des classes utilitaires qui effectuent des tâches spécifiques comme la gestion de l'espacement, des couleurs, de la typographie, et plus encore. Par exemple, des classes comme p-4 pour le padding ou text-center pour centrer le texte permettent de styliser rapidement les éléments.

* **Personnalisation Facile** : Avec un fichier de configuration (tailwind.config.js), vous pouvez facilement personnaliser les valeurs par défaut de Tailwind CSS, telles que les couleurs, les espacements, les tailles de police, et plus encore. Cela permet de créer un design sur mesure tout en conservant la cohérence et la réutilisabilité des classes utilitaires.

* **Responsive Design** : Tailwind CSS facilite la création de designs réactifs grâce à un système de classes utilitaires spécifiques aux points de rupture (breakpoints). Par exemple, vous pouvez utiliser des classes comme md:text-lg pour appliquer des styles uniquement sur des écrans de taille moyenne ou plus.

* **Performance Optimisée** : Tailwind CSS inclut un outil de purge qui supprime automatiquement toutes les classes inutilisées de votre feuille de styles en production, réduisant ainsi la taille du fichier CSS final et améliorant les performances de votre site web.

* **Modularité et Composabilité** : Grâce à ses classes utilitaires, Tailwind CSS encourage la création de composants réutilisables et modulaires. Cela conduit à un code plus propre, plus maintenable et plus facile à comprendre.

* **Support des Plugins** : Tailwind CSS possède un écosystème riche de plugins qui permettent d'ajouter facilement des fonctionnalités supplémentaires, comme les formulaires, les animations, et les typographies avancées.

## Installation et configuration

Exemple de layout table : [https://flowbite.com/docs/components/tables/](https://flowbite.com/docs/components/tables/)     
Header de table : [https://flowbite.com/blocks/application/table-headers/](https://flowbite.com/blocks/application/table-headers/)    
Footer de table : [https://flowbite.com/blocks/application/table-footers/](https://flowbite.com/blocks/application/table-footers/)    

Documentation **Next** : [https://tailwindcss.com/docs/guides/nextjs](https://tailwindcss.com/docs/guides/nextjs)    
Documentation **Angular** : [https://tailwindcss.com/docs/guides/angular](https://tailwindcss.com/docs/guides/angular)    
Bibliothèque d'éléments : [https://tailwindui.com/components#product-application-ui](https://tailwindui.com/components#product-application-ui)    


## Installation et configuration

Documentation **Next** : [https://tailwindcss.com/docs/guides/nextjs](https://tailwindcss.com/docs/guides/nextjs)    
Documentation **Angular** : [https://tailwindcss.com/docs/guides/angular](https://tailwindcss.com/docs/guides/angular)    
Bibliothèque d'éléments : [https://tailwindui.com/components#product-application-ui](https://tailwindui.com/components#product-application-ui)    

### Angular
*Installation Angular*
````
npm install tailwindcss @tailwindcss/postcss postcss --force
````
*Créer un fichier **.postcssrc.json** à la racine du projet*

````javascript
{
  "plugins": {
    "@tailwindcss/postcss": {}
  }
}
````

*Importer Tailwind dans la feuille de style globale styles.css*

````css
@import "tailwindcss";
````

### React / Next
*Installation dans un projet Angular / Next / React*
```
// v4
npm install tailwindcss @tailwindcss/postcss postcss

// v3
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

*Créer un fichier **postcss.config.mjs** (v4)*

````javascript
const config = {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};
export default config;
````

_(**NextJS**) tailwind.config.js (tailwind v3)_

<details>
  <summary>Code</summary>

```
module.exports = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",

    // Or if using `src` directory:
    "./src/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```  
</details>


_(**Angular**) tailwind.config.js (tailwind v3)_
<details>
  <summary>Code</summary>

```
module.exports = {
  content: [
    "./src/**/*.{html,ts}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```  
</details>

_global.scss (**NextJS**) ou styles.scss (**Angular**)_

```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

## Utilisation

Son utilisation est très simple, il suffit de renseigner les classes css fournies (voir documentation) sur les éléments html :

````html
<div class="p-4 rounded-md text-lg flex items-center w-48">
  Hello world
</div>
````

* ````p-4```` : padding: 1rem;
* ````rounded-md```` : border-radius: 0.375rem;
* ````flex```` : display: flex
* ````items-center```` : align-items: center;
* ````w-48```` : width de 192px


## Personnalisation des styles

De base, Tailwind CSS fourni une très grande liste de classes css (voir documentation), cependant, il est possible de toutes les surcharger ou d'en créer de nouvelles pour les besoins spécifiques d'un projet.

### Personnalisation tailwind v4

Tout se fait depuis le fichier *styles.css* ou *global.css*

````css
/* You can add global styles to this file, and also import other style files */
@import "tailwindcss";

@theme {
    --color-blue100: #9cc1ff;
    --color-blue200: #1D6DF5;   
    --color-blue250: #195DD0;
    --color-blue300: #014095;
    --color-grey50: #efefef;
    --color-grey100: #ececf5;
    --color-grey150: #c2c3c7;
    --color-grey200: #74758c;
    --color-grey300: #353643;
    --color-grey400: #2e2c3633;
    --color-red100: #c65146;
    --color-red600: #C65146;
    --color-red700: #A43B31;
    --color-green50: #F4F9F5;
    --color-green100: #4f8258;
    --color-customBro: #014095;

    /* spacings */
    --spacing-3xs: 5px;
    --spacing-2xs: 8px;
    --spacing-xs: 10px;
    --spacing-sm: 15px;
    --spacing-md: 20px;
    --spacing-lg: 25px;
    --spacing-xl: 30px;
    --spacing-xxl: 60px;
    --spacing-3xl: 150px;

    /* border radius */
    --radius-sm: 3px;
    --radius-md: 6px;
    --radius-lg: 9px;
    --radius-xl: 99px;

    /* font size */
    --font-size-3xs: 0.5rem;
    --font-size-xxs: 0.75rem;
    --font-size-xs: 0.8125rem;
    --font-size-sm: 0.875rem;
    --font-size-md: 1rem;
    --font-size-lg: 1.125rem;
    --font-size-xl: 1.375rem;
    --font-size-xxl: 1.625rem;
    --font-size-3xl: 1.875rem;
    --font-size-4xl: 2.5rem;
}   
````

> Consulter la liste des mots clé préfixe des variables : [https://tailwindcss.com/docs/theme#theme-variable-namespaces](https://tailwindcss.com/docs/theme#theme-variable-namespaces)

*Utilisation*

````html
<h1 class="text-3xl font-bold underline text-green100">Hello World</h1>
<h1 class="text-3xl font-bold underline text-blue300">Hello World</h1>

<div>
    <div class="bg-green100 w-50 h-50 m-3xl rounded-sm"></div>
    <div class="bg-blue200 w-50 h-50 rounded-xl"></div>
</div>
````

### Personnalisation tailwind v3

*tailwind.config.js*
````javascript
module.exports = {
  content: [
    // ...
  ],
  theme: {
    extend: {
      colors: {
        "green100": "#50d71e",
      },
      spacing: {
        5: "5px", // syntaxe avec nombre
        10: "10px",
        xss: "5px", // syntaxe avec mot clé
        xs: "10px",
        sm: "15px",
        md: "20px",
        lg: "25px",
        xl: "30px",
        xxl: "60px",
      },
      padding: {
        xss: "5px",
        xs: "10px",
      },
      borderRadius: {
        sm: "3px",
        md: "6px",
        lg: "9px",
      },
      fontSize: {
        xxs: "12px",
        xs: "13px",
        sm: "14px",
        md: "16px",
        lg: "18px",
        xl: "22px",
        xxl: "30px",
      },
    },
  },
  plugins: [],
};
````

#### Exemple d'utilisation des classes surchargées

*NextJS*
````html
<div className="p-xs bg-green100 m-md rounded-md text-lg">Box</div>
````

*Angular*
````html
<div class="p-xs bg-green100 m-md rounded-md text-lg">Box</div>
````

## Création de classes spécifiques

Dans certain cas, il se peut qu'une combinaison de styles soit dupliquée dans plusieurs composants / pages de l'application.

Dans **l'idéal**, si une combinaison de styles doit être réutilisée (comme on le fait traditionnellement en créant une classe css que l'on va réutiliser ailleurs), il est **conseillé de créer des composants génériques** qui vont implémenter les styles comme vu précédemment.

Il est toutefois possible de créer des classes css s'appuyant sur les classes css de tailwind via l'utilisation de la directive  ````@apply````, mais celà n'est pas forcément conseillé.

> Commencer à utiliser ````@apply```` pour tout, revient finalement à écrire du CSS et donc perdre tous les avantages de flux de travail et de maintenabilité que Tailwind nous offre

* Devoir trouver un nouveau nom de classe css qui ne soit pas déjà utilisé
* Devoir naviguer dans plusieurs fichiers css pour modifier des styles
* La modification d'un style ne va-t'il pas avoir un effet de bord négatif ailleurs dans l'application

> ````@apply```` doit donc être utilisé pour des éléments très petits et hautement réutilisables comme les boutons et les contrôles de formulaire — et même dans ce cas seulement si vous n'utilisez pas un framework comme React où un composant serait un meilleur choix.

### @apply

**1** - Créer un répertoire ````.vscode```` à la racine du projet      
**2** - Dans le répertoire ````.vscode````, créer un fichier **settings.json** contenant le code suivant permettant de désactiver le warning *unknownAtRules*

<details>
  <summary>settings.json</summary>

````json
{
  "scss.lint.unknownAtRules": "ignore"
}
````
</details>

**3** -  Dans le répertoire ````.vscode````, créer un fichier **tailwind.json**

<details>
  <summary>tailwind.json</summary>

````json
{
  "version": 1.1,
  "atDirectives": [
    {
      "name": "@tailwind",
      "description": "Use the `@tailwind` directive to insert Tailwind's `base`, `components`, `utilities` and `screens` styles into your CSS.",
      "references": [
        {
          "name": "Tailwind Documentation",
          "url": "https://tailwindcss.com/docs/functions-and-directives#tailwind"
        }
      ]
    },
    {
      "name": "@apply",
      "description": "Use the `@apply` directive to inline any existing utility classes into your own custom CSS. This is useful when you find a common utility pattern in your HTML that you’d like to extract to a new component.",
      "references": [
        {
          "name": "Tailwind Documentation",
          "url": "https://tailwindcss.com/docs/functions-and-directives#apply"
        }
      ]
    },
    {
      "name": "@responsive",
      "description": "You can generate responsive variants of your own classes by wrapping their definitions in the `@responsive` directive:\n```css\n@responsive {\n  .alert {\n    background-color: #E53E3E;\n  }\n}\n```\n",
      "references": [
        {
          "name": "Tailwind Documentation",
          "url": "https://tailwindcss.com/docs/functions-and-directives#responsive"
        }
      ]
    },
    {
      "name": "@screen",
      "description": "The `@screen` directive allows you to create media queries that reference your breakpoints by **name** instead of duplicating their values in your own CSS:\n```css\n@screen sm {\n  /* ... */\n}\n```\n…gets transformed into this:\n```css\n@media (min-width: 640px) {\n  /* ... */\n}\n```\n",
      "references": [
        {
          "name": "Tailwind Documentation",
          "url": "https://tailwindcss.com/docs/functions-and-directives#screen"
        }
      ]
    },
    {
      "name": "@variants",
      "description": "Generate `hover`, `focus`, `active` and other **variants** of your own utilities by wrapping their definitions in the `@variants` directive:\n```css\n@variants hover, focus {\n   .btn-brand {\n    background-color: #3182CE;\n  }\n}\n```\n",
      "references": [
        {
          "name": "Tailwind Documentation",
          "url": "https://tailwindcss.com/docs/functions-and-directives#variants"
        }
      ]
    }
  ]
}
````  
</details>

**4** - Déclaration de la classe avec ````@apply````

<details>
  <summary>global.scss / styles.scss</summary>

````scss
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";

@layer base {
  h1 {
    @apply text-2xl;
  }
  h2 {
    @apply text-xl;
  }
}

@layer components {
  .btn-blue {
    @apply bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded;
  }
}

@layer utilities {
  .filter-none {
    filter: none;
  }
  .filter-grayscale {
    filter: grayscale(100%);
  }
}
````

Utilisation

````html
<button class="btn-blue">Hello</button>
````
  
</details>

*Angular*
````html
<div class="p-xs bg-green100 m-md rounded-md text-lg">Box</div>
````

## Bonnes pratiques

<details>
  <summary></summary>

- https://evilmartians.com/chronicles/5-best-practices-for-preventing-chaos-in-tailwind-css
- https://github.com/tailwindlabs/prettier-plugin-tailwindcss
- https://www.uxpin.com/studio/blog/tailwind-best-practices/

* Utiliser le fichier tailwind.config.js pour définir les tokens (variables) définis par les graphistes 

````typescript
module.exports = {
  theme: {
    colors: {
      primary: 'oklch(75% 0.18 154)',
      secondary: 'oklch(40% 0.23 283)',
      error: 'oklch(54% 0.22 29)'
    },
    spacing: {
      'sm': '4px',
      'md': '8px',
      'lg': '12px'
    },
    screens: {
      'sm': '640px',
      'md': '768px'
    },
  },
  //...
}

<button class="bg-primary">Standard button</button>
<div class="bg-primary">First tab</div>
````

* utiliser purge CSS

Leverage Tailwind’s PurgeCSS
One of the most common concerns with Tailwind is the potential for bloat due to the large number of utility classes. However, by configuring PurgeCSS, you can automatically remove unused CSS, reducing the final file size and improving performance. Tailwind makes it easy to integrate PurgeCSS into your build process:

````typescript
module.exports = {
  purge: ['./src/**/*.html', './src/**/*.js'],

  // other configurations...
};
````

By specifying the files where your classes are used, PurgeCSS will strip out any unused styles, ensuring your CSS is as lean as possible.* éviter de définir les valeurs à la volée : ````p-[123px] mb-[11px] gap-[3px] bg-[#eeccff]````

* vision mobile first

* avoir une approche composant : créer des composants génériques définissant les classes tailwindcss afin de centraliser les styles
 ex :

````
	<!-- Reusable button with a long list of Tailwind classes: -->
	<button class="bg-yellow-700 border-2 font-semibold border border-gray-300 text-green p-4 rounded">
	Custom Button
	</button>

	<!-- Instead of repeating this structure over and over again, create a reusable component: -->
	<CustomButton>Custom Button</CustomButton>
````
	
* éviter autant que possible l'utilisation de @apply (augmente la taille du bundle css). Cela retire l'intérêt de tailwind (qui évite le casse tête des classes css).
réserver cet usage pour des cas très ponctuels ou spécifiques

* Essayer d'adopter un ordonnancement logique dans le listing des classes. Ou du moins grouper à la suite
toutes les classes concernant le même domaine (font spacing display...) Keep class ordering
	- le plugin prettier https://github.com/tailwindlabs/prettier-plugin-tailwindcss permet de gérer ça automatiquement

  
</details>

## Gestion dark et light theme

Pour gérer facilement un dark / light theme, il est nécessaire de suivre les étapes suivantes :

**1 - configuration du tailwind.config.js**

````typescript
module.exports = {
    content: ["./src/**/*.{html,ts}"],
    theme: {
        extend: {
            
        },
    },
    plugins: [],
    darkMode: 'class',	// <--- rajouter cette propriété
};
````

**2 - configuration styles.css**

````css
@import "tailwindcss";

@custom-variant dark (&:where(.dark, .dark *));	// <--- rajouter cet import, ce n'est pas grave si VSCode indique un warning dessus (voir extension tailwind css intellisence)
````

**3 - création d'un service theme.ts**

<details>
	<summary>code du service</summary>
	
````typescript
import { Injectable, signal } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class ThemeService {
  private readonly darkMode = signal<boolean>(true);

  isDarkMode() {
    return this.darkMode();
  }

  toggleTheme() {
    const isDark = !this.darkMode();
    this.darkMode.set(isDark);
    
    const html = document.documentElement;
    if (isDark) {
      html.classList.add('dark');
    } else {
      html.classList.remove('dark');
    }
  }

  constructor() {
    // Initialize theme based on system preference
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
    this.darkMode.set(prefersDark);
  }
}
````
</details>

**4 - création d'un composant theme-toggle button**

Ajouter ce composant dans le header de l'application ou dans un menu quelconque

<details>
	<summary>code du composant Angular</summary>

````typescript
import { Component, inject } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ThemeService } from '../../../services/theme';


@Component({
  selector: 'app-theme-toggle',
  standalone: true,
  imports: [CommonModule],
  template: `
    <button
      (click)="themeService.toggleTheme()"
      class="cursor-pointer rounded-lg p-2 bg-gray-100 dark:bg-transparent hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-gray-200 dark:focus:ring-gray-700"
      aria-label="Toggle dark mode"
    >
      <!-- Sun icon -->
      @if(themeService.isDarkMode()) {

          <svg
            class="w-5 h-5"
            fill="currentColor"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"
            />
          </svg>
      } @else {
      <!-- Moon icon -->
      <svg
        class="w-5 h-5"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" />
      </svg>
    }
    </button>
  `
})
export class ThemeToggle {
  themeService = inject(ThemeService);
}
````
 
</details>

**5 - Adapter tous les composants**

Il suffit ensuite dans tous les composants, de spécifier les classes css de base et de les étendre avec leur version ````dark:````

*user.html*

````html
<div class="bg-slate-200 dark:bg-slate-900 text-black dark:text-slate-200 hover:bg-slate-400 dark:hover:bg-slate-100">
</div>
````
