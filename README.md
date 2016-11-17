##Website Performance Optimization

### Critical Rendering Path Optimization

1. Removed the render blocking of JavaScript by using the async attribute to the script tag
2. Removed the render blocking of the CSS files (google fonts and print)by using the media attribute in the link tag
3. Removed the render blocking of the CSS file (style.css) by inlining it
4. Optimized the images using ImageOptim

### Frame Rate Optimization

**Changes made on `views/js/main.js` file:**

* Moved changedSliderLabel outsize of resizePizzas function

function changeSliderLabel(size) {
  var pizzaInnerHTML = document.getElementById("pizzaSize").innerHTML;
    switch (size) {
        case "1":
            pizzaInnerHTML = "Small";
            return;
        case "2":
            pizzaInnerHTML = "Medium";
            return;
        case "3":
            pizzaInnerHTML = "Large";
            return;
    }
}

* Moved DOM calculation and set to variable scrollItem outside of for loop
* Moved DOM query outside of function and set assigned to variable
* Use style.transform with translateX instead of style.left 

unction updatePositions() {
  frame++;
  window.performance.mark("mark_start_frame");
  var scrollItem = document.body.scrollTop / 1250;
  var items = document.getElementsByClassName('mover');
  for (var i = 0; i < items.length; i++) {
  var phase = Math.sin(scrollItem + (i % 5));
  items[i].style.transform = "translateX(" + (items[i].basicLeft - 900 + 100 * phase) + "px)";
  }


Now, `views/pizza.html` renders with a consistent frame-rate at 60fps when scrolling.

### Computational Efficiency


###Minification of CSS and JS, and Image Optimization

**How to run Grunt on this project?**

- Download the project assets and make sure `src` folder, `Gruntfile.js` and `package.json` files are under one folder.
- Open your terminal window.
- Ensure that you have the _npm_ package manager or _Node.js_ installed and up-to-date by running `npm update -g npm`.
- Install Grunt's command line interface (CLI) by running `npm install -g grunt-cli`.
- Since, `Gruntfile.js` and `package.json` are already configured for the project with the needed tasks and Grunt plugins --> you are ready to run Grunt:
* Go to the project's root directory in your terminal.
* Install project dependencies by running `npm install`.
* Run Grunt with `grunt`.
