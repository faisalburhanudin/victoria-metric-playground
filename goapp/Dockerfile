FROM golang:1.21.1 AS builder

# Copy the code from the host and compile it
WORKDIR /home
COPY . ./
RUN go mod vendor
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .

FROM scratch
COPY --from=builder /app ./
ENTRYPOINT ["./app"]