---
id: writing-classes
title: Writing Classes for the Croissant Framework
---

## Class Basics

All classes by default should extend the `Core` class, although this is not strictly necessary.

## Class Folder Structure
Classes are distributed among a number of folders within the file structure. This allows you to keep your project-specific classes seperate from the Framework classes or any plugin libraries you may have added from the Framework Extension library.

By default, all project-specific classes should be stored in `croissant\libraries`.

## Class Initialisation

All classes have the option of extending the default Singleton object. This is not a requirement and classes can be accessed staticly without this initialisation step, however by extending the Core class you will have `self::` reference to all objects and data within the Singleton.

```php
<?php
namespace Croissant;

class MyClass extends Core {

	static $core;

	public static function Initialise() {
		if (!isset(self::$core)) {
			self::$core = parent::Initialise();
		}
		return self::$core;
	}

	\\ your method definitions
	public static function MyMethod($variables) {
	}
}
```

### Accessing and storing shared variables
If you have extended the `Core` class and included the `Initialise` method in your class, you will be able to access and retrieve arbitrary data from the Singleton using the `self::$core` object.

## Using Your Class
The Framework classloader will automatically recognise and initialise your new class. You will be able to access the public methods from anywhere by using the static referencing method: `MyClass::MyMethod($var)`. You do not need to `use` your class in your worker files or other classes.