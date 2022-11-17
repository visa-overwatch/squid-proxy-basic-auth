
# Basic Authentication Squid Docker

Minimal docker image with [Squid] that only proxies authenticated requests and (optionally) only to certain domains.

Forked from: https://github.com/dafinley/squid-proxy-basic-auth

## Prerequisites

You will need to have [Docker] installed.

## Usage

Clone the repo:

```bash
git clone https://github.com/anisgandoura/squid-proxy-basic-auth.git
cd squid-proxy-basic-auth
```

Build the Docker Image

```bash
docker build -t squid-auth:1.0 .
```

Create the new container from the squid-auth:1.0 image

```bash
docker run -d -e PROXY_USERNAME=my_user_name_example -e PROXY_PASSWORD=random_password_as_example --network host squid-auth:1.0
```

If you want to limit network scope, use this command instead:
```bash
docker run -d -e PROXY_USERNAME=my_user_name_example -e PROXY_PASSWORD=random_password_as_example -p 3128:3128 squid-auth:1.0
```

You will need to replace ```my_user_name_example``` and ```random_password_as_example``` in the command above by the username and password you want to use.

To use the proxy, open a new terminal and test it:

```bash
curl --proxy-basic --proxy-user my_user_name_example:random_password_as_example --proxy http://127.0.0.1:3128 https://api.ipify.org
```

In production, you will need to replace ```http://127.0.0.1:3128``` by the real ip / port.

License
----

BSD

   [squid]: <http://www.squid-cache.org/>
   [docker]: <https://docs.docker.com/engine/install/>
