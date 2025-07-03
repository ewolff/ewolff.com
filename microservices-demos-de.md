---
title: "Microservices Demos"
layout: de
---

## Synchrone Kommunikation

Es gibt verschiedene Möglichkeiten für synchrone Kommunikation
zwischen Microservices:

* Die [Consul-Demo](https://github.com/ewolff/microservice-consul) ist
in Java mit Spring Cloud/Boot geschrieben. Die Demo verwendet Consul
für Service Discovery, Apache httpd für das Routing, Hystrix für
die Resilience und Ribbon für Lastverteilung. Außerdem
bietet sie eine
[Prometheus-Installation](https://github.com/ewolff/microservice-consul#prometheus)
für das Monitoring, einen
[ELK-Stack](https://github.com/ewolff/microservice-consul#elastic-stack)
für die Log-Analyse und
[Zipkin](https://github.com/ewolff/microservice-consul#zipkin), um
Aufrufe zwischen Microservices zu tracen.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-consul/blob/master/WIE-LAUFEN.md)

* Die [Consul
DNS-Demo](https://github.com/ewolff/microservice-consul-dns) ist
ebenfalls in Java mit Spring Cloud/Boot geschrieben. Die Demo
verwendet Consul für die Service Discovery, jedoch mit seiner
DNS-Schnittstelle und automatischer Registrierung unter Verwendung von
Registrator. Apache httpd wird für das Routing verwendet.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-consul-dns/blob/master/WIE-LAUFEN.md)

* Die [Netflix-Demo](https://github.com/ewolff/microservice) verwendet
den Netflix-Stack. Die Demo ist in Java mit Spring Cloud/Boot
geschrieben. Sie verwendet Netflix Eureka für die Service Discovery,
Netflix Zuul für das Routing, Hystrix für die Resilience und Ribbon
für die Load Balancing.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice/blob/master/WIE-LAUFEN.md)

* Kubernetes ist ein System zum Ausführen von Docker-Containern in
einem Cluster. Die
[Kubernetes-Demo](https://github.com/ewolff/microservice-kubernetes)
ist in Java mit Spring Cloud/Boot geschrieben. Sie verwendet
Kubernetes für die Service Discovery, Routing und Load Balancing. Die
Demo verwendet auch Hystrix für die Resilience. Der Code ist nicht von
Kubernetes abhängig.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-kubernetes/blob/master/WIE-LAUFEN.md)

* Cloud Foundry ist eine PaaS (Platform as a Service). Es bietet einer
Anwendung eine Umgebung zum Ausführen. Die [Cloud Foundry-Demo](https://github.com/ewolff/microservice-cloudfoundry) ist in
Java mit Spring Cloud/Boot geschrieben. Sie verwendet Cloud Foundry
für Deployment, Service Discovery, Routing und Load Balancing. Die
Demo verwendet auch Hystrix für die Resilience. Der Code ist nicht von
Cloud Foundry abhängig.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-cloudfoundry/blob/master/WIE-LAUFEN.md)

## Asynchrone Kommunikation

Asynchrone Kommunikation erleichtert den Umgang mit unzuverlässigen
Netzwerken und Microservices:

* Das [Kafka-Beispiel](https://github.com/ewolff/microservice-kafka)
  verwendet Apache Kafka für die Kommunikation. Kafka ist eine
  nachrichtenorientierte Middleware und ermöglicht es Systemen,
  Nachrichten miteinander auszutauschen.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-kafka/blob/master/WIE-LAUFEN.md)

* [Atom](https://github.com/ewolff/microservice-atom) erwendet REST /
  HTTP für die asynchrone Kommunikation im Atom-Format.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-atom/blob/master/WIE-LAUFEN.md)

* [Istio](https://github.com/ewolff/microservice-istio) erweitert das
  oben genannte Atom-Beispiel und verwendet den
  Istio-Service-Mesh. Das Beispiel zeigt auch Monitoring mit
  Prometheus und Grafana, Tracing mit Jaeger, Logging mit
  Elasticsearch und Kibana, sowie auch Resilience mit Retry, Timeout
  und Circuit Breaker.
  - [Englische Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-istio/blob/master/HOW-TO-RUN.md)

* Die [Dapr-Demo](https://github.com/ewolff/microservice-dapr)
  erweitert das oben genannte Atom-Beispiel und nutzt Dapr . Das
  Beispiel unterstützt Monitoring mit Prometheus und Grafana, Tracing
  mit Zipkin, sowie auch Resilienz mit Retry und Circuit Breaker.
  - [Englische Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-dapr/blob/master/HOW-TO-RUN.md)

* [Spring](https://github.com/ewolff/microservice-spring) extends the
  erweitert das oben genannte Atom-Beispiel und nutzt Micrometer.io
  für Tracing und Metriken sowie Resilience4J für Resilience.
  - [Englische Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-spring/blob/main/HOW-TO-RUN.md)

## UI Integration

Die Integration über die Benutzeroberfläche (UI) ermöglicht eine sehr
lose Kopplung:

* Die [ESI-Demo](https://github.com/ewolff/SCS-ESI) zeigt, wie Edge
  Side Includes (ESI) verwendet werden können, um die
  Benutzeroberfläche von Microservices zu integrieren. Ein
  Microservice ist in Java mit Spring Boot geschrieben, der andere in
  Go. Der Go-Microservice wird mit mehrstufigen Docker-Containern
  erstellt.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/SCS-ESI/blob/master/WIE-LAUFEN.md)

* Das [jQuery-Beispiel](https://github.com/ewolff/SCS-jQuery) zeigt,
  wie jQuery verwendet werden kann, um die Benutzeroberfläche von
  Microservices zu integrieren.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/SCS-jQuery/blob/master/WIE-LAUFEN.md)

* [Crimson
  Assurance](https://github.com/ewolff/crimson-assurance-demo) ist
  eine komplexere Demonstration für eine Frontend-Integration. Die
  Website für jede Demo erklärt, wie die Demo erstellt und gestartet
  werden kann.
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/crimson-insurance-demo/blob/master/WIE-LAUFEN.md)

## Continuous Delivery

* ["User Registration"](https://github.com/ewolff/user-registration-V2/)
zeigt alle Teile einer Continuous Delivery-Pipeline mit einer einfachen [Demo-Anwendung](https://github.com/ewolff/user-registration-V2/tree/master/user-registration-application).
  - [Jenkins](https://github.com/ewolff/user-registration-V2/tree/master/ci-setup)  als CI-Server
  - nstallation von Software mit [Chef](https://github.com/ewolff/user-registration-V2/tree/master/chef).
  - [Graphite](https://github.com/ewolff/user-registration-V2/tree/master/graphite) für das Monitoring.
  - [Log
    Analyse](https://github.com/ewolff/user-registration-V2/tree/master/log-analysis)
    mit dem Elastic Stack.
  - [Akzeptanztests](https://github.com/ewolff/user-registration-V2/tree/master/user-registration-acceptancetest-jbehave) mit JBehave.
  - [Akzeptanztests](https://github.com/ewolff/user-registration-V2/tree/master/user-registration-acceptancetest-selenium) mit Selenium.
  - [Kapazitätstest](https://github.com/ewolff/user-registration-V2/tree/master/user-registration-capacitytest-gatling) mit Gatling
