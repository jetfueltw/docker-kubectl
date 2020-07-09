# build stage
FROM alpine:latest AS builder

ENV KUBECTL_VERSION=v1.18.5

RUN set -ex && \
    apk add --no-cache curl && \
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl

# final stage
FROM alpine:latest

WORKDIR /usr/local/bin

COPY --from=builder /kubectl .
