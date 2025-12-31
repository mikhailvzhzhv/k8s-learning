FROM golang:1.25 AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o backend-service .


FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/backend-service /app/

CMD ["./backend-service"]