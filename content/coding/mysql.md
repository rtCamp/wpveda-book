# MySQL

TODO:
1. Writing MySQL queries in WordPress
2. WPDB class
3. dbdelta - database migrations in WordPress
4. Finding slow queries
5. MySQL index/flat tables for frequent joins
6. WordPress query monitor plugin
7. WordPress object cache
7. Which PHP functions to avoid e.g. avoid `curl` in favor of `wp_remote_get`



## Table Name

Format: "Plugin slug" + "_" + "purpose"

Plugin name should have `-` replaces by `_`


# dbdelta

Ability
-------
=> dbDelta function has the ability to examine the current table structure, compares it to the desired table structure, 
and either adds or modifies the table as necessary, so it can be very handy for updates of our plugin.

Major Disadvantage
------------------
=> dbDelta function is only adds or modifies the table fields not removes it, This means that if you decide to remove 
any particular field on your table and hoping dbDelta will help you out with it, you are wrong.

=> Description : https://developer.wordpress.org/reference/functions/dbdelta

=> Use : http://hungred.com/how-to/wordpress-dbdelta-function/

	=> Must read "Strengthen and Weakness of dbDelta Function" and "Conclusion" on above link.
