---
id: redis
title: Redis Access
---
The _Redis_ class allows direct access to an installed [Redis](https://redis.io) server. Most of the more commonly-used Redis methods are available.

```php
Redis::Set($key, $value, $ttl = 0, $overwrite = false)
```
Set a key into the Redis store.
<br /><br />

```php
Redis::Get($key)
```
Get a value from the Redis store by key.
<br /><br />

```php
Redis::Delete($key)
```
Delete a key from the Redis store immediately.
<br /><br />
```php
Redis::Flush()
```
Flush the Redis store.
<br /><br />
```php
Redis::HashGet($key, $field)
```
Returns the value associated with field in the hash stored at key.
<br /><br />
```php
Redis::HashSet($key, $field, $value)
```
Sets field in the hash stored at key to value. If key does not exist, a new key holding a hash is created. If field already exists in the hash, it is overwritten.
<br /><br />
```php
Redis::HashGetAll($key)
```
Returns all fields and values of the hash stored at key. In the returned value, every field name is followed by its value, so the length of the reply is twice the size of the hash.
<br /><br />
```php
Redis::HashKeys($key)
```
Returns all field names in the hash stored at key.
<br /><br />
```php
Redis::HashLength($key)
```
Returns the number of fields contained in the hash stored at key.
<br /><br />
```php
Redis::HashMultiSet($key, $values)
```
Multiple sets field in the hash stored at key to value.
<br /><br />
```php
Redis::ListRange($key, $start, $end)
```
Returns the specified elements of the list stored at key. The offsets start and stop are zero-based indexes, with 0 being the first element of the list (the head of the list), 1 being the next element and so on.
<br /><br />
```php
Redis::ListTrim($key, $start, $end)
```
Trim an existing list so that it will contain only the specified range of elements specified.
<br /><br />
```php
Redis::ListIndex($key, $start)
```
Returns the element at index index in the list stored at key.
<br /><br />
```php
Redis::ListPush($key, $value)
```
Insert all the specified values at the head of the list stored at key. If key does not exist, it is created as empty list before performing the push operations.
<br /><br />
```php
Redis::ListPop($key)
```
Removes and returns the first element of the list stored at key.
<br /><br />
```php
Redis::ListLength($key)
```
Returns the length of the list stored at key. If key does not exist, it is interpreted as an empty list and 0 is returned. 