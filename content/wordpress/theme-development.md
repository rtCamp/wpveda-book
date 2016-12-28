# **WordPress Theme Development**

### **What is a Theme?**

A WordPress theme changes the design of your website, often including its layout. Changing your theme changes how your site looks on the front-end, i.e. what a visitor sees when they browse to your site on the web. There are thousands of free WordPress themes in the [WordPress.org Theme Directory](https://wordpress.org/themes/), though many WordPress sites use custom themes.



### **What can themes do? **

Themes take the content and data stored by WordPress and display it in the browser. When you create a WordPress theme, you decide how that content looks and is displayed. There are many options available to you when building your theme. For example:

* Your theme can have different layouts, such as static or responsive, using one column or two.
* Your theme can display content anywhere you want it to be displayed.
* Your theme can specify which devices or actions make your content visible.
* Your theme can customize its typography and design elements using CSS.
* Other design elements like images and videos can be included anywhere in your theme.

WordPress themes are incredibly powerful. But, as with every web design project, a theme is more than color and layout. Good themes improve engagement with your website’s content _in addition_ to being beautiful.

### **What are themes made of?**

At their most basic level, WordPress themes are collections of different files that work together to create what you see, as well as how your site behaves.

**Required files**

There are only **two files absolutely required in a WordPress** theme:

1. `index.php` – the main template file
2. `style.css` – the main style file

Though not required, you may see additional files in a theme’s folder including:

* PHP files – including [template files](https://developer.wordpress.org/themes/basics/template-files/)
* [Localization files](https://developer.wordpress.org/theme/functionality/localization/)
* CSS files
* Graphics
* JavaScript
* Text files – usually license info_, _`readme.txt`_ _instructions, and a changelog file

### What is the difference between a theme and a plugin?

It is common to find cross-over between features found in themes and plugins. However, best practices are:

* a theme controls the _presentation_ of content; whereas
* a plugin is used to control the behavior and features of your WordPress site.


### **Template Terminology**

* [Page Templates](https://developer.wordpress.org/themes/basics/page-templates/)

* [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/)

* [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/)



### **Template partials**

A template partial is a piece of a template that is included as a part of another template, such as a site header.

* header.php

* footer.php

* sidebar.php



### **Template files**

WordPress themes are made up of template files. These are PHP files that contain a mixture of HTML, Template Tags, and PHP code.



### **Common WordPress template files**

* index.php

* 404.php

* comments.php

* front-page.php

* home.php

* category.php

* tag.php

* attachment.php


* header.php

* single.php

* page.php

* taxonomy.php

* author.php

* date.php

* archive.php

* search.php



### **Template Functions**

* [get\_header\(\)](https://developer.wordpress.org/reference/functions/get_header/)

* [get\_sidebar\(\)](https://developer.wordpress.org/reference/functions/get_sidebar/)

* [get\_footer\(\)](https://developer.wordpress.org/reference/functions/get_footer/)

* [get\_search\_form\(\)](https://developer.wordpress.org/reference/functions/get_search_form/)

* [get\_template\_part\(\)](https://developer.wordpress.org/reference/functions/get_template_part/)


* [locate\_template](https://developer.wordpress.org/reference/functions/locate_template/)

* [load\_template](https://developer.wordpress.org/reference/functions/load_template/)



### **Template Hierarchy**

WordPress uses the [query string](https://codex.wordpress.org/Glossary#Query_String "Glossary") to decide which template or set of templates should be used to display the page. The query string is information that is contained in the link to each part of your website. It comes after the initial question mark and may contain a number of parameters separated by ampersands.

Put simply, WordPress searches down through the template hierarchy until it finds a matching template file. To determine which template file to use, WordPress:

1. Matches every query string to a query type to decide which page is being requested \(for example, a search page, a category page, etc\);
2. Selects the template in the order determined by the template hierarchy;
3. Looks for template files with specific names in the current theme’s directory and uses the **first matching template file** as specified by the hierarchy.

With the exception of the basic `index.php` template file, you can choose whether you want to implement a particular template file or not.

If WordPress cannot find a template file with a matching name, it will skip to the next file in the hierarchy. If WordPress cannot find any matching template file, the theme’s `index.php` file will be used.

**Examples**

If your blog is at `http://example.com/blog/` and a visitor clicks on a link to a category page such as `http://example.com/blog/category/your-cat/`, WordPress looks for a template file in the current theme’s directory that matches the category’s ID to generate the correct page. More specifically, WordPress follows this procedure:

1. Looks for a template file in the current theme’s directory that matches the category’s slug. If the category slug is “unicorns,” then WordPress looks for a template file named `category-unicorns.php`.
2. If `category-unicorns.php` is missing and the category’s ID is 4, WordPress looks for a template file named `category-4.php`.
3. If `category-4.php` is missing, WordPress will look for a generic category template file, `category.php`.
4. If `category.php` does not exist, WordPress will look for a generic archive template, `archive.php`.
5. If `archive.php` is also missing, WordPress will fall back to the main theme template file, `index.php`.


Please see: [https://wphierarchy.com/](https://wphierarchy.com/)



### Plugin API Hooks

a few hooks need to be included in your theme templates. These hooks are fired by special Template Tags:

* wp\_head\(\)

* wp\_footer\(\)

* wp\_meta\(\)

* comment\_form\(\)



### **The Loop**

The Loop is the default mechanism WordPress uses for outputting posts through a theme’s template files.

```php
<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>
 
        <h2><?php the_title(); ?></h2>
    <?php the_post_thumbnail(); ?>
    <?php the_excerpt(); ?>
<?php endwhile; else: ?>
    <?php _e( 'Sorry, no posts matched your criteria.', 'textdomain' ); ?>
<?php endif; ?>
```

### **Theme Functions**

The **functions.php** file is where you add unique features to your WordPress theme. It can be used to hook into the core functions of WordPress to make your theme more modular, extensible, and functional.



### **Including CSS & JavaScript**

Enqueue the script or style using wp\_enqueue\_script\(\) or wp\_enqueue\_style\(\)

Bind callback function to wp\_enqueue\_scripts hook.

```php
function add_theme_scripts() {
  wp_enqueue_style( 'style', get_stylesheet_uri() );
 
  wp_enqueue_style( 'slider', get_template_directory_uri() . '/css/slider.css', array(), '1.1', 'all');
 
  wp_enqueue_script( 'script', get_template_directory_uri() . '/js/script.js', array ( 'jquery' ), 1.1, true);
 
    if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
      wp_enqueue_script( 'comment-reply' );
    }
}
add_action( 'wp_enqueue_scripts', 'add_theme_scripts' );

```

### **Conditional Tags**

Conditional Tags can be used in your Template Files to alter the display of content depending on the conditions that the current page matches.

For example: _is\_home\(\), is\_front\_page\(\)_

### **Theme Functionality**

* [Custom headers](https://developer.wordpress.org/themes/functionality/custom-headers/)

* [Sidebars](https://developer.wordpress.org/themes/functionality/sidebars/)

* [Widgets](https://developer.wordpress.org/themes/functionality/widgets/)

* [Navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/)

* [Pages, Posts, and Custom Post Type](https://developer.wordpress.org/themes/functionality/pages-posts-custom-post-types/)

* [Categories, Tags, and Custom Taxonomies](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/)

* [404 Pages](https://developer.wordpress.org/themes/functionality/404-pages/)


* [Accessibility](https://developer.wordpress.org/themes/functionality/accessibility/)

* [Pagination](http://Pagination)

* [Comments](http://Comments)

* [Media](http://Media)

* [Featured Images & Post Thumbnails](https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/)

* [Post Formats](https://developer.wordpress.org/themes/functionality/post-formats/)

* [Internationalization](https://developer.wordpress.org/themes/functionality/internationalization/)

* [Localization](https://developer.wordpress.org/themes/functionality/localization/)



### **Child Theme**

A child theme allows you to change small aspects of your site’s appearance yet still preserve your theme’s look and functionality.

**Why child theme?**

* Make your modifications portable and replicable;

* Keep customization separate from parent theme functions;

* Allow parent themes to be updated without destroying your modifications;

* Save on development time since you are not recreating the wheel;


**How to Create a Child Theme?**

1. Create a child theme folder: {parent\_theme\_name}-child

2. Create a stylesheet: style.css

3. Create a functions.php file

4. Inherit styles: _@import url \("..\/twentythirteen\/style.css"\);_

5. Add Template Files

6. Including Other Files

7. Enqueuing Styles and Scripts


**Child Theme CSS Header**

_Theme Name_ – needs to be unique to your theme

_Template_ – the name of the parent theme directory

```
/*
Theme Name:     Twenty Thirteen Child
Theme URI:      http://example.com/
Description:    Child theme for the Twenty Thirteen theme
Author:         Your name here
Author URI:     http://example.com/about/
Template:       twentythirteen
Version:        0.1.0
*/
```



### **Theme Security**

* [SQL injection](https://developer.wordpress.org/themes/advanced-topics/theme-security/#sql%c2%a0injection)

* [Cross Site Scripting \(XSS\)](https://developer.wordpress.org/themes/advanced-topics/theme-security/#cross-site-scripting-xss)

* [Cross-site Request Forgery \(CSRF\)](https://developer.wordpress.org/themes/advanced-topics/theme-security/#cross-site-request-forgery-csrf)




### UI Best Practices

* Logo Homepage Link

* Descriptive Anchor Text

* Style Links with Underlines

* Different Link Colors

* Descriptive Buttons


* Color Contrast

* Sufficient Font Size

* Associate Labels with Inputs

* Placeholder Text in Forms



**References**

[https://developer.wordpress.org/themes/](https://developer.wordpress.org/themes/)

[https://underscores.me/](https://underscores.me/)

[https://developer.wordpress.org/themes/template-files-section/](https://developer.wordpress.org/themes/template-files-section/)



