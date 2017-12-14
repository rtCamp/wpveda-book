# **WordPress Architecture**

## **WordPress File and Directory Structure**

* wp-admin/
* wp-includes/
* wp-content/
* index.php
* wp-blog-header.php
* wp-load.php
* wp-config.php
* wp-settings.php
* wp-cron.php

**wp-includes** folder contains all the other PHP files and classes which is required for WordPress’ core operations. Again, you shouldn’t want to edit any files in this directory.

**wp-admin** folder contains the various files of the WordPress dashboard. You know that all administrative or functions related to WordPress, such as writing posts, moderating comments, installing plugins and themes are done via the WordPress dashboard. Again, you shouldn’t want to edit any files in this directory.

**wp-content** folder contains all user uploaded data and is again divided into four sub-folders:

* themes
* plugins
* upload
* mu-plugins

**References**

[https://codex.wordpress.org/WordPress\_Files](https://codex.wordpress.org/WordPress_Files)

[http://www.wpexplorer.com/wordpress-internal-function/](http://www.wpexplorer.com/wordpress-internal-function/)

## **WordPress Database Tables**

{prefix}\_users

{prefix}\_usermeta

{prefix}\_posts

{prefix}\_postmeta

{prefix}\_comments

{prefix}\_commentmeta

{prefix}\_terms

{prefix}\_termmeta

{prefix}\_term\_taxonomy

{prefix}\_term\_relationship

{prefix}\_options

{prefix}\_links

**References** [https://codex.wordpress.org/Database\_Description](https://codex.wordpress.org/Database_Description)

## **WordPress Core Load**

**References**

[https://www.rarst.net/wordpress/wordpress-core-load/](https://www.rarst.net/wordpress/wordpress-core-load/)

[https://www.rarst.net/wordpress/wordpress-query-functions/](https://www.rarst.net/wordpress/wordpress-query-functions/)

[https://codex.wordpress.org/Plugin\_API/Action\_Reference](https://codex.wordpress.org/Plugin_API/Action_Reference)

[http://rachievee.com/the-wordpress-hooks-firing-sequence/](http://rachievee.com/the-wordpress-hooks-firing-sequence/)

