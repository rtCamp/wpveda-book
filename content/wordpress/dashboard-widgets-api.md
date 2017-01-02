# **Dashboard Widgets API**

The [Dashboard Widgets API](https://codex.wordpress.org/Dashboard_Widgets_API), makes it very simple for plugin or theme authors to add new widgets to the admin dashboard.

**Add Dashboard Widgets**

[wp\_add\_dashboard\_widget\(\)](https://codex.wordpress.org/Function_Reference/wp_add_dashboard_widget "Function Reference/wp add dashboard widget") function is used to display widgets on dashboard.

To run the function you will need to hook into the action '[wp\_dashboard\_setup](https://developer.wordpress.org/reference/hooks/wp_dashboard_setup/)' via [add\_action\(\)](https://developer.wordpress.org/reference/functions/add_action/). For the Network Admin dashboard, use the hook '[wp\_network\_dashboard\_setup](https://developer.wordpress.org/reference/hooks/wp_network_dashboard_setup/)'.

**Example**

```php
/**
 * Add a widget to the dashboard.
 *
 * This function is hooked into the 'wp_dashboard_setup' action below.
 */
function example_add_dashboard_widgets() {

	wp_add_dashboard_widget(
                 'example_dashboard_widget',         // Widget slug.
                 'Example Dashboard Widget',         // Title.
                 'example_dashboard_widget_function' // Display/callback function.
        );	
}
add_action( 'wp_dashboard_setup', 'example_add_dashboard_widgets' ); // For site dashboard.
add_action( 'wp_network_dashboard_setup', 'example_add_dashboard_widgets' ); // For network admin dashboard.

/**
 * Create the function to output the contents of our Dashboard Widget.
 */
function example_dashboard_widget_function() {

	// Display whatever it is you want to show.
	echo "Hello World, I'm a great Dashboard Widget";
}
```



