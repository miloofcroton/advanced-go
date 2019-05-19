FROM golang:1.8.1-alpine

ENV SOURCES /go/src/github.com/miloofcroton/advanced-go/consul-k8s/
COPY . ${SOURCES}

RUN cd ${SOURCES}server/ && CGO_ENABLED=0 go build

WORKDIR ${SOURCES}server/
CMD ${SOURCES}server/server
