jquery.validate.inline
======================

This plugin is the base of [ASP.NET MVC Inline Validation Plugin](http://nuget.org/packages/AspNetMvcInlineValidation/) 
and trying to accomplish just a thing: 

Make the validation messages of jquery.validate.js better-looking and layout-friendly, just like 
what [jquery.validationEngine](http://www.position-absolute.com/articles/jquery-form-validator-because-form-validation-is-a-mess/) dose.

#### IDEA
Strictly speaking, jquery.validationEngine.js is a alternative of jquery.validate.js.  It is also a complete validation solution, 
including required, regular expression, phone, email validation rules, even ajax and customized validation functions.

I like the display style of validationEngine, but it is sometimes difficult to replace the valdation mechanism.  For example, 
ASP.NET MVC already chose jquery.validates for client-side validation, the inline prompt style of jquery.validationEngine is good, 
but it's absolutely painful to give up built-in validation features.  So, I start to think about how to combine them.

I choose the easist way to integrate jquery.validate with jquery.validationEngine -- 
Include the whole jquery.validationEngine.js, slightly modify the plugin by add one line of code 
to expose the internal methods, then append my plugin to use internal methods to show inline prompt messages.

Because the validationEngine.jquery.css and jquery.validationEngine.js are included directly, it's easier
to upgrade when validationEngine release new version.  The drawback is that unused code increases plugin size to 91KB,
29KB for minified version, I guess it's still fine.

#### HOW TO USE

It's simple to use jquery.validate.inline.

The original style:

![Screenshot](https://raw.github.com/darkthread/jquery.validate.inline/master/doc/orig-mvc-validation-style.gif)

Include jquery.validate.inline.js and validationEngine.jquery.css in your webpage, then add one line:
``` javascript
$("form").makeValidationInline();
```

Now you got the new inline style

![Screenshot](https://raw.github.com/darkthread/jquery.validate.inline/master/doc/new-mvc-validation-style.gif)

#### TIPS

jquery.validationEngine 2.0 supports unobtrusive promopt position settings and auto update of prompt position 
when page layout changes.  

You can assign specific prompt postion for each field by data-prompt-postion="..." HTML5 attribute.
If only topLeft or topRight is not flexible enough, you can use optional offsetX, offsetY parameters for fully customization.

``` html
<input type="text" id="Text2" name="Text2" data-val="true" data-val-required="Required" 
 data-prompt-position="bottomRight: -20,2" />
```

When elements in webpage show or hide dynamically, sometimes the fields will change their positions, too.
When fields move, the validation prompts are still fixed at the original positions. validationEngine provides a 
updatePromptsPosition event to recalculate and update the positions of prompts.

The updatePromptsPosition event is binded to the form after .makeValidationInline(), so triggered it 
anytime when fields move, you will see the magic.

``` javascript
$("#form1").trigger("updatePromptsPosition");
```

#### DEMO

[Online Demo](http://htmlpreview.github.io/?https://github.com/darkthread/jquery.validate.inline/blob/master/src/demo.html)
