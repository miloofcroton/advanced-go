# advanced go

This is a playground for a lot of different go frameworks and tools. I want to carry some of this work into other architectures that I try to build.

## gin-web

This is an exploration of [gin-gonic](https://github.com/gin-gonic/gin), an http framework.

## consul-web

This is an exploration of [consul] for service discovery and configuration.

## consul-core

Run this to use with consul-simple. It's just a barebones setup.

## consul-simple

- run `consul-core` first
- server has microservice registration with consul
- client has microservice lookup with consul

## consul-k8s

- start with `kubectl apply -f cluster`
- server has microservice registration with consul
- client has microservice lookup with consul
