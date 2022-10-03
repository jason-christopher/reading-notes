# Class 1 - HTML, CSS, & JavaScript Background

This reading lesson is important because it details some basic information of HTML, CSS, and JavaScript to provide some background before getting into the technical information. 

## Getting Started

1. Compose a short poem describing how HTTP sends data between computers.

* The DNS server matches an IP address to a website name.  
Because remembering IP addresses would be an impossible game.  
The client sends an HTTP request to the server to access a site.  
The server approves the request and sends some packets. Alright!  

2. Describe how HTML, CSS, and JS files are “parsed” in the browser.  

* HTML files are parsed first, then CSS stylesheets, and finally JavaScript scripts.

3. How can you find images to add to a Website?

* The readings says to go to Google Images and search for something suitable, but we need to make sure to credit the owner of the image. We can also go to a website like Unsplash to use images that are free to the public.

4. How do you create a String vs a Number in JavaScript?

* Create a string variable using `let variable = '';` and a number by `let variable = 4;` (or any other number). A string will be defined using `' '` or `" "` around the text.

5. What is a Variable and why are they important in JavaScript?

* Variables are containers that store values and declared with the `let`, `const`, or `var` keyword, followed by the name you give to the variable. (https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

## Introduction to HTML

1. What is an HTML attribute?

* Attributes contain extra information about the element that won't appear in the content. (https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)

2. Describe the Anatomy of an HTMl element.

* HTML ***elements*** contain and ***opening tag*** (`<p>`), the ***content***, and a ***closing tag*** (`</p>`).

3. What is the Difference between `<article>` and `<section>` element tags?

* `<article>` encloses a block of related content that makes sense on its own without the rest of the page (e.g., a single blog post), while a `<section>` is more for grouping together a single part of the page that constitutes one single piece of functionality (e.g., a mini map, or a set of article headlines and summaries), or a theme. (https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)

4. What Elements does a “typical” website include?

* A typical website will contain a `<!DOCTYPE HTML>` and everything else will be encompassed in the`<html>` section. This will include the `<head>` section that may include links to the CSS styleSheet or JavaScript script, `<meta>`, and `<title>`. The content of the site is usually in the `<body>` section that is broken up into the `<header>`, `<main>`, and `<footer>` sections.

5. How does metadata influence Search Engine Optimization?

* Two meta elements that are useful to include on your page define the author of the page, and provide a concise description of the page. Specifying a description that includes keywords relating to the content of your page is useful as it has the potential to make your page appear higher in relevant searches performed in search engines. (https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)

6. How is the `<meta>` HTML tag used when specifying metadata?

* The `<meta>` tag specifies your document's character encoding. For example, a common `charset` attribute is: `<meta charset="utf-8"/>`. This tag can also include description and author information. (https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)

## How to start to design a Website

1. What is the first step to designing a Website?

* The first step should be deciding what you want to accomplish by defining the goals and vision.

2. What is the most important question to answer when designing a Website?

* What exactly do I want to accomplish?

## Semantics

1. Why should you use an `<h1>` element over a `<span>` element to display a top level heading?

* Using `<span>` can render an element to look like a top level heading, but it has no semantic value, so it will not get any extra benefits. It is therefore a good idea to use the right HTML element for the right job. HTML should be coded to represent the data that will be populated and not based on its default presentation styling. Presentation (how it should look), is the sole responsibility of CSS. (https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

2. What are the benefits of using semantic tags in our HTML?

* Search engines will consider its contents as important keywords to influence the page's search rankings.
* Screen readers can use it as a signpost to help visually impaired users navigate a page.
* Finding blocks of meaningful code is significantly easier than searching through endless divs with or without semantic or namespaced classes.
* Suggests to the developer the type of data that will be populated.
* Semantic naming mirrors proper custom element/component naming.  
(https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

## What is JavaScript?

1. Describe 2 things that require JavaScript in the Browser?

* The DOM (Document Object Model) API allows you to manipulate HTML and CSS, creating, removing and changing HTML, dynamically applying new styles to your page, etc. Every time you see a popup window appear on a page, or some new content displayed (as we saw above in our simple demo) for example, that's the DOM in action.
* The Geolocation API retrieves geographical information. This is how Google Maps is able to find your location and plot it on a map.  
(https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript)

2. How can you add JavaScript to an HTML document?

* Internal JavaScript - adding `<script>` elements in the `<head>` section.
* External JavaScript - linking a separate .js file.
* Inline JavaScript handlers - writing `<script>` elements directly in the line desired line of HTML.

## Things I want to know more about

* I think I answered all my questions!
