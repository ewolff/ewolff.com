---
title: "Microservices Demos"
---

# Microservices Demos

## Synchronous Communication

There are several options for synchronous communication between microservices:

* The [Consul demo](https://github.com/ewolff/microservice-consul) is
written in Java with Spring Cloud / Boot. The demo uses Consul for
service discovery, Apache httpd for routing, Hystrix for resilience
and Ribbon for load balancing. It also provides a
[Prometheus installation](https://github.com/ewolff/microservice-consul#prometheus)
for monitoring and an
[ELK stack](https://github.com/ewolff/microservice-consul#elastic-stack)
for log analysis.
  - [How to run](https://github.com/ewolff/microservice-consul/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-consul/blob/master/WIE-LAUFEN.md)

* The [Netflix demo](https://github.com/ewolff/microservice) uses the
  Netflix stack. The demo is written
  in Java with Spring Cloud / Boot. It uses Netflix Eureka for service discovery,
  Netflix Zuul for routing, Hystrix for resilience and Ribbon for load
  balancing.
  - [How to run](https://github.com/ewolff/microservice/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice/blob/master/WIE-LAUFEN.md)

* Kubernetes is a system to run Docker containers in a cluster. The
  [Kubernetes demo](https://github.com/ewolff/microservice-kubernetes)
  is written in Java with Spring Cloud / Boot. It uses Kubernetes for
  service discovery, routing and load balancing.  The demo also uses
  Hystrix for resilience. The code does not depend on Kubernetes.
  - [How to run](https://github.com/ewolff/microservice-kubernetes/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-kubernetes/blob/master/WIE-LAUFEN.md)

* Cloud Foundry is a PaaS. It provides an application with an
  environment to run in. The
  [Cloud Foundry demo](https://github.com/ewolff/microservice-cloudfoundry)
  is written in Java with Spring Cloud / Boot. Uses Cloud Foundry for
  deployment, service discovery, routing and load balancing.  The demo
  also uses Hystrix for resilience. The code does not depend on Cloud
  Foundry.
  - [How to run](https://github.com/ewolff/microservice-cloudfoundry/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-cloudfoundry/blob/master/WIE-LAUFEN.md)

## Asynchronous Communication

Asynchronous communication makes it easier to deal with unreliable
networks and services:

* [Kafka](https://github.com/ewolff/microservice-kafka) uses Kafka for
communication. Kafka is a message-oriented middleware and allows
systems to send messages to one another.
  - [How to run](https://github.com/ewolff/microservice-kafka/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-kafka/blob/master/WIE-LAUFEN.md)

* [Atom](https://github.com/ewolff/microservice-atom) uses REST / HTTP
  for asynchronous communication with the Atom format.
  - [How to run](https://github.com/ewolff/microservice-atom/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/microservice-atom/blob/master/WIE-LAUFEN.md)

## UI Integration

UI integration provides very loose coupling:

* [ESI](https://github.com/ewolff/SCS-ESI) shows how Edge Side
Includes (ESI) can be used to integrate the UI of microservices. On
microservice is written in Java with Spring Boot, the other one with
Go. The Go microservices is built using multi stage Docker containers.
  - [How to run](https://github.com/ewolff/SCS-ESI/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/SCS-ESI/blob/master/WIE-LAUFEN.md)

* [jQuery](https://github.com/ewolff/SCS-jQuery) shows how jQuery can
  be used to integrate the UI of microservices.
  - [How to run](https://github.com/ewolff/SCS-jQuery/blob/master/HOW-TO-RUN.md)
  - [Deutsche Anleitung zum Starten des Beispiels](https://github.com/ewolff/SCS-jQuery/blob/master/WIE-LAUFEN.md)

The website for each demo explains how the demo can be built and
started.
