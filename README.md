# ELK v 0.1

Elasticsearch=8.5.1
Logstash=8.5.1 
Kibana=8.5.1
Filebeat=8.5.1
Metricbeat=8.5.1

----

### краткая инструкция по деплою с docker-compose:

# сборка и запуск контейнеров
```
# build
docker-compose -f docker-compose.yml build
# run 
docker-compose -f docker-compose.yml up -d
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
