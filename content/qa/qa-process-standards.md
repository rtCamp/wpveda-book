### QA Process Standards

Once the development is completed the QA team members works on **QA of the Theme and Help Manual.**

##### QA team ensures the following:

**PSD to WordPress:**

In this case designs may be provided by client or design may be created in-house. In both the cases fundamental testing confirms the following points:

1. Test the theme as per the mock up designs. \(need to check it pixel by pixel comparison\)
2. Cross browser compatibility testing of the theme including browsers such as : FF, Chrome, Safari, Opera,  & IE9+.
3. If it is not possible to make it fully compatible for old browsers like IE8 then raise a ticket/task to gracefully degrade any such functionality for IE8 or for any such browsers for which the functionality is not supported by the browser in its default. 
   Also Foundation Framework don’t support IE8 browser.

**HTML to WordPress**

In this case client expects his site to be same as his old HTML site. The reason why he is migrating to WordPress is to have better control over content management and he may want to have blog in his new site. Client expects that his users should not notice that he has changed the platform, hence, fundamental testing confirms the following points:

1. Cross browser compatibility testing of the theme.
2. The new WordPress site matches the old HTML site in its look except blog which may or may not exist on his old site.
3. The Blog page confirms the aesthetics and blog design goes with overall site design.

**Mobile Testing:**

1. After completed the desktop testing, we will check the site in Mobile devices like i-Pad, i-Phone, i-Pod 
   & android phones. Testing should be carried out for both \_Landscape and Portrait \_mode. Testers can also refer this
   [link](http://gs.statcounter.com/screen-resolution-stats/desktop/worldwide) in order to test the maximum used devices worldwide. However , this is completely dependent on project requirements. 
2. If the site is responsive than it should be made as design provided else it will look same as desktop view \(due to set up of viewport\).

**Functionality Testing:**

1. QA team arranges a small meeting with the developer to understand the functionality specification for the theme developed.
2. Do the functionality testing as per discussed with developer by feeding input and examining output for various Test Cases.

**Reporting:**

1. Report the issues on bug tracker. 
2. QA team can assign the tickets to respective developer or the respective member of the team will take care of it in case if the QA member is not sure who is going to fix the bug.
3. Once the testing is done, QA team member comments on AC Task that **Testing has been done**.

**Re-testing & Regression Testing:**

1. QA team Re-test the theme once the notification from the developer is received mentioning that the bugs/issues reported earlier by QA team, are resolved.
2. Re-testing is done to make sure that the tests cases which failed in last execution are passing after the defects against those failures are fixed by the developer. If the issues are not resolved then QA members have authority to re-opened that issues.
3. Regression testing is done to check if the defect fixes have not impacted other functionality of the theme that was working fine before applying the code changes.
4. Regression testing is right time to start automating test cases using Selenium.

**Help Manual:**

1. QA team prepares the Help Manual for Clients \(admin users\) by which they can easily manage the WP enable site.
2. This User manual is prepare using Google drive document, when the developer is busy in resolving the bugs. 
3. After completion of user manual it must be cross check from developer for confirmation whether all points are covered in that document or not.
4. Finally we need to download that document into PDF format with proper formatting so that we can send it to the Client.

**Go Live testing:**

Once the theme has been made live, QA team re-test the theme & ensures that the GO LIVE check list should be covered as mentioned [here](/testing/go-live-check-list.md).

