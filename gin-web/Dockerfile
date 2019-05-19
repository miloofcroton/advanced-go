# FROM golang:1.8.1-alpine
# LABEL maintainer="Jack Toumey"

# RUN apk update && apk upgrade && apk add --no-cache bash git
# RUN go get github.com/gin-gonic/gin

# ENV SOURCES /go/src/github.com/miloofcroton/advanced-go/gin-web/
# COPY ./gin-web ${SOURCES}/gin-web

# RUN chmod +x /go/src/github.com/miloofcroton/advanced-go/gin-web/gin-web

# WORKDIR ${SOURCES}
# CMD ${SOURCES}gin-web
# EXPOSE 8080


FROM golang:1.8.1-alpine

RUN apk update && apk upgrade && apk add --no-cache bash git
RUN go get github.com/gin-gonic/gin

ENV SOURCES /go/src/github.com/miloofcroton/advanced-go/gin-web/
COPY . ${SOURCES}

RUN cd ${SOURCES} && CGO_ENABLED=0 go build

WORKDIR ${SOURCES}
CMD ${SOURCES}gin-web
EXPOSE 8080
