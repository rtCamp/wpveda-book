# Codeception

Codeception is a PHP testing framework, it can be setup very easily.

## Install Codeception

Refer this [doc](http://codeception.com/quickstart) for installing.

Recommended way to install it is composer, add `composer.json` into your project root directory.

`{`

`"name": "author",`

`"require-dev": {`

`"codeception/codeception": "2.2.4",`

`"lucatume/wp-browser": "dev-master"`

`}`

`}`

Run `composer install`

_  
lucatume/wp-browser- It contains the extension for WordPress. For more info refer _[_https://github.com/lucatume/wp-browser_](https://github.com/lucatume/wp-browser)

## Important Commands:

First to make wpcept command work, will have to create an alias -`alias wpcept=./vendor/bin/wpcept`

1. ### `wpcept bootstrap`

   It will create a test directory.

2. ### `wpcept generate:cept acceptance Test`

   It creates an acceptance test php file under acceptance directory.

3. ### `wpcept run acceptance test.php`

   It will run one test only.

## Configure

Configure your respective yml file, like for acceptance test cases configure acceptance.suite.yml. Below is the example file:

`# Codeception Test Suite Configuration`

`# Suite for WordPress acceptance tests.`

`# Perform tests using or simulating a browser.`

`class_name: AcceptanceTester`

`modules:`

`enabled:`

`- \Helper\Acceptance`

`- WPWebDriver`

`- Asserts`

`config:`

`WPWebDriver:`

`host: 'hub-cloud.browserstack.com'`

`port: 80`

`browser: 'chrome'`

`url: 'test url'`

`adminUsername: 'WP_USERNAMA'`

`adminPassword: 'WP_PASS'`

`adminPath: '/wp-admin'`

`capabilities:`

`'browserstack.user': 'BS_USERNAME'`

`'browserstack.key': 'SECRET_KEY'`

`'os': 'OS X'`

`'os_version' : 'Mountain Lion'`

`'browser' : 'Chrome'`

`'browserstack.debug': 'true'`

`extensions:`

`enabled: [Codeception\Extension\Recorder]`

`config:`

`Codeception\Extension\Recorder:`

`delete_successful: false`

## Links that might help:

1. [http://codeception.com/docs/06-ReusingTestCode](#)

2. [http://theaveragedev.com/first-step-into-wordpress-plugin-acceptance-testing/](http://theaveragedev.com/first-step-into-wordpress-plugin-acceptance-testing/)

3. [http://codeception.com/docs/reference/Commands](http://codeception.com/docs/reference/Commands)

4. [http://codeception.com/for/wordpress](http://codeception.com/for/wordpress)

5. [http://codeception.com/docs/modules/WebDriver](http://codeception.com/docs/modules/WebDriver)



