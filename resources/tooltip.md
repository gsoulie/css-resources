[< Back to main menu](https://github.com/gsoulie/css-resources/blob/main/README.md)     

# Pure css tooltip

*html*

````html
<div class="wrapper">
  <div class="popover__content">
      <span>your tooltip message</span>
  </div>
</div>
````

*css*

````css
.popover__content {
  opacity: 0;
  visibility: hidden;
  position: absolute;
  //left: -150px;
  transform: translate(0, 10px);
  background-color: #ff6161;
  border-radius: 5px;
  padding: 0.8rem;
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.26);
  width: auto;
  cursor: pointer;
}
.popover__content:before {
  position: absolute;
  z-index: -1;
  content: "";
  right: calc(50% - 10px);
  top: -8px;
  border-style: solid;
  border-width: 0 10px 10px 10px;
  border-color: transparent transparent #ff6161 transparent;
  transition-duration: 0.3s;
  transition-property: transform;
}
.wrapper:hover .popover__content {
  z-index: 10;
  opacity: 1;
  visibility: visible;
  transform: translate(0, 50px);  // <-- à ajuster
  transition: all 0.5s cubic-bezier(0.75, -0.02, 0.2, 0.97);
}
````
