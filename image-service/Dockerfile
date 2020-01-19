FROM golang:latest
ENV GO111MODULE=on
ENV GOPROXY=https://goproxy.io
COPY . /build
WORKDIR /build
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GOARM=6 go build -ldflags '-w -s' -o app

FROM scratch
COPY --from=0 /build/app /
EXPOSE 8081
ENTRYPOINT ["/app"]


