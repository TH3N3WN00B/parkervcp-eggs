# Redis

## From their [Website](https://redis.io/)

Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.

## Server Startup

The console is already authenticated with the password set in the `SERVER_PASSWORD` variable, so commands such as `SAVE` or `INFO` can be run directly.

The server is marked as started once Redis answers a `PING`, so it only shows as running when it is ready to accept connections.

## Minimum RAM warning

It's recommended to have 4gb of RAM for redis

See here <https://docs.redislabs.com/latest/rs/administering/designing-production/hardware-requirements/>

## Server Ports

Ports required to run the server in a table format.

| Port    | default |
|---------|---------|
| Server  |  6379   |
