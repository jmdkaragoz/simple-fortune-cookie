FROM golang:1.16-buster AS build

WORKDIR /app


COPY go.mod ./
COPY ./static ./static
COPY ./templates ./templates
RUN pwd
RUN ls -la
RUN ls -la /app
RUN ls -la ./templates
RUN ls -la ./static
#COPY go.sum ./
RUN go mod download

COPY *.go ./

RUN go build -o /frontend

##
## Deploy
##

FROM ubuntu

WORKDIR /

COPY --from=build /frontend /frontend

EXPOSE 8080

#USER nonroot:nonroot

ENTRYPOINT ["/frontend"]
