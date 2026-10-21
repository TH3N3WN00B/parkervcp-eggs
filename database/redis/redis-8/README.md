# Redis

## From their [Website](https://redis.io/)

Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.

## Redis Version

This egg uses the `ghcr.io/parkervcp/yolks:redis_8` image, which is built on `redis:8-bookworm` and always ships the latest Redis 8.2.x release.
The exact version is printed in the console on every start (`redis_version:...`).

## Server Startup

You must first authenticate before trying to execute commands, to do this run `AUTH <YOUR_PASSWORD_HERE>` (without the `<>`). This should be the same as the password set in the `SERVER_PASSWORD` variable.

The server is marked as started once Redis answers a `PING`, so it only shows as running when it is ready to accept connections.

## Minimum RAM warning

It's recommended to have 4gb of RAM for redis

See here <https://docs.redislabs.com/latest/rs/administering/designing-production/hardware-requirements/>

## Server Ports

Ports required to run the server in a table format.

| Port    | default |
|---------|---------|
| Server  |  6379   |
