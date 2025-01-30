FROM ubuntu:latest

RUN apt-get update --fix-missing -y

RUN apt-get upgrade -y

RUN apt-get install postfix -y

RUN apt install dovecot-imapd dovecot-pop3d -y

COPY main.cf /etc/postfix

# Add User
RUN useradd -m bob
RUN useradd -m patrick
RUN useradd -m werllison
RUN useradd -m redes

# Set user password
RUN echo "bob:redes"|chpasswd
RUN echo "patrick:redes"|chpasswd
RUN echo "werllison:redes"|chpasswd
RUN echo "redes:redes"|chpasswd

CMD ["postfix", "start-fg"]