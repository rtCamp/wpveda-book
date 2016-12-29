# **Widgets API**

The [Widgets API](https://codex.wordpress.org/Widgets_API), allows developers to build custom widgets for use in sidebars and other widgetized areas of a theme.

The API simplifies the widget creation process, and makes all widgets multiple instance capable.

**Developing Widgets**

To create a widget, you only need to extend the standard `WP_Widget` class and some of its functions.

The widget can then be registered using the `widgets_init` hook:

**Default Usage**

```php
class My_Widget extends WP_Widget {

	/**
	 * Sets up the widgets name etc
	 */
	public function __construct() {
		$widget_ops = array( 
			'classname' => 'my_widget',
			'description' => 'My Widget is awesome',
		);
		parent::__construct( 'my_widget', 'My Widget', $widget_ops );
	}

	/**
	 * Outputs the content of the widget
	 *
	 * @param array $args
	 * @param array $instance
	 */
	public function widget( $args, $instance ) {
		// outputs the content of the widget
	}

	/**
	 * Outputs the options form on admin
	 *
	 * @param array $instance The widget options
	 */
	public function form( $instance ) {
		// outputs the options form on admin
	}

	/**
	 * Processing widget options on save
	 *
	 * @param array $new_instance The new options
	 * @param array $old_instance The previous options
	 */
	public function update( $new_instance, $old_instance ) {
		// processes widget options to be saved
	}
}
```

**Register Widget**

```php
// register Foo_Widget widget
function register_foo_widget() {
    register_widget( 'Foo_Widget' );
}
add_action( 'widgets_init', 'register_foo_widget' );
```

**Displaying Widgets and Widget Areas**

```php
<?php if ( is_active_sidebar( 'left-sidebar' ) ) : ?>
    <ul id="sidebar">
        <?php dynamic_sidebar( 'left-sidebar' ); ?>
    </ul>
<?php endif; ?>
```

**How widgets stored in database?**

`sidebars_widgets` option store which widgets assigned to which sidebar.
`widget_{widget_id}` option store widgets settings. For example : `widget_recent-posts`

**Function Reference**

**Widget Functions**

* [is\_active\_widget\(\)](https://developer.wordpress.org/reference/functions/is_active_widget/)

* [the\_widget\(\)](https://developer.wordpress.org/reference/functions/the_widget/)

* [register\_widget\(\)](https://developer.wordpress.org/reference/functions/register_widget/)

* [unregister\_widget\(\)](https://developer.wordpress.org/reference/functions/unregister_widget/)


**Sidebar Functions**

* [register\_sidebar\(\)](https://developer.wordpress.org/reference/functions/register_sidebar/)

* [register\_sidebars\(\)](https://developer.wordpress.org/reference/functions/register_sidebars/)

* [unregister\_sidebar\(\)](https://developer.wordpress.org/reference/functions/unregister_sidebar/)

* [dynamic\_sidebar\(\)](https://developer.wordpress.org/reference/functions/dynamic_sidebar/)


**References**

[Widgets API Documentation](https://automattic.com/code/widgets/api/)

[Widgets\_API
](https://codex.wordpress.org/Widgets_API)

[Sidebars](https://codex.wordpress.org/Sidebars)


