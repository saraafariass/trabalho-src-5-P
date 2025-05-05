FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y slapd ldap-utils

# Define senha padrão "admin" para o admin
RUN echo "slapd slapd/no_configuration boolean false" | debconf-set-selections && \
    echo "slapd slapd/password1 password admin" | debconf-set-selections && \
    echo "slapd slapd/password2 password admin" | debconf-set-selections && \
    dpkg-reconfigure -f noninteractive slapd

EXPOSE 389

CMD ["/usr/sbin/slapd", "-d", "0"]
