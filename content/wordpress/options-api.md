# Options API

The [Options API](https://developer.wordpress.org/plugins/settings/options-api/) focuses on managing data using a simple key\/value system.

The Options API, added in WordPress 1.0, allows creating, reading, updating and deleting of WordPress options. In combination with the [Settings API](https://developer.wordpress.org/plugins/settings/settings-api/) it allows controlling of options defined in settings pages.

### Where Options are Stored?

Options are stored in the `{$wpdb->prefix}_options` table. `$wpdb->prefix` is defined by the `$table_prefix` variable set in the `wp-config.php` file.

### Function Reference

**Add Option**

[add\_option\(\)](https://developer.wordpress.org/reference/functions/add_option/)

[add\_site\_option\(\)](https://developer.wordpress.org/reference/functions/add_site_option/)

**Get Option**

[get\_option\(\)](https://developer.wordpress.org/reference/functions/get_option/)

[get\_site\_option\(\)](https://developer.wordpress.org/reference/functions/get_site_option/)

**Update Option**

[update\_option\(\)](https://developer.wordpress.org/reference/functions/update_option/)

[update\_site\_option\(\)](https://developer.wordpress.org/reference/functions/update_site_option/)

**Delete Option**

[delete\_option\(\)](https://developer.wordpress.org/reference/functions/delete_option/)

[delete\_site\_option\(\)](https://developer.wordpress.org/reference/functions/delete_site_option/)



### References

[https:\/\/developer.wordpress.org\/plugins\/settings\/](https://developer.wordpress.org/plugins/settings/)

[https:\/\/developer.wordpress.org\/plugins\/settings\/custom-settings-page\/](https://developer.wordpress.org/plugins/settings/custom-settings-page/)

