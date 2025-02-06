FROM ubuntu:latest

RUN apt-get update --fix-missing -y

RUN apt-get upgrade -y

RUN apt-get install postfix -y

RUN apt install dovecot-imapd dovecot-pop3d -y

COPY main.cf /etc/postfix

COPY ./dovecot/10-auth.conf /etc/dovecot/conf.d

COPY ./dovecot/10-ssl.conf /etc/dovecot/conf.d/

COPY ./dovecot/10-mail.conf /etc/dovecot/conf.d/10-mail.conf

CMD ["sh", "-c", "service syslog-ng start ; service postfix start ; service dovecot start; tail -F /var/log/mail.log"]