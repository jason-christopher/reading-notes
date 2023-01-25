# Django Forms

Django Forms provides a framework that lets you define forms and their fields programmatically, and then use these objects to both generate the form HTML code and handle much of the validation and user interaction.

## Django Form Handling Process

A process flowchart of how Django handles form requests is shown below, starting with a request for a page containing a form (shown in green).

![Django Forms Flowchart](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png)

Based on the diagram above, the main things that Django's form handling does are:

1. Display the default form the first time it is requested by the user.
   * The form may contain blank fields if you're creating a new record, or it may be pre-populated with initial values (for example, if you are changing a record, or have useful default initial values).
   * The form is referred to as ***unbound*** at this point, because it isn't associated with any user-entered data (though it may have initial values).
2. Receive data from a submit request and bind it to the form.
   * Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
3. Clean and validate the data.
   * Cleaning the data performs sanitization of the input fields, such as removing invalid characters that might be used to send malicious content to the server, and converts them into consistent Python types.
   * Validation checks that the values are appropriate for the field (for example, that they are in the right date range, aren't too short or too long, etc.)
4. If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
5. If all data is valid, perform required actions (such as save the data, send an email, return the result of a search, upload a file, and so on).
6. Once all actions are complete, redirect the user to another page.

## Form

* The `Form` class is the heart of Django's form handling system. It specifies the fields in the form, their layout, display widgets, labels, initial values, valid values, and (once validated) the error messages associated with invalid fields. The class also provides methods for rendering itself in templates using predefined formats (tables, lists, etc.) or for getting the value of any element (enabling fine-grained manual rendering).

## Declaring a Form

* The declaration syntax for a `Form` is very similar to that for declaring a `Model`, and shares the same field types (and some similar parameters). This makes sense because in both cases we need to ensure that each field handles the right types of data, is constrained to valid data, and has a description for display/documentation.
* Form data is stored in an application's forms.py file, inside the application directory. Create and open the file `locallibrary/catalog/forms.py`. To create a Form, we import the forms library, derive from the Form class, and declare the form's fields. A very basic form class for our library book renewal form is shown below — add this to your new file:

  ```python
  from django import forms

  class RenewBookForm(forms.Form):
      renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")
  ```

## Form Fields

* In this case, we have a single `DateField` for entering the renewal date that will render in HTML with a blank value, the default label ***"Renewal date:"***, and some helpful usage text: ***"Enter a date between now and 4 weeks (default 3 weeks)."*** As none of the other optional arguments are specified the field will accept dates using the input_formats: YYYY-MM-DD (2016-11-06), MM/DD/YYYY (02/26/2016), MM/DD/YY (10/25/16), and will be rendered using the default widget: `DateInput`.
* There are many other types of form fields, which you will largely recognize from their similarity to the equivalent model field classes:
  * `BooleanField`, `CharField`, `ChoiceField`, `TypedChoiceField`, `DateField`, `DateTimeField`, `DecimalField`, `DurationField`, `EmailField`, `FileField`, `FilePathField`, `FloatField`, `ImageField`, `IntegerField`, `GenericIPAddressField`, `MultipleChoiceField`, `TypedMultipleChoiceField`, `NullBooleanField`, `RegexField`, `SlugField`, `TimeField`, `URLField`, `UUIDField`, `ComboField`, `MultiValueField`, `SplitDateTimeField`, `ModelMultipleChoiceField`, `ModelChoiceField`
* The arguments that are common to most fields are listed below (these have sensible default values):
  * `required`: If `True`, the field may not be left blank or given a None value. Fields are required by default, so you would set `required=False` to allow blank values in the form.
  * `label`: The label to use when rendering the field in HTML. If a label is not specified, Django will create one from the field name by capitalizing the first letter and replacing underscores with spaces (e.g. Renewal date).
  * `label_suffix`: By default, a colon is displayed after the label (e.g. Renewal date​:). This argument allows you to specify a different suffix containing other character(s).
  * `initial`: The initial value for the field when the form is displayed.
  * `widget`: The display widget to use.
  * `help_text` (as seen in the example above): Additional text that can be displayed in forms to explain how to use the field.
  * `error_messages`: A list of error messages for the field. You can override these with your own messages if needed.
  * `validators`: A list of functions that will be called on the field when it is validated.
  * `localize`: Enables the localization of form data input (see link for more information).
  * `disabled`: The field is displayed but its value cannot be edited if this is `True`. The default is `False`.

## Validation

* Django provides numerous places where you can validate your data. The easiest way to validate a single field is to override the method `clean_<fieldname>()` for the field you want to check.
