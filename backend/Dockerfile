FROM golang:1.16-buster AS build

WORKDIR /app

# Download necessary Go modules
COPY go.mod ./
COPY go.sum ./
RUN go mod download

COPY *.go ./

RUN go build -o /backend

FROM gcr.io/distroless/base-debian10

WORKDIR /

COPY --from=build /backend /backend

EXPOSE 8080

USER nonroot:nonroot

ENTRYPOINT ["/backend"]