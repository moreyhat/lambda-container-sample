FROM golang:latest AS builder

WORKDIR /go/src/app
COPY app .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM public.ecr.aws/lambda/go:latest
COPY --from=builder /go/src/app/app /var/task
CMD ["app"]