FROM golang:1.8.1-alpine

RUN apk update && apk upgrade && apk add --no-cache bash git build-base

RUN go get github.com/Shopify/sarama

ENV SOURCES /go/src/github.com/miloofcroton/advanced-go/go-kafka/
COPY . ${SOURCES}

RUN cd ${SOURCES}subscriber/ && CGO_ENABLED=0 go build

ENV BROKER_ADDR localhost:9092

WORKDIR ${SOURCES}subscriber/
CMD ${SOURCES}subscriber/subscriber
