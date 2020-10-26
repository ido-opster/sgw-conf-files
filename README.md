# Opster Search Gateway

This repo contains resources and instructions on how to install and run Opster Search Gateway


## Search Gateway installation:
- set up index template in the Elasticsearch that will store the SG logs. The template is located here: https://github.com/Opster/sgw-conf-files/blob/master/opster-sg-template.json
- create index with alias and right settings - prepared for rollover
```
PUT http://es-for-logs:9200/opster-sg-00001
{
  "aliases": {
    "opster-sg": {
      "is_write_index": true
    }
  }
}
```
- download the SG configuration files from the repo. The files are located at:
  * The SG config: https://github.com/Opster/sgw-conf-files/blob/master/default.conf
  * The search logs config: https://github.com/Opster/sgw-conf-files/blob/master/logback.xml
- update the config with:
  * ES url (in SG config)
  * Update userParameter with the header containing the user-IDs (in SG config)
  * ES-logs url (in the logback config)
- run the SG : 
```
docker run -it -d -v logback.xml:/app/resources/logback.xml -v default.conf:/app/resources/default.conf -p 9200:9200 -p 5555:5555 opsterio/sgw:latest
```
- connect prometheus to the SG
- import grafana dashboard. The dashboard is located here: 
```
curl -LO https://raw.githubusercontent.com/Opster/sgw-conf-files/master/SGW-Grafana-Dashboard.json
```
- import kibana dashboard
- run a search and operations manualy through the SG
- Check the search logs, kibana and grafana dashboard and make sure all is connected as expected
- configure kibana es-url to point to the SG
