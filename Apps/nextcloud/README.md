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

`/DATA/AppData/Nextcloud/data/config`

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

For additional information and advanced tuning options, visit the [GitHub repository](https://github.com/crazy-max/docker-nextcloud/tree/master).
