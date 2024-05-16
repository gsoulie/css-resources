[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

# Présentation 

Tailwind CSS est un framework CSS utilitaire conçu pour rendre le processus de développement de sites web et d'applications web plus rapide et plus efficace. Contrairement aux frameworks traditionnels qui fournissent des composants préconstruits (comme Bootstrap ou Foundation), Tailwind CSS adopte une approche différente en offrant une série de classes utilitaires de bas niveau. Ces classes permettent aux développeurs de construire des interfaces utilisateur directement dans leur HTML, sans avoir à écrire de CSS personnalisé.

**Principales caractéristiques de Tailwind CSS**

* **Classes Utilitaires** : Tailwind CSS propose des classes utilitaires qui effectuent des tâches spécifiques comme la gestion de l'espacement, des couleurs, de la typographie, et plus encore. Par exemple, des classes comme p-4 pour le padding ou text-center pour centrer le texte permettent de styliser rapidement les éléments.

* **Personnalisation Facile** : Avec un fichier de configuration (tailwind.config.js), vous pouvez facilement personnaliser les valeurs par défaut de Tailwind CSS, telles que les couleurs, les espacements, les tailles de police, et plus encore. Cela permet de créer un design sur mesure tout en conservant la cohérence et la réutilisabilité des classes utilitaires.

* **Responsive Design** : Tailwind CSS facilite la création de designs réactifs grâce à un système de classes utilitaires spécifiques aux points de rupture (breakpoints). Par exemple, vous pouvez utiliser des classes comme md:text-lg pour appliquer des styles uniquement sur des écrans de taille moyenne ou plus.

* **Performance Optimisée** : Tailwind CSS inclut un outil de purge qui supprime automatiquement toutes les classes inutilisées de votre feuille de styles en production, réduisant ainsi la taille du fichier CSS final et améliorant les performances de votre site web.

* **Modularité et Composabilité** : Grâce à ses classes utilitaires, Tailwind CSS encourage la création de composants réutilisables et modulaires. Cela conduit à un code plus propre, plus maintenable et plus facile à comprendre.

* **Support des Plugins** : Tailwind CSS possède un écosystème riche de plugins qui permettent d'ajouter facilement des fonctionnalités supplémentaires, comme les formulaires, les animations, et les typographies avancées.

## Installation et configuration


Documentation **Next** : [https://tailwindcss.com/docs/guides/nextjs](https://tailwindcss.com/docs/guides/nextjs)    
Documentation **Angular** : [https://tailwindcss.com/docs/guides/angular](https://tailwindcss.com/docs/guides/angular)

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
/** @type {import('tailwindcss').Config} */
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
