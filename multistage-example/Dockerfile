FROM golang:1.12.6-alpine3.10 AS builder
ADD . /app/backend
WORKDIR /app/backend
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -o /main .

# final stage
FROM alpine:latest
COPY --from=builder /main ./
RUN chmod +x ./main
ENTRYPOINT ["./main"]
EXPOSE 3030