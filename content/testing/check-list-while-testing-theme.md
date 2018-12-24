# rtQA Checklist while testing theme

QA Team member should cross check all the points listed below while testing the theme. This checklist points may vary as per the requirement and scope of the project. However, this has been prepared considering the most common points to be tested.

* ### **Wordpress Settings**

  1. Check Title and Tagline
  2. Logo - Should be clickable and it should look proper on all devices
  3. Pagination Pattern
  4. Site Favicon
  5. Social links should open in new tab
  6. Use site logo on wp backend login page instead of wordpress logo
* ### **Comments**

  1. If comments have disabled then should display appropriate message in front end.
  2. Discussions/comments: Threaded Comments
  3. Discussions/comments: Multiple pages of comments
  4. Reply and Submit Button styling
  5. Block Quote comment styling
  6. E.g. Different comments styling

     1. Comment th tag styling.
     2. Comment &lt;h1&gt; to &lt;h6&gt; tags style properly.
     3. Comment unordered list. Must be bullets.
     4. Ordered list. Must be numbering.
     5. All trackbacks display properly with hover effect.
* ### **Search Template**

  1. Search Result should appear as expected
  2. If post contains media elements then they should be rendered properly in search result.
  3. Pagination pattern should be consistent.
  4. Hit the url /?s= should display the all posts and pages and should be styled properly.
  5. Hit the url /?s=asdf and if there is not data found for the entered search string then page should not look broken. It should styled properly.
* ### **Homepage Settings**

  1. Check if the Home page shows correct data with proper styling
  2. Set the page template if required.
* ### **404 Page**

  1. This page should be styled properly so that it does not look broken.
  2. If custom design is given by the client then it should be as per design given.
  3. To test the 404 page hit the url as per the given pattern - &lt;Site\_Url&gt;**/asdf**
* ### **Posts / Pages / Archives \(Category Page\)**

  1. Test for Scheduled post, Draft post, Sticky post, Post without content.
  2. No or long title – observe layout and permalink. Check for overflow issues.
  3. Featured Images should be displayed correctly.
  4. Pages – Template \(Default / Other templates\) should be assigned properly
  5. Posts – Format \(Standard/Aside/Image/Link/Quote/Status\)
  6. Links and read more links.
  7. Media \(Image, Audio, Video\) : \(un\)captioned, alignment \(left, right, centre\), borders.
  8. Test Gallery Images. It should appear properly.
  9. Images, Audio and Video \(linked\) – displays correct and does not overflow content area.
  10. Images/Audio and Video \(attached\) – displays correct and does not overflow content area.
  11. Categories and tags – Should be displayed properly.
  12. Post/Page – Meta info should be displayed properly.
  13. For Protected Post

      1. Password form should appear correctly.
      2. Content and comments should not be displayed without entering password.
* ### **Menubar**

  1. Check if the header menu should be sticky.
  2. Check for level support.
  3. Hover effect / Current menu effect should be as per requirement.
  4. Check if footer menu appears properly.Footer – copyright statement, year should be dynamic.
* ### **Cross browser Testing should be carried out for UI and Functional testing on below browsers.**

  1. Chrome Browser
  2. Firefox
  3. Safari
  4. Opera \(if needed\)
  5. IE \(edge\)
* ### **Responsive Testing should be carried out on both mode. \(Landscape + Portrait\)**

  1. Android
  2. i-Devices \(iPhone and iPad\)

`Note: Query Monitor Plugin`

`While testing theme keep the Query Monitor plugin activated so that all other notices, warnings and PHP Errors along deprecated functions can be validated.`

