# Class 4 - Structure Web Pages with HTML

## Wireframes

* Allows designers to define and plan the information hierarchy of the website design
* Plain black & white diagram before building with code
* Can be drawn by hand or by using software such as:
  * Invision
  * Balsamiq
  * UXPin
  * Wireframe.cc
* 6 steps to make a wireframe:
  1. Do your research
  2. Prepare your research for quick reference
  3. Make sure you have your user flow mapped out
  4. Draft, don't draw. Sketch, don't illustrate
  5. Add some detail and get testing
  6. Start tuning your wireframes into prototypes
* 3 key principles to make a good wireframe:
  1. Clarity - needs to answer the question of what the site is
  2. Confidence - ease of navigation and clear calls to action to increase user confidence
  3. Simplicity - don't be distracting, remove the "fluff"  

***

## HTML Basics

### What is HTML?

* **H**yper**T**ext **M**arkup **L**anguage (HTML) is a markup language used to structure a web page and its content.
* Consists of a series of ***elements*** using ***tags*** to enclose different parts of the content to make it appear a certain way.

***

## Anatomy of an HTML Element

* `<p>Mat cat is very Grumpy</p>` - designates a ***paragraph*** with an ***opening tag*** `<p>` and a ***closing tag*** `</p>`. 

![Anatomy of an HTML Element](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-small.png)

* Elements can have ***attributes*** such as a ***class*** or ***id*** to be able to reference later. They should have:
  * a space between it and the element
  * the attribute name followed by `=`
  * the attribute value wrapped in `"value"`

![Element Attribute](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-attribute-small.png)

* Elements can be nested:
  * `<p>My cat is <strong>very</strong> grumpy.</p>`
  * uses the `<strong></strong>` element to make `very` **bold**

* Some elements have no content and are called ***empty elements***.
  * `<img src="images/firefox-icon.png" alt="My test image" />`
  * adds an image without requiring a closing tag `</image>`

***  

## Anatomy of an HTML Document

### Preamble

* Every HTML document will have the following to identify it as an HTML file :  
`<!DOCTYPE html></html>`  

* To designate the language:
`<html lang="en-US">`

### Head

* The first portion after the preamble will be the ***head*** of the document for all the information that *isn't* content:
`<head></head>`

* To set the document to use UTF-8 to include the most characters from the vast majority of written languages:
`<meta charset="utf-8">`

* Viewport element ensures the page renders at the width of viewport, preventing mobile browsers from rendering pages wider than the viewport and then shrinking them down.
`<meta name="viewport" content="width=device-width">`

* Sets the title of your page, which is the title that appears in the browser tab the page is loaded in. It is also used to describe the page when you bookmark/favorite it.
`<title></title>`

### Body

* Contains all the content that you want to show to web users when they visit your page.
`<body></body>`

* Further broken down into:
  * Header - `<header></header>`
  * Main - `<main></main>`
  * Footer - `<footer></footer>`

***

## Elements

* Headings - can be between `<h1></h1>` and `<h6></h6>`, similar to MarkDown headings.

* Paragraphs - contains paragraphs of text between `<p></p>`.

* Lists - can be an ordered or unordered list
  * Unordered lists are for lists where the order of the items doesn't matter, such as a shopping list. These are wrapped in `<ul></ul>`.
  * Ordered lists are for lists where the order of the items does matter, such as a recipe. These are wrapped in `<ol></ol>`.
  * Each item inside the list is put inside `<li></li>`.
  