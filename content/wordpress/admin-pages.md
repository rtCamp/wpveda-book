WordPress Admin Pages
=====================

If you are building a wordpress plugin / theme there are situations where you want to create a backend page.

There are two types of an admin page

1.Top-level admin page

2.Sub-level admin page

#### 1. Top-level admin page

This will create a brand-new menu in the admin menu sidebar.

`add_menu_page()` function is used to create top-level admin page.

```php
<?php
add_menu_page( $page_title, $menu_title, $capability, $menu_slug, $function, $icon_url, $position );
?>
```

###### Example

```php
<?php
add_action( 'admin_menu', 'register_my_custom_menu_page' );

function register_my_custom_menu_page(){
   add_menu_page( 'custom menu title', 'custom menu', 'manage_options', 'custompage', 'my_custom_menu_page', plugins_url( 'myplugin/images/icon.png' ), 6 );
   }

function my_custom_menu_page(){
   echo "Admin Page Test";
   }
?>
```

#### 2. Sub-level admin page

There are different functions by using which you can create a sub-level admin page.

The `add_submenu_page()` function is used to add sub-level menus anywhere.

```php
<?php
add_submenu_page( $parent_slug, $page_title, $menu_title, $capability, $menu_slug, $function );
?>
```

`$parent_slug` is the slug name of the parent menu. For example -

To add menu in Dashboard use `$parent_slug` as `index.php`

To add menu in Posts use `$parent_slug` as `edit.php`

and so on.

###### Example

```php
<?php
add_action('admin_menu', 'register_my_custom_submenu_page');

function register_my_custom_submenu_page() {
   add_submenu_page( 'edit.php', 'My Custom Submenu Page', 'My Custom Submenu Page', 'manage_options', 'my-custom-submenu-page', 'my_custom_submenu_page_callback' );
}

function my_custom_submenu_page_callback() {
echo '<div class="wrap"><div id="icon-tools" class="icon32"></div>';
    echo '<h2>My Custom Submenu Page</h2>';
echo '</div>';
}
?>
```

Built in top-level pages have there own functions to add sub menus. For example -

To add a menu item under posts you can use [add_posts_page](https://codex.wordpress.org/Function_Reference/add_posts_page)

To add a menu item under pages you use [add_pages_page](https://codex.wordpress.org/Function_Reference/add_pages_page)

To add a menu item under media you use [add_media_page](https://codex.wordpress.org/Function_Reference/add_media_page)

and so on.

###### Example

```php
<?php
add_action('admin_menu', 'my_plugin_menu');

function my_plugin_menu() {
  add_posts_page('My Plugin Posts Page', 'My Plugin', 'read', 'my-unique-identifier', 'my_plugin_function');
  }
?>
```

#### Reference Links

https://codex.wordpress.org/Creating_Options_Pages

https://codex.wordpress.org/Function_Reference/add_menu_page

https://codex.wordpress.org/Function_Reference/add_submenu_page

http://premium.wpmudev.org/blog/creating-wordpress-admin-pages/?nlpd=b&utm_expid=3606929-34.mZctMukzSv6Wvz3lKaD43w.1&utm_referrer=https%3A%2F%2Fwww.google.co.in%2F
