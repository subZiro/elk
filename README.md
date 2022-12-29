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

# сборка и запуск контейнеров с добавлением авторизации
```
docker-compose -f docker-compose.yml build
docker-compose -f docker-compose.yml up -d elasticsearch

# создание паролей коробочным пользователям auto - в автоматическом режиме/interactive - в ручном
./bin/elasticsearch-setup-passwords auto

# экспорт созданные пароли в переменные окружения
APM_SYSTEM, KIBANA_SYSTEM, KIBANA, LOGSTASH_SYSTEM, BEATS_SYSTEM, REMOTE_MONITORING_SYSTEM, ELASTIC

# запуск kibana 
docker-compose -f docker-compose.yml up -d kibana

# создать хранилище ключей.
./bin/kibana-keystore create
# просмотр хранилища ключей.
./bin/kibana-keystore list
# добавление пользователя kibana и пароль, введённый на шаге создания паролей в Elasticsearch
./bin/kibana-keystore add elasticsearch.username
./bin/kibana-keystore add elasticsearch.password

# сгенерировать ключи шифрования и сохранить значния KIBANA_XEE, KIBANA_XRE, KIBANA_XSE
./bin/kibana-encryption-keys generate

# обновить конфигурационые файлы контейнеров
# elasticsearch.yml
xpack.security.enabled: true

# filebeat.yml в блок output.elasticsearch:
username: elastic
password: ${ELASTIC}

# kibana.yml
elasticsearch.username: "kibana"
elasticsearch.password: ${KIBANA}
xpack.encryptedSavedObjects.encryptionKey: ${KIBANA_XEE}
xpack.reporting.encryptionKey: ${KIBANA_XRE}
xpack.security.encryptionKey: ${KIBANA_XSE}

# logstash.yml
xpack.monitoring.enabled: true
xpack.monitoring.elasticsearch.username: elastic
xpack.monitoring.elasticsearch.password: ${ELASTIC}

# metricbeat.yml
username: remote_monitoring_user
password: ${REMOTE_MONITORING_SYSTEM}
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
