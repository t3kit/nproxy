# docker compose configuration to start nginx proxy to use with t3kit project.

[Based on Automated Nginx Reverse Proxy for Docker](https://github.com/jwilder/nginx-proxy)

We need it for an easier way to handle several t3kit projects in one local machine. The main advantage of it is just to use one VIRTUAL_HOST env variable to separate it from other projects

## Usage

- Clone this repository
- Run `docker compose up` inside of the cloned folder

Also, there is possibility to start nginx proxy container using just Docker

```shell
docker network create nproxy
docker run -d -p=80:80 --name=nproxy --restart=unless-stopped --network=nproxy -v=/var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy
```

***

Here is a [typo3 v9 installation](https://github.com/t3kit/t3kit-starter) using this approach with all needed documentation to start. Just copy this repo into two separate folders, install composer dependency, change VIRTUAL_HOST in .env file and start docker compose to test it.
