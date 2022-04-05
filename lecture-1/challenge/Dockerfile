# syntax=docker/dockerfile:1

FROM golang:1.18-alpine
WORKDIR /build/
COPY go.mod ./
RUN go mod download
COPY *.go ./
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o go-hello-world .

FROM scratch
WORKDIR /app/
COPY --from=0 /build/go-hello-world ./

CMD [ "./go-hello-world" ]
