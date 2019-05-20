# go-micro

## Pre-reqs

Assuming you're using vscode, install the `vscode-proto3` extension to get syntax highlighting.

## Building the server and client

```bash
$ docker-compose build
$ docker images
```

## Running the server and client

```bash
$ docker-compose up
```

## Access the Hystrix dashboard

Open a browser at the following URL: http://localhost:9002/hystrix/

Add the following URL to monitor: http://go-micro-client:8081/hystrix.stream

