---
id: intro-inbuilt
title: Introduction
---
The Croissant Framework comes with a number of pre-existing classes and methods to make development easier.

Most of these functions are related to managing the serverside rendering of HTML pages using the Smarty template engine, however a number of other convenience methods are also made available.

# Defines

There are a number of pre-defines constants available.

**`IS_AJAX_CALL`**

This is a pre-defined constant that evaluates to `true` or `false` depending on whether the incoming request that is being made was initated by the client as an Ajax call or not. This can be used to reroute execution of part or all of a worker, and determine whether or not to halt execution before attempting to render a display template.

The in-built function `Core::JSONWrite()` is a useful adjunct to this constant:

```php
function renderComponent($data) {
	if (!IS_AJAX_CALL) {
		return;
	}
	Core::Assign('data', $data);
	$renderedHtml = Core::Fetch('dataTemplate.tpl');
	Core::JSONWrite($renderedHtml);
	die();
}
```
This call assumes the data to be returned is valid, so writes JSON-encoded data along with a `200 OK` header.

# Classes

## Core

## Cookies
The [Cookie class](cookies) allows simplified access to reading and writing cookies.

## Session
The [Session class](sessions) provides simplified access to storing and retrieving Session data using a key-value store.

## User

## Cache
The [Cache class](cacheclass) provides simplified access to a transient key-value store. 
