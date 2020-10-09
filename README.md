# linux-monitoing by docker prometheus
- this repo helps users to monitors their linux os and generate alerts by prometheus containers
- however, prometheus is not the only application useful for monitoring and generating alerts
- node-exporter is needed to get data from linux os
- alertmanager is needed to set up outgoing alert server (i.e. mail)
- grafana is used to visualize data from linux os by designing dashboard (can be obtained from grafana community)
- reference:
  - [prometheus config setting](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)
  - [prometheus rule setting](https://prometheus.io/docs/prometheus/latest/configuration/recording_rules/)
  - [alertmanager config setting](https://prometheus.io/docs/alerting/latest/configuration/)
  

# Prerequesite
- basic knowledge of docker operation
  - `docker-compose build && docker-compose up` to ini containers
  - `docker exec -it <container> bash` to get inside containers file system
  

# docker containers
- node-exporter
- prometheus
- alertmanager
- grafana

# node-exporter
- export linux metrics to [http://localhost:9100/metrics](http://localhost:9100/metrics)
- node-exporter is targeted and collected by prometheus

# prometheus
- collect metrics from node-exporter [http://localhost:9090/targets](http://localhost:9090/targets)
- define monitoring rules in /prometheus/testing_rules.yml
- send requests to AlertManager when alerts need to be sent to receivers

# alertmanager
- handle alert sending to receiver via sms, wechat, email, discord...

# grafana
- visualize metrics collected by prometheus from node-exporter
- import dashboard from community
- monitoring rules can reference dashboard design
