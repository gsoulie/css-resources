[< Back to main Menu](https://github.com/gsoulie/css-resources/blob/master/index.md)    

# Animations

* [fade-in avec from bottom](#fade-in-avec-from-bottom)     

## Fade-in avec from bottom

<details>
        <summary>Fade-in</summary>

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

</details>

## Ouverture modale avec translation et opacité

<details>
	<summary>Transition simple</summary>
	
*Modal.scss*
````css
.Modal {
  position: fixed;
  z-index: 200;
  border: 1px solid #eee;
  box-shadow: 0 2px 2px #ccc;
  background-color: white;
  padding: 10px;
  text-align: center;
  box-sizing: border-box;
  top: 30%;
  left: 25%;
  width: 50%;
  transition: all 0.6s ease-out;	// <-- animation
}
.ModalOpen {
  opacity: 1;
  translate: 0 0;	// <-- transate Y effect
  //transform: translateY(0);
}
.ModalClosed {
  opacity: 0;
  translate: 0 100px;	// <-- transate Y effect
  //transform: translateY(100px);
}

````

</details>

<details>
	<summary>Animations css avec @keyframes</summary>

Il est possible de transformer l'exemple précédent en utilisant les ````@keyframes```` de la manière suivante 

*Modal.scss*
````css
.ModalOpen {
  animation: openModal 0.6s ease-out forwards;	// 'forwards' important sinon l'animation tournera en boucle
}
.ModalClosed {
  animation: closeModal 0.6s ease-out forwards;
}

@keyframes openModal {
  0% {
    opacity: 0;
    translate: 0 -100%;
  }
  50% {
    opacity: 1;
    translate: 0 20%;
  }
  100% {
    opacity: 1;
    translate: 0 0;
  }
}

@keyframes closeModal {
  0% {
    opacity: 1;
    translate: 0 0;
  }
  50% {
    opacity: 0.8;
    translate: 0 60%;
  }
  100% {
    opacity: 0;
    translate: 0 -200%;
  }
}
````

</details>
