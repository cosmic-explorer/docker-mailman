FROM debian:bookworm-slim as base

ARG FQDN

ENV DEBIAN_FRONTEND=noninteractive
ENV FQDN=${FQDN}

RUN apt update && apt upgrade -y &&\
    apt install -y apache2 apache2-utils supervisor build-essential \
                   libexpat1-dev libapache2-mod-authnz-external libapache2-mod-auth-openidc \
                   tmux vim curl ksh tcl openssl cmake rsync \
                   telnet lynx less 

RUN apt install -y libcgi-untaint-perl cpanminus j2cli

COPY docker/proxy.j2 /tmp/

RUN j2 /tmp/proxy.j2 > /etc/apache2/sites-available/proxy.conf &&\
    a2ensite proxy.conf && \
    a2dissite 000-default && \
    a2enmod cgid proxy proxy_http rewrite ssl authnz_external include ldap authnz_ldap


COPY docker/supervisord.conf /etc/supervisord.conf

CMD [ "/usr/bin/supervisord" ]
