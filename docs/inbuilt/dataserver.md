---
id: dataserver
title: Dataserver Access Functions
---

The Croissant Dataserver is a seperate service from the Croissant Framework, and provides a simple way of accessing data in a structurerd manner. See the documentation for the Croissnt Dataserver for more information.

# Dataserver Access
The Dataserver class provides two methods for accessing data stored on the Dataserver. Both methods return data as a structured array.

## Successful Call
```php
$response = array();
$response['statusCode'] = 0;
$response['result'] = ...;
```

## Unsuccesful Call or Error state
```php
$response = array();
$response['statusCode'] = 1;
$response['error'] = {plain text error message};
$response['errorType'] = {defined error code, optional};
$response['errorData'] = {Any specific error data or messages returned};

```
It is up to the developer to implement handling of the returned data and any error handling needed.

# Read vs Write
The Dataserver supports switching between `Read`ing data and `Write`ing data to different endpoints seamlessly, allowing architecture that supports realtime write consistency and eventual read consistency at an infrastructure level without front-end developers needing to know where data is stored or retrieved from.

## Methods
```php
Write($library, $function, $parameters = array(), $database = '', $readonly = false)
```
The `Write` method is the equivalent of a REST POST call. This will make a call to the Dataserver enpoint configured as the primary Write endpoint. Setting `$readonly` to `true` will redirect the call to the Dataserver endpoint configured as the primary Read endpoint.

```php
Read($library, $function, $parameters = array(), $database = '')
```
The `Read` method is an override for the Write method, setting the `$readonly` flag `true` for every call.

## Scaling
As both the Read and Write endpoints are configured as FQDNs, immediate horizontal scaling can be achieved using a Load Balancer on the URI, and further sclaing (horizontal and vertical) can be offloaded onto the Dataserver layer (the implement Croissant Dataserver service and the databases used).