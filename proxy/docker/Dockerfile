FROM nginx:1.27.3

ARG FQDN

ENV DEBIAN_FRONTEND=noninteractive
ENV FQDN=${FQDN}

RUN apt update && apt upgrade -y && \
    apt install -y build-essential wget less vim telnet dnsutils

COPY docker/nginx.conf /etc/nginx

