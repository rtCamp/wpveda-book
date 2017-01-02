# The Customizer API

The Customizer is a framework for live-previewing any change to WordPress. It provides a simple and consistent interface for users to customize various aspects of their theme and their site, from colors and layouts to widgets, menus, and more. Themes and plugins alike can add custom options to the Customizer.

The Customizer is the canonical way to add options to your theme.

![](/assets/customizer-twentysevnteen-theme.png)

### **Customizer Objects**

The Customizer API is object-oriented. There are four main types of Customizer objects: Panels, Sections, Settings, and Controls.

Settings associate UI elements \(controls\) with settings that are saved in the database. Sections are UI containers for controls, to improve their organization. Panels are containers for sections, allowing multiple sections to be grouped together.

Each Customizer object is represented by a PHP class, and all of the objects are managed by the Customize Manager object, [WP\_Customize\_Manager](https://developer.wordpress.org/reference/classes/wp_customize_manager/).

To add, remove, or modify any Customizer object, and to access the Customizer Manager, use the [`customize_register`](https://developer.wordpress.org/reference/hooks/customize_register/) hook:

```php
function themeslug_customize_register( $wp_customize ) {
  // Do stuff with $wp_customize, the WP_Customize_Manager object.
}
add_action( 'customize_register', 'themeslug_customize_register' );
```

**Panels**

The Customizer Panels API allows developers to create an additional layer of hierarchy beyond controls and sections.

More than simply grouping sections of controls, panels are designed to provide distinct contexts for the Customizer, such as Customizing Widgets, Menus, or perhaps in the future, editing posts.

```php
$wp_customize->add_panel( 'menus', array(
  'title' => __( 'Menus' ),
  'description' => $description, // Include html tags such as <p>.
  'priority' => 160, // Mixed with top-level-section hierarchy.
) );
$wp_customize->add_section( $section_id , array(
  'title' => $menu->name,
  'panel' => 'menus',
) );
```

Panels must contain at least one Section, which must contain at least one Control, to be displayed. 

**Sections**

Sections are UI containers for Customizer controls. You can also add custom controls to the core sections.

if you have more than a few options you may want to add one or more custom sections. Use the [`add_section`](https://developer.wordpress.org/reference/classes/wp_customize_manager/add_section/) method of the [WP\_Customize\_Manager](https://developer.wordpress.org/reference/classes/wp_customize_manager/) object to add a new section:

```php
$wp_customize->add_section( 'custom_css', array(
  'title' => __( 'Custom CSS' ),
  'description' => __( 'Add custom CSS here' ),
  'panel' => '', // Not typically needed.
  'priority' => 160,
  'capability' => 'edit_theme_options',
  'theme_supports' => '', // Rarely needed.
) );
```

**Settings**

Settings handle live-previewing, saving, and sanitization of your Customizer objects.

There are several parameters available when adding a new setting:

```php
$wp_customize->add_setting( 'setting_id', array(
  'type' => 'theme_mod', // or 'option'
  'capability' => 'edit_theme_options',
  'theme_supports' => '', // Rarely needed.
  'default' => '',
  'transport' => 'refresh', // or postMessage
  'sanitize_callback' => '',
  'sanitize_js_callback' => '', // Basically to_json.
) );
```

There are two primary types of settings: **options and theme modifications**.

**Options** are stored directly in the wp\_options table of the WordPress database and apply to the site regardless of the active theme. Themes should rarely if ever add settings of the option type.

**Theme mods**, on the other hand, are specific to a particular theme. Most theme options should be theme\_mods. For example, a custom CSS plugin could register a custom theme css setting as a theme\_mod, allowing each theme to have a unique set of CSS rules without losing the CSS when switching themes then switching back.

Note that the Customizer can handle options stored as keyed arrays for settings using the option type. This allows multiple settings to be stored in a single option that isn’t a theme mod. To retrieve and use the values of your Customizer options, use [`get_theme_mod()`](https://developer.wordpress.org/reference/functions/get_theme_mod/) and [`get_option()`](https://developer.wordpress.org/reference/functions/get_option/) with the setting id:

**Controls**

Controls are the primary Customizer object for creating UI. Specifically, every control must be associated with a setting, and that setting will save user-entered data from the control to the database \(in addition to displaying it in the live-preview and sanitizing it\).

Controls can be added by the Customizer Manager and provide a robust set of UI options with minimal effort:

```php
$wp_customize->add_control( 'setting_id', array(
  'type' => 'date',
  'priority' => 10, // Within the section.
  'section' => 'colors', // Required, core or custom.
  'label' => __( 'Date' ),
  'description' => __( 'This is a date control with a red border.' ),
  'input_attrs' => array(
    'class' => 'my-custom-class-for-js',
    'style' => 'border: 1px solid #900',
    'placeholder' => __( 'mm/dd/yyyy' ),
  ),
  'active_callback' => 'is_front_page',
) );
```

The most important parameter when adding a control is its type — this determines what type of UI the Customizer will display. Core provides several built-in control types:

Core controls include **text**, **checkbox**, **textarea**, **radio**, **select**, and **dropdown-pages**.
Additional input types such as **email**, **url**, **number**, **hidden**, and **date** are supported implicitly.
Default **text**.

**Built-in custom control**

* WP\_Customize\_Color\_Control

* WP\_Customize\_Media\_Control

* WP\_Customize\_Cropped\_Image\_Control



### **Custom Panels, Sections, Settings and Controls**

Custom Controls, Sections, and Panels can be easily created by subclassing the PHP objects associated with each Customizer object: [`WP_Customize_Control`](https://developer.wordpress.org/reference/classes/wp_customize_control/), [`WP_Customize_Setting`](https://developer.wordpress.org/reference/classes/wp_customize_setting/)[,](https://developer.wordpress.org/reference/classes/wp_customize_setting/)[** **](https://developer.wordpress.org/reference/classes/wp_customize_setting/)[`WP_Customize_Section`](https://developer.wordpress.org/reference/classes/wp_customize_section/), and [`WP_Customize_Panel`](https://developer.wordpress.org/reference/classes/wp_customize_panel/)

For more see: [https:\/\/developer.wordpress.org\/themes\/advanced-topics\/customizer-api\/\#custom-controls-sections-and-panels](https://developer.wordpress.org/themes/advanced-topics/customizer-api/#custom-controls-sections-and-panels)



### **References**

[https:\/\/developer.wordpress.org\/themes\/advanced-topics\/customizer-api\/](https://developer.wordpress.org/themes/advanced-topics/customizer-api/)
[https:\/\/developer.wordpress.org\/reference\/classes\/wp\_customize\_manager\/
](https://developer.wordpress.org/themes/advanced-topics/customizer-api/)[https:\/\/premium.wpmudev.org\/blog\/creating-custom-controls-wordpress-theme-customizer\/
](https://premium.wpmudev.org/blog/creating-custom-controls-wordpress-theme-customizer/)[https:\/\/github.com\/bueltge\/Wordpress-Theme-Customizer-Custom-Controls
](https://github.com/bueltge/Wordpress-Theme-Customizer-Custom-Controls)[http:\/\/taqui.in\/customizer-javascript-api-quick-reference\/
](http://taqui.in/customizer-javascript-api-quick-reference/)[https:\/\/gist.github.com\/westonruter\/a15b99bdd07e6f4aae7a
](https://gist.github.com/westonruter/a15b99bdd07e6f4aae7a)

 



