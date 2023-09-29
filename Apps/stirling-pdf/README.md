# NGINX Proxy

In case you have a nginx proxy, you should add this two lines to your config:
```
client_max_body_size 0;
proxy_read_timeout 3600;
```
### If you have Nginx Proxy Manager

Go to `Edit domain > Advanced` and under `Custom Nginx Configuration` add those two lines.


# Login / Security

This app comes by default with the `DOCKER_ENABLE_SECURITY=true` environment variable.
To enable Login, you should edit the settings file which can be found here:
`/DATA/AppData/TMC-Store/stirling-pdf/configs/settings.yml`

Change the first variable inside the Security group called `enableLogin` from `false` to `true`.

Restart container and the default login is:
username: `admin`
password: `stirling`
