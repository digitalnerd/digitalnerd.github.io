---
layout: post
title: Prometheus
---
Prometheus + Alertmanager + Grafana + InfluxDB

```bash
it is test
```

``
it is test
``

`
it is test
`

```
$ sudo -i
# mkdir -p /usr/lib/prometheus \
           /docker/{prometheus,alertmanager,grafana,influxdb}/config
# cd /usr/lib/prometheus
# cat << EOF > docker-compose.yml
version: "3"

volumes:
  prometheus:
    external: true
  alertmanager:
    external: true
  grafana:
    external: true
  influxdb:
    external: true

services:
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    ports:
      - 9090:9090
    volumes:
      - /docker/prometheus/config:/etc/prometheus/
      - prometheus:/prometheus
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'
      - '--web.enable-admin-api'
      - '--web.console.libraries=/usr/share/prometheus/console_libraries'
      - '--web.console.templates=/usr/share/prometheus/consoles'
    restart: unless-stopped

  alertmanager:
    image: prom/alertmanager
    container_name: alertmanager
    ports:
      - 9093:9093
    volumes:
      - /docker/alertmanager/config:/prometheus
      - alertmanager:/data
    command:
      - '--config.file:/prometheus/alertmanager.yml'
      - '--storage.path=/data'
  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - 3000:3000
    volumes:
      - /docker/grafana/config:/etc/grafana
      - grafana:/var/lib/grafana/
    restart: unless-stopped

  influxdb:
    image: influxdb
    container_name: influxdb
    ports:
      - 8086:8086
      - 8083:8083
      - 8090:8090
    environment:
      - INFLUXDB_DB=prometheus
      - INFLUXDB_HTTP_AUTH_ENABLED=true
      - INFLUXDB_ADMIN_USER=root
      - INFLUXDB_ADMIN_PASSWORD=toor
     volumes:
       - influxdb:/var/lib/influxdb
     restart: unless-stopped
EOF
```
Запускаем стек мониторинга и проверяем статус контейнеров:

```
$ sudo docker-compose up -d 
$ sudo docker-compose ps
```
