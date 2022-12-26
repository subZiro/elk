# ELK v0.1

Elasticsearch Logstash Kibana (Filebeat, Metricbeat)

----

### краткая инструкция по деплою с docker-compose:

# сборка и запуск контейнеров
```
+ docker-compose -f docker-compose.yml build
+ docker-compose -f docker-compose.yml up -d

проект доступен в по адресу:
elastic = http://localhost:9200/
kibana = http://localhost:5601/
```

# Адреса

```
проект доступен в по адресу:
elasticsearch:
- http://127.0.0.1:9200/
- просмотр доступных нод кластера - http://127.0.0.1:9200/_cat/nodes
- просмотр доступных индексов кластера - http://127.0.0.1:9200/_cat/indices

kibana:
- http://127.0.0.1:5601/
```
