[< Back to main Menu](https://github.com/gsoulie/Mobile-App-Development)    

# Css

* [Sticky navbar](https://github.com/gsoulie/css-resources/blob/master/css-sticky-navbar.md)     
* [Collection de layout / pattern prêt à l'emploi](https://csslayout.io/) / https://codyhouse.co/nuggets     
* [Css défensif](https://defensivecss.dev/)      
* [Tooltip](https://github.com/gsoulie/css-resources/blob/main/resources/tooltip.md)      
* [Checkbox animations](https://getcssscan.com/css-checkboxes-examples)     

### Première lettre en majuscule

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
### Animation underline sur un lien

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
