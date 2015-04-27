#Plugin file sturcture

Suggested:

```
├── README.txt
├── sample-plugin.php
├── app
├── assests
├── bin
├── languages
├── lib
├── templates
├── tests
└── vendor
```

TODO
1. Finalize a structure to cover edge cases
2. folders which are not needed by a plugin will be marked optional
3. Explain purpose each file/folder

#### 1. README.txt
It is good practice to write readme.txt file because this file give plugin summary and milestone.

In readme.txt file, mainly three sections will covered `Description`, `Installation`, `Changelog`. You can decribe plugin summary using this sections.

**Reference:** https://wordpress.org/plugins/about/readme.txt

#### 2. sample-plugin.php
This the main file of plugin where you can add plugin information header and starting writing of plugin. You can also change file name like `index.php` or based on plugin name like `akismet.php (Akismet Plugin)`.

Wordpress determine entry point/main file of plugin by using plugin information header.

**Standard plugin information header** lets WordPress recognize that your Plugin exists, add it to the Plugin management screen so it can be activated, load it, and run its functions; without the header, your Plugin will never be activated and will never run. Here is the header format:

```
<?php
/**
 * Plugin Name: Name of the plugin, must be unique.
 * Plugin URI: http://URI_Of_Page_Describing_Plugin_and_Updates
 * Description: A brief description of the plugin.
 * Version: The plugin's version number. Example: 1.0.0
 * Author: Name of the plugin author
 * Author URI: http://URI_Of_The_Plugin_Author
 * Text Domain: Optional. Plugin's text domain for localization. Example: mytextdomain
 * Domain Path: Optional. Plugin's relative directory path to .mo files. Example: /locale/
 * Network: Optional. Whether the plugin can only be activated network wide. Example: true
 * License: A short license name. Example: GPL2
 */
 ```
 **Reference:** https://codex.wordpress.org/Writing_a_Plugin

#### 3. app

#### 4. assests
This folder contain `css`, `js`, `images`, `fonts` subfolder and each sub folder contain respective files.

#### 5. bin

#### 6. languages
Contain languages files `(.pot, .mo)` for multiple language support in plugin.

**Reference:**
http://premium.wpmudev.org/blog/localize-a-wordpress-plugin-and-make-it-translation-ready/

#### 7. lib

#### 8. templates
This folder contain templates files of your plugin. And also you can give option to developer to override your plugin template files in theme folder.

#### 9. tests
This folder contain your test cases files like phpunit test cases.

**Referenc:**
https://pippinsplugins.com/unit-tests-wordpress-plugins-introduction/

#### 10. vendor
