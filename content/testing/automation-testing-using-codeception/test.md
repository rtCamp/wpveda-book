### Codeception Setup Guide line

Codeception is a PHP Testing Framework. It is very easy to install and set up test environment in your system. You can write your automation test cases in your favourite text editor/IDE and run them in the browser you wish. Let’s see everything in details:

#### Why use Codeception?

* It combines all testing types \(acceptance, functional and unit\)
* Has support for in built WordPress functions. Supported functions can be checked here -&gt; [https://github.com/lucatume/wp-browser](https://github.com/lucatume/wp-browser)
* Good documentation is available here -&gt; [http://codeception.com/docs/modules/WebDriver](http://codeception.com/docs/modules/WebDriver)
* Tests can be executed using Firefox, Chrome, Safari and other browsers including PhantomJS with Selenium WebDriver or using cloud testing services like BrowserStack, saucelab etc.
* Tests can be executed inside a PHP framework. Supported frameworks are Symfony, Laravel, Zend Framework, Yii, Phalcon etc
* Codeception simplifies REST and SOAP testing. There are flexible commands to test structure and data of JSON and XML responses.
* Codeception supports Behavior Driven Development\(BDD\)
* It is very popular in WordPress companies. VIP partners like 10up, XWP, rtCamp use it to test their projects.

#### Installing Codeception

You can install the codeception either way explain below.

1. Using Composer
2. Using PHAR file

I have set up my system using **composer **though you can choose any option, whichever works best for you. If you want to install using the second method, please check this [link](http://codeception.com/install). Alternatively, please keep reading this article for the first method.

#### Installing Composer

```
curl -sS https://getcomposer.org/installer | php
```

Check [this](https://getcomposer.org/doc/00-intro.md) link for more information about composer.

#### Running Composer

The resulting file is **composer.phar**, a PHP Archive that can be executed directly via PHP. Execute command below in order to run Composer.

```
php composer.phar
```

However, we want composer to be accessible **globally **by simply typing composer. To do this, move it to`/usr/local/bin/`

```
sudo mv composer.phar /usr/local/bin/
```

Now, add below line to`~/.bash_profile`file

```
nano ~/.bash_profile
alias composer="php /usr/local/bin/composer.phar"
```

Now, reopen the terminal and run

```
composer
```

----Screen------

#### Installing Codeception

Now to the Project folder and create `tests` directory where you want to place the automated test cases.

E.g. If you are working on Automation of **XYZ** Plugin then go the plugin directory and create and test directory inside `XYZ` proejct folder.

Inside the `test` directory create one `composer.json` file and add the below lines of code and save it.

> {
>
>     "require": {
>
>     },
>
>     "require-dev": {
>
>         "lucatume/wp-browser": "\*"
>
>     }
>
> }

Now, open the terminal and jump till the `test` folder. Run the below command which will install the codeception for you.

```
composer update
```

_If you have any doubt regarding composer install v/s composer update then please read _[_here_](https://stackoverflow.com/questions/33052195/what-are-the-differences-between-composer-update-and-composer-install)_. _

Once it is installed, you can cross check the same by relaunching the terminal and execute the below command. Which will show you the installed codeception version along with different commands and usage.

```
codecept
```

#### ![](/assets/1.jpg)

#### Setup Codeception for Project



