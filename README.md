# monitoring-2.0

==============================================================

Monitoring 2.0
Nexus
We have 2 vms:
1. vm1 and vm2 are virtual private servers. Public IP addresses and IP private addresses
is assigned by provider
2. One vm is “monitored” vm, another is “monitoring” vm
3. The monitored node runs Sonatype Nexus, launched in docker. This node and
application will be the main goal of monitoring

Needs
1. The architecture described in Nexus section must be implemented
2. Pull/push approaches for metrics collection must be used, depending on the situation.
Make sure you have the justification for the decision
3. Monitoring must have a single point of view on all graphs and metrics of the system,
docker, and application.
4. Monitoring must include JAVA-specific metrics as well
5. Monitoring must have a single point of view on all system and application logs.
6. Monitoring must support access control rules. Engineers must be only involved in the
servers and services they are responding for
7. Monitoring must provide a possibility to make drill-down investigations using panels with
graphs.

Resources
- vm1, 2.59.38.181, adminroot / M9MRCuUCmHjjvySggoB3
- vm2, 2.59.38.187, adminroot / zGsJPBsJWx6TwYUzDz3F

=====================================================================================

Solution:

Stack:
AdvancedHosters - Docker - Prometheus - Loki - Grafana - Sonatype Nexus - Git

ssh adminroot@2.59.38.181  ---  adminroot@wvds147624  ---  monitored_vm  
ssh adminroot@2.59.38.187  ---  adminroot@wvds147625  ---  monitoring_vm

=====================================================================================

Docs/Articles:

Global:
1. https://www.atatus.com/blog/java-performance-metrics/
2. https://github.com/shazforiot/Promtail-Loki-Grafana-using-Docker-Compose/tree/main
3. https://docs.docker.com/config/daemon/ 
4. https://github.com/ChristianLempa/boilerplates/tree/main

Nexus:
1. https://help.sonatype.com/en/monitoring.html 
2. https://help.sonatype.com/en/support-features.html#SupportFeatures-Prometheus 
3. https://support.sonatype.com/hc/en-us/articles/213465498-Configuring-Nexus-Repository-2-for-JMX-connections
4. https://support.sonatype.com/hc/en-us/articles/218501277-Configuring-Nexus-Repository-3-To-Allow-JMX-Connections
5. https://help.sonatype.com/en/continuous-monitoring-of-applications.html 
6. https://stackoverflow.com/questions/39163880/monitoring-nexus-oss-3-0-1 
7. https://www.coachdevops.com/2022/01/install-sonatype-nexus-3-using-docker.html
8. https://github.com/sonatype/helm3-charts/issues/99 

Portainer:
1. https://github.com/ChristianLempa/boilerplates/blob/main/docker-compose/portainer/docker-compose.yaml

Grafana:
1. https://grafana.com/blog/2020/06/25/monitoring-java-applications-with-the-prometheus-jmx-exporter-and-grafana/
2. https://grafana.com/blog/2024/03/11/removal-of-angularjs-support-in-grafana-what-you-need-to-know/ 
3. https://grafana.com/docs/grafana/latest/administration/roles-and-permissions/access-control/custom-role-actions-scopes/
4. https://grafana.com/go/webinar/getting-started-with-logging-and-grafana-loki/?pg=dash-search&plcmt=featured-cta1 

Grafana/dashboards:
1. https://grafana.com/grafana/dashboards/
2. https://grafana.com/grafana/dashboards/14282-cadvisor-exporter/
3. https://grafana.com/grafana/dashboards/13407-loki2-0-global-metrics/
4. https://grafana.com/grafana/dashboards/1860-node-exporter-full/
5. https://grafana.com/grafana/dashboards/16459-infra-nexus/

Prometheus:
1. https://habr.com/ru/companies/nixys/articles/785070/
2. https://www.tencentcloud.com/document/product/457/38367
3. https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#actuator.metrics.export.prometheus 

Prometheus_exporters:
1. https://github.com/prometheus/node_exporter
2. https://github.com/google/cadvisor
3. https://github.com/prometheus/jmx_exporter/tree/main
4. https://github.com/ocadotechnology/nexus-exporter
5. https://github.com/ChristianLempa/boilerplates/blob/main/docker-compose/nodeexporter/docker-compose.yaml 

Loki:
1. https://raw.githubusercontent.com/grafana/loki/v2.2.1/cmd/loki/loki-local-config.yaml
2. https://grafana.com/go/webinar/getting-started-with-logging-and-grafana-loki/?pg=dash-search&plcmt=featured-cta1
3. https://grafana.com/docs/loki/latest/setup/install/docker/
4. https://grafana.com/docs/loki/latest/configure/
5. https://github.com/grafana/loki
6. https://grafana.com/docs/loki/latest/send-data/docker-driver/configuration/

Promtail:
1. https://grafana.com/docs/loki/latest/send-data/promtail/configuration/
2. https://gist.github.com/ruanbekker/c6fa9bc6882e6f324b4319c5e3622460
3. https://raw.githubusercontent.com/grafana/loki/v2.2.1/cmd/promtail/promtail-docker-config.yaml
4. https://github.com/grafana/loki/issues/3635
5. https://github.com/grafana/loki/issues/333 

Video:
1. Server Monitoring // Prometheus and Grafana Tutorial - https://www.youtube.com/watch?v=9TJx7QTrTyo&t=334s
1. Monitoring Java Applications with Prometheus and Grafana - https://www.youtube.com/watch?v=27Yc3gdeuQ0
2. JMX Exporter - https://www.youtube.com/watch?v=0JDwT10PUyg
4. Loki and Promtail - https://www.youtube.com/watch?v=x2usZVRnXK4
5. Promtail Loki Grafana Using Docker Compose - https://www.youtube.com/watch?v=pnycjg_9M-o

=====================================================================================

Resourses:


monitored_vm:

Portainer  ---  http://2.59.38.181:9000/#!/init/admin  

Nexus      ---  http://2.59.38.181:8081/  

http://2.59.38.181:8081/service/metrics/healthcheck  
http://2.59.38.181:8081/service/metrics/data  
http://2.59.38.181:8081/service/metrics/ping  
http://2.59.38.181:8081/service/metrics/threads  

cAdvisor   ---  http://2.59.38.181:8080/containers/

Nexus Exporter --- http://2.59.38.181:9184/  

Node Exporter --- http://2.59.38.181:9100/  

=============


monitoring_vm:

Portainer  ---  http://2.59.38.187:9000/#!/init/admin  

cAdvisor --- http://2.59.38.187:8080/containers/  

Prometheus --- http://2.59.38.187:9090/  

Loki --- http://2.59.38.187:3100/metrics  
         http://2.59.38.187:3100/ready  


Grafana  ---  http://2.59.38.187:3000/login  
              http://2.59.38.187:3000/?orgId=1  ---   Internal Org  
              http://2.59.38.187:3000/?orgId=2  ---   Client Org  

=====================================================================================
