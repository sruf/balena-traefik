FROM traefik:v2.4

COPY traefik.toml /var/traefik/traefik.toml
COPY entrypoint.sh /entrypoint.sh

RUN mkdir -p /etc/traefik
WORKDIR /etc/traefik

VOLUME /var/certs

EXPOSE 80/tcp 443/tcp 8080/tcp

RUN apk add --no-cache gettext \
    && chmod +x /entrypoint.sh
