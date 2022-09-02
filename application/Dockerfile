FROM golang as compiler

WORKDIR /app

COPY go.mod ./
RUN go mod download
COPY *.go ./

RUN CGO_ENABLED=0 go build .

## Build image from scratch
FROM scratch

COPY --from=compiler /app/hello .
EXPOSE 8080

CMD ["./hello"]
