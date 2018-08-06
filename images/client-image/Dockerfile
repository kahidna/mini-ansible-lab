FROM rastasheep/ubuntu-sshd:latest

MAINTAINER Alfin Hidayat <https://github.com/kahidna>

RUN apt-get update && apt-get install -y python inetutils-ping vim nano

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
