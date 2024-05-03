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

==============================================================

Solution:

Stack:
AdvancedHosters - Docker - Prometheus - Loki - Grafana - Sonatype Nexus - Git

ssh adminroot@2.59.38.181  ---  adminroot@wvds147624  ---  monitored_vm
ssh adminroot@2.59.38.187  ---  adminroot@wvds147625  ---  monitoring_vm

==============================================================

Docs/Articles:

1. https://support.sonatype.com/hc/en-us/articles/213465498-Configuring-Nexus-Repository-2-for-JMX-connections
2. https://help.sonatype.com/en/monitoring.html
   https://help.sonatype.com/en/continuous-monitoring-of-applications.html

3. https://grafana.com/blog/2020/06/25/monitoring-java-applications-with-the-prometheus-jmx-exporter-and-grafana/

4. https://www.atatus.com/blog/java-performance-metrics/
5. https://stackoverflow.com/questions/39163880/monitoring-nexus-oss-3-0-1
6. https://www.tencentcloud.com/document/product/457/38367

7. https://www.coachdevops.com/2022/01/install-sonatype-nexus-3-using-docker.html

https://support.sonatype.com/hc/en-us/articles/218501277-Configuring-Nexus-Repository-3-To-Allow-JMX-Connections

https://github.com/sonatype/helm3-charts/issues/99
https://help.sonatype.com/en/support-features.html#SupportFeatures-Prometheus



https://github.com/prometheus/node_exporter
https://github.com/google/cadvisor
https://github.com/prometheus/jmx_exporter/tree/main
https://github.com/ocadotechnology/nexus-exporter

https://github.com/ChristianLempa/boilerplates/blob/main/docker-compose/nodeexporter/docker-compose.yaml

https://grafana.com/grafana/dashboards/16459-infra-nexus/

https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#actuator.metrics.export.prometheus

https://grafana.com/blog/2024/03/11/removal-of-angularjs-support-in-grafana-what-you-need-to-know/


Prometheus:
https://habr.com/ru/companies/nixys/articles/785070/

Loki:
https://grafana.com/go/webinar/getting-started-with-logging-and-grafana-loki/?pg=dash-search&plcmt=featured-cta1
https://grafana.com/docs/loki/latest/setup/install/docker/
https://github.com/grafana/loki



https://github.com/shazforiot/Promtail-Loki-Grafana-using-Docker-Compose/blob/main/docker-compose.yml
https://gist.github.com/ruanbekker/c6fa9bc6882e6f324b4319c5e3622460 -- promtail_docker_logs.md

https://raw.githubusercontent.com/grafana/loki/v2.2.1/cmd/promtail/promtail-docker-config.yaml
https://raw.githubusercontent.com/grafana/loki/v2.2.1/cmd/loki/loki-local-config.yaml


Video:

1. https://www.youtube.com/watch?v=27Yc3gdeuQ0
2. https://www.youtube.com/watch?v=9TJx7QTrTyo&t=334s

3. JMX Exporter - https://www.youtube.com/watch?v=0JDwT10PUyg
4. Loki and Promtail - https://www.youtube.com/watch?v=x2usZVRnXK4
https://www.youtube.com/watch?v=pnycjg_9M-o
https://www.youtube.com/watch?v=eJtrxj9U_P8


https://www.youtube.com/watch?v=_qhrRUKOzVE


grafana/dashboards:
https://grafana.com/grafana/dashboards/16459-infra-nexus/

==============================================================

