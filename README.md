jquery.validate.inline
======================

This plugin is the base of [ASP.NET MVC Inline Validation Plugin](http://nuget.org/packages/AspNetMvcInlineValidation/) 
and doing just one simple thing: 

Change the display style of jquery.validate.js, make validation messages better-looking and layout-friendly 
in the [jquery.validationEngine](http://www.position-absolute.com/articles/jquery-form-validator-because-form-validation-is-a-mess/) way.

#### IDEA
In fact, jquery.validationEngine.js is an alternative of jquery.validat.js.  It is a complete validation solution, 
including required, regular expression, phone, email validation rules, even ajax and customized validation functions.

Sometimes it's not easy to change the valdation mechanism.  For example, ASP.NET MVC and some other solutions 
already chose jquery.validates, I like the inline prompt style of jquery.validationEngine, but I don't want to 
give up the existing built-in validation features.  So I start to think about how to combine them.

I choose the easist way to integrate jquery.validate with jquery.validationEngine -- 
Include the whole jquery.validationEngine.js, slightly modify the plugin by add one line code 
to expose the internal methods, then append my plugin code to use internal methods to display inline prompt messages.

Because the validationEngine.jquery.css and jquery.validationEngine.js are included completely, it's not difficult
to upgrade when validationEngine release new version.  The only disadvantage is some useless code increase plugin size.

#### HOW TO USE
It's very simple to use jquery.validate.inline.

The original display

![Screenshot](https://raw.github.com/darkthread/jquery.validate.inline/master/doc/new-mvc-validation-style.gif)

Include jquery.validate.inline.js and validationEngine.jquery.css in your webpage, and add a line:
``` html
$("form").makeValidationInline();
```

The new display

![Screenshot](https://raw.github.com/darkthread/jquery.validate.inline/master/doc/new-mvc-validation-style.gif)

#### DEMO

[Online Demo](http://htmlpreview.github.io/?https://github.com/darkthread/jquery.validate.inline/blob/master/src/demo.html)
