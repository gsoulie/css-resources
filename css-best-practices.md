[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

* [Sélection des sous-classes](#sélection-des-sous-classes)    

# Organisation des feuilles de style css

Voici une bonne pratique d'organisation des fichiers de style css. L'idée est de séparer les styles par domaines et de les centraliser dans un fichier *settings.scss* qui aura pour rôle de créer des variables css permettant d'exposer les différents styles dans toute l'application.

Cette architecture est la plus optimisée car elle évite d'importer des fichier css dans les composants. Celà allège ainsi les pages.

## Organisation des fichiers de styles

*_colors.scss*
````css
$primary: #007bff;
$secondary: #6c757d;
$success: #28a745;
$danger: #dc3545;
$white: #fff;
$black: #000;
````

*_spacing.scss*
````css
$spacer: 1rem;
$spacer-sm: $spacer * 0.5;
$spacer-lg: $spacer * 1.5;
````

*_typography.scss*
````css
$font-family-base: sans-serif;
$font-size-base: 1rem;
$font-weight-bold: bold;
````

## Centralisation des différents fichiers

Créer ensuite un fichier qui va centraliser les styles et créer des variables css accessibles partout

*settings.scss*
````css
@use "./colors";
@use "./spacing";
@use "./typography";

:root {
  // Couleurs
  --primary: #{colors.$primary};
  --secondary: #{colors.$secondary};
  --success: #{colors.$success};
  --danger: #{colors.$danger};
    --white: #{colors.$white};
    --black: #{colors.$black};

  // Espacements
  --spacer: #{spacing.$spacer};
  --spacer-sm: #{spacing.$spacer-sm};
  --spacer-lg: #{spacing.$spacer-lg};

  // Typographie
  --font-family-base: #{typography.$font-family-base};
  --font-size-base: #{typography.$font-size-base};
  --font-weight-bold: #{typography.$font-weight-bold};
}
````

## Utilisation dans les composants Angular :

Dans les fichiers SCSS de vos composants, vous utilisez les variables CSS :

````css
.my-element {
  background-color: var(--primary);
  padding: var(--spacer);
  margin-bottom: var(--spacer-lg);
  font-family: var(--font-family-base);
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-bold);
  color: var(--white);
}

.another-element {
    background-color: var(--black);
    color: var(--danger);
}
````

## Sélection des sous-classes

Bonne pratiques pour sélectionner les classes css 

*html*

````html
<div class="my-loader">
  <div class="my-loader__wrapper">
    <div class="my-loader__logo">
    ...
    <div class="my-loader__title">
...
````

````css
.my-loader {
  /* Styles pour .my-loader */
  &__wrapper {
    /* Styles pour .my-loader__wrapper */
  }

  &__logo {
    /* Styles pour .my-loader__logo */
  }

  &__title {
    /* Styles pour .my-loader__title */
  }
}
````
