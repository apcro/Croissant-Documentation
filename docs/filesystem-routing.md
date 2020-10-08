---
id: filesystem-routing
title: File System Routing
---
At a basic level, the top level "route" matches the first part of a URI passed to the framework. This is implemented within the `/customers/[yourapp]/workers` folder as a PHP file. Any subsequent parts of the URI are made available to the matching `worker.php` file in the `$args` array.

## Simple routes

At a basic level, any `.php` file in the `/workers` folder automatically becomes a valid route.
 
To implement the "route" `www.myserver.com/homepage`, create a PHP file in `/croissant/workers` called `homepage.php`.

This file will contain all the business logic for displaying your homepage content, including any necessary logic to process any parameters passed to the worker.
 - `/workershomepage.php` -> `/homepage`

## Nested Routes
The router supports nested routes as well. Any workers implemented in filders under the `/workers` folder will be automatically available as routes.

 - `workers/user/login.php` -> `user/login`
 - `workers/about/us.php` -> `about/us`

 ## Index Routes
 Index routes for nested folders are not currently supported.
 - `workers/about/` -> (will return a `404` error)

## Execution Scope
### Globals
Croissant does not support globals by design, although globals may be used if desired. In general though globals are not needed, as the base "worker" implemented to handle all routing executes within the scope of `index.php`.

If temporary access is needed to a shared variable value, this can be stored as part of the Singleton object.
 - `Core::$core->$var = $var`
 - `$var = Core::$core->$var`

If more permanent access is needed, values can be stored using the [Session](inbuilt/sessions) class or the [Cache](inbuilt/cacheclass) class.

### Execution
The basic execution path is:

* `index.php` preamble
* pass execution to selected `worker.php` (if it exists)
* `index.php` closing (unless the worker stops script execution)