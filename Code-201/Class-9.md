# Class 9 - Forms and JS Events

## HTML Forms

1. Why are forms so important in web development?
   * It is the main way to get input from a user to be used in other portions of a site.
2. When designing a form, what are some key things to keep in mind when it comes to user experience?
   * Strong information architecture, label placement and optimization, efficient field descriptions, be careful with placeholders, and providing feedback. <https://www.smashingmagazine.com/2018/08/ux-html5-mobile-form-part-1/>
3. List 5 form elements and explain their importance.
   * `<form>` - defines a form and attributes that determine the form's behavior
   * `<fieldset>` - convenient way to create groups of widgets that share the same purpose, for styling and semantic purposes
   * `<legend>` - formally describes the purpose of the `<fieldset>` it is included inside
   * `<label>` - the formal way to define a label for an HTML form widget
   * `<textarea>` - a multi-line text field to input a message
   <https://developer.mozilla.org/en-US/docs/Learn/Forms/Your_first_form>

## Events

1. How would you describe events to a non-technical friend?
   * In order for a site to initiate an action, it must be triggered by an ***event***.
2. When using the `addEventListener()` method, what 2 arguments will you need to provide?
   * The name of the event we want to register this handler for, and the code that comprises the handler function we want to run in response to it. <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events>
3. Describe the event object. Why is the target within the event object useful?
   * The event object is automatically passed to event handlers to provide extra features and information. The target property of the event object is always a reference to the element the event occurred upon. <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events>
4. What is the difference between event bubbling and event capturing?
   * An event is captured by the innermost element and propagated outward in event bubbling, but in event capturing, an event is captured by the outermost element and propagated inward.
