# syntax=docker/dockerfile:1
FROM golang:1.16 AS builder
WORKDIR /usr/src/app
COPY Code.go ./
# GO111MODULE=off forces Go to behave the GOPATH way, 
# even outside of GOPATH.
# Erro: go: go.mod file not found in current directory 
# or any parent directory; see 'go help modules'
RUN go env -w GO111MODULE=off
RUN go get -d -v
RUN go build -o .

FROM scratch
WORKDIR /root/
COPY --from=builder /usr/src/app ./
CMD ["./app"]