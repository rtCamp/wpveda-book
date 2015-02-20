# Database Design

If your WordPress plugin* needs a database table, it's better to start with a database design.

If you need more than one table, it is likely that your app will be using some MYSQL JOINs.

A database design help us anticipate database related WordPress issues* early on.

**Note: WordPress themes should not requrie seprate database table. That is against WordPress conventions. A theme must use theme options at the max, and theme options should be limited to storing things like logo, color, fonts, etc settign which are theme dependent. No data that should remain present after changing a theme, should be part of theme.
*

TODO:
1. Links to some guide on MySQL Workbench
2. It will be good to have wordpress schema mysql workbench project. It can be useful for others to start builind their own schema.
