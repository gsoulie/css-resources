[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

# Animations

* [fade-in avec from bottom](#fade-in-avec-from-bottom)     

## Fade-in avec from bottom

````html
<div id="logo-container">
        <img
          class="anim-logo"
          width="100"
          height="60"
          src="../../../assets/images/logo.svg"
        />
</div>
````

````css
#logo-container {
  width: 100%;
  float: left;
  height: 60px;
  opacity: 0; /* Définir l'opacité à 0 pour commencer */
  animation-name: fade-in; /* Nommer l'animation */
  animation-duration: 3s; /* Durée de l'animation */
  animation-fill-mode: forwards; /* Maintenir l'élément à l'état final de l'animation */
}
/* Définir l'animation fade-in */
@keyframes fade-in {
  from {
    opacity: 0; /* Début de l'animation */
  }
  to {
    opacity: 1; /* Fin de l'animation */
  }
}
.anim-logo {
  height: 60px;
  margin-top: 100px;
  animation-name: from-bottom; /* Nommer l'animation */
  animation-duration: 1s; /* Durée de l'animation */
  animation-fill-mode: forwards; /* Maintenir l'élément à l'état final de l'animation */
}
/* Définir l'animation from-bottom */
@keyframes from-bottom {
  from {
    margin-top: 100px; /* Début de l'animation */
  }
  to {
    margin-top: 0px; /* Fin de l'animation */
  }
}
````
