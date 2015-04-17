# WordPress Object Cache

TODO:
1. How to use it?
2. When to use it?
3. examples
4. reference links

##What is object cache ?

Caching is simply the act of storing computed data somewhere for later use, and is an incredibly important concept in WordPress. There are different ways to employ caching, and often multiple methods will be used.

The "Object Cache"

Object caching is the act of caching data or objects for later use. In the context of WordPress, objects are cached in memory so they can be retrieved quickly.

In WordPress, the object cache functionality provided by [WP_Object_Cache](http://codex.wordpress.org/Class_Reference/WP_Object_Cache), and the [Transient API](http://codex.wordpress.org/Transients_API) are great solutions for improving performance on long-running queries, complex functions, or similar.

On a regular WordPress install, the difference between transients and the object cache is that transients are persistent and would write to the options table, while the object cache only persists for the particular page load.


##When to use it ?
[WP_Object_Cache](http://codex.worhttp://memcached.org/dpress.org/Class_Reference/WP_Object_Cache) is WordPress' class for caching data which may be computationally expensive to regenerate, such as the result of complex database queries.

The advantage of using the WP_Object_Cache class is primarily performance. Using this class allows you to extend WordPress to use the absolute best caching engines in the world. For instance, using [Memcached](http://memcached.org/) as WordPress’ object cache gives ridiculously fast data access that easily scales to multiple servers. [Memcached](http://memcached.org/) is an important caching engine for use with high traffic websites. With the WP_Object_Cache class, developers can finely tune the caching experience in WordPress, whereas using the transients API gives you very little control over the caching engine. Relating this class back to the metaphor, the WP_Object_Cache class allows you to precisely decide where your food will be stored.


#####[Wordpress object cache functions](http://codex.wordpress.org/Class_Reference/WP_Object_Cache#wp_cache_functions)

This function adds data to the cache if the cache key doesn't already exist. If it does exist, the data is not added and the function returns false.

````ruby
wp_cache_set( $key, $data, $group, $expire )
````

Adds data to the cache. If the cache key already exists, then it will be overwritten; if not then it will be created.

````ruby
wp_cache_get( $key, $group )
wp_cache_get( $key, $group = '', $force = false, $found = null )
````

Returns the value of the cached object, or false if the cache key doesn't exist.

````ruby
wp_cache_get( $key, $group )
wp_cache_get( $key, $group = '', $force = false, $found = null )
````


##Emamples
In the below example, imagine the $query variable is an expensive SQL query.

````ruby
$result = wp_cache_get( 'my_result' );
if ( false === $result ) {
	$result = $wpdb->get_results( $query );
	wp_cache_set( 'my_result', $result );
}
````

Retrieve top 10 most-commented posts and cache the results.
````ruby
function prefix_get_top_commented_posts() {
    // Check for the top_commented_posts key in the 'top_posts' group.
    $top_commented_posts = wp_cache_get( 'prefix_top_commented_posts', 'top_posts' );

    // If nothing is found, build the object.
    if ( false === $top_commented_posts ) {
        // Grab the top 10 most commented posts.
        $top_commented_posts = new WP_Query( 'orderby=comment_count&posts_per_page=10' );

        if ( ! is_wp_error( $top_commented_posts ) && $top_commented_posts->have_posts() ) {
            // Cache the whole WP_Query object in the cache and store it for 5 minutes (300 secs).
            wp_cache_set( 'prefix_top_commented_posts', $top_commented_posts, 'top_posts', 5 * MINUTE_IN_SECONDS )
        }
    }
    return $top_commented_posts;
}
````
In the above example, the cache is checked for an object with the 10 most commented posts and would generate the list in case the object is not in the cache yet. Generally, calls to WP_Query other than the main query should be cached.

As the content is cached for 300 seconds, the query execution is limited to one time every 5 minutes, which is nice.

However, the cache rebuild in this example would always be triggered by a visitor who would hit a stale cache, which will increase the page load time for the visitors and under high-traffic conditions. This can cause race conditions when a lot of people hit a stale cache for a complex query at the same time. In the worst case, this could cause queries at the database server to pile up causing replication, lag, or worse.

That said, a relatively easy solution for this problem is to make sure that your users would ideally always hit a primed cache. To accomplish this, you need to think about the conditions that need to be met to make the cached value invalid. In our case this would be the change of a comment.

The easiest hook we could identify that would be triggered for any of this actions would be wp_update_comment_count set as do_action( 'wp_update_comment_count', $post_id, $new, $old ).

````ruby
/**
 * Prime the cache for the top 10 most-commented posts.
 *
 * @param int $post_id Post ID.
 * @param int $new     The new comment count.
 * @param int $old     The old comment count.
 */
function prefix_refresh_top_commented_posts( $post_id, $new, $old ) {
    // Force the cache refresh for top-commented posts.
    prefix_get_top_commented_posts( $force_refresh = true );
}
add_action( 'wp_update_comment_count', 'prefix_refresh_top_commented_posts', 10, 3 );

function prefix_get_top_commented_posts( $force_refresh = false ) {
    // Check for the top_commented_posts key in the 'top_posts' group.
    $top_commented_posts = wp_cache_get( 'prefix_top_commented_posts', 'top_posts' );

    // If nothing is found, build the object.
    if ( true === $force_refresh || false === $top_commented_posts ) {
        // Grab the top 10 most commented posts.
        $top_commented_posts = new WP_Query( 'orderby=comment_count&posts_per_page=10' );

        if ( ! is_wp_error( $top_commented_posts ) && $top_commented_posts->have_posts() ) {
            // In this case we don't need a timed cache expiration.
            wp_cache_set( 'prefix_top_commented_posts', $top_commented_posts, 'top_posts' )
        }
    }
    return $top_commented_posts;
}
````

##Important Notes
- As the objects are stored in memory, you need to consider that these objects can be cleared at any time and that your code must be constructed in a way that it would not rely on the objects being in place.
- The storage size is limited by the total available memory for PHP on the server. Do not store large data sets, or you might end up with an “Out of memory” message.0
- Using this type of cache makes sense only for operations repeated more than once in the creation of a page.
- It works with WordPress since version 2.0.

##Refence links

1. http://codex.wordpress.org/Class_Reference/WP_Object_Cache
2. https://10up.github.io/Engineering-Best-Practices/php/#performance
3. https://www.tollmanz.com/core-caching-concepts-in-wordpress/
