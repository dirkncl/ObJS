ObJS
====

## A 3D Wavefront obj file viewer for HTML5 written in JavaScript ###

<a href="http://imgur.com/kT7mGoK"><img src="http://i.imgur.com/kT7mGoK.png" title="ObJS - Bolt" /></a>



### Features ###

* Object rotation with the mouse.
* Zoom control with the mousewheel.
* Choose to draw (or not) vertizes, edges or faces.
* Use mtl files for material color.
* Change colors of background, vertizes, edges, and faces during runtime.
* Change face transparency during runtime, so hidden elements are visible.
* Change zoom and rotation speed during runtime.



### How to use ###

Just include the *ObJS.js* in your project, create a ObJS object, and initalize its canvas.
```javascript
myObJS = new ObJS();
myObJS.initCanvas(canvas);
```
* *canvas* is the canvas element in witch the model will be represented. If this parameter is not specified, the script will try to use a canvas called *ObJSCanvas*.

Then you can load any obj model by calling
```javascript
myObJS.load(file);
```
* *file* is a character string with the path to the file, relative or absolute.


If you want to clear the canvas, just call
```javascript
myObJS.clear();
```
Note that the canvas is automatically cleared when a new object is loaded.



### Transformations ###

The model can be rotated and zoomed in and out with the mouse, but it can also be done programmatically.

##### Rotate the object #####
```javascript
myObJS.rotateX(-1); //Rotate along the X edge to the left
myObJS.rotateX(1);  //Rotate along the X edge to the right
myObJS.rotateY(-1); //Rotate along the Y edge to the left
myObJS.rotateY(1);  //Rotate along the Y edge to the right
```
Note that the rotation speed can be set (see *Seting rotation speed*).

##### Zoom #####
```javascript
myObJS.zoom("+"); //Zoom in
myObJS.zoom("-"); //Zoom out
```
Note that the zoom speed can be set (see *Seting zoom speed*).



### Customization ###

You can change parameters such as the elements to draw, their color, transparency, rotation speed, zoom speed... in the script, but much of them can be changed on runtime, so you can use controls.

##### Select which elements to draw #####
```javascript
myObJS.drawElement(keyword, on);
```
* *keyword* is a character string indicating witch element you want or don't want to be drawn. Possible values are
	- *'backg'*, for the background.
	- *'verts'*, for the vertizes.
	- *'edges'*, for the edges.
	- *'faces'*, for the faces.
* *on* is a Boolean value, indicating if the element is to be drawn or not.

##### Select color for elements #####
```javascript
myObJS.colorElement(keyword, color);
```
* *keyword* is a character string indicating witch element you want to colorize. Possible values are
	- *'backg'*, for the background.
	- *'verts'*, for the vertizes.
	- *'edges'*, for the edges.
	- *'faces'*, for the faces.
* *color* is a character string with the HEX codeo for the desired color, for example *'#ff0000'* for red.

##### Use materials #####

If a .mtl file is present in the same directory as the obj file, you can use the materials there to colorize the model (enabled by default). 
```javascript
myObJS.linkMaterial(true); //Use .mtl file
myObJS.linkMaterial(false); //Don't use .mtl file
```
Note that, when using .mtl files, faces with no material assigned will use the color defined by the user.

##### Select face transparency #####
```javascript
myObJS.setAlpha(percent);
```
* *percent* is an integer, between 0 and 100, indicating the level of transparency you want to apply to the faces.

##### Set rotation speed #####
```javascript
myObJS.setRotationSpeed(value);
```
* *value* is an integer, between 0 and 10. The greater it is, the greater the rotation speed.

##### Set zoom speed #####
```javascript
myObJS.setZoomSpeed(value);
```
* *value* is an integer, between 0 and 10. The greater it is, the greater the zoom speed.