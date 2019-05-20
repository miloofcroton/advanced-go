FROM golang:1.10.0-alpine

RUN apk update && apk upgrade && apk add --no-cache bash git

RUN go get github.com/micro/protobuf/proto
RUN go get -u github.com/micro/protobuf/protoc-gen-go
RUN go get -u github.com/micro/micro

ENV SOURCES /go/src/github.com/miloofcroton/advanced-go/go-micro/
COPY . ${SOURCES}

RUN cd ${SOURCES}server/ && CGO_ENABLED=0 go build

ENV CONSUL_HTTP_ADDR localhost:8500

WORKDIR ${SOURCES}server/
CMD ${SOURCES}server/server
