---
title: "Microservices Demos"
---

# Microservices Demos

## Synchronous Communication

* The [Consul demo](https://github.com/ewolff/microservice-consul) is written
  in Java with Spring Cloud / Boot. The demo uses Consul for service discovery,
  Apache httpd for routing, Hystrix for resilience and Ribbon for load
  balancing. It also provides a
  [Prometheus installation](https://github.com/ewolff/microservice-consul#prometheus)
  for monitoring 
  and an
  [ELK stack](https://github.com/ewolff/microservice-consul#elastic-stack)
  for log analysis.

* The [Netflix demo](https://github.com/ewolff/microservice) uses the
  Netflix stack. The demo is written
  in Java with Spring Cloud / Boot. It uses Netflix Eureka for service discovery,
  Netflix Zuul for routing, Hystrix for resilience and Ribbon for load
  balancing.

* Kubernetes is a system to run Docker containers in a cluster. The
  [Kubernetes demo](https://github.com/ewolff/microservice-kubernetes)
  is written in Java with Spring Cloud / Boot. It uses Kubernetes for
  service discovery, routing and load balancing.  The demo also uses
  Hystrix for resilience. The code does not depend on Kubernetes.

* Cloud Foundry is a PaaS. It provides an application with an
  environment to run in. The
  [Cloud Foundry demo](https://github.com/ewolff/microservice-cloudfoundry)
  is written in Java with Spring Cloud / Boot. Uses Cloud Foundry for
  deployment, service discovery, routing and load balancing.  The demo
  also uses Hystrix for resilience. The code does not depend on Cloud
  Foundry.

## Asynchronous Communication

* [Kafka](https://github.com/ewolff/microservice-kafka) uses Kafka for
communication. Kafka is a message-oriented middleware and allows
systems to send messages to one another.

* [Atom](https://github.com/ewolff/microservice-atom) uses REST / HTTP
  for asynchronous communication with the Atom format.

## UI Integration

* [ESI](https://github.com/ewolff/SCS-ESI) shows how Edge Side
Includes (ESI) can be used to integrate the UI of microservices. On
microservice is written in Java with Spring Boot, the other one with
Go. The Go microservices is built using multi stage Docker containers.

* [jQuery](https://github.com/ewolff/SCS-jQuery) shows how jQuery can
  be used to integrate the UI of microservices.
