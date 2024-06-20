[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

* [Composant Bouton React générique avec styles tailwind](https://github.com/gsoulie/css-resources/tree/main/css-react-compo)     

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

Documentation **Next** : [https://tailwindcss.com/docs/guides/nextjs](https://tailwindcss.com/docs/guides/nextjs)    
Documentation **Angular** : [https://tailwindcss.com/docs/guides/angular](https://tailwindcss.com/docs/guides/angular)    
Bibliothèque d'éléments : [https://tailwindui.com/components#product-application-ui](https://tailwindui.com/components#product-application-ui)    

*Installation dans un projet Angular / Next / React*
```
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

_(**NextJS**) tailwind.config.js_

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

_(**Angular**) tailwind.config.js_

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

#### Exemple de surcharge

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
