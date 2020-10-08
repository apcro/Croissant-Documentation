---
id: cacheclass
title: The Cache Class
---
The [Cache class](cacheclass) provides simplified access to a transient key-value store. Where the key-value data is stored can be defined in the `local.configuration.php` file, or within the cache call itself.

Currently only `disk` and `redis` are valid values for `CACHETYPE`. If [Redis](https://redis.io/) is not installed, any call to the `Cache::Store()` or `Cache::Retrieve()` methods will return `false`.

```php
Store($key, $data, $cachetype = CACHETYPE, $expiretime = 3600)
```

Store a value in the selected cache using the key provided. `$cachetype` and `$expiretime` are optional.

```php
Retrieve($key, $cachetype = CACHETYPE, $expiretime = 3600)
```

Retrieve a value from the selected cache using the key provided. `$cachetype` and `$expiretime` are optional. If `$expiretime` is provided, this will reset the expiry of the value. The can be used to create a self-destructing token that refreshes itself on every access.

```php
ExpireKey($key, $cachetype = CACHETYPE)
```

Expires the given key immediately.