# sgw
### How to run
```
docker run -it -d -v logback.xml:/app/resources/logback.xml -v default.conf:/app/resources/default.conf -p 9200:9200 -p 5555:5555 opsterio/sgw:latest
```
### Configuration files can be download the following way:
```
curl -LO https://raw.githubusercontent.com/Opster/sgw-conf-files/master/default.conf
curl -LO https://raw.githubusercontent.com/Opster/sgw-conf-files/master/logback.xml
```
### Monitoring files can be download the following way:
```
curl -LO https://raw.githubusercontent.com/Opster/sgw-conf-files/master/SGW-Grafana-Dashboard.json
```
