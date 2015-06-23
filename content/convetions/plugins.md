#Plugin file structure

Suggested:

```
.
|-- admin
|-- assets
|-- bin
|-- build
|-- includes
|-- index.php
|-- languages
|-- lib
|-- LICENSE.txt
|-- plugin-name.php
|-- public
|-- README.txt
|-- tests
|-- uninstall.php
`-- vendor
```

TODO
1. Finalize a structure to cover edge cases
2. folders which are not needed by a plugin will be marked optional
3. Explain purpose each file/folder

Plugin divided into major three part and many other optional part.


### 1. admin
Admin folder contains classes and assets which is use only admin side. It contains subfolder to store admin assets.
```
|-- admin
|   |-- class-plugin-name-admin.php
|   |-- css
|   |   `-- plugin-name-admin.css
|   |-- index.php
|   |-- js
|   |   `-- plugin-name-admin.js
|   |-- font
|   |-- img
|   |-- page
|   |-- classes
|   |   |-- prefix-modulename
|   |       |-- class-prefix-classname.php
|   |   |-- prefix-modulename2
|   |       |-- class-prefix-classname2.php
```
**class-plugin-name-admin.php** is class file which is responsible for admin side functionality.

**classes** is module structure for our plugin. Each module class will have prefix-modulename as parent folder. All module related classes will be clubbed in this folder.

**page** contains template file for wordpress admin page.

### 2. assets
The assets directory contains three files.

```
|-- assets
|   |-- banner-772x250.png
|   |-- icon-256x256.png
|   `-- screenshot-1.png
```

**banner-772x250.png** is used to represent the plugin’s header image.

**icon-256x256.png** is a used to represent the plugin’s icon image (which is new as of WordPress 4.0).

**screenshot-1.png** is used to represent a single screenshot of the plugin that corresponds to the “Screenshots” heading in your plugin README.txt.

When committing code to the WordPress Plugin Repository, all of the banner, icon, and screenshot should be placed in the assets directory of the Repository.

### 3. bin ( optional )
Bin folder contains binary file if existed. like media encoding file.

### 4. build
This folder stores script and other stuff which are use to build the application. This folder should not pushed on svn repository.

**Example**:  Pre-commit hook file, Travis script, Markdown generator etc.

You can find build script for wordpress plugin from https://github.com/xwp/wp-dev-lib

### 5. includes
Includes is folder where functionality shared between the admin area and the public-facing parts of the site reside

```
|-- includes
|   |-- class-plugin-name-activator.php
|   |-- class-plugin-name-deactivator.php
|   |-- class-plugin-name-i18n.php
|   |-- class-plugin-name-loader.php
|   |-- class-plugin-name.php
|   `-- index.php
```
Includes contains above file. every file has its own purpose.

**class-plugin-name-activator.php** is where contains code to perform on plugin activation hook.

**class-plugin-name-deactivator.php** is where contains code to perform on plugin deactivator hook.

**class-plugin-name-i18n.php** is contains code to support internationalize for plugin. it's contains code to support language file.

**class-plugin-name-loader.php** contains loaded class  which  is used to register all filters and actions with WordPress.

**class-plugin-name.php** is file which is load all part [ admin | public | include ] of plugin.

This class initialized loader class object and it's use in entire project to register action & hook.

### 6. languages
This folder contains languages files `(.pot, .mo)` for multiple language support in plugin.

**Reference:**
http://premium.wpmudev.org/blog/localize-a-wordpress-plugin-and-make-it-translation-ready/

### 7. lib ( optional )
Lib is where store code which is developed by us to use in plugin but this code may be used any other plugin also.

**Example**: Most of plugin need to deal with database to handle custom tables in wordpress.

There is class which is user to check plugin version and update database custom table on plugin version update.

This code may be use for other plugin so we keep that code on Lib folder and we can use same folder in other repository.

### 8.LICENSE.txt
This file contains plugin license information.

### 9.plugin-name.php
This the main file of plugin where you can add plugin information header and starting writing of plugin. You can also change file name like `index.php` or based on plugin name like `akismet.php (Akismet Plugin)`.

Wordpress determine entry point/main file of plugin by using plugin information header.

**Standard plugin information header** lets WordPress recognize that your Plugin exists, add it to the Plugin management screen so it can be activated, load it, and run its functions; without the header, your Plugin will never be activated and will never run. Here is the header format:

```
/**
 * plugin information
 *
 * @wordpress-plugin
 * Plugin Name:     Name of the plugin, must be unique.
 * Plugin URI:      http://URI_Of_Page_Describing_Plugin_and_Updates
 * Description:     A brief description of the plugin.
 * Version:         The plugin's version number. Example: 1.0.0
 * Author:          The plugin author
 * Author URI:      http//URI_Of_The_Plugin_Author
 * License:         A short license name. Example: GPL2
 * License URI:     http://www.gnu.org/licenses/gpl-2.0.txt
 * Text Domain:     Optional. Plugin's text domain for localization.
 *                  Example: mytextdomain
 * Domain Path:     Optional. Plugin's relative directory path to .mo files.
 *                  Example: /locale/
 * Network:         Optional. Whether the plugin can only be
 *                  activated network wide. Example: true
 */
 ```
 **Reference:** https://codex.wordpress.org/Writing_a_Plugin

### 10. public
public folder contains all public-facing functionality. It contains subfolder to store admin assets.
```
|-- public
|   |-- class-plugin-name-public.php
|   |-- css
|   |   `-- plugin-name-public.css
|   |-- index.php
|   |-- js
|   |   `-- plugin-name-public.js
|   |-- img
|   |-- font
|   |-- template

```

**class-plugin-name-public.php** is class to load public facing functionality.

**template** folder contains templates files of your plugin. And also you can give option to developer to override your plugin template files in theme folder.


### 11. README.txt
It is good practice to write readme.txt file because this file give plugin summary and milestone.

In readme.txt file, mainly three sections will covered `Description`, `Installation`, `Changelog`. You can describe plugin summary using this sections.

**Reference:** https://wordpress.org/plugins/about/readme.txt

### 12. tests
This folder contains your test cases files like phpunit & selenium test cases.
This folder contains two folder
```
|-- tests
|   |-- function-tests
|   `-- unit-tests
```
**function-tests** contains test cases files which are use to check functional testing.

**unit-tests** contains phpunit test cases files which are use to check unit testing

**Referenc:**
https://pippinsplugins.com/unit-tests-wordpress-plugins-introduction/


### 13. uninstall.php
This file contains code which are Fired when the plugin is uninstalled.

### 14. vendor
This folder contains third party libs like google oauth lib.


** Plugin structure reference: https://github.com/DevinVinson/WordPress-Plugin-Boilerplate **
