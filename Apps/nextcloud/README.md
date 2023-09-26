# After installation

## Creating an Admin Account with database connection

`1. Enter your Username & Password of your choice`

`2. Select Storage & Database`

`3. Select MySQL/MariaDB`

`4. Input this into req. fields`
   
| Input fields             |Values                                                                |
| ----------------- | ------------------------------------------------------------------ |
| Database user: | **nextcloud** |
| Database password: | **nextcloud** |
| Database name: | **nextcloud** |
| Database host: | **nextcloud-db** |

`5. Press **INSTALL**`

---

## Enabling cronjob as the Background service

`1. Go to Administration settings`

`2. On the left, go to Basic settings`

`3. Under Background jobs, select Cron (Recommended)`

---

## Redis cache
Redis is recommended, alongside APCu to make Nextcloud faster. If you want to enable Redis, open CasaOS Files manager and go:

`/DATA/AppData/Nextcloud/data/config`

Now open and edit **config.php**

Find the link:

`'memcache.local' => '\OC\Memcache\APCu',`

and replace it with this:

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

### For more info and tuning, visit https://github.com/crazy-max/docker-nextcloud/tree/master
