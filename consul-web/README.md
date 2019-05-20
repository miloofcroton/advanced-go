# consul

## start consul

Start consul-web with gin-web:

```shell
docker-compose up
```
## consul web UI

Open a browser to `http://localhost:8500/` and browse to the KV section.

## consul CLI

Pre-reqs:
- install `consul` via `brew install consul`

No port configuration necessary because it's already running on the default port, 8500

### create, read, update and delete key-value pairs

```shell
consul kv get example/key
consul kv put example/key "Hello World."

consul kv put foo bar
consul kv get foo

consul kv put foo zip
consul kv get foo

consul kv delete foo
consul kv delete example/key
```

## consul HTTP API

Pre-reqs:
- Import the supplied Postman JSON collection file and use them to do the following
- Have Postman

### register agents

`PUT` to `http://localhost:8500/v1/agent/service/register`

header:
```
{
    "Content-Type": "application/json"
}
```

body:
```
{
  "ID": "gin-web-01",
  "Name": "gin-web",
  "Tags": [
    "advanced-go",
    "v1"
  ],
  "Address": "gin-web-01",
  "Port": 8080,
  "EnableTagOverride": false,
  "check": {
    "id": "ping",
    "name": "HTTP API on port 8080",
    "http": "http://gin-web-01:8080/ping",
    "interval": "5s",
    "timeout": "1s"
  }
}
```

and for the second service, with everything else the same:

```
{
  "ID": "gin-web-02",
  "Name": "gin-web",
  "Tags": [
    "advanced-go",
    "v1"
  ],
  "Address": "gin-web-02",
  "Port": 9090,
  "EnableTagOverride": false,
  "check": {
    "id": "ping",
    "name": "HTTP API on port 9090",
    "http": "http://gin-web-02:9090/ping",
    "interval": "5s",
    "timeout": "1s"
  }
}
```

### deregister agents

`PUT` to `http://localhost:8500/v1/agent/service/deregister/gin-web-01`

header:
```
{
    "Content-Type": "application/json"
}
```

body:
```
{
  "ID": "gin-web-01",
  "Name": "Gin Web",
  "Tags": [
    "advanced-go",
    "v1"
  ],
  "Address": "gin-web-01",
  "Port": 8080,
  "EnableTagOverride": false,
  "Check": {
    "DeregisterCriticalServiceAfter": "5m",
    "HTTP": "http://gin-web-01:8080/ping",
    "Interval": "10s",
    "TTL": "15s"
  }
}
```

`PUT` to `http://localhost:8500/v1/agent/service/deregister/gin-web-02`

(the header and body is the same)


## health checks

For the example microservice we will call the `/ping` endpoints periodically to check their health.
When everythin is running OK, stop one of the **gin-web** containers. One of the health checks will
become unhealthy. Then start again, and the service should become healthy again.
