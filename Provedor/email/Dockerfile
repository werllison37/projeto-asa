FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive 

RUN apt-get update --fix-missing -y && \
    apt-get upgrade -y && \
    apt-get install -y \
    postfix \
    dovecot-imapd \
    dovecot-pop3d \
    rsyslog && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

COPY main.cf /etc/postfix

COPY ./dovecot/dovecot.conf /etc/dovecot/dovecot.conf

COPY ./dovecot/10-auth.conf /etc/dovecot/conf.d

COPY ./dovecot/10-ssl.conf /etc/dovecot/conf.d/

COPY ./dovecot/10-mail.conf /etc/dovecot/conf.d/10-mail.conf

CMD ["sh", "-c", "service syslog-ng start ; service postfix start ; service dovecot start; tail -F /var/log/mail.log"]