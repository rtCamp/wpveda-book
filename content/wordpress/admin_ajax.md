# Admin AJAX

Apart from using WordPress Admin AJAX for all your AJAX needs, it can be also used to code long running processes without worrying about timeouts.

Some examples:
1. New release of your plugin adds new mysql column to a custom database. You need to calculate values of new fields for all rows.
2. You need to loop through all posts without worrying about timeouts. Specaily when dataset is very big and/or WordPress is running on low-end hosting.
