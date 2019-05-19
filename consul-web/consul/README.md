# Service Discovery with Consul

## Start and Run Consul

Start consul-web with gin-web:

```bash
$ docker-compose up
```

## Exploring the HTTP API

Import the supplied Postman JSON collection file and perform the HTTP calls.

## Healtch Checks

For the example microservice we will call the `/ping` endpoints periodically to check their health.
When everythin is running OK, stop one of the **gin-web** containers. One of the health checks will
become unhealthy. The start again, and the service should become healthy again.
