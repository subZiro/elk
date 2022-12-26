FROM docker.elastic.co/logstash/logstash:7.17.0

COPY --chown=root:logstash ./logstash/logstash.conf /usr/share/logstash/pipeline/logstash.conf
COPY --chown=root:logstash ./logstash/logstash.yml /usr/share/logstash/config/logstash.yml
