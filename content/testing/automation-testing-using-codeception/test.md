### Codeception Setup Guide line

Codeception is a PHP Testing Framework. It is very easy to install and set up test environment in your system. You can write your automation test cases in your favourite text editor/IDE and run them in the browser you wish. Let’s see everything in details:

#### Why use Codeception?

* It combines all testing types \(acceptance, functional and unit\)
* Has support for in built WordPress functions. Supported functions can be checked here -&gt; [https://github.com/lucatume/wp-browser](https://github.com/lucatume/wp-browser)
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

The resulting file is **composer.phar**, a PHP Archive that can be executed directly via PHP. Execute command below in order to run Composer.

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

Now, reopen the terminal and run

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
> ```
> "require": {
>
> },
>
> "require-dev": {
>
>     "lucatume/wp-browser": "\*"
>
> }
> ```
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

To fully use the WordPress specific modules of the **WPBrowser **suite you need to setup a local WordPress installation.

```
vendor/bin/codecept bootstrap
```

The above command \_**codecept bootstrap **\_creates the **codeception.yml file and** **tests directory. **Inside the tests directory it creates the **acceptance, functional and unit suites** a configuration file for each.

Edit the codeception.yml file to match your local WordPress setup and point the modules to the local WordPress installation folder, the local WordPress URL and so on.

#### Acceptance Test

Acceptance tests emulate the behaviour of a real user visiting your site.

You can use the **WebDriver module** defined by Codeception. The WPWebDriver module drives a real browser in the same way the WebDriver does. The modules require some WordPress specific parameters to work.

#### Configuring `tests/acceptance.suite.yml`

```
class_name: AcceptanceTester
modules:
    enabled:
        - \Helper\Acceptance
        - WPWebDriver
        - Asserts
    config:
        WPWebDriver:
            port: '<Port_ID>'
            browser: '<Browser_Name>'
            url: '<Test_Url>'
            adminUsername: ''
            adminPassword: ''
            adminPath: '/wp-admin'
```

Codeception scenario tests are called **Cepts**.

`vendor/bin.codecept generate:cept acceptance Login`

OR

`codecept generate:cept acceptance Login`

This command will generate **LoginCept.php **file under acceptance directory.

#### Write your sample scenario

```
<?php
$I = new AcceptanceTester($scenario);
$I->wantTo('sign in my web site');
$I->amOnPage('/wp-admin');
$I->fillfield('input#user_login','test');
$I->fillfield('input#user_pass','12345');
$I->seeElement( 'input#wp-submit' );
$I->click( 'input#wp-submit' );
$I->wait(5);
$I->seeElement( 'li#menu-dashboard' );
?
>
```

#### Understanding the Webdriver Module

The WPWebDriver module requires a**Selenium or PhantomJS server **to run. In order to run Selenium, you need to download Selenium Server and get it running. Alternatively, you may use PhantomJS headless browser but this is useful only if you want to run headless script. \(I use selenium server.\) This way you can see the actual output in the real browser in your **Local **system along with terminal will prompt which code line is being executed.

#### How to run scenario using Selenium Server

**1. Launch The Selenium Server**

1. Download [Selenium Server](https://www.seleniumhq.org/download/) if it isn’t there.
2. Launch the server with command :
   `java -jar selenium-server-standalone X.xx.xxx.jar`

**2. Launch the respective driver \(chrome or firefox\)**

> \_**NOTE:**\_To run the scenario in the browser you have to download the driver for the relevant browser. E.g. I want to run my test in chrome browser then you will need Chrome Driver. To run the scenario in Firefox browser you have to download the Gecko driver.

1. Download the latest [Chrome driver](https://sites.google.com/a/chromium.org/chromedriver/) OR [Firefox driver](https://github.com/mozilla/geckodriver/releases).
2. Move it to `/use/local/bin` to make it available globally.
3. For chrome, execute `chromedriver --url-base=/wd/hub`
4. For Firefox, execute`geckodriver`

**3. Run the Scenario using codecept command**

```
codecept run test/acceptance/LoginCept.php
```

### Cloud Testing

Sometimes you may need to test the site on different environments with a different set of browsers and OS which we call cross browser testing.

For example, you may need to test your website on IE browser with requested browser version on Windows OS and you are working on Mac or Linux System. So here comes the use of Cloud Testing where it provides you the different set of browsers along with browser versions and Operating System.

Cloud Testing services can run your WebDriver tests in the cloud. Codeception provides support for Browserstack, Sauce lab, TestingBot etc. You can choose your cloud and set up accordingly. We are using Browserstack for the same. You just need to set the WebDriver configuration to as explain below.

* Specify the host to connect to \(depends on the cloud provider\)
* Authentication details \(to use your account\)
* Browser
* OS

Reconfigure`tests/acceptance.suite.yml`file as shown below.

```
class_name: AcceptanceTester
modules:
    enabled:
        - \Helper\Acceptance
        - WPWebDriver
        - Asserts
    config:
        WPWebDriver:
            host:hub.browserstack.com
            port: '80'
            browser: '<Browser_Name>'
            url: '<Test_Url>'
            adminUsername: ''
            adminPassword: ''
            adminPath: '/wp-admin'
            capabilities:
              'browserstack.user': '<Browserstack_Username>'
              'browserstack.key': '<Browserstack_Acceskey>'
              'os': '<OS_Name>'
```

You can set many other parameters under capabilities as per your need. E.g., Screen resolution, browser version, os version, etc. Check this [link](https://www.browserstack.com/automate/codeception) for detailed description and run your scenario the same way.

To see the execution step by step use below command

```
codecept run test/acceptance/LoginCept.php --steps
```

To debug the execution step by step use below comm

```
codecept run test/acceptance/LoginCept.php --debug
```

Check the below screenshot for how it looks when your test runs successfully.

![](/assets/sample-test-run_png__585×350_.png)

#### References {#references}

1. [Codeception](http://codeception.com/)
2. [Codeception for WordPress](http://codeception.com/for/wordpress) \(That is what we’ve used\)
3. [Codeception commands](http://codeception.com/docs/reference/Commands)
4. [Codeception Webdriver Module](http://codeception.com/docs/modules/WebDriver)
5. [Browserstack integration with codeception](https://www.browserstack.com/automate/codeception)
6. [Php Test Club – Codeception Forum](http://phptest.club/c/codeception)



