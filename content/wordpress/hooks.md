#WordPress Hooks

####Definition of Terms####
A **Hook** is a generic term in WordPress that refers to places where you can add your own code or change what WordPress is doing or outputting by default. Two types of hooks exist in WordPress: actions and filters.

An **Action** in WordPress is a hook that is triggered at specific time when WordPress is running and lets you take an action. This can include things like creating a widget when WordPress is initializing or sending a Tweet when someone publishes a post, or you might want to add extra widgets or menus, or add a promotional message to your page.

A **Filter** in WordPress allows you get and modify WordPress data before it is sent to the database or the browser. for example, you might want to insert another CSS class in a WordPress HTML element, or modify some of Customizr’s page blocks.

#### Actions v/s filters####

#####Actions#####
- When something has to be added
- declared with add_action().
- used with do_action().

#####Filters#####
* When something has to be changed
* declared with apply_filters().
* used with add_filters().

####How to Add and Remove Your Own Functions####

If you would like to hook in your own functions, the process is quite simple. You first need to know a few pieces of information. For actions, you’ll want to know the name of the hook, as well as when exactly it runs. For filters, you also need to know the name of the hook, but you want to know what value you are going to get and have to return, as well. The final bit of information you need is the name of the function where you have all your code.

#####How to Hook into an Action#####
```add_action( $hook, $function_to_add, $priority, $accepted_args );```
#####How to Hook into an Filter#####
```add_filter( $tag, $function_to_add, $priority, $accepted_args );```
#####How to Unhook from Actions and Filters#####
To remove a hook is quite simple. Use the function remove_action or remove_filter along with the name of the hook, function, and priority. The priority is optional and helpful if you have to unhook a function that is hooked more than once and you only want to remove a specific occurrence of that function.

```remove_action( $tag, $function_to_remove, $priority );```

```remove_filter( $tag, $function_to_remove, $priority );```

#### Examples WordPress of Hooks in Action ####
More than 200 hooks exist in WordPress. Below you will find a few examples of common hooks in use.

#####Register a Custom Menu in the Admin#####

```
function register_my_custom_menu_page() {
 add_menu_page( 'custom menu title', 'custom menu', 'manage_options', 'myplugin/myplugin-admin.php', '', 'dashicons-admin-site', 6 );
}
add_action( 'admin_menu', 'register_my_custom_menu_page' );
```
#####Change the Excerpt Length####

```
function excerpt_length_example( $words ) {
 return 15;
}
add_filter( 'excerpt_length', 'excerpt_length_example' );
```
####Refrence Links####
- http://teamtreehouse.com/library/wordpress-hooks-actions-and-filters (watch videos)
- http://doc.presscustomizr.com/customizr/wordpress-actions-filters-and-hooks-a-guide-for-non-developers/
- http://codex.wordpress.org/Plugin_API
- http://codex.wordpress.org/Plugin_API/Action_Reference
- http://codex.wordpress.org/Plugin_API/Filter_Reference
