# Theme file sturcture

Before starting theme development, you must know how the way wordpress select templates files to display pages on your site. It is issential to understand the template heirarchy of Wordpress theme.

http://codex.wordpress.org/Template_Hierarchy


We should know the Basic template files of wordpress for theme development. Here you will get the explanation about the basic template files of wordpress theme.

http://codex.wordpress.org/Stepping_into_Templates




## rtPanel


We use our 'rtPanel' customized wordpress theme for the theme development. You can download the rtPanel theme from Wordpress repo https://wordpress.org/themes/rtpanel or download from Git repo http://git.rtcamp.com/rtpanel/rtpanel

Before starting development you need to set up dependencies for rtpanel like here.
http://docs.rtcamp.com/rtpanel/developer/setup-rtpanel-development/

Structure of rtPanel Theme


* admin : In this directory we store all admin side functionality, CSS and jquery.
  * CSS :
    * rtp-admin.css : We write all admin side CSS (rtp theme options and metabox CSS) in this file.
  * js :
    * rtp-admin.js : We write all admin side jQuery (rtp theme options) in this file.
  * lib :
    * rtp-admin-functions.php : Here we write all support functions for rtp theme options.
    * rtp-deprecated.php : We write all deprecated functions from past rtPanel versions. You shouldn't use these functions and look for the alternatives instead.
    * rtp-general-options.php : Displays rtPanel General options tab.
    * rtp-post-comments-options.php : Displays rtPanel Post & Comments options tab.
    * rtp-settings-metaboxes.php : Here we write all rtPanel theme option metaboxes.
  * rtp-theme-options.php : Theme options page tabs are loaded in this file.
* assests : This directory contains foundation and saas files.
  * fontello : We use Fontello tool to include vector images into webfonts. https://github.com/fontello/fontello/wiki
    * css : We keep Fontello CSS files to include fontello fonts in project in this direcory.
    * font : This directory contains Fontello font files to include.
    * config.json : It is coinfiguration json file.
  * foundation : This directory contains Foundation files.
  * rtpanel :
    * scss : We write all our theme related CSS in this directory files. We separated CSS sections into SAAS files (.scss).
      * plugins : Plugin related SAAS files are saved in this directory.
* img : We keep all theme related images in this direcory.
* js :
   * jquery.sidr.min.js :
   * rtp-app.js :
   * rtp-concat-lib.js :
   * languages :
* lib :
   * rtp-comments.php :
   * rtp-default-functions.php :
   * rtp-hooks.php :
   * rtp-init.php :
   * rtp-post-summaries.php :
   * rtp-search.php :
   * rtp-sidebars.php :
* 404.php :
* comments.php :
* footer.php :
* functions.php :
* Gruntfile.js :
* header.php :
* image.php :
* index.php :
* loop-common.php :
* package.json ;
* readme.txt :
* screenshot.png
* search.php :
* sidebar.php :
* style.css :
* template-full-width.php :












