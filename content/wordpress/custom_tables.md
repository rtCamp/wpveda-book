# Custom Tables in Wordpress

If you are writing a plugin for WordPress, you will almost certainly find that you need to store some information in the WordPress database.
Sometimes the data is so large that you can't manage with wp_postmeta or wp_options tables which is wordpress default tables. 
e.g. Think about the realestate websites, in that case each and every property have number of data like Rooms, Bathrooms, floors, etc. 
In that kind of situation you need to store data in a separate MySQL tables which is generally called custom tables.

There are many ways to add custom tables and manage them, some ways are :

1. Using the wordpress way refer below links.

=> Managing the table : https://codex.wordpress.org/Creating_Tables_with_Plugins

=> Managing the data : https://codex.wordpress.org/Class_Reference/wpdb


2. Using the open source library like rt-lib.

=> https://github.com/rtCamp/rt-lib