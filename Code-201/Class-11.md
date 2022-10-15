# Class 11 - Audio, Video, Images

## Video and Audio Content

1. Explain how the ability to use video and audio on the web has evolved since the early 2000s.
   * The first influx of online videos and audio were made possible by proprietary plugin-based technologies like Flash and Silverlight. Both of these had security and accessibility issues, and are now obsolete, in favor of native HTML solutions `<video>` and `<audio>` elements and the availability of JavaScript APIs for controlling them. <https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content>
2. Describe the use of the `src` and `controls` attributes in the `<video>` element.
   * `src` - In the same way as for the `<img>` element, the src (source) attribute contains a path to the video you want to embed.
   * `controls` - Users must be able to control video and audio playback. You must either use the controls attribute to include the browser's own control interface, or build your interface using the appropriate JavaScript API.
   <https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content>
3. Why is it important to have ***fallback content*** inside the `<video>` element?
   * It will be displayed if the browser accessing the page doesn't support the `<video>` element, allowing us to provide a fallback for older browsers. This can be anything you like; in this case, we've provided a direct link to the video file, so the user can at least access it some way regardless of what browser they are using.
   <https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content>
4. Write a very short story where `<audio>` and `<video>` are characters.
   * `<audio>` and `<video>` are best friends and provide pure joy to everyone they meet.

## CSS Grid

1. How does Grid layout differ from Flex?
   * Grid is tw-dimensional while Flex is only one-dimensional and doesn't easily create a grid system in CSS.
2. Grid container, grid item, and grid line are a few important terms to understand when using Grid. Please describe these terms in a few sentences.
   * Grid Container - The element on which `display: grid` is applied. It’s the direct parent of all the grid items. In this example container is the grid container.
   * Grid Item - The children (i.e. direct descendants) of the grid container. Here the `item` elements are grid items, but `sub-item` isn’t.
   * Grid Line - The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.
   <https://css-tricks.com/snippets/css/complete-guide-grid/>

## Responsive Images

1. Besides making a site visually appealing across different screen sizes, why should developers make images responsive?
   * It increases the performance on different devices.
2. Define the following `<img>` attributes `srcset` and `sizes`. Write an example of how they are used.
   * `srcset` - defines the set of images we will allow the browser to choose between, and what size each image is. Each set of image information is separated from the previous one by a comma.
   * `sizes` - defines a set of media conditions (e.g. screen widths) and indicates what image size would be best to choose, when certain media conditions are true.
   <https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images>

   ```
   <img srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"
   sizes="(max-width: 600px) 480px,
         800px;
   src="elva-fairy-800w.jpg"
   alt="Elva dressed as a fairy" />

3. How is `srcset` more helpful for responsive images than CSS or JavaScript?
   * Instead of modifying a single source, multiple sources can be chosen depending on the screen size conditions.
