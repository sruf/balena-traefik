# balena-traefik

[traefik](https://containo.us/traefik/) stack for balenaCloud to proxy https domains to services on the same balena application


## Requirements

- RaspberryPi3, RaspberryPi4, or a similar device supported by BalenaCloud
- Available domain with one of the supported DNS providers (see https://doc.traefik.io/traefik/v2.4/https/acme/#providers)
- Subdomains for each service (service.example.com) or a wildcard subdomain pointing to the balena device


## Getting Started

You can one-click-deploy this project to balena using the button below:

[![](https://balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/klutchell/balena-traefik&defaultDeviceType=raspberry-pi)


## Manual Deployment

Alternatively, deployment can be carried out by manually creating a [balenaCloud account](https://dashboard.balena-cloud.com) and application, flashing a device, downloading the project and pushing it via either Git or the [balena CLI](https://github.com/balena-io/balena-cli).


### Application Environment Variables

Application envionment variables apply to all services within the application, and can be applied fleet-wide to apply to multiple devices.

|Name|Example|Purpose|
|---|---|---|
|`ACME_EMAIL`   |`foo@bar.com`      |email address to use for LetsEncrypt ACME registration|
|`DNS_PROVIDER` |`inwx`             |DNS provider; refer to https://doc.traefik.io/traefik/v2.4/https/acme/#providers|
|`MAIN_URL`     |`url.tld`          |tld domain
|`INWX_USERNAME`|`username`         |username for the DNS provider (if you do not use INWX, you will need to adapt the name of the environment variable)
|`INWX_PASSWORD`|`password`         |password for the DNS provider
|`LOG_LEVEL`    |`INFO`             |can be `INFO` or `DEBUG`
|`USERS`        |`[\"user:pass\"]`  |array of htpasswd created user:pass combinations; quotation marks must be escaped


## Usage

Add each service to your docker-compose.yml file. Indicate the subdomain on which the service should be made available by traefik as a label. If you want to use a different TLD for a service, you will need to specify a separate traefik router and certResolver. 


## Contributing

Please open an issue or submit a pull request with any features, fixes, or changes.


## References

- <https://docs.traefik.io/v2.2/https/tls/>
- <https://docs.traefik.io/v2.2/https/acme/>
- <https://docs.traefik.io/v2.2/middlewares/basicauth/>
- <https://docs.traefik.io/v2.2/middlewares/headers/>
- <https://ssl-config.mozilla.org/>
- <https://docs.linuxserver.io/images/docker-letsencrypt>
- <https://github.com/linuxserver/reverse-proxy-confs>

## License

[MIT License](./LICENSE)
