
# Basic Authentication Squid Docker

Minimal docker image with [Squid] that only proxies authenticated requests and (optionally) only to certain domains.

Forked from: https://github.com/dafinley/squid-proxy-basic-auth

## Prerequisites

You will need to have [Docker] installed.

## Usage

Run the container:
```bash
docker run -d -e PROXY_USERNAME=user -e PROXY_PASSWORD=pass -p 3128:3128 ghcr.io/visa-overwatch/squid-proxy-basic-auth
```

You will need to replace ```user``` and ```pass``` in the command above by the username and password you want to use.

To use the proxy, open a new terminal and test it:

```bash
curl --proxy-basic --proxy-user user:pass --proxy http://127.0.0.1:3128 https://api.ipify.org
```

In production, you will need to replace ```http://127.0.0.1:3128``` by the real ip / port.

License
----

BSD

   [squid]: <http://www.squid-cache.org/>
   [docker]: <https://docs.docker.com/engine/install/>
