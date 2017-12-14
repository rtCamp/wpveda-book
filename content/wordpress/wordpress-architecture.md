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

1. {prefix}\_users
2. {prefix}\_usermeta
3. {prefix}\_posts
4. {prefix}\_postmeta
5. {prefix}\_comments
6. {prefix}\_commentmeta
7. {prefix}\_terms
8. {prefix}\_termmeta
9. {prefix}\_term\_taxonomy
10. {prefix}\_term\_relationship
11. {prefix}\_options
12. {prefix}\_links

**References** [https://codex.wordpress.org/Database\_Description](https://codex.wordpress.org/Database_Description)

## **WordPress Core Load**

**References**

[https://www.rarst.net/wordpress/wordpress-core-load/](https://www.rarst.net/wordpress/wordpress-core-load/)

[https://www.rarst.net/wordpress/wordpress-query-functions/](https://www.rarst.net/wordpress/wordpress-query-functions/)

[https://codex.wordpress.org/Plugin\_API/Action\_Reference](https://codex.wordpress.org/Plugin_API/Action_Reference)

[http://rachievee.com/the-wordpress-hooks-firing-sequence/](http://rachievee.com/the-wordpress-hooks-firing-sequence/)

