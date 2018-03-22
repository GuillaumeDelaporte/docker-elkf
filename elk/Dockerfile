FROM sebp/elkx

RUN /opt/logstash/bin/logstash-plugin install logstash-input-beats && \
    /opt/elasticsearch/bin/elasticsearch-plugin install ingest-geoip
