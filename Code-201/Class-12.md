# Class 12 - Canvas and Chart.js

## JavaScript Canvas

1. What does the `<canvas>` allow a developer to achieve?
   * To draw two-dimensional graphics using JavaScript.
2. What is the importance of the closing `</canvas>` tag?
   * Any content between the opening and closing tags is fallback content that will display only if the browser doesn’t support the `<canvas>` element. <https://www.javascripttutorial.net/web-apis/javascript-canvas/>
3. Explain what the `getContext()` method does.
   * It returns a render context object. The type of context is the single argument. Use the "2d" to get a 2D rendering context object, which is an instance of the CanvasRenderingContext2D interface. The 2D rendering context allows you to draw shapes, text, images, and other objects.
   <https://www.javascripttutorial.net/web-apis/javascript-canvas/>

## Chart.js

1. What is Chart.js and how it can be brought into your project?
   * It's a free JavaScript library for making HTML-based charts using the `<canvas>` tag.
2. List 3 different Chart types you can create using Chart.js.
   * Line Chart - `type: 'line';`
   * Bar Chart - `type: 'bar';`
   * Pie Chart - `type: 'pie';`

## Create Animated Charts with Chart.js

1. What are some advantages to displaying data via a chart over a table?
   * Charts are far better for displaying data visually than tables. <https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/>
2. How could Chart.js aid your previously created applications visually?
   * The table we made for Salmon Cookies could better be represented with a chart to show number of cookies sold per hour or which locations sell more cookies without having to compare values in the table.
