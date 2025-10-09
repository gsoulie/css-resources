Ce document présente la manière de réaliser la migration de node-sass de l'ancienne syntaxe ````@import```` vers la nouvelle syntaxe ````@use````

La migration de Sass de la syntaxe ````@import```` vers ````@use```` (et ````@forward````) a été introduite pour résoudre plusieurs problèmes liés à l’ancienne approche. Voici les raisons et bénéfices principaux :

## Raisons de la migration

**Problèmes de performances**
@import charge et compile chaque fichier Sass plusieurs fois, ce qui ralentit la compilation, surtout dans les gros projets.

**Conflits de noms**
Avec @import, toutes les variables, mixins et fonctions sont fusionnées dans un espace global, ce qui peut causer des conflits (ex. : deux fichiers définissant $primary-color).

**Manque de modularité**
Impossible de contrôler précisément ce qui est importé (ex. : importer uniquement une fonction ou une variable spécifique).

## Bénéfices de @use

**Meilleures performances**
Chaque fichier est compilé une seule fois, ce qui accélère la compilation.

**Espaces de noms**
Les éléments importés sont préfixés par le nom du module, évitant les conflits.

## Ancienne syntaxe

Exemple de fichier de variables *colors.scss*
````css
$grey100: #f6f6f6;
$red100: #e2001a;
$green100: #5ca9ad;
````

*settings.scss*

````css
  @import "./colors.scss"; // import des couleurs

// spacings
$spacing--11: -11px;
$spacing--7: -7px;
$spacing-2: 2px;

// fonts
$size-sm: 0.8em;
$size-md: 1em;
````

*button.scss*

````css
@import "./colors.scss";

.red-button {
 background: $red100;
 colors: white
}
````

## Nouvelle syntaxe

La nouvelle syntaxe implique :
* Remplacer ````@import```` par ````@use````
* Donner un alias au fichier importer pour pouvoir l'utiliser

Exemple de fichier de variables *colors.scss*
````css
$grey100: #f6f6f6;
$red100: #e2001a;
$green100: #5ca9ad;
````

*settings.scss*

````css
@use "./colors.scss" as colors;
@forward "./colors.scss"; // Nécessaire pour pouvoir utiliser les variables de colors à travers le fichier settings.scss

// spacings
$spacing--11: -11px;
$spacing--7: -7px;
$spacing-2: 2px;

// fonts
$size-sm: 0.8em;
$size-md: 1em;
````

*button.scss* - Variante avece utilisation des couleurs en directe 

````css
@use "./colors.scss" as colors;
@use "./settings.scss" as settings;

.red-button {
 background: colors.$red100;
 colors: white;
 padding: settings.$spacing-md;
}
````

*button.scss* - Variante avece utilisation des couleurs via settings.scss (possible **uniquement** si settings ````@forward```` les colors

````css
@use "./settings.scss" as settings;

.red-button {
 background: settings.$red100;
 colors: white;
 padding: settings.$spacing-md;
}
````
