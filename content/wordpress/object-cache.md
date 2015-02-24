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

##Emample
In the below example, imagine the $query variable is an expensive SQL query.

$result = wp_cache_get( 'my_result' );
if ( false === $result ) {
	$result = $wpdb->get_results( $query );
	wp_cache_set( 'my_result', $result );
}
// Do something with $result;



##Note
As the objects are stored in memory, you need to consider that these objects can be cleared at any time and that your code must be constructed in a way that it would not rely on the objects being in place.
