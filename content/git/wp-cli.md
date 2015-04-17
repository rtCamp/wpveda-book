# WP-CLI

TODO:
1. ~~using wp-cli~~
2. ~~useful wp-cli plugins~~
3. userful core wp-cli commands list

## What is wp-cli

A command line interface for WordPress

WP-CLI is a set of command-line tools for managing WordPress installations. You can update plugins, set up multisite installs and much more, without using a web browser.
## Let's Install wp-cli

Download wp-cli.phar using curl or wget
```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
```
or
```bash
wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
```
Check if it works using following command
```
php wp-cli.phar --info
```
Now, we don't want to use `php wp-cli.phar` as command so let's put it somewhere in path so we can use it as `wp`.
```bash
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```
try running `wp --info`

For all command list run `wp help` you can also run help for subcommand `wp help plugin`

Refer: [wp-cli homepage](http://wp-cli.org/) if any error occurs during installation.


## Useful wp-cli plugin commands
So before you try this command go to your wordpress installation directory. (/var/www/{example.com}/htdocs/)

Let’s try to install the Hello Dolly plugin from wordpress.org:
``` bash
wp plugin install hello-dolly
```

Output:
```bash
Installing Hello Dolly (1.5)

Downloading install package from http://downloads.WordPress.org/plugin/hello-dolly.1.5.zip ...
Unpacking the package ...
Installing the plugin ...
Plugin installed successfully.
```

####SUB-COMMANDS

`wp plugin {command-name} {plugin-name}` manage plugin.

| Name          | Description |
| --            | -- |
| active        | Active a plugin. |
| deactive      | Deactivate a plugin. |
| delete        | Delete plugin files. |
| get           | Get a plugin. |
| install       | Install a plugin. |
| is-installed  | Check if the plugin is installed. |
| list      	| Get a list of plugins. |
| path      	| Get the path to a plugin or to the plugin directory.|
| search	    | Search the wordpress.org plugin repository.|
| status    	| See the status of one or all plugins.|
| toggle	    | Toggle a plugin's activation state.|
| uninstall 	| Uninstall a plugin.|
| update    	| Update one or more plugins. |


## Requirements
* UNIX-like environment (OS X, Linux, FreeBSD, Cygwin)
* PHP 5.3.2 or later
* WordPress 3.5.2 or later
