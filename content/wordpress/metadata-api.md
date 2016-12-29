# Metadata API

Metadata, by its very definition, is information about information. In the case of WordPress, it’s information associated with posts, users, comments and terms.

An example would be a Content Type called Products with a metadata field for price. This field would be stored in the `postmeta` table.

The [Metadata API](https://codex.wordpress.org/Metadata_API) is a simple and standardized way for retrieving and manipulating metadata of various WordPress object types.

### **The Metadata Tables**

* {prefix}\_postmeta

* {prefix}\_commentmeta

* {prefix}\_usermeta

* {prefix}\_termmeta


### **The Metadata Tables Fields**

* meta\_id

* object\_id

* meta\_key

* meta\_value


### Managing Post Metadata

**Adding Metadata**

Adding metadata can be done quite easily with [add\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/add_post_meta/). The function accepts a `post_id`, a `meta_key`, a `meta_value`, and a `unique` flag.

The `meta_key` is how your plugin will reference the meta value elsewhere in your code. Something like `mycrazymetakeyname` would work, however a prefix related to your plugin or theme followed by a description of the key would be more useful. `wporg_featured_menu` might be a good one. It should be noted that the same `meta_key` may be used multiple times to store variations of the metadata \(see the unique flag below\).

The `meta_value` can be a string, integer, or an array. If it’s an array, it will be automatically serialized before being stored in the database.

The `unique` flag allows you to declare whether this key should be unique. A **non** unique key is something a post can have multiple variations of, like price.

If you only ever want **one** price for a post, you should flag it `unique` and the `meta_key` will have one value only.

* [add\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/add_post_meta/)

* [add\_user\_meta\(\)](https://developer.wordpress.org/reference/functions/add_user_meta/)

* [add\_comment\_meta\(\)](https://developer.wordpress.org/reference/functions/add_comment_meta/)

* [add\_term\_meta\(\)](https://developer.wordpress.org/reference/functions/add_term_meta/)


**Updating Metadata**

If a key already exists and you want to update it, use [update\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/update_post_meta/). If you use this function and the key does **NOT** exist, then it will create it, as if you’d used [add\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/add_post_meta/).

Similar to [add\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/add_post_meta/), the function accepts a `post_id`, a `meta_key`, a `meta_value`, and a `unique` flag.

* [update\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/update_post_meta/)

* [update\_user\_meta\(\)](https://developer.wordpress.org/reference/functions/update_user_meta/)

* [update\_comment\_meta\(\)](https://developer.wordpress.org/reference/functions/update_comment_meta/)

* [update\_term\_meta\(\)](https://developer.wordpress.org/reference/functions/update_term_meta/)


**Deleting Metadata**

[delete\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/delete_post_meta/) takes a `post_id`, a `meta_key`, and optionally `meta_value`. It does exactly what the name suggests.

* [delete\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/delete_post_meta/)

* [delete\_user\_meta\(\)](https://developer.wordpress.org/reference/functions/delete_user_meta/)

* [delete\_comment\_meta\(\)](https://developer.wordpress.org/reference/functions/delete_comment_meta/)

* [delete\_term\_meta\(\)](https://developer.wordpress.org/reference/functions/delete_term_meta/)


**Getting metadata**

* [get\_post\_meta\(\)](https://developer.wordpress.org/reference/functions/get_post_meta/)

* [get\_user\_meta\(\)](https://developer.wordpress.org/reference/functions/get_user_meta/)

* [get\_comment\_meta\(\)](https://developer.wordpress.org/reference/functions/get_comment_meta/)

* [get\_term\_meta\(\)](https://developer.wordpress.org/reference/functions/get_term_meta/)


**Add\/Delete Metadata**

* [add\_metadata\(\)](https://developer.wordpress.org/reference/functions/add_metadata/)

* [delete\_metadata\(\)](https://developer.wordpress.org/reference/functions/delete_metadata/)


**Get\/Update Metadata**

* [get\_metadata\(\)](https://developer.wordpress.org/reference/functions/get_metadata/)

* [update\_metadata\(\)](https://developer.wordpress.org/reference/functions/update_metadata/)


### **Hidden Custom Fields**

WordPress will not show custom fields which have meta\_key starting with an “\_” \(underscore\) in the custom fields list on the post edit screen or when using the the\_meta\(\) template function.

### Custom Meta Boxes

**What is a Meta Box?**

When a user edits a post, the edit screen is composed of several default boxes: Editor, Publish, Categories, Tags, etc. These boxes are meta boxes. Plugins can add custom meta boxes to an edit screen of any post type.

The content of custom meta boxes are usually HTML form elements where the user enters data related to a Plugin’s purpose, but the content can be practically any HTML you desire.

**Why Use Meta Boxes?**

Meta boxes are handy, flexible, modular edit screen elements that can be used to collect information related to the post being edited. Your custom meta box will be on the same screen as all the other post related information; so a clear relationship is established.

Meta boxes are easily hidden from users that do not need to see them, and displayed to those that do. Meta boxes can be user-arranged on the edit screen. The users are free to arrange the edit screen in a way that suits them, giving users control over their editing environment.

**Adding Meta Boxes**

To create a meta box use the [add\_meta\_box\(\)](https://developer.wordpress.org/reference/functions/add_meta_box/) function and plug it’s execution to the [`add_meta_boxes`](https://developer.wordpress.org/reference/hooks/add_meta_boxes/) action hook.

```php
function wporg_add_custom_box()
{
    $screens = ['post', 'wporg_cpt'];
    foreach ($screens as $screen) {
        add_meta_box(
            'wporg_box_id',           // Unique ID
            'Custom Meta Box Title',  // Box title
            'wporg_custom_box_html',  // Content callback, must be of type callable
            $screen                   // Post type
        );
    }
}
add_action('add_meta_boxes', 'wporg_add_custom_box');
```

**Saving Values**

When a post type is saved or updated, several actions fire, any of which might be appropriate to hook into in order to save the entered values.

```php
function wporg_save_postdata($post_id)
{
    if (array_key_exists('wporg_field', $_POST)) {
        update_post_meta(
            $post_id,
            '_wporg_meta_key',
            $_POST['wporg_field']
        );
    }
}
add_action('save_post', 'wporg_save_postdata');
```

**Removing Meta Boxes**

To remove an existing meta box from an edit screen use the [remove\_meta\_box\(\)](https://developer.wordpress.org/reference/functions/remove_meta_box/)function. The passed parameters must exactly match those used to add the meta box with [add\_meta\_box\(\)](https://developer.wordpress.org/reference/functions/add_meta_box/).

To remove default meta boxes check the source code for the parameters used. The default [add\_meta\_box\(\)](https://developer.wordpress.org/reference/functions/add_meta_box/) calls are made from `wp-includes/edit-form-advanced.php`.



### **Extending the metadata API**

Metadata API is actually quite simple to extend, allowing developers to easily register their own kind of metadata that is attached to their own, custom objects.

**How to extend the metadata API?**

1. You need to create a custom table in which to store the metadata.

2. You need to make WordPress aware of the meta table.

3. You can optionally define wrapper functions or class methods for the core metadata functions that make it easier to interact with your metadata layer.


**Creating the metadata table**

    CREATE TABLE `wp_bookmeta` (
      `meta_id` bigint(20) NOT NULL AUTO_INCREMENT,
      `affiliate_id` bigint(20) NOT NULL DEFAULT '0',
      `meta_key` varchar(255) DEFAULT NULL,
      `meta_value` longtext,
      PRIMARY KEY (`meta_id`),
      KEY `affiliate_id` (`affiliate_id`),
      KEY `meta_key` (`meta_key`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

**Make WordPress aware of the meta table**

```php
function register_metadata_table() {
     global $wpdb;
     $wpdb->bookmeta = $wpdb->prefix . 'bookmeta';
}
add_action( 'plugins_loaded', 'register_metadata_table' );
```

**Interacting with the metadata**

`add_metadata( 'book', $book_id, 'some_key', 'The value' );`



`update_metadata( 'book', $book_id, 'some_key', 'The value' );`



`get_metadata( 'book', $book_id, 'some_key', $single = true );`



`delete_metadata( 'book', $book_id, 'some_key' );`

### **References**

[https://developer.wordpress.org/plugins/metadata/](https://developer.wordpress.org/plugins/metadata/)

[https://pippinsplugins.com/extending-wordpress-metadata-api/](https://pippinsplugins.com/extending-wordpress-metadata-api/)

[https://code.tutsplus.com/tutorials/understanding-and-working-with-metadata-in-wordpress--cms-21034](https://code.tutsplus.com/tutorials/understanding-and-working-with-metadata-in-wordpress--cms-21034)

