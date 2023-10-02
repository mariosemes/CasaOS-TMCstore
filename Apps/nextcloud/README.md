# After Installation

Once you have completed the installation, follow these steps to set up an admin account with a database connection:

1. Enter your desired Username and Password.
2. Choose your preferred Storage and Database option.
3. Select MySQL/MariaDB.
4. Fill in the required fields as follows:

| Input fields       | Values         |
| ------------------ | -------------- |
| Database user      | nextcloud      |
| Database password  | nextcloud      |
| Database name      | nextcloud      |
| Database host      | nextcloud-db   |

5. Click on the **INSTALL** button to proceed.

---

## Enabling the Background Service (cronjob)

To enable the cronjob as the background service, follow these steps:

1. Go to the Administration settings.
2. From the left-hand menu, select Basic settings.
3. Under Background jobs, choose Cron (Recommended).

---

## Redis Cache

To maximize the speed of Nextcloud, it is recommended to use Redis in conjunction with APCu. If you wish to enable Redis, navigate to the CasaOS Files manager following this path:

`/DATA/AppData/TMC-Store/Nextcloud/data/config`

Open and edit the **config.php** file. Locate the following line:

`'memcache.local' => '\OC\Memcache\APCu',`

Replace it with the following code:

```
    'memcache.local' => '\OC\Memcache\APCu',
    'memcache.distributed' => '\OC\Memcache\Redis',
    'memcache.locking' => '\OC\Memcache\Redis',
    'redis' => array(
        'host' => 'redis',
        'port' => 6379,
    ),
```
---

## "Access trough untrusted domain" error

In case you get the "Access trough untrusted domain" error, you should edit/add this to your `config.php` file:

```
    'trusted_domains' => 
      array (
        0 => '<reaplce-with-server-ip-address:port>',
        1 => '<your.domain.com>',
        2 => '<delete.this.if.you.dont.have.more.domains>',
      ),
```

**Friendly Reminder:** When adding domains and addresses to the trusted_domains configuration in your Nextcloud instance, make sure to include all the domains and addresses from which you would like to access Nextcloud. It is important to note that you should only use clean domain names without including 'http', 'https', or any forward slashes in the naming. Keep the entries simple and straightforward.

---

## Nextcloud does not redirect to dashboard after login

In case you have to reload the page after login to ge to the dashboard, just add this to your config.php file:

```'overwriteprotocol' => 'https',```

---

For additional information and advanced tuning options, visit the [GitHub repository](https://github.com/crazy-max/docker-nextcloud/tree/master).
