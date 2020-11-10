# elasticsearch-metrics

https://grafana.net/dashboards/878

Run either as a standalone script or docker container.

## To build the container:

```bash
git clone https://github.com/alfonso-rb/elasticsearch-metrics.git es-monitor
cd es-monitor
docker build -t <user>/es-monitor:latest .
```

## To run it:

```bash
docker run -d -e ES_METRICS_CLUSTER_URL=http://search1.example.net:9200 \
-e ES_METRICS_INDEX_NAME=elasticsearch_metrics-search1 \
-e ES_METRICS_MONITORING_CLUSTER_URL=http://es-monitor.example.net:9200 \
-e ES_METRICS_INTERVAL=180 \
-e ES_METRICS_READ_SECURITY=True \
-e ES_METRICS_READ_USERNAME=read_username \
-e ES_METRICS_READ_PASSWORD=read_password \
-e ES_METRICS_WRITE_SECURITY=True \
-e ES_METRICS_WRITE_USERNAME=write_username \
-e ES_METRICS_WRITE_PASSWORD=write_password \
<user>/es-monitor:latest
```

## Environment defaults:

- ES_METRICS_CLUSTER_URL: http://server1:9200
- ES_METRICS_INDEX_NAME: elasticsearch_metrics-search1
- ES_METRICS_MONITORING_CLUSTER_URL: http://server2:9200
- ES_METRICS_INTERVAL: 60
- ES_METRICS_READ_SECURITY: False
- ES_METRICS_READ_USERNAME: read_username
- ES_METRICS_READ_PASSWORD: read_password
- ES_METRICS_WRITE_SECURITY: False
- ES_METRICS_WRITE_USERNAME: write_username
- ES_METRICS_WRITE_PASSWORD: write_password

## To Do:
- Docker compose file
- Verify support for ES 7.0+
- verify variable file functionality
- code to grab credentials from vault

## Author Information
Alfonso Brown - albrown@ea.com