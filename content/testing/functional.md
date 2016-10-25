# Functional Testing

Check if a site functions properly.

## Two main categories:
1. cross-browser (css/js front-end perfection)
2. single-browser (raw functionality tests)


## Tools

1. Selenium
2. Node.js based

### Compare

| Selenium | node.js |
| -- | -- |
| Tests are written in JAVA | Tests are written in nodejs |
| Complicated to setup | Much easier to setup |
| Tools are finalized | Exacts tools are yet to finalize |

### Node.js based options

**List of tools**

1. [phantomjs](http://phantomjs.org/) -  Runs a WebKit engine with full JavaScript access, but without the graphical portion.
2. [theintern.io](http://theintern.io/#compare) - has too many features and still not much talked about. Need to check why?
3. [karma](http://karma-runner.github.io/) - from Angular JS team.

4. [nightwatchjs](http://nightwatchjs.org/) - Node.js powered browser automation framework. It uses the Selenium WebDriver protocol.

**Evaluation criteria**
1. Do we need unit testing in nodejs?
2. Do we need cross-browser testing in nodejs?
3. Cookie/session support
4. File upload support
5. AJAX support
