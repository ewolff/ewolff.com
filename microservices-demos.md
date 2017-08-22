# Microservices Demos

## Synchronous Communication

* [Consul-Demo](https://github.com/ewolff/microservice-consul) written
  in Java with Spring Cloud / Boot. Uses Consul for service discovery,
  Apache httpd for routing, Hystrix for resilience and Ribbon for load
  balancing. It also provides a Prometheus installation for monitoring
  and an ELK stack implementation for lag analysis.


* [Netflix-Demo](https://github.com/ewolff/microservice) written
  in Java with Spring Cloud / Boot. Uses Netflix Eureka for service discovery,
  Netflix Zuul for routing, Hystrix for resilience and Ribbon for load
  balancing.

* [Kubernetes](https://github.com/ewolff/microservice-kubernetes)
  written in Java with Spring Cloud / Boot. Uses Kubernetes for
  service discovery, routing and load balancing.  The demo also uses
  Hystrix for resilience. The code does not depend on Kubernetes.

* [Cloud Foundry](https://github.com/ewolff/microservice-cloudfoundry)
  written in Java with Spring Cloud / Boot. Uses Cloud Foundry for
  deployment, service discovery, routing and load balancing.  The demo
  also uses Hystrix for resilience. The code does not depend on
  Cloud Foundry.

## Asynchronous Communication

* [Kafka](https://github.com/ewolff/microservice-kafka) uses Kafka for
communication.

* [Atom](https://github.com/ewolff/microservice-atom) uses REST / HTTP
  for asynchronous communication with the Atom format.

## UI Integration

* [ESI](https://github.com/ewolff/SCS-ESI) shows how Edge Side
Includes (ESI) can be used to integrate the UI of microservices. On
microservice is written in Java with Spring Boot, the other one with
Go. The Go microservices is built using multi stage Docker containers.

* [jQuery](https://github.com/ewolff/SCS-jQuery) shows how jQuery can
  be used to integrate the UI of microservices.
