Nightwatch.js
==================
Write End-to-End tests in Node.js quickly and effortlessly that run against a Selenium server.

Set up of Nightwatchjs
---------------------------------------
The Set up of Nighrwatchjs is easy. You can set up nightwatchjs with the help of below steps.

###Install Nightwatch

Refer steps for installing http://nightwatchjs.org/guide#install-nightwatch

*Note: Make sure set runner globally with adding the -g option after npm install.*

### Install JAVA

Refer: https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get

###Download and start Selenium Server
Refer steps for starting and running the Selenium server http://nightwatchjs.org/guide#running-the-selenium-server

*Note: For best practice, running Selenium Automatically with changing perameter in configuration file.*

e.g.

    "start_process" : true,

    "server_path" : "PATH OF SELENIUM JAR FILES IN SYSTEM",

### Base Configuration File of nightwatchjs
*Nightwatchjs follows a folder structure for running the test*
1. Tests Folder- For running the nightwatchjs tests, you have to create a folder in your project e.g. tests (if folder your name is different, change the name in configuration file accordingly)
2. ConfigurationFile- Create a file with name of nightwatch.json. Place all code of configuration file from http://nightwatchjs.org/guide#settings-file
3. Reports Folder- It will have all reports of Tests.
4. Selenium jars file-  selenium-server-standalone-2.45.0.jar.
5. globals.js file- Place global.js file in project folder.

```
var HtmlReporter = require('nightwatch-html-reporter');
	var reporter = new HtmlReporter({
	    openBrowser: true,
	    reportsDirectory: __dirname + '/reports'
	});
	module.exports = {
	    reporter: reporter.fn
	};```

### Install nightwatch html reporter
Refer: https://github.com/jls/nightwatch-html-reporter

Done! Now, Write your first script
-----------------------------

Now, Select any editor(IDE) for writing your test script.
###Your first script
Refer: http://nightwatchjs.org/guide#writing-tests

Running your test script
-------------
*Before run your test script. Make sure selenium server
is running.*

*For Checking the server status, open this page in any browser
http://localhost:4444/selenium-server/driver/?cmd=getLogMessages*

*It will show you a 'OK' message on web page if server is running otherwise show 'Unable to connect'*

#####Run Test: 

Go TO your Project Folder in your system --> Run command-  nightwatch -- test folderName/testfileName

e.g. ankit@ankit-PC:~/eclips-workspace/night-watch-setup$ nightwatch --test tests/title.js
