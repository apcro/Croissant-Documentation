---
id: dataserver-advanced
title: Advanced Dataserver Access
---
## Transactions Class
Included in the Dataserver functionlity is a special _Transactions_ class. This class allows developers to chian Dataserver calls into a single transaction, allowing the retrieval of disparate sets of data in a single transaction.

```php
ToTemplate($method, $return, $params = '', $client = '', $database = '')
```
Adds a Dataserver call to the Transaction list. This method also allows querying a specific database or, in a multi-tenant installation, a specific client's dataset programmatically.

```php
Process($totemplate = true)
```
Initiates the list of transactions, returning all the retrieved data as an array of `$result`. If the `$totemplate` flag is `true`, the returned result will be `Assign`ed for immediate use in Smarty templates.