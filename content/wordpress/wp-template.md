# Creating wordpress templates using wp.template

**wp.template** Create an Underscore.js _.template() function to be used to generate dynamic HTML blocks from pre-defined templates inside specially formed `<script>` tags. The source is defined in js/_enqueues/wp/util.js and output in `wp-includes/js/wp-util.js` during build.

## Template Interpolation

WordPress defines its own interpolation tags using the _.template( options ) to avoid incompatibility in some PHP configurations with asp_tags enabled. The WordPress-specific interpolation syntax is inspired by Mustache templating syntax:

* Interpolate (unescaped): {{{ }}}
* Interpolate (escaped): {{ }}
* Evaluate: <# #>

**References**

[https://codex.wordpress.org/Javascript_Reference/wp.template](https://codex.wordpress.org/Javascript_Reference/wp.template)

[https://lkwdwrd.com/wp-template-js-templates-wp](https://lkwdwrd.com/wp-template-js-templates-wp)