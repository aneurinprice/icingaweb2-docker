Accepts http conntections on port 80

Environment Variables and Default Values:

Variable	            |	Default Value |Acceptable Options
----------------------------|-----------------|-----------------------
phptimezone                 |  Europe/London  | String [See PHP Docs](https://www.php.net/manual/en/timezones.php)



## Example command: ##
  - `docker run -d -p 80:80 -e timezone="America/New_york -v $(pwd)/icingaweb:/etc/icingaweb2  registry.nyeprice.space/docker-icingaweb2/docker-icingaweb2:latest`


# ICINGAWEB2-DOCKER

[Dockerhub](https://hub.docker.com/r/m08y/influxdb-collectd-docker)

[Github](https://github.com/aneurinprice/influxdb-collectd-docker)

It's pretty self explanitory. This is a fork of the Official Influxdb Docker Image that comes pre-loaded with the Collectd  Typeset. This will still require all the config from influxdb. Because their documentation (at the time of writing this) is terrible, I have included a snippet that should work in most situations

## Example Influxdb Config
```
[meta]
  dir = "/var/lib/influxdb/meta"

[data]
  dir = "/var/lib/influxdb/data"
  engine = "tsm1"
  wal-dir = "/var/lib/influxdb/wal"

[[collectd]]
  enabled = true
  bind-address = ":25826" # the bind address
  database = "collectd" # Name of the database that will be written to
  retention-policy = ""
  batch-size = 5000 # will flush if this many points get buffered
  batch-pending = 10 # number of batches that may be pending in memory
  batch-timeout = "10s"
  read-buffer = 0 # UDP read buffer size, 0 means to use OS default
  typesdb = "/usr/share/collectd/types.db"
```

## How to run
```
docker run -d -p 25826:25826 -v $PWD/influxdb.conf:/etc/influxdb/influxdb.conf m08y/influxdb-collectd-docker:latest
```

## Gotchas
  - For Instructions how to use this image, please see [The Official Influxdb Docker Documentation](https://hub.docker.com/_/influxdb)

