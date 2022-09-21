# Class 5 - Design Web Pages with CSS

## What is CSS?

* CSS (Cascading Style Sheets) - changes the appearance and presentation of the HTML content
* It's a rule-based language defined by rules that specify groups of styles that should be applied to particular elements or groups of elements on your web page

## CSS Syntax

> `h1 {color: red; font-size: 5px;}`

* **Selector** - The CSS rule that selects the HTML element, followed by curly brackets `{ }`. `h1` is the selector in the above example.
* **Properties** - Characteristic to modify, followed by a colon `:`. `color` and `font-size` are the properties in the above example.
* **Value** - (self explanatory), followed by a semi-colon `;`. `red` and `5px` are the values in the above example.

## Inserting CSS into Document

1. **External CSS** - Adding a separate "stylesheet" that contains only CSS code. Needs to be referenced in the HTML with: `<link rel="stylesheet" href="[file-name].css">`
2. **Internal CSS** - CSS code inserted into the HTML file (usually in the `<head>` section) using the `<style>` HTML element: `<style>h1 {color: maroon; margin-left: 40px;}</style>`
3. **Inline CSS** - Applies CSS code to a single HTML element within the HTML file using the `style=` attribute: `<h1 style="color:blue;text-align:center;">This is a heading</h1>`

## Cascading Order

* All the styles in a page will "cascade" into a new "virtual" style sheet by the following rules, where number one has the highest priority:
  1. Inline style (inside an HTML element)
  2. External and internal style sheets (in the `<head>` section)
  3. Browser default

## CSS Color Property

* The `color` property specifies the color of the ***text*** (not background or any other element).
* `color` can be defined a few ways:
  1. **HEX** - `color: #92a8d1;`
  2. **RGB** - `color: rgb(201, 76, 76);`
  * Sets red, green, and blue values between 0-255
  * Black would be `color: (0,0,0);`
  * White would be `color: (255,255,255);`
  3. **RGBA** - `color: rgba(201, 76, 76, 0.6);`
  * Same as RGB, but adds ***opacity*** as the last value between 0-1
  * 0 makes the text invisible
  * 1 makes the text normal
  4. **HSL** - `color: hsl(73, 50%, 75%);`
  * Sets hue (0-360), saturation (%), and lightness (%)
  * Hue of 0 is red, 120 is green, and 240 is blue
  * Saturation of 0% means a shade of gray and 100% is the full color
  * Lightness of 0% is black, and 100% is white
  5. **HSLA** - `color: hsla(73, 50%, 75%, 0.7);`
  * Same as HSL, but adds ***opacity*** as the last value between 0-1
  * 0 makes the text invisible
  * 1 makes the text normal

## Reset CSS

* The goal of a reset stylesheet is to reduce browser inconsistencies in things like default line heights, margins and font sizes of headings, etc.
* The reset styles given here are intentionally very generic.
