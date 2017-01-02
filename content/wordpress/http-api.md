# HTTP API

Within PHP, there are many possible ways for sending HTTP requests. Examples include `file_get_contents`, `fsockopen`, and `cURL` but developers have to support it afterwards to keep them working.

The WordPress HTTP API was created to standardize a single API that handled everything with regards to HTTP as simply as possible. The HTTP API supports various PHP HTTP transports or implementations to cater for different hosting environments and configurations.

Wordpress has following methods for sending HTTP requests.

* [wp\_remote\_get\(\)](https://codex.wordpress.org/Function_Reference/wp_remote_get) – send HTTP GET method requests.

* [wp\_remote\_post\(\)](https://codex.wordpress.org/Function_Reference/wp_remote_post) – send HTTP POST requests.

* [wp\_remote\_head\(\)](https://codex.wordpress.org/Function_Reference/wp_remote_head) – send HTTP HEAD requests.

* [wp\_remote\_request\(\)](https://codex.wordpress.org/Function_Reference/wp_remote_request) – send requests using any custom HTTP method, be it GET, POST, HEAD, PUT or DELETE.


#### How to use it

```php
<?php $response = wp_remote_get( $url, $args ); ?>
```

Where `$url` is the site url to retrieve and `$args` is the array. This functions will return an array in the response.

To retrieve the different parts of response wordpress has provided following helper functions.

* [wp\_remote\_retrieve\_body\(\)](http://codex.wordpress.org/Function_Reference/wp_remote_retrieve_body) - Retrieves just the body from the response.

* [wp\_remote\_retrieve\_headers\(\)](http://codex.wordpress.org/Function_Reference/wp_remote_retrieve_headers) - Retrieves headers from response.

* [wp\_remote\_retrieve\_response\_code\(\)](http://codex.wordpress.org/Function_Reference/wp_remote_retrieve_response_code) - Retrieves the response code.


#### Example

```php
<?php
$url = "http://www.example.com/index.php?action=foo";
$args = array(
'timeout' => 120,
'httpversion' => '1.1',
'headers' => array( "Content-type" => "application/json" ),
);
$response = wp_remote_get( $url, $args );
if ( is_wp_error( $response ) ) {
   $error_message = $response->get_error_message();
   echo "Something went wrong: $error_message";
} else {
   $response_body = wp_remote_retrieve_body( $response );
   echo 'Response:<pre>';
   print_r( $response_body );
   echo '</pre>';
}

?>
```

#### Reference

[http:\/\/codex.wordpress.org\/Function\_Reference\/wp\_remote\_get](http://codex.wordpress.org/Function_Reference/wp_remote_get)

[http:\/\/codex.wordpress.org\/Function\_Reference\/wp\_remote\_retrieve\_body](http://codex.wordpress.org/Function_Reference/wp_remote_retrieve_body)

[http:\/\/www.sitepoint.com\/the-wordpress-http-api\/](http://www.sitepoint.com/the-wordpress-http-api/)

