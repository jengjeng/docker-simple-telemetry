Installiation
===

```bash
docker run -d --rm --name grafana -p 3000:3000 -p 8083:8083 -p 8086:8086 grafana/grafana
docker run -d --rm --name influxdb --net=container:grafana -v $PWD:/var/lib/influxdb influxdb
docker run -d --rm --net=container:grafana --name telegraf telegraf
```

[OPTIONAL] Create user for influxdb

```bash
docker exec -it {INFLUXDB_CONTAINER_ID} bash
CREATE USER admin WITH PASSWORD 'admin' WITH ALL PRIVILEGES
```