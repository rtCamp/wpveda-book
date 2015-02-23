#Translation Ready

###Translating Your Theme

**Refer for more details**: 
http://code.tutsplus.com/tutorials/translating-your-theme--wp-25014

1. Acquire or Create a POT File for Your WordPress Theme

POT stands for “Portable Object Template,” and a POT file (aka .po file) is basically a list of all the English-language text found within the files of a localized WordPress theme.

2. Translate the POT File and Upload to Your Theme Folder

Once you have the POT file, you’ll need to open it in a program like POEdit, and translate the English language into your preferred language. When complete, you’ll want to save the file twice, as two separate files – a .po file and a .mo file. When you save the files, you must name them according to your language code.

3. Tell WordPress What Language to Use

If your theme does not already include it, you’ll need to add the following line to the very top of your functions.php file (just before the opening <?php tag):

```  
load_theme_textdomain('text_domain');

```

Notice “text_domain” above – it’s called the text domain name. You can use any name you want, but you should use the same name that’s used throughout the theme in the gettext function.

So, for example, if your gettext functions look something like this:

```  
 _e("About the Author", "text_domian"); 

```

You’ll want to use “wp-inspired” in place of the text_domain above.

Finally, if you haven’t done so already, you’ll need to make sure your wp-config.php file matches your language files. For example, if you’re using a French translation, you’ll need to add the fr_FR.po and fr_FR.mo files to your theme folder, then set your language in wp-config.php, like this:

```
define ('WPLANG', 'fr_FR');
```

By the way, your wp-config.php file is located in the main directory where all your core WordPress files are located.

Save your wp-config.php file, upload it to your WordPress installation, and you are ready to go.

**Refer for more details: **
https://make.wordpress.org/polyglots/handbook/translating/basics/

