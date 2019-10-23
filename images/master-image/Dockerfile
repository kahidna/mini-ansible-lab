FROM rastasheep/ubuntu-sshd:latest

MAINTAINER Alfin Hidayat <https://github.com/kahidna>

RUN apt-get update && apt-get install -y ansible ansible-lint inetutils-ping vim nano

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
