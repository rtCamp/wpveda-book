# Checklist for Testing Major Releases of Plugins and WordPress

During the period of time, there will be major releases of WordPress and Plugins like BuddyPress and rtMedia. QA Team member should be aware of the releases and check the compatibility of plugins with our **core rtMedia plugin and the Pro-add-on’s**.

QA Team member should cross-check all the points listed below while testing. This checklist points may vary as per the requirement. However, this has been prepared considering the most common points to be tested.

### **Checklist for Testing WordPress with rtMedia core, BuddyPress and bbPress** {#checklist-for-testing-wordpress-with-rtmedia-core-buddypress-and-bbpress}

**Below are the steps to follow while testing**

* Install the released version \( or it can be also Beta/RC release \) of WordPress and/or any plugins listed above
* Install stable versions of the rest things.

**E.g.**If BuddyPress is released then install the released version of it and install the latest stable version of WordPress and rtMedia core.

#### **Major functionalities cover the following** {#major-functionalities-cover-the-following-%c2%a0}

1. **Upload Functionality from Media tab – Check for both When the direct upload is enabled or disabled**
   **along with upload terms on/off**
   * Test for each single media upload – Image, Audio, and Video
   * Upload multiple media’s and check if any functionality breaks.
   * Check for media upload in comment
   * Check for the UI on uploading single media and multiple media’s.
   * Check with masonry on/off
   * Check with Load More and Pagination option
   * Check the media with/without lightbox
   * Check with Privacy enabled/disabled mode
2. **Activity Feed Upload functionality** – **Check for both When the direct upload is enabled or disabled along with upload terms on/off**
   * Test for each single media upload – Image, Audio, and Video
   * Check uploading some text with media and check the UI. Also, check uploading multiple media and check the UI.
   * Check with masonry on/off
   * Check basic functionalities of post Edit, Comment and Delete.
   * Check the media with/without lightbox
   * Check with Privacy enabled/disabled mode
3. **Group  Upload functionality **– **Check for both When the direct upload is enabled or disabled along with upload terms on/off **
   * The test scenario would remain same for activity and media page for the specific group as explained in point 1 and 2.
4. **Forum**
   * Test normal upload functionality by creating a forum and topic

Note: Test should be carried out with all major browsers \( Chrome, Firefox, Safari, and Opera \)

Along with rtMedia Core plugin test should be carried out with **rtMedia Pro-add-on’s.**

* Check basic functionality of add-ons with rtMedia core and Major releases of Plugins listed above. The basic functionality shouldn’t break.

**We follow a format while testing please refer – **[**here**](https://docs.google.com/spreadsheets/d/1LNDdvBGfpVK1aKZcvMiH4slpab_oUxnjah73Acgr6gw/edit?usp=sharing)**. Give the name of the sheet for which the testing round is to be conducted as given in the sample file link.**

  


