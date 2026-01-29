FROM golang:1.22-alpine AS build

WORKDIR /app
COPY . .

RUN go build -ldflags="-w -s" -o monero-node

FROM alpine:latest AS run

WORKDIR /app

COPY --from=build /app/monero-node ./monero-node

EXPOSE 80

CMD ["./monero-node"]
