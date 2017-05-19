## Website Performance Optimization Portfolio Project

The objective of [this project](https://github.com/udacity/frontend-nanodegree-mobile-portfolio) was to optimize the Critical Rendering Path and make it run at 60 fps.

### How to Run

Download or clone the repository and run `index.html`.
Or see it live [here](https://ericp3reira.github.io/udacity-optimized-portfolio/).

### Changes made

#### Part 1: Optimize PageSpeed Insights score for index.html

- All code in style.css are in the head tag, excluding a request;
- Media queries (print and portrait) are downloaded only if required;
- Scripts are at the bottom of body;
- Scripts that doesn't need to be loaded at first page load are asynchronous;
- Images are resized and compacted;
- Google fonts load after the html, not blocking the rendering.

[PageSpeed](https://developers.google.com/speed/pagespeed/insights/?url=https%3A%2F%2Fericp3reira.github.io%2Fudacity-optimized-portfolio%2F&tab=mobile):
Mobile: 94/100,
Desktop: 92/100

#### Part 2: Optimize Frames per Second in pizza.html

- `resizePizzas()` was causing layout thrashing by calling and changing the width of `.randomPizzaContainer` several times during the `for` loop. So the following steps were needed:

  - `changeSliderLabel()` was incorporated into `sizeSwitcher()`, using only one `switch` loop;
  - `determineDx()` was unnecessary and deleted;
  - `document.querySelectorAll(".randomPizzaContainer")` was transferred to a variable outside the `for` loop, being called only once;
  - `newWidth` is defined with `sizeSwitcher()` and doesn't need calculations;
  - `changePizzaSizes()` was unnecessary and deleted.


- `updatePositions` was also causing low fps. Defining `document.body.scrollTop` to a variable outside the `for` loop solved it.


#### Part 3: To-Do

- Minify HTML, CSS and JS files;
- Better image optimization;
- Refactor CSS;
- CSS pizza animation (maybe).
