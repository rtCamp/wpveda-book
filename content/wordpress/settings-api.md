# Settings API

The [Settings API](https://developer.wordpress.org/plugins/settings/settings-api/) focuses on providing a way for developers to create forms and manage form data.

The Settings API, allows admin pages containing settings forms to be managed semi-automatically. It lets you define settings pages, sections within those pages and fields within the sections.

New settings pages can be registered along with sections and fields inside them. Existing settings pages can also be added to by registering new settings sections or fields inside of them.

Organizing registration and validation of fields still requires some effort from developers, but avoids a lot of complex debugging of underlying options management.

### **Why Use the Settings API?**

* Visual Consistency

* Robustness \(Future-Proofing!\)

* Less Work!

  * Handling Form Submissions

  * Includes Security Measures

  * Sanitizing Data



### **Settings API - Function Reference**

**Setting Register\/Unregister**

[register\_setting\(\)](https://developer.wordpress.org/reference/functions/register_setting/)

[unregister\_setting\(\)](https://developer.wordpress.org/reference/functions/unregister_setting/)

**Add Field\/Section**

[add\_settings\_section\(\)](https://developer.wordpress.org/reference/functions/add_settings_section/)

[add\_settings\_field\(\)](https://developer.wordpress.org/reference/functions/add_settings_field/)

**Options Form Rendering**

[settings\_fields\(\)](https://developer.wordpress.org/reference/functions/settings_fields/)

[do\_settings\_sections\(\)](https://developer.wordpress.org/reference/functions/do_settings_sections/)

[do\_settings\_fields\(\)](https://developer.wordpress.org/reference/functions/do_settings_fields/)

**Errors**

[add\_settings\_error\(\)](https://developer.wordpress.org/reference/functions/add_settings_error/)

[get\_settings\_errors\(\)](https://developer.wordpress.org/reference/functions/get_settings_errors/)

[settings\_errors\(\)](https://developer.wordpress.org/reference/functions/settings_errors/)

See example: [https:\/\/developer.wordpress.org\/plugins\/settings\/custom-settings-page\/](https://developer.wordpress.org/plugins/settings/custom-settings-page/)

### Reference links

[https:\/\/developer.wordpress.org\/plugins\/settings\/settings-api\/](https://developer.wordpress.org/plugins/settings/settings-api/)

[https:\/\/codex.wordpress.org\/Settings\_API](https://codex.wordpress.org/Settings_API)

[The Complete Guide to the WordPress Settings API](https://code.tutsplus.com/series/the-complete-guide-to-the-wordpress-settings-api--cms-624)

[Create a WordPress Theme Settings Page with the Settings API](https://www.sitepoint.com/create-a-wordpress-theme-settings-page-with-the-settings-api/)

