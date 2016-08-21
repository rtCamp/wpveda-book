Σελίδες διαχείρισης του WordPress
=====================

Αν δημιουργείτε ένα πρόσθετο/θέμα για το WordPress υπάρχουν περιστάσεις που πρέπει να δημιουργήσετε σελίδες στον πίνακα ελέγχου.

Υπάρχουν δυο τύποι σελίδων για των πίνακα ελέγχου

1.Σελίδες ανώτερου επιπέδου (Top-Level)

2.Σελίδες κατώτερου επιπέδου (Sub-Level)

#### 1. Σελίδες ανώτερου επιπέδου

Η ακόλουθη συνάρτηση θα δημιουργήσει ένα νέο μενού στην πλευρική μπάρα μενού του πίνακα ελέγχου.

Η συνάρτηση `add_menu_page()` χρησιμοποιείτε για να δημιουργήσει ένα μενού ανώτερου επιπέδου.

```php
<?php
add_menu_page( $τίτλος_σελίδας, $τίτλος_μενού, $δικαιώματα_πρόσβασης, $slug_μενού, $συνάρτηση, $url_εικονιδίου, $θέση );
?>
```

###### Παράδειγμα

```php
<?php
add_action( 'admin_menu', 'register_my_custom_menu_page' );

function register_my_custom_menu_page(){
   add_menu_page( 'Ο τίτλος της σελίδας', 'Νέο μενού', 'manage_options', 'custompage', 'my_custom_menu_page', plugins_url( 'myplugin/images/icon.png' ), 6 );
   }

function my_custom_menu_page(){
   echo "Δοκιμαστική σελίδα...";
   }
?>
```

#### 2. Σελίδες κατώτερου επιπέδου

Για την δημιουργία σελίδες κατώτερου επιπέδου στον πίνακα διαχείρισης υπάρχει διαφορετική συνάρτηση.

Η συνάρτηση `add_submenu_page()` χρησιμοποιείτε για να προσθέσει μια σελίδα κατώτερου επιπέδου σε όποιο μενού θέλετε.

```php
<?php
add_submenu_page( $parent_slug, $τίτλος_σελίδας, $τίτλος_μενού, $capability, $menu_slug, $συνάρτηση );
?>
```

`$parent_slug` είναι το slug του γονικού μενού. Για παράδειγμα -

Για να προσθέσετε ένα μενού κατώτερου επιπέδου στο μενού Πίνακας ελέγχου μπορείτε να χρησιμοποιήσετε στο `$parent_slug` το `index.php`

Για να προσθέσετε ένα μενού κατώτερου επιπέδου στο μενού άρθρα μπορείτε να χρησιμοποιήσετε στο `$parent_slug` το `edit.php`

και πάει λέγοντας

###### Παράδειγμα

```php
<?php
add_action('admin_menu', 'register_my_custom_submenu_page');

function register_my_custom_submenu_page() {
   add_submenu_page( 'edit.php', 'Σελίδα κατώτερου επιπέδου', 'Σελίδα κατώτερου επιπέδου', 'manage_options', 'my-custom-submenu-page', 'my_custom_submenu_page_callback' );
}

function my_custom_submenu_page_callback() {
echo '<div class="wrap"><div id="icon-tools" class="icon32"></div>';
    echo '<h2>Η δική μου σελίδα κατώτερου επιπέδου</h2>';
echo '</div>';
}
?>
```

Επιπλέον, τα εξ ορισμού μενού ανωτέρου επιπέδου, έχουν τις δικές τους συναρτήσεις για την προσθήκη μενού κατώτερου επιπέδου. Για παράδειγμα -

Για την προσθήκη μενού κατώτερου επιπέδου στα άρθρα μπορείτε να χρησιμοποιήσετε την συνάρτηση [add_posts_page](https://codex.wordpress.org/Function_Reference/add_posts_page)

Για την προσθήκη μενού κατώτερου επιπέδου στις σελίδες μπορείτε να χρησιμοποιήσετε την συνάρτηση [add_pages_page](https://codex.wordpress.org/Function_Reference/add_pages_page)

Για την προσθήκη μενού κατώτερου επιπέδου στις σελίδα με τα πολυμέσα μπορείτε να χρησιμοποιήσετε την συνάρτηση [add_media_page](https://codex.wordpress.org/Function_Reference/add_media_page)

και πάει λέγοντας.

###### Παράδειγμα

```php
<?php
add_action('admin_menu', 'my_plugin_menu');

function my_plugin_menu() {
  add_posts_page('Υπό σελίδα στα άρθρα για το πρόσθετο μου', 'Πρόσθετο', 'read', 'my-unique-identifier', 'my_plugin_function');
  }
?>
```

#### Αναφορές

https://codex.wordpress.org/Creating_Options_Pages

https://codex.wordpress.org/Function_Reference/add_menu_page

https://codex.wordpress.org/Function_Reference/add_submenu_page

http://premium.wpmudev.org/blog/creating-wordpress-admin-pages/?nlpd=b&utm_expid=3606929-34.mZctMukzSv6Wvz3lKaD43w.1&utm_referrer=https%3A%2F%2Fwww.google.co.in%2F