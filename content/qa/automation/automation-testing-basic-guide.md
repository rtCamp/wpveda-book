### Automation Testing Basic Guide

Before jump into any test tool, let's go through some basic concept automation testing. If you are already aware about few things listed below then please free to move to the next chapter.

1. **What is Automation Testing?**
   The test scenario which is executed by some tool is called Automation testing.
2. **Why Automation Testing is needed? Or Goal of using Automation Testing.**  
   There are many points which we can consider that why automation testing needed or it is important.

   * The basic reason is that It does not require manual intervenation.
   * It is easy to run the automation script for a multilingual sites then testing it manually
   * Increases the speed of testing
   * Manual Testing can become boring and hence error-prone.

3. **Is Automation Testing is an alternate to Manual Testing?**  
   No. It is not an alternate to manual testing. Since every test scenario can not be tested automatically. There are certain creiteria to automate the test cases. If something does not fulfill the scope of automation then it can not be automated. And hence we can not completely relay on Automation Testing.

4. **Which test cases should be automated?**

   **We can consider the below scenarios where the test cases can be automated.**

   * Test Cases that are very tedious or difficult to perform manually
   * Test Cases which are time-consuming if they run manually
   * Some common functionalities used across the website
   * Test scenarios which have large number of data to be cross verified during the test. E.g. Form Submission, User Registration etc
   * It also depends upon the complexity of the test cases
   * Automated test case should be executed over the different set of browsers. If the automated test case can be run on a specific browser then there is no use of automation feature since the site needs to be tested over multiple browser. In short, there should a cross browser compatibilty.

   **The following category of test cases are not suitable for automation.**

   * Test Cases that are newly designed and not executed manually at least once
   * Test Cases for which the requirements are frequently changing
   * Test cases which are executed on an ad-hoc basis.

> **Note :** Maintainance of automatd test cases are very much important**. **As new functionalities or features are added, the automation Scripts need to be added, reviewed and maintained for each release cycle.



