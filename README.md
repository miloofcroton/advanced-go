# advanced go

This is a playground for a lot of different go frameworks and tools. I want to carry some of this work into other architectures that I try to build.

## tech choices

- kubernetes/docker (duh)
- go
- consul
- go-micro
- protobuf
- hystrix
- kafka
- rabbitmq

## directories

### gin-web

This is an exploration of [gin-gonic](https://github.com/gin-gonic/gin), an http framework.

### consul-web

This is an exploration of [consul] for service discovery and configuration.

### consul-core

Run this to use with consul-simple. It's just a barebones setup.

### consul-simple

- run `consul-core` first
- server has microservice registration with consul
- client has microservice lookup with consul

### consul-k8s

- start with `kubectl apply -f cluster`
- server has microservice registration with consul
- client has microservice lookup with consul

### go-micro

- uses consul for service discovery
- implements RPC with ProtoBuf
  - 1 producer, 2 MOM (one for each direction), 1 consumer
- uses hystrix
  - 1 producer, 1 MOM, 1 consumer
- uses go-micro

### go-rabbitmq

- implements async messaging with work queues and rabbitmq
  - 1 producer, 1 MOM, n-consumers

### go-kafka

- implements topic-based async pub-sub communication with kafka
  - 1 producer, n-MOMs, n-consumers
- implements broadcasting with zookeeper
  - 1 producer, 1-MOM, 0 to n-consumers

