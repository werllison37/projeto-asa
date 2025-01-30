FROM ubuntu:latest 

RUN apt-get update -y 

RUN apt-get install bind9 dnsutils -y

COPY named.conf.local /etc/bind
COPY db.barreta.com.br /etc/bind
COPY db.buzios.com.br /etc/bind
COPY db.pirangi.com.br /etc/bind

EXPOSE 53/tcp
EXPOSE 53/udp

CMD ["/usr/sbin/named", "-g", "-c", "/etc/bind/named.conf", "-u", "bind"]