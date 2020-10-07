---
id: install
title: Installation
---

Extract the downloaded archive and copy the contained folders and files to your webserver directory.

## 1. Set the permissions
Before you start with the installation process, ensure that the folders you've just uploaded have the right permission settings. We recommend `CHMOD 755`. Croissant needs to be able to write to the following files and directories and each of their subdirectories:

| File / Folder | Description |
| --- | --- |
| `/croissant/docroot/images` | Stores uploaded images |

<br />
The actual permission settings depend on the user that the webserver is running with and the owner of the folders. If your webserver has problems with the CHMOD 755, you can also try 775 and lastly 777 in this order.
<br /><br />

**Important** You should always avoid 777 permissions on your production webserver, since this will allow anyone who has access to the machine to edit the files.
 

## 2. Create the database

Next thing we need to do is create an empty database for Croissant to work with using a tool like phpMyAdmin.


## 3. Import Croissant Schema

Import sql file from `Croissant-Dataserver/trunk/croissant_schema.sql`.

## 4. Setup the configuration file
### Step 1 - Website config file

* Copy the source file from `Croissant-Web/croissant/configuration/sample.configuration.php` to `Croissant-Web/croissant/configuration/local.configuration.php`.

* Edit `local.configuration.php` to match your desired configuration.

### Step 2 - Dataserver config file

* Copy the source file from `Croissant-Dataserver/sample.database.configuration.php` to `Croissant-Dataserver/database.configuration.php`.

* Edit `database.configuration.php` to match your desired configuration.