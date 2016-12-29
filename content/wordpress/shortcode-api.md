# **Shortcode API**

The [Shortcode API](https://codex.wordpress.org/Shortcode_API) is a simple set of functions for creating WordPress shortcodes for use in posts and pages.

For instance, the following shortcode would add a photo gallery of images attached to that post or page: _\[gallery\]_

The API enables plugin developers to create special kinds of content \(e.g. forms, content generators\) that users can attach to certain pages by adding the corresponding shortcode into the page text.

**How to add shortcode?**

`add_shortcode( string $tag, callable $function )`

```php
// [bartag foo="foo-value"]
function bartag_func( $atts ) {
    $a = shortcode_atts( array(
        'foo' => 'something',
        'bar' => 'something else',
    ), $atts );

    return "foo = {$a['foo']}";
}
add_shortcode( 'bartag', 'bartag_func' );
```

**Note:**_** **__There can only be one hook for each shortcode._

**Callback Function Parameters**

* **$atts **-** **an associative array of attributes, or an empty string if no attributes are given

* **$content **-** **the enclosed content \(if the shortcode is used in its enclosing form\)

* **$tag **-** **the shortcode tag, useful for shared callback functions


**Function Reference**

Combine user attributes with known attributes and fill in defaults when needed.

`shortcode_atts( array $pairs, array $atts, string $shortcode = '' )`

Search content for shortcodes and filter shortcodes through their hooks.

`do_shortcode( string $content, bool $ignore_html = false )`

### References

[**Shortcode\_API**](https://codex.wordpress.org/Shortcode_API)





