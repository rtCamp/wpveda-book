# Code Sniffer

**First Check if phpcs is installed or not**

`which phpcs`  
It should return path of current phpcs installation.   
If returned nothing probably phpcs is not installed.

`phpcs --version`   
To check which version you're using. Always try to get latest version. Head out to [https://github.com/squizlabs/PHP\_CodeSniffer/releases](https://github.com/squizlabs/PHP_CodeSniffer/releases) to check latest version.

## Install or update.

Depends on method you've installed phpcs you need to update.

### Composer install or update.

Assuming you have php and [composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx) pre installed.

Go to composer dir `cd ~/.composer`

`composer global require "squizlabs/php_codesniffer=*"`

`composer update squizlabs/php_codesniffer` to update if you already have installed.

Then you can check version by doing `./vendor/bin/phpcs --version`  
Add `~/.composer/vendor/bin` to $PATH in `.bashrc` or `.zshrc` and reload terminal or open new tab.

### Or Direct download

```
curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && chmod +x phpcs.phar && mv phpcs.phar /usr/local/bin/phpcs
curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar && chmod +x phpcbf.phar && mv phpcbf.phar /usr/local/bin/phpcbf
```

`/usr/local/bin/` You can change this to custom path like `~/.bin` and add that custom path to $PATH as mentioned above in composer install section.

### Install WPCS and PHPCompatibility

You can install WPCS via git repo as mentioned below.

```
cd ~/Documents
mkdir Coding-Standards && cd $_
git clone -b master https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git wpcs
git clone -b master https://github.com/wimg/PHPCompatibility.git PHPCompatibility
pwd # copy this
ln -s {paste here}/PHPCompatibility/PHPCompatibility wpcs/PHPCompatibility
phpcs --config-set installed_paths {Paste here again}/wpcs # remember this path
```

Note: you can also install WPCS via composer.

### Check and Fix phpcs path

Try `phpcs -i` it should show WordPress, PHPCompatibility, WordPress-Extra, WordPress-Docs, WordPress-Core ruleset there.

If somehow it doesn't show you, you need to exec last command `phpcs --config-set...` again. \(you should do this everywhere you update phpcs\)

### Update WPCS and PHPCompatibility

```
phpcs --config-show
```

Copy path given in installed\_paths. If you don't get that path check above section on how to fix that.

```
cd {Paste here}
git pull origin master 
cd PHPCompatibility
git pull origin master
```

Note: You should update wpcs every month or so or on every release.

