# WordPress CSS

### WordPress inbuilt CSS classes

[WordPress Default CSS Styles](http://digwp.com/2010/05/default-wordpress-css-styles-hooks)

[WordPress CSS: Understanding the Native Classes](https://css-tricks.com/back-basics-wordpress-css-understanding-native-classes/)


### WordPress admin pages style guide

[Creating Admin Themes](http://codex.wordpress.org/Creating_Admin_Themes)

### Theme post-editor style
```
add_editor_style( $stylesheet );
```

`$stylesheet`

(string/array) (optional) Path to a stylesheet file, relative to the current theme directory, or an array thereof to link multiple stylesheet files.
Default: "editor-style.css"

**Example**

```
function my_theme_add_editor_styles() {
    add_editor_style( '/path-to-css/editor-style.css' );
}

add_action( 'admin_init', 'my_theme_add_editor_styles' );
```
**For more details :** https://codex.wordpress.org/Function_Reference/add_editor_style

### WordPress style and script

##### Register and enqueue Style

1. [Register Style](http://codex.wordpress.org/Function_Reference/wp_register_style)
1. [Enqueue Style](http://codex.wordpress.org/Function_Reference/wp_enqueue_style)

##### Register and enqueue Script

1. [Register Script](http://codex.wordpress.org/Function_Reference/wp_register_script)
1. [Enqueue Script](http://codex.wordpress.org/Function_Reference/wp_enqueue_script)

**Example**

```
/**
 * Proper way to enqueue scripts and styles
 */
function theme_name_scripts() {
	wp_enqueue_style( 'style-name', get_stylesheet_uri() );
	wp_enqueue_script( 'script-name', get_template_directory_uri() . '/js/example.js', array(), '1.0.0', true );
}

add_action( 'wp_enqueue_scripts', 'theme_name_scripts' );
```
