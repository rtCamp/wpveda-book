# Site Migration using Command line


Take a backup of SOURCE site Database,

```bash
mysqldump -u [USERNAME] -p[PASSWORD] EXAMPLE.com > /var/www/EXAMPLE.com/EXAMPLE.com.sql
```

`rsync` all files and folder from SOURCE server to REMOTE server,

```bash
cd /var/www/EXAMPLE.com/

rsync -avzh --progress --exclude=wp-config.php . [USER]@[REMOTE_HOST]:/var/www/[REMOTE_HOST].com/
```

On Remote server import Database,

```bash
/var/www/[REMOTE_HOST].com/
mysql -u [USERNAME] -p[PASSWORD] [DATABASE_NAME] < EXAMPLE.com.sql

```

Setup Home and Site URL in Remote wp-config.php file,

```php
define( 'WP_HOME', 'http://[REMOTE_HOST].com' );
define( 'WP_SITEURL', 'http://[REMOTE_HOST].com' );
```

**Important:** Do not forget to search and replace older host name with REMOTE host name.
