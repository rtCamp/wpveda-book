# PHP

TODO:
1. ~~PHP codeing style as per WordPres~~s
2. ~~Naming conventions~~
2. Code Sniffer
4. Debugging PHP code using xdebug profiling. Webgrind and cachegrind.
5. WordPress debug log
6. WordPress query monitor plugin
7. Which PHP functions to avoid e.g. avoid `curl` in favor of `wp_remote_get`

Whenever we set code to screen, we must follow some sort of logic. You may well be the only person who understands that logic, but you still make the effort. The reason we follow standards and practices is to adhere to a common logic, so that we find each other’s code understandable and sensible. The PHP parser doesn’t care how you format your code, so why should you? In reality, the format of your code makes a huge difference in every way imaginable.

Keep the following points in mind when writing PHP code for WordPress, whether for core programming code, plugins, or themes.

### Line breaks

WordPress’ documentation says nothing in particular about line breaks, but adding a line break after most statements is common practice. Variable definitions, `if` blocks, `array` items and so on should be on separate lines.

```
$my_value = 'Me';
$your_value = 'You';
$their_value = 'Them';

if ( $my_value == 'You' ) {
  echo 'It seems like you are mixed up with me';
}
```

### Single and Double Quotes

Use single and double quotes when appropriate. If you’re not evaluating anything in the string, use single quotes. You should almost never have to escape quotes in a string, because you can just alternate your quoting style, like so:

```
echo '<a href="/static/link" title="Yeah yeah!">Link name</a>';
echo "<a href='$link' title='$linktitle'>$linkname</a>";
```

Text that goes into attributes should be run through `esc_attr()` so that single or double quotes do not end the attribute value and invalidate the HTML and cause a security issue.

### Indentation

Indent code to show a logical structure. The goal here is readability, so any indentation that makes the code more readable is a good practice. Use **real tabs** and **not spaces**, as this allows the most flexibility across clients. Use tabs at the beginning of lines, and use spaces for mid-line indentation.

**Exception:** if you have a block of code that would be more readable if things are aligned, use spaces:

```
[tab]$foo   = 'somevalue';
[tab]$foo2  = 'somevalue2';
[tab]$foo34 = 'somevalue3';
[tab]$foo5  = 'somevalue4';
```

### Brace Style

The easiest method is to always use braces. The standards allow for the omission of braces for single-line if statements but only if there are no multi-line blocks in the same logical structure. Omitting braces is not allowed for single-line loops, though. This is too convoluted — just always requiring braces would be much simpler. In addition, the standards dictate that an opening brace should be put on the same line as the initial statement, not on the line below (as specified in the PHP documentation).

```
if ( condition ) {
    action1();
    action2();
} elseif ( condition2 && condition3 ) {
    action3();
    action4();
} else {
    defaultaction();
}
```

Furthermore, if you have a really long block, consider whether it can be broken into two or more shorter blocks or functions. If you consider such a long block unavoidable, please put a short comment at the end so people can tell at glance what that ending brace ends – typically this is appropriate for a logic block, longer than about 35 rows, but any code that’s not intuitively obvious can be commented.

```
if ( condition ) {
    action0();
}

if ( condition ) {
    action1();
} elseif ( condition2 ) {
    action2a();
    action2b();
}

foreach ( $items as $item ) {
    process_item( $item );
}
```

Note that requiring the use of braces just means that ***single-statement inline control structures*** are prohibited. You are free to use the alternative syntax for control structures (e.g. `if`/`endif`, `while`/`endwhile`)—especially in your templates where PHP code is embedded within HTML, for instance:

```
<?php if ( have_posts() ) : ?>
    <div class="hfeed">
        <?php while ( have_posts() ) : the_post(); ?>
            <article id="post-<?php the_ID() ?>" class="<?php post_class() ?>">
                <!-- ... -->
            </article>
        <?php endwhile; ?>
    </div>
<?php endif; ?>
```

### Formatting SQL statements

SQL query keywords must be capitalized, and complex queries should be broken into multiple lines and indent if it is sufficiently complex to warrant it. Most statements work well as one line though. Always capitalize the SQL parts of the statement like `UPDATE` or `WHERE`.

Functions that update the database should expect their parameters to lack SQL slash escaping when passed. Escaping should be done as close to the time of the query as possible, preferably by using `$wpdb->prepare()`

`$wpdb->prepare()` is a method that handles escaping, quoting, and int-casting for SQL queries. It uses a subset of the `sprintf()` style of formatting. Example :

```
$var = "dangerous'"; // raw data that may or may not need to be escaped
$id = some_foo_number(); // data we expect to be an integer, but we're not certain

$wpdb->query( $wpdb->prepare( "UPDATE $wpdb->posts SET post_title = %s WHERE ID = %d", $var, $id ) );
```

`%s` is used for string placeholders and `%d` is used for integer placeholders. Note that they are not ‘quoted’! `$wpdb->prepare()` will take care of escaping and quoting for us. The benefit of this is that we don’t have to remember to manually use [esc_sql()](https://codex.wordpress.org/Function_Reference/esc_sql), and also that it is easy to see at a glance whether something has been escaped or not, because it happens right when the query happens.

### Database Queries

Avoid touching the database directly. If there is a defined function that can get the data you need, use it. Database abstraction (using functions instead of queries) helps keep your code forward-compatible and, in cases where results are cached in memory, it can be many times faster.

###### Efficient Database Queries

When querying the database in WordPress, you should generally use a `WP_Query` object. `WP_Query` objects take a number of useful arguments and do things behind-the-scenes that other database access methods such as `get_posts()` do not.

Here are a few key points:

* Only run the queries that you need.

    A new `WP_Query` object runs five queries by default, including calculating pagination and priming the term and meta caches. Each of the following arguments will remove a query:
    * `'no_found_rows' => true`: useful when pagination is not needed.
    * `'update_post_meta_cache' => false`: useful when post meta will not be utilized.
    * `'update_post_term_cache' => false`: useful when taxonomy terms will not be utilized.
    * `'fields' => 'ids'`: useful when only the post IDs are needed (less typical).

* Do not use `posts_per_page => -1`.

    This is a performance hazard. What if we have 100,000 posts? This could crash the site. If you are writing a widget, for example, and just want to grab all of a custom post type, determine a reasonable upper limit for your situation.
    ```
// Query for 500 posts.
new WP_Query( array(
  'posts_per_page' => 500,
));
    ```
* Do not use `$wpdb` or `get_posts()` unless you have good reason.

    `get_posts()` actually calls `WP_Query`, but calling `get_posts()` directly bypasses a number of filters by default. Not sure whether you need these things or not? You probably don't.
* If you don't plan to paginate query results, always pass `no_found_rows => true` to `WP_Query`. This will tell WordPress not to run `SQL_CALC_FOUND_ROWS` on the SQL query drastically speeding up your query. `SQL_CALC_FOUND_ROWS` calculates the total number of rows in your query which is required to know the total amount of "pages" for pagination.

    ```
// Skip SQL_CALC_FOUND_ROWS for performance (no pagination).
new WP_Query( array(
  'no_found_rows' => true,
));
    ```
* A [taxonomy](http://codex.wordpress.org/Taxonomies) is a tool that lets us group or classify posts.

    Post meta lets us store unique information about specific posts. As such the way post meta is stored does not facilitate efficient post lookups. Generally, looking up posts by post meta should be avoided (sometimes it can't). If you have to use one, make sure that it's not the main query and that it's cached.
* Passing `cache_results => false` to `WP_Query` is usually not a good idea.

    If `cache_results => true` (which is true by default if you have caching enabled and an object cache setup), `WP_Query` will cache the posts found among other things. It makes sense to use `cache_results => false` in rare situations (possibly `WP-CLI` commands).
* Multi-dimensional queries should be avoided.

    Examples of multi-dimensional queries include:
    * Querying for posts based on terms across multiple taxonomies
    * Querying multiple post meta keys

    Each extra dimension of a query joins an extra database table. Instead, query by the minimum number of dimensions possible and use PHP to filter out results you don't need.

    Here is an example of a 2-dimensional query:
    ```
// Query for posts with both a particular category and tag.
new WP_Query( array(
  'category_name' => 'cat-slug',
  'tag' => 'tag-slug',
));
```

###### WP_Query vs. get_posts() vs. query_posts()

As outlined above, `get_posts()` and `WP_Query`, apart from some slight nuances, are quite similar. Both have the same performance cost (minus the implication of skipping filters): the query performed.

`query_posts()`, on the other hand, behaves quite differently than the other two and should almost never be used. Specifically:

* It creates a new `WP_Query` object with the parameters you specify.
* It replaces the existing main query loop with a new instance of `WP_Query`.

If you must touch the database, get in touch with some developers by posting a message to the [wp-hackers mailing list](https://codex.wordpress.org/Mailing_Lists#Hackers). They may want to consider creating a function for the next WordPress version to cover the functionality you wanted.

### Design Patterns

Using a common set of design patterns while working with PHP code is the easiest way to ensure the maintainability of a project. This section addresses standard practices that set a low barrier for entry to new developers on the project.

###### Namespacing

All functional code should be properly namespaced. We do this to logically organize our code and to prevent collisions in the global namespace. Generally, this means using a PHP `namespace` identifier at the top of included files:

```
namespace wpveda\Utilities\API;

function do_something() {
  // ...
}
```

If the code is for general release to the WordPress.org theme or plugin repositories, the [minimum PHP compatibility](https://wordpress.org/about/requirements/) of WordPress itself must be met. Unfortunately, PHP namespaces are not supported in version < 5.3, so instead, a class would be used to wrap static functions to serve as a **pseudo** namespace:

```
/**
 * Namespaced class name example.
 */
class Wpveda_Utilities_API {
    public static function do_something() {
        // ...
    }
}
```

The similar structure of the namespace and the static class will allow for simple onboarding to either style of project (and a quick upgrade to PHP namespaces if and when WordPress raises its minimum version requirements).

Anything declared in the global namespace, including a namespace itself, should be written in such a way as to ensure uniqueness. A namespace like `wpveda` is (most likely) unique; `theme` is not. A simple way to ensure uniqueness is to prefix a declaration with unique prefix.

###### Object Design

Firstly, if a function is not specific to an object, it should be included in a functional `namespace` as referenced above.

Objects should be well-defined, atomic, and fully documented in the leading docblock for the file. Every method and property within the object must themselves be fully-documented, and relate to the object itself.

```
/**
 * Video.
 *
 * This is a video object that wraps both traditional WordPress posts
 * and various YouTube meta information APIs hidden beneath them.
 *
 * @package    ClientTheme
 * @subpackage Content
 */
class Prefix_Video {

    /**
     * WordPress post object used for data storage.
     *
     * @access protected
     * @var WP_Post
     */
    protected $_post;

    /**
     * Default video constructor.
     *
     * @access public
     *
     * @see get_post()
     * @throws Exception Throws an exception if the data passed is not a post or post ID.
     *
     * @param int|WP_Post $post Post ID or WP_Post object.
     */
    public function __construct( $post = null ) {
        if ( null === $post ) {
            throw new Exception( 'Invalid post supplied' );
        }

        $this->_post = get_post( $post );
    }
}
```

###### Visibility

In terms of [Object-Oriented Programming (OOP)](http://en.wikipedia.org/wiki/Object-oriented_programming), public properties and methods should obviously be `public`. Anything intended to be private should actually be specified as `protected`. There should be no `private` fields or properties without well-documented and agreed-upon rationale.

###### Structure and Patterns

* Singletons are not advised. There is little justification for this pattern in practice and they cause more maintainability problems than they fix.
* Class inheritance should be used where possible to produce [DRY](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself) code and share previously-developed components throughout the application.
* Global variables should be avoided. If objects need to be passed throughout the theme or plugin, those objects should either be passed as parameters or referenced through an object factory.
* Hidden dependencies (API functions, super-globals, etc) should be documented in the docblock of every function/method or property.


### Naming Conventions

Use lowercase letters in variable, action, and function names (never `camelCase`). Separate words via underscores. Don’t abbreviate variable names un-necessarily; let the code be unambiguous and self-documenting.

```
function some_name( $some_variable ) { [...] }
```

Class names should use capitalized words separated by underscores. Any acronyms should be all upper case.

```
class Wpveda_Category extends Wpveda { [...] }
class WP_HTTP { [...] }
```

Constants should be in all upper-case with underscores separating words:

```
define( 'DOING_AJAX', true );
```

Files should be named descriptively using lowercase letters. Hyphens should separate words.

```
my-plugin-name.php
```


Class file names should be based on the class name with `class-` prepended and the underscores in the class name replaced with hyphens, for example `WP_Error` becomes:

```
class-wp-error.php
```

This file-naming standard is for all current and new files with classes. There is one exception for three files that contain code that got ported into BackPress: class.wp-dependencies.php, class.wp-scripts.php, class.wp-styles.php. Those files are prepended with `class.`, a dot after the word class instead of a hyphen.

Files containing template tags in `wp-includes` should have `-template` appended to the end of the name so that they are obvious.

```
general-template.php
```

### Self-Explanatory Flag Values for Function Arguments

Prefer string values to just `true` and `false` when calling functions.

```
// Incorrect
function eat( $what, $slowly = true ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', true ); // what does true mean?
eat( 'dogfood', false ); // what does false mean? The opposite of true?
```

Since PHP doesn’t support named arguments, the values of the flags are meaningless, and each time we come across a function call like the examples above, we have to search for the function definition. The code can be made more readable by using descriptive string values, instead of booleans.

```
// Correct
function eat( $what, $speed = 'slowly' ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', 'slowly' );
eat( 'dogfood', 'quickly' );
```

### Space Usage

Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators.

```
x == 23
foo && bar
! foo
array( 1, 2, 3 )
$baz . '-5'
$term .= 'X'
```
Put spaces on both sides of the opening and closing parenthesis of `if`, `elseif`, `foreach`, `for`, and `switch` blocks.

```
foreach ( $foo as $bar ) { ...
```

When defining a function, do it like so:

```
function my_function( $param1 = 'foo', $param2 = 'bar' ) { ...
```

When calling a function, do it like so:

```
my_function( $param1, func_param( $param2 ) );
```

When performing logical comparisons, do it like so:

```
if ( ! $foo ) { ...
```

When [type casting](http://www.php.net/manual/en/language.types.type-juggling.php#language.types.typecasting), do it like so:

```
foreach ( (array) $foo as $bar ) { ...

$foo = (boolean) $bar;
```

When referring to array items, only include a space around the index if it is a variable, for example:

```
$x = $foo['bar']; // correct
$x = $foo[ 'bar' ]; // incorrect

$x = $foo[0]; // correct
$x = $foo[ 0 ]; // incorrect

$x = $foo[ $bar ]; // correct
$x = $foo[$bar]; // incorrect
```

### Some useful information

* Ternary Operator :

    [Ternary](http://en.wikipedia.org/wiki/Ternary_operation) operators are fine, but always have them test if the statement is true, not false. Otherwise, it just gets confusing. (An exception would be using `! empty()`, as testing for false here is generally more intuitive.)

    For example:

    ```
// (if statement is true) ? (do this) : (else, do this);
$musictype = ( 'jazz' == $music ) ? 'cool' : 'blah';
// (if field is not empty ) ? (do this) : (else, do this);
    ```

* Yoda Conditions:

    ```
if ( true == $the_force ) {
    $victorious = you_will( $be );
}
    ```

    When doing logical comparisons, always put the variable on the right side, constants or literals on the left.

    In the above example, if you omit an equals sign (admit it, it happens even to the most seasoned of us), you’ll get a parse error, because you can’t assign to a constant like `true`. If the statement were the other way around `( $the_force = true )`, the assignment would be perfectly valid, returning `1`, causing the if statement to evaluate to `true`, and you could be chasing that bug for a while.

    A little bizarre, it is, to read. Get used to it, you will.

    This applies to ==, !=, ===, and !==. Yoda conditions for <, >, <= or >= are significantly more difficult to read and are best avoided.

* **Important:** Never use shorthand PHP start tags. Always use full PHP tags.

    Correct:
    ```
<?php ... ?>
<?php echo $var; ?>
    ```

    Incorrect:
    ```
<? ... ?>
<?= $var ?>
    ```

* Error Control Operator `@` : ***PHP supports one error control operator: the at sign (@). When prepended to an expression in PHP, any error messages that might be generated by that expression will be ignored.***

    While this operator does exist in Core, it is often used lazily instead of doing proper error checking. Its use is highly discouraged, as even the PHP docs also state:

    ***Warning: Currently the “@” error-control operator prefix will even disable error reporting for critical errors that will terminate script execution. Among other things, this means that if you use “@” to suppress errors from a certain function and either it isn’t available or has been mistyped, the script will die right there with no indication as to why.***

* Remove trailing whitespace at the end of each line of code. Omitting the closing PHP tag at the end of a file is preferred. If you use the tag, make sure you remove trailing whitespace.

* Don’t `extract()` : `extract()` is a terrible function that makes code harder to debug and harder to understand. We should discourage it’s use and remove all of our uses of it.

## Useful links

[WordPress coding standard for PHP](https://make.wordpress.org/core/handbook/coding-standards/php/)
