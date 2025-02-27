FROM debian:latest

RUN apt-get update && apt-get install -y openssh-server

RUN mkdir /var/run/sshd

RUN useradd -m -s /bin/bash werllison && echo 'werllison:asa' | chpasswd && usermod -aG sudo werllison

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config

RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

RUN chmod 755 /var/run/sshd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
