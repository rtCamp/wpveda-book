#Translation Ready

Wordpress is used All over the world, As developer you may need to provide your plugin/theme to diffrent languages speaking users, It will be good idea if you create your theme/plugin translation ready.

### How translation happens ?

Wordpress uses gettext libraries for translation 
1. Developer are required to wrap translable stings into special functions
2. Special tools like POEdit used to parse code files and extract translatable content to get POT file
3. This POT files are sent to glotpress which retruns PO files which are translated files
4. PO files are compiled to MO files which are faster to access because they are machine readable

### Configuring Site for trasnlation
* Acquire or Create a POT File for Your WordPress Theme

POT stands for “Portable Object Template,” and a POT file (aka .po file) is basically a list of all the English-language text found within the files of a localized WordPress theme.

* Translate the POT File and Upload to Your Theme Folder

Once you have the POT file, you’ll need to open it in a program like POEdit, and translate the English language into your preferred language. When complete, you’ll want to save the file twice, as two separate files – a .po file and a .mo file. When you save the files, you must name them according to your language code.

* Tell WordPress What Language to Use

If your theme does not already include it, you’ll need to add the following line to the very top of your functions.php file (just after the opening <?php tag):

```  
load_theme_textdomain('text_domain');

```

Notice “text_domain” above – it’s called the text domain name. You can use any name you want, but you should use the same name that’s used throughout the theme in the gettext function.
#### Best Practices 

You may want to define a constant for your text domain later on it will be hepful in your translation, check example below

```
// Define Text domain consant
define( 'MY_THEME_TEXT_DOMAIN', 'text-domain' );
//load text domain with constant
load_theme_textdomain( MY_THEME_TEXT_DOMAIN );
//User Constants in gettext functions
_e( 'Hello World',MY_THEME_TEXT_DOMAIN );
```

## Gettext functions
There are four main gettext functions
* ```__()``` Basic funcion that will returs trasnlated text.
* ```_e()``` It has same function as ```__()``` but it echos the output.
* ```_n()``` Checks for possible pural string
* ```_x()``` Useful for when the translation of the word depends on the context.

### ```__()``` && ```_e()```
Both function are basic function for translation, lets check out example for each
```
 echo __( 'Hello World', 'text-domain' );
 _e( 'Hello World', 'text-domain' );
```
Both functions worked same way except ```__()``` returns string and  ```_e()``` echos it.

What if we have php variable in string, lets say we want to display color

```
$color=the_color();
_e('the sky is $color', 'text-domain')
```
Above example wont work because it will try to find `the sky is blue` which it wont be able to find, instead we can do like followings

```
echo __('the sky is ', 'text-domain'). $color;
```
OR
```
printf( __( 'the skye is %s', 'text-domain' ),  $color );
//OR
echo sprintf( __( 'the skye is %s', 'text-domain' ),  $color );
```
### ``` _n() ```
The `_n()` function is used to parse pural string, you can use this function when your output is dependent. 

eg :

Spam deletion, What if we delete only one spam? The output will be: "We deleted 1 spam messages.", which is definitely not correct English, and would certainly be incorrect for many other languages as well. 

```
printf( _n( 'We deleted one spam message.', 'We deleted %d spam messages.', $count, 'text-domain' ), $count );
```
So if we deleted one spam message it will show `We deleted one spam message.`
if it has more than one the it will show `We deleted 10 spam messages.`

### ```_x()``` && ```_ex()```
Sometimes a single term is used in several contexts. Although it is one and the same word in English, it may need to be translated differently in some languages. For example, the word "Post" can be used both as a verb ("Click here to post your comment") and as a noun ("Edit this post").

In such cases, the `_x()` function should be used. It is similar to `__()`, but it has an additional second argument.

```
echo _x( 'post link' , 'A link to the post', 'text-doamin' );
_ex( 'post link' , 'Submit a link', 'text-domain' );
```
### Other functions
the other functio are mostly puporse dependent or hybrid
* ```_nx()``` A hybrid of `_n()` and `_x()`. It supports contexts and plurals.

```
    _nx( $single, $plural, $number, $context, $domain );
```

* ```esc_attr_x()```Retrieves the translation of `$text` in a gettext context, and escapes it for safe use in an attribute

```
    esc_attr_x( $text, $context, $domain );
```

* ```esc_html_x()``` Retrieves the translation of $text in a gettext context, and escapes it for safe use in HTML.

```
    esc_html_x( $text, $context, $domain );  
```

Finally, if you haven’t done so already, you’ll need to make sure your wp-config.php file matches your language files. For example, if you’re using a French translation, you’ll need to add the fr_FR.po and fr_FR.mo files to your theme folder, then set your language in wp-config.php, like this:

```
define ('WPLANG', 'fr_FR');
```

By the way, your wp-config.php file is located in the main directory where all your core WordPress files are located.

Save your wp-config.php file, upload it to your WordPress installation, and you are ready to go.

**Refer for more details: **

Wordpress : http://codex.wordpress.org/I18n_for_WordPress_Developers

Make Wordpress : https://make.wordpress.org/polyglots/handbook/translating/basics/

Code Tutplus : http://code.tutsplus.com/tutorials/translating-your-theme--wp-25014

