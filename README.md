Installiation
===

Install images
---

```bash
docker pull grafana/grafana
docker pull influxdb
docker pull telegraf
```

Run containers
---

```bash
docker run -d --rm -p 3000:3000 -p 8083:8083 -p 8086:8086 -v $PWD/influxdb:/var/lib/influxdb --name influxdb influxdb
docker run -d --rm --net=container:influxdb -v $PWD/grafana:/var/lib/grafana --name grafana grafana/grafana
docker run -d --rm --net=container:influxdb --name telegraf telegraf
```
Go to `http://localhost:3000/` with us/pw `admin/admin` then create new datasource with `telegraf` database.

[OPTIONAL] Create user for influxdb

```bash
docker exec -it {INFLUXDB_CONTAINER_ID} bash
CREATE USER admin WITH PASSWORD 'admin' WITH ALL PRIVILEGES
```