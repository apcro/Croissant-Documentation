---
id: sessions
title: Session Functions
---

```php
SetVariable($var, $data)
```
Store the provided `$data` in the current user session with the key `$var`. Passing a null value or empty string in the `$data` argument will delete the data stored with the key `$var` from the session.

```php
GetVariable($var)
```
Retrieves the value stored in the current user session with the provided key `$var`.