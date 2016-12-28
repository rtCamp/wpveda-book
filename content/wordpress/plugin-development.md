# **WordPress Plugin Development**

### **What is a Plugin?**

Plugins are packages of code that extend the core functionality of WordPress. WordPress plugins are made up of PHP code and other assets, these include, but are not limited to: images, CSS, and JavaScript.

Using WordPress’ custom post types, you could write a plugin that creates a full-featured support ticketing system with email notifications, custom ticket statuses, and a client-facing portal. The possibilities are endless!

### **Why We Make Plugins?**

If there’s one cardinal rule in WordPress development, it’s this: **Don’t touch WordPress core**. This means that you don’t edit core WordPress files to add functionality to your site. This is because, when WordPress updates to a new version, it overwrites the local files. Any functionality you want to add should be added through plugins using approved WordPress APIs.

Plugins allow you to greatly extend the functionality of WordPress without touching WordPress core itself.

### **Plugin Basics Requirements**

* Create a directory for your plugin, e.g. _plugin-name_ in wp-content directory and create a new PHP file, e.g. _plugin-name.php_

* Header Requirements : header comment is what tells WordPress that a file is a plugin.

* Including a Software License

* Activation / Deactivation Hooks

* Uninstall Methods


### **Header Requirements**

```
<?php
/*
Plugin Name: WordPress.org Plugin
Plugin URI:  https://developer.wordpress.org/plugins/the-basics/
Description: Basic WordPress Plugin Header Comment
Version:     20160911
Author:      WordPress.org
Author URI:  https://developer.wordpress.org/
License:     GPL2
License URI: https://www.gnu.org/licenses/gpl-2.0.html
Text Domain: wporg
Domain Path: /languages
*/
```

### **Activation / Deactivation Hooks**

Activation and deactivation hooks provide ways to perform actions when plugins are activated or deactivated.

To set up an activation hook, use the register\_activation\_hook\(\) function:

```
register_activation_hook( __FILE__, 'pluginprefix_function_to_run' );
```

To set up a deactivation hook, use the register\_deactivation\_hook\(\) function:

```
register_deactivation_hook( __FILE__, 'pluginprefix_function_to_run' );
```

### **Uninstall Methods**

A plugin is considered uninstalled if a user has deactivated the plugin, and then clicks the delete link within the WordPress Admin.

**Method 1: register_uninstall_hook**

```
register_uninstall_hook( __FILE__, 'pluginprefix_function_to_run' );
```

**Method 2: uninstall.php**
    `/plugin-name/uninstall.php`

**Note:** When using uninstall.php, before executing, the plugin should always check for the constant **WP_UNINSTALL_PLUGIN** to prevent direct access. The constant will be defined by WordPress during the uninstall.php invocation. The constant is NOT defined when uninstall is performed by register_uninstall_hook().

### **Plugin Security**

* [Checking User Capabilities](https://developer.wordpress.org/plugins/security/checking-user-capabilities/)

* [Data Validation](https://developer.wordpress.org/plugins/security/data-validation/)

* [Securing Input](https://developer.wordpress.org/plugins/security/securing-input/)

* [Securing Output](https://developer.wordpress.org/plugins/security/securing-output/)

* [Nonces](https://developer.wordpress.org/plugins/security/nonces/)


### **Plugin Territory**

* Analytics scripts

* SEO options (meta tags, page title, post titles, robots.txt, etc.)

* Content Sharing buttons/links

* Custom post-content shortcodes

* Custom Post Types

* Custom Taxonomies

* Disabling the admin toolbar


### **Best Practices**

* Avoid Naming Collisions

* Prefix Everything

* Check for Existing Implementations

* File Organization

* Folder Structure

* Conditional Loading


### **Plugin Folder Structure**

```
/plugin-name
     plugin-name.php
     uninstall.php
     /languages
     /includes
     /admin
     /admin/js
     /admin/css
     /admin/images
     /public
     /public/js
     /public/css
     /public/images
```

**References**

[https://developer.wordpress.org/plugins/](https://developer.wordpress.org/plugins/)

[http://wppb.me/](http://wppb.me/)

[https://github.com/DevinVinson/WordPress-Plugin-Boilerplate](https://github.com/DevinVinson/WordPress-Plugin-Boilerplate)

[https://make.wordpress.org/themes/handbook/guidelines/plugin-territory/](https://make.wordpress.org/themes/handbook/guidelines/plugin-territory/)

[https://github.com/claudiosanches/wordpress-plugin-boilerplate](https://github.com/claudiosanches/wordpress-plugin-boilerplate)

