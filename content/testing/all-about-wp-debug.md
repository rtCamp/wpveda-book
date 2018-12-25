### How to open wp-c

### 

### All about WP Debug

WP\_DEBUG is a PHP constant that can be used to trigger the **debug mode** throughout WordPress. It is assumed to be false by default and is usually set to true in the **wp-config.php** file on development copies of WordPress.

There are other constants used along with WP\_DEBUG constant. Let’s understand the usage of these constants in detail.

1. **WP\_DEBUG**

   To enable debugging mode, add the following line to the wp-config.php file

   `define('WP_DEBUG', true);`

2. **WP\_DEBUG\_LOG**

   When WP\_DEBUG\_LOG and WP\_DEBUG are enabled, WordPress saves all error information to the debug.log file in the wp-content directory. By default, this setting is disabled.

   To enable this setting, add the following line to the wp-config.php file:

   `define('WP_DEBUG_LOG', true);`

3. **WP\_DEBUG\_DISPLAY**

   When WP\_DEBUG\_DISPLAY and WP\_DEBUG are enabled, WordPress displays error and warning messages on web pages. By default, this setting is enabled. When this setting is disabled, debugging messages are hidden from view.

   To disable this setting, add the following line to the wp-config.php file:

   `define('WP_DEBUG_DISPLAY', false);`

4. **SCRIPT\_DEBUG**

   When SCRIPT\_DEBUG is enabled, WordPress uses development versions of core CSS and JavaScript files instead of the compressed versions that it normally uses. By default, this setting is disabled. You can use this setting to test modifications to built-in .js or .css files.

   To enable this setting, add the following line to the wp-config.php file:

   `define('SCRIPT_DEBUG', true);`

   #### **Putting it All Together**

   > **    
   > **// Turn debugging on  
   > define\('WP\_DEBUG', true\);  
   >   
   > // Tell WordPress to log everything to /wp-content/debug.log  
   > define\('WP\_DEBUG\_LOG', true\);  
   >   
   > // Turn off the display of error messages on your site  
   > define\('WP\_DEBUG\_DISPLAY', false\);  
   >   
   > // For good measure, you can also add the following code, which will hide errors from being displayed on-screen  
   > @ini\_set\('display\_errors', 0\);

   _**NOTE:** Don’t forget that WP\_DEBUG is for local development use and should not be used on live sites._

Read more about WP\_DEBUG - [https://codex.wordpress.org/WP\_DEBUG](https://codex.wordpress.org/WP_DEBUG)

