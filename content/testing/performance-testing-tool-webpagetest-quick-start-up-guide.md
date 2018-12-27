# Performance Testing tool – Webpagetest Quick start up Guide

#### **Performance Testing** {#performance-testing}

Performance Testing is a type of testing to ensure software applications will perform well under their expected workload. Performance testing is the type of **Non-Functional Testing. **There are different tools to measure the performance of the website. We are going to explore **Webpage test **performance testing tool, explained as below :

**WebPagetest **is used for measuring and analyzing the performance of web pages. Webpagetest enables you to run web performance tests on your site from a number of different locations across the world in a number of different browsers.

### **Running a Performance Test** {#running-a-performance-test}

1. Visit - [https://www.webpagetest.org/](https://www.webpagetest.org/)
2. Select **Simple Testing **to perform simple tests
3. Enter URL that needs to be tested.
4. Select the Test Configurations \(Either Desktop, Mobile testing\)
5. Include Repeat View \(Only if required\)
6. After everything is configured click on **Start Test **button. The request will be sent to the selected location for testing.

**Note:**The test may take time depending on how many tests are ahead of yours.

Lets us understand the terminologies used in the Webpage test tool.

#### **Optimization Grades**[\#**Optimization Grades**](https://cafe.rtcamp.com/handbook/quality-assurance/performance-testing-tool-webpagetest-quick-start-up-guide/#optimization-grades) {#optimization-grades}

Following are some of the optimization grades shown after the test is completed.

* **Keep-alive Enabled**
  * Each request for a piece of content on the page \(image, javascript, CSS, flash, etc\) needs to be made over a connection to the web server.  Setting up new connections can take a lot of time so it is best to reuse connections when you can and keep-alive is the way that is done.
* **Compress Text**
  * Just about everything on a page that isn’t an image or video is the text of some kind \(HTML, javascript, CSS\).  Text compresses really well and HTTP provides a way to transfer the files in compressed form. Enabling compression for text resources is usually just a server configuration change without requiring any changes to the page itself and can both improve the performance and reduce the costs of serving the content \(by reducing the amount of data transmitted\).
* **Compress Images**
  * The image compression check just looks at photo images \(JPEG files\) and makes sure the quality isn’t set too high.  JPEG images can usually be compressed pretty substantially without any noticeable reduction in visual quality.
* **Cache Static Content**
  * Static Content is the pieces of content on your page that don’t change frequently \(images, javascript, css\).  You can configure them so that the user’s browser will store them in a cache so if the user comes back to the page \(or visits another page that uses the same file\) they can just use the copy they already have instead of requesting the file from the web server.
* **Combine JS/CSS Files**
  * Improving performance usually means reducing the number of requests for content and one of the easiest \(and most significant\) ways to do that is to reduce the number of individual css and javascript files that load at the beginning of the page \(in the &lt;head&gt; which blocks the page from displaying to the user\).
* **Use of CDN**
  * Each request for a piece of content to the web server has to travel from the user’s browser all the way to the server and back.  As you get further and further from the server this can become a significant amount of time \(which adds up quickly as there are more requests on the page\).  Ultimately the time it takes is limited by the speed of light so there’s not much you can do except to move your server closer to the users.

#### **Page Level Metrics** {#page-level-metrics}

Following are some of the page level metrics captured and displayed for the overall page.

* **Load Time**
  * The Load Time is measured as the time from the start of the initial navigation until the beginning of the window load event \(onload\).
* **Fully Loaded**
  * The Fully Loaded time is measured as the time from the start of the initial navigation until there were 2 seconds of no network activity after Document Complete.  This will usually include any activity that is triggered by javascript after the main page loads.
* **First Byte**
  * The First Byte time \(often abbreviated as TTFB\) is measured as the time from the start of the initial navigation until the first byte of the base page is received by the browser \(after following redirects\).
* **First View**
  * The First View row is a test that was done with a browser that had its cache and cookies cleared out and represents what a first-time visitor to the page will experience.
* **Repeat View**
  * The Repeat View row is a test that was done immediately after the First View test without clearing out anything.  The browser window is closed after the First View test and then a new browser is launched to do the Repeat View test.
* **Start Render**
  * The Start Render time is measured as the time from the start of the initial navigation until the first non-white content is painted to the browser display.
* **Speed Index**
  * The Speed Index is a calculated metric that represents how quickly the page rendered the user-visible content \(lower is better\).
* **DOM Elements**
  * The DOM Elements metric is the count of the DOM elements on the tested page as measured at the end of the test.

**Reference Links**  
[https://sites.google.com/a/webpagetest.org/docs/](https://sites.google.com/a/webpagetest.org/docs/)

