---
id: core
title: Core Functionality
---

There are a number of inbuilt functions to make developing and delivering website content easier.

## Accessing framework methods and function
No special steps are needed to access any of the libraries or methods within the Croissant framework, as the `index.ph`p preamble takes care of loading everything and the framework itself handles class loading.

This allows you to access all functionality using a static referencing approach, without needing to `use` or instantiate any classes. The framework takes car of this for you, as well as caching a reference to a class once it's used for the first time so the class loader and pre-processor does not run on each subsequent call.

For more information on how Classes are constructed see [Writing Classes for the Croissant Framework](../developer/writing-classes).

## Building Pages
The framework allows each rendered page to have a unique set of Javascript and CSS, determined by the developer at development time. By default these files are delivered individually to the client when requested, however there is a built-in minification and bundling package that creates cached and minified versions of the selected CSS and Javascript files at run time.
These minification routines automatically detect changes to the javascript and css bundles for a particular page, and cache the bundle the first time the page is requested by any user session.

## Adding Javascript to a page

	`Core::AddJavascript('/path/to/file.js'[, 'footer']);`

You can add a Javascript file to a page by passing it’s path using `Core::AddJavascript()`. This function has a second optional parameter to select the place on the page the file should be added, either within the `<head>` section, or at the end of the page just before the closing `</body>` tag.


By default, Core::AddJavascript() looks for Javascript files in the docroot/css folder. Javascript files are added to the page in the order they are added using this call in a worker.

## Adding CSS to a page
```php
Core::AddCSS('/path/to/file.css')
```

You can add a CSS file to a page by passing it’s path using `Core::AddCSS()`.
By default, `Core::AddCSS()` looks for CSS files in the `docroot/css` folder. CSS files are added to the page in the order they are added using this call in a worker.

### Using SASS or LESS
You can use any CSS pre-processor you like, as long as the compiled CSS is in the `docroot\css` folder.

## Setting the Page Title
```php
Core::PageTitle('page title')
```

Calling this method at any time will set the value displayed for the individual rendered page's title.

## Setting the Page Metadata
```php
Core::PageMeta('meta tags')
```

Calling this method at any time will set the value displayed for the individual rendered page's metatag string.

## Setting the Page Template
```php
Core::Template('/path/to/template.tpl')
```

Calling this method at any time will set the Smarty template to be used to render the current page. This will overwrite any previous calls to this method.

If your worker is an AJAX worker, then you do not need to set the render template.

## Adding Data to Templates
```php
Core::Assign('key', 'variable')
```

Calling this method will make a specific variable value available to the Smarty template to access using the given key. For example: `Core::Assign('userid', 99)` will make the variable `$userid` available for use in a Smarty template.

```scss
<h1>Your UserID is {$userid}</h1>
```