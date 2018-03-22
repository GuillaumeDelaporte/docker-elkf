Prise de note
-------
##### Log format
[log format](http://docs.openio.io/master/source/admin-guide/operations_log_format.html)
##### Filebeat
* format :
* codecs :
* modules :

* prospectors : permet de spécifier quel(s) fichier(s) à envoyer à logstash et comment ils sont maintenus   [doc](https://www.elastic.co/guide/en/beats/filebeat/current/configuration-filebeat-options.html)



##### Pattern par degfaut de logstash
[ Lite des patterns logstash](https://github.com/logstash-plugins/logstash-patterns-core/blob/master/patterns/grok-patterns)

##### Créer des comptes kibana et logstash
```
curl -XPUT -u elastic:elastic 'localhost:9200/_xpack/security/user/kibana/_password?pretty' -H 'Content-Type: application/json' -d' {"password" : "elastic"}'
```
```
curl -XPUT -u elastic:elastic 'localhost:9200/_xpack/security/user/logstash_system/_password?pretty' -H 'Content-Type: application/json' -d' {"password" : "elastic"}'
```
docker exec loganalyzer_elk_1 service kibana start
docker exec loganalyzer_elk_1 service logstash start

/opt/logstash/bin/logstash --path.data /tmp/logstash/data -e 'input { stdin { } } output { elasticsearch { hosts => ["localhost"] user => "elastic" password => "elastic" }}'
