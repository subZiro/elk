# ELK v 0.1

Elasticsearch Logstash Kibana (Filebeat, Metricbeat)

----

### краткая инструкция по деплою с docker-compose:

# сборка и запуск контейнеров
```
+ docker-compose -f docker-compose.yml build
+ docker-compose -f docker-compose.yml up -d
```

# адреса

```
elasticsearch:
- http://localhost:9200
- состояние кластера - http://localhost:9200/_cat/health
- просмотр доступных нод кластера - http://localhost:9200/_cat/nodes
- просмотр доступных индексов кластера - http://localhost:9200/_cat/indices

kibana:
- http://localhost:5601
```
