# Class 8 - CSS Layout

## Learn CSS - Flexbox

1. Flexbox is designed for one-dimensional content. Explain what this means.
   * It helps flow HTML elements along a single axis. For example, it would take 3 `<div>`'s and adjust the layout of those elements along the horizontal axis.
2. Explain the difference between the main axis and cross axis.
   * The main axis is the direction the elements flow, while the cross axis is perpendicular to the main axis. For example, if `flex-direction` is set to `row`, then the main axis would be the horizontal axis and the cross axis would be the vertical axis.
3. How can using certain properties of flexbox negatively impact accessibility?
   * Properties that reorder the visual display away from how things are ordered in the HTML document can negatively impact accessibility. The row-reverse and column-reverse values reorders the visual order, not the logical order. The logical order is the order that a screen reader will read out the content, and anyone navigating using the keyboard will follow. <https://web.dev/learn/css/flexboxC>

## CSS Layout - Flexbox

1. What are some advantages of using flexbox over float?
   * Floats cannot achieve the following simple layout designs:
     * Vertically centering a block of content inside its parent.
     * Making all the children of a container take up an equal amount of the available width/height, regardless of how much width/height is available.
     * Making all columns in a multiple-column layout adopt the same height even if they contain a different amount of content.
     <https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox>
2. How does this topic connect with your long term goals?
   * Knowing how to appropriately design a page's layout will help me present information in a more efficient way for a potential customer.
