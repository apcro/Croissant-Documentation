---
id: helloworld
title: Hello World
---

Writing <em>Hello World</em> in the Croissant framework is very simple.

By default, since the framework loads the `homepage.php` worker from the `workers` folder, the simplest <em>Hello World</em> is adding the following PHP code to `homepage.php`:

```php
<?php
namespace Croissant;
echo 'Hello World';
die();
```

This will cause the framework to echo "Hello World" and then halt execution.

## Hello World with style
To create a simple <em>Hello World</em> example using a template, create a new file in the `/templates` folder called `helloworld.tpl` (if it doesn't already exist). 

Add the following markup.

```scss
<h1>Hello World</h1>
```

In your `homepage.php` file, use:

```php
<?php
namespace Croissant;
Core::Template('helloworld.tpl');
```
This will display the content of the `helloworld.tpl` template using default browser styling.

## Hello World with <em>more</em> style
To add custom styling, create a new css file in the `docroot\css` folder called `helloworld.css`, and add the following line to `homepage.php`

```php
<?php
namespace Croissant;
Core::Template('helloworld.tpl');
Core::AddCSS('helloworld.css');
```

In your new `homepage.css` file add whatever style you want for your `<h1>` tag.

```css
h1 {
	font-size: 2em;
	color: blue;
}
```

## Adding data to Hello World
The Croissant Framework makes use of [Smarty](https://www.smarty.net/) as its default rendering engine, and a number of methods have been added to make using Smarty simpler.

 To add data to a template to be rendered, you _Assign_ the data, then reference it in the template. 

`homepage.php`
```php
<?php
namespace Croissant;
Core::Template('helloworld.tpl');
Core::AddCSS('helloworld.css');
Core::Assign('name', 'John Smith');
```
`homepage.tpl`
```scss
<h1>Hello {$name}</h1>
```