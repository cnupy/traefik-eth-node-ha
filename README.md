# Overview

Traefik Ethereum nodes deployment in high availability failover mode.

You will need a HTTP service to monitor both execution and consensus

client health in order for failover to work. The health monitoring 

service should return HTTP 200 OK if the node is in sync and has enough peers,

otherwise HTTP status above 400.

See: https://github.com/cnupy/ethnode-health

# How to run

`cp .env.example .env` and edit `.env` 

- set `TRAEFIK_LISTEN_IP` or leave `0.0.0.0` to listen on all host IPs,

- set `EC_LISTEN_HOST` and `CC_LISTEN_HOST` to set execution and consensus client hosts

- set main and backup execution and consensus client URLs, ports and http scheme (`http` or `https`)

- set network name and whether the network is internal or external

To start the container execute:

`docker compose build && docker compose up -d`

# ToDo

Enable HTTPS entry point and ACME provider (like Let's Encrypt) automatic certificate generation.