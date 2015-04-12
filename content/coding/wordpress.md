# WordPress & CSS

###WordPress CSS classes available for use

.alignnone

.aligncenter

.alignright

.alignleft

.wpcaption

.size-full

.size-large

.size-medium

.size-thumbnail

**Refer for more details**: http://digwp.com/2010/05/default-wordpress-css-styles-hooks


### WordPress admin pages style guide

*#wphead*

The main title of the admin panel. Used to display the name of the blog and a link to View Site.

*#adminmenu ul*

The main level navigation bar, for links: Dashboard, Write, Manage, etc.

*#adminmenu2 ul*

The sub level navigation bar, for links (example: under Manage: Posts, Pages, Categories).

*.wrap*

The basic wrapper for all content in the admin panel, set in a <div>.

*#zeitgeist*

The sidebar on the Dashboard displaying Latest Activity and Blog Stats.

*#footer*

The footer at the bottom, with Wordpress logo, version number, and help links.

*.wrap h2*

Individual Page headers for the various subpanels, like General Options.

### Theme post-editor style
``` add_editor_style( $stylesheet );```

$stylesheet
(string/array) (optional) Path to a stylesheet file, relative to the current theme directory, or an array thereof to link multiple stylesheet files.
Default: "editor-style.css"

### WordPress enqueue style

**Refer** : http://codex.wordpress.org/Function_Reference/wp_enqueue_style

### WordPress enqueue script
**Refer** : http://codex.wordpress.org/Function_Reference/wp_enqueue_script
