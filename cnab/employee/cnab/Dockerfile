FROM alpine:latest

ENV HELM_VERSION="v2.11.0"
ENV KUBE_VERSION="v1.11.3"

RUN apk update

RUN apk add --update ca-certificates curl \
 && apk add --update -t deps wget \
 && wget https://storage.googleapis.com/kubernetes-helm/helm-${HELM_VERSION}-linux-amd64.tar.gz \
 && tar -xvf helm-${HELM_VERSION}-linux-amd64.tar.gz \
 && mv linux-amd64/helm /usr/local/bin \
 && curl -LO https://storage.googleapis.com/kubernetes-release/release/${KUBE_VERSION}/bin/linux/amd64/kubectl \
 && mv ./kubectl /usr/local/bin \
 && chmod 755 /usr/local/bin/kubectl \
 && apk del --purge deps curl \
 && rm /var/cache/apk/*

RUN helm init -c

COPY Dockerfile cnab/Dockerfile
COPY app/ /cnab/app/


