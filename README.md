# ICINGAWEB2-DOCKER

[Dockerhub](https://hub.docker.com/r/m08y/icingaweb2-docker)

[Github](https://github.com/aneurinprice/icingaweb2-docker)

Docker container for [Icingaweb2](https://github.com/Icinga/icingaweb2). This will need `/etc/icingaweb2` persisting and the `phptimezone` variable setting.

# Variables
Variable	            |	Default Value |Acceptable Options
----------------------------|-----------------|-----------------------
phptimezone                 |  Europe/London  | String [See PHP Docs](https://www.php.net/manual/en/timezones.php)

## How to run
```
docker run -d -p 80:80 -e timezone="America/New_york -v $(pwd)/icingaweb:/etc/icingaweb2 m08y/icingaweb2-docker
```
